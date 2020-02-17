---
title: AEM-formulieren verharden en beveiligen op OSGi-omgeving
seo-title: AEM-formulieren verharden en beveiligen op OSGi-omgeving
description: Leer aanbevelingen en beste praktijken voor het beveiligen van Vormen AEM op server OSGi.
seo-description: Leer aanbevelingen en beste praktijken voor het beveiligen van Vormen AEM op server OSGi.
uuid: abca7e7c-38c3-44f5-8d8a-4615cfce26c6
topic-tags: Security
discoiquuid: b1bd04bf-0d6d-4e6b-8c7c-eafd1a24b5fe
translation-type: tm+mt
source-git-commit: 5120bbdefea528ad6d07a9c99df565555b6a8444

---


# AEM-formulieren verharden en beveiligen op OSGi-omgeving {#hardening-and-securing-aem-forms-on-osgi-environment}

Leer aanbevelingen en beste praktijken voor het beveiligen van Vormen AEM op server OSGi.

Het beveiligen van een serveromgeving is van het grootste belang voor een organisatie. In dit artikel worden aanbevelingen en aanbevolen procedures beschreven voor het beveiligen van servers waarop AEM Forms wordt uitgevoerd. Dit is geen uitgebreid host-hardend document voor uw besturingssysteem. In plaats daarvan, beschrijft dit artikel diverse veiligheid-verhardende montages die u zou moeten uitvoeren om de veiligheid van uw opgestelde toepassing te verbeteren. Om ervoor te zorgen dat de toepassingsservers veilig blijven, echter, zou u veiligheid controle, opsporing, en reactieprocedures naast aanbevelingen ook moeten uitvoeren die in dit artikel worden verstrekt. Het document bevat ook beproefde methoden en richtlijnen voor het beveiligen van PII (Persoonlijk identificeerbare informatie).

Het artikel is bedoeld voor consultants, beveiligingsspecialisten, systeemarchitecten en IT-professionals die verantwoordelijk zijn voor de planning van de toepassing of de ontwikkeling van de infrastructuur en de implementatie van AEM Forms. Deze rollen omvatten de volgende gemeenschappelijke rollen:

* IT en de ingenieurs van verrichtingen die veilige Webtoepassingen en servers in hun eigen of klantenorganisaties moeten opstellen.
* Architecten en planners die verantwoordelijk zijn voor de planning van de architectuurinspanningen voor de klanten in hun organisaties.
* IT-beveiligingsspecialisten die zich richten op het bieden van beveiliging op alle platforms binnen hun organisatie.
* Consultants van Adobe en partners die gedetailleerde bronnen voor klanten en partners nodig hebben.

Het volgende beeld toont componenten en protocollen die in een typische plaatsing van Vormen AEM, met inbegrip van de aangewezen firewalltopologie worden gebruikt:

![typische architectuur](assets/typical-architecture.png)

AEM Forms is zeer aanpasbaar en kan in veel verschillende omgevingen werken. Sommige aanbevelingen zijn mogelijk niet van toepassing op uw organisatie.

## Beveiligde transportlaag {#secure-transport-layer}

De kwetsbaarheid van de laagveiligheid van het vervoer is onder de eerste bedreigingen aan om het even welke Internet-Onder ogen ziet of intranet-Onder ogen ziet toepassingsserver. Deze sectie beschrijft het proces om gastheren op het netwerk tegen deze kwetsbaarheid te verharden. Het richt netwerksegmentatie, de stapelverharding van het Protocol van de Controle van de Transmissie/van Internet-protocol (TCP/IP), en het gebruik van firewalls voor gastheerbescherming.

### Open eindpunten beperken {#limit-open-endpoints}

Een organisatie kan een externe firewall hebben om toegang tussen een eindgebruiker en AEM Forms te beperken publiceer Farm. De organisatie kan een interne firewall ook hebben om toegang tussen te beperken publiceer landbouwbedrijf en andere binnen organisatieelementen (bijvoorbeeld, auteursinstantie, verwerkingsinstantie, gegevensbestanden). firewalls toestaan toegang tot een beperkt aantal URL&#39;s van AEM-formulieren voor eindgebruikers en binnen organisaties toe te staan:

#### Externe firewall configureren {#configure-external-firewall}

U kunt een externe firewall zo configureren dat bepaalde URL&#39;s van AEM-formulieren toegang hebben tot internet. U hebt toegang tot deze URL&#39;s nodig als u een adaptief formulier, HTML5, letter voor correspondentiebeheer of als u zich wilt aanmelden bij een AEM Forms-server:

<table> 
 <tbody>
  <tr>
   <td>Component</td> 
   <td>URI</td> 
  </tr>
  <tr>
   <td>Aangepaste formulieren</td> 
   <td>
    <ul> 
     <li>/content/dam/formsanddocuments/AF_PATH/jcr:content</li> 
     <li>/etc/clientlibs/fd/</li> 
     <li>/content/forms/af/AF_PATH</li> 
     <li>/libs/graniet/csrf/</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>HTML5-formulieren</td> 
   <td>
    <ul> 
     <li>/content/forms/formsets/profiles/</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Correspondentenbeheer </td> 
   <td>
    <ul> 
     <li>/aem/forms/createcorrespondence* </li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Forms Portal </td> 
   <td>
    <ul> 
     <li>/content/forms/portal/</li> 
     <li>/libs/cq/ui/widgets*</li> 
     <li>/libs/cq/security/</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td> AEM Forms App</td> 
   <td>
    <ul> 
     <li>/j_security_check*</li> 
     <li>/soap/services/AuthenticationManagerService</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

#### Interne firewall configureren {#configure-internal-firewall}

U kunt de interne firewall vormen om bepaalde componenten van Vormen AEM (bijvoorbeeld, auteursinstantie, verwerkingsinstantie, gegevensbestanden) toe te staan om met te communiceren publiceer landbouwbedrijf en andere interne componenten die in het topologiediagram worden vermeld:

<table> 
 <tbody>
  <tr>
   <td>Host<br /> </td> 
   <td>URI</td> 
  </tr>
  <tr>
   <td>Farm publiceren (publicatieknooppunten)</td> 
   <td>/bin/receive</td> 
  </tr>
  <tr>
   <td>Verwerkingsserver</td> 
   <td>/content/forms/fp/*</td> 
  </tr>
  <tr>
   <td>Forms Workflow add-on server (AEM Forms on JEE server)</td> 
   <td>/soap/sdk</td> 
  </tr>
 </tbody>
</table>

#### Machtigingen van de bewaarplaats van de opstelling en toegangsbeheerlijsten (ACLs) {#setup-repository-permissions-and-access-control-lists-acls}

Standaard zijn de middelen op de publicatieknooppunten toegankelijk voor iedereen. Alleen-lezen toegang is ingeschakeld voor alle elementen. Het is vereist anonieme toegang toe te laten. Als u de formulierweergave wilt beperken en alleen voor geverifieerde gebruikers toegang wilt geven, gebruikt u een algemene groep om alleen geverifieerde gebruikers alleen-lezentoegang te geven tot de elementen die beschikbaar zijn op de publicatieknooppunten. De volgende locaties/mappen bevatten formulierelementen die verharding vereisen (alleen-lezen toegang voor geverifieerde gebruikers):

* /content/&amp;ast;
* /etc.clientlibs/fd/&amp;ast;
* /libs/fd/&amp;ast;

## Formuliergegevens veilig verwerken {#securely-handle-forms-data}

In AEM Forms worden gegevens opgeslagen op vooraf gedefinieerde locaties en tijdelijke mappen. U moet de gegevens beveiligen om onbevoegd gebruik te voorkomen.

### Periodieke opschoning van tijdelijke map instellen {#setup-periodic-cleanup-of-temporary-folder}

Wanneer u formulieren configureert voor bestandsbijlagen, controleert u of voorbeeldcomponenten, worden de bijbehorende gegevens opgeslagen op de publicatieknooppunten op /tmp/fd/. De gegevens worden periodiek gewist. U kunt de standaardtaak voor het wissen van gegevens wijzigen en deze agressiever maken. Als u de taak die is gepland voor het wissen van gegevens wilt wijzigen, opent u AEM Web Console, opent u de tijdelijke taak Opslag opschonen in AEM-formulieren en wijzigt u de expressie Uitsnijden.

In de bovenstaande scenario&#39;s worden de gegevens alleen opgeslagen voor geverifieerde gebruikers. Bovendien wordt het gegeven beschermd met toegangsbeheerlijsten (ACLs). Het wijzigen van de gegevenswissing is dus een extra stap om informatie te beveiligen.

### Beveiligde gegevens opgeslagen door verzendactie van formulierportal {#secure-data-saved-by-forms-portal-submit-action}

Standaard slaat de verzendactie van een portal Formulieren met aangepaste formulieren gegevens op in de lokale opslagplaats van het publicatieknooppunt. De gegevens worden opgeslagen op /content/forms/fp. **Het wordt afgeraden gegevens op te slaan in een publicatie-instantie.**

U kunt de opslagdienst vormen om over-de-draad naar de verwerkingscluster te verzenden zonder om het even wat plaatselijk op te slaan publiceer knoop. De verwerkingscluster bevindt zich in een veilige zone achter de privéfirewall en de gegevens blijven veilig.

Gebruik de referenties van de verwerkingsserver voor de AEM DS-instellingenservice om gegevens van het publicatieknooppunt naar de verwerkingsserver te posten. Het wordt aanbevolen referenties te gebruiken van een niet-administratieve gebruiker met lees-schrijftoegang tot de opslagplaats van de verwerkingsserver. Voor meer informatie, zie het [Vormen de opslagdiensten voor concepten en voorlegging](/help/forms/using/configuring-draft-submission-storage.md).

### Beveiligde gegevens die worden verwerkt door FDM (Form Data Model) {#secure-data-handled-by-form-data-model-fdm}

Gebruik gebruikersaccounts met minimaal vereiste rechten om gegevensbronnen voor het formuliergegevensmodel (FDM) te configureren. Het gebruik van een beheeraccount kan onbevoegde gebruikers toegang bieden tot metagegevens en schema-entiteiten.\
De integratie van gegevens verstrekt ook methodes om FDM de dienstverzoeken toe te laten. U kunt machtigingsmechanismen vóór en na uitvoering invoegen om een aanvraag te valideren. De serviceaanvragen worden gegenereerd tijdens het vooraf invullen van een formulier, het verzenden van een formulier en het aanroepen van services via een regel.

**** Voorafgaande goedkeuring: U kunt de pre-procesvergunning gebruiken om authentificatie van een verzoek te bevestigen alvorens het uit te voeren. U kunt input, de dienst en verzoekdetails gebruiken om uitvoering van het verzoek toe te staan of tegen te houden. U kunt een uitzondering OPERATION_ACCESS_DENIED van de gegevensintegratie terugkeren als de uitvoering wordt tegengehouden. U kunt ook de clientaanvraag wijzigen voordat u deze ter uitvoering verzendt. U kunt bijvoorbeeld de invoer wijzigen en aanvullende informatie toevoegen.

**** Autorisatie na verwerking: U kunt de postprocesvergunning gebruiken om de resultaten te bevestigen en te controleren alvorens de resultaten aan aanvrager terug te keren. U kunt ook aanvullende gegevens filteren, verwijderen en invoegen.

### Gebruikerstoegang beperken {#limit-user-access}

Voor auteur-, publicatie- en verwerkingsinstanties is een andere set met gebruikersinstellingen vereist. Voer geen enkel exemplaar met beheerdersreferenties uit.

**Op een publicatie-instantie:**

* Alleen gebruikers van een groep met formuliergebruikers kunnen formulieren voorvertonen, ontwerpen maken en verzenden.
* Alleen gebruikers van een cm-user-agent-groep kunnen een voorbeeld van correspondentiebeheerletters bekijken.
* Alle niet-essentiële anonieme toegang uitschakelen.

**Op een instantie van de auteur:**

* Er is een andere set vooraf gedefinieerde groepen met specifieke rechten voor elke persoon. Wijs gebruikers toe aan groep.

   * Een gebruiker van een gebruikersgroep voor formulieren:

      * U kunt een formulier maken, invullen, publiceren en verzenden.
      * kan geen adaptief formulier op basis van XDP maken.
      * geen machtigingen hebben om scripts voor adaptieve formulieren te schrijven.
      * kan XDP of een pakket dat XDP bevat niet importeren
   * Een gebruiker van een gebruikersgroep voor formulieren maakt, vult, publiceert en verzendt alle typen formulieren, schrijft scripts voor adaptieve formulieren en importeert pakketten met XDP.
   * Een gebruiker van malplaatje-auteurs en malplaatje-macht-gebruiker kan voorproef en een malplaatje creëren.
   * Een gebruiker van fdm-auteurs kan een model van vormgegevens tot stand brengen en wijzigen.
   * Een gebruiker van cm-user-agent groep kan correspondentiebeheerbrieven creëren, voorproef, en publiceren.
   * Een gebruiker van een groep workfloweditors kan een inbox-toepassing en workflowmodel maken.


**Bij de verwerkingsauteur:**

* Voor het op afstand opslaan en verzenden van gebruiksgevallen maakt u een gebruiker met lees-, maak- en wijzigingsmachtigingen voor de inhoud/het formulier/fp-pad van de crx-gegevensopslagruimte.
* Voeg een gebruiker toe aan een groep met workflowgebruikers om een gebruiker in staat te stellen AEM-inbox-toepassingen te gebruiken.

## Beveiligde intranetelementen van een AEM Forms-omgeving {#secure-intranet-elements-of-an-aem-forms-environment}

Over het algemeen worden clusters en Forms Workflow Add-on (AEM Forms on JEE) uitgevoerd achter een firewall. Deze zijn dus veilig. U kunt nog steeds een paar stappen uitvoeren om deze omgevingen te beschadigen:

### Veilig verwerkingscluster {#secure-processing-cluster}

Een verwerkingscluster wordt uitgevoerd in de auteursmodus, maar gebruikt deze niet voor ontwikkelingsactiviteiten. Sta niet toe dat een normale gebruiker wordt opgenomen in de groepen van inhoudsauteurs en gebruikers van formulieren in een verwerkingscluster.

### Gebruik de beste praktijken van AEM om een milieu van Vormen te beveiligen AEM {#use-aem-best-practices-to-secure-an-aem-forms-environment}

Dit document bevat specifieke instructies voor de omgeving van AEM Forms. U zou moeten nemen om ervoor te zorgen dat uw onderliggende installatie AEM wanneer opgesteld veilig is. Zie de documentatie van de [AEM-beveiligingscontrolelijst](/help/sites-administering/security-checklist.md) voor gedetailleerde instructies.
