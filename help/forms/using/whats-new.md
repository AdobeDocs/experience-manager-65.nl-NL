---
title: Overzicht van nieuwe functies| AEM 6.5-formulieren
seo-title: Overzicht van nieuwe functies| AEM 6.5-formulieren
description: Nieuwste functies en verbeteringen in formulieren en documenten van de meest geavanceerde oplossing voor het beheer van digitale ervaringen ter wereld.
seo-description: Nieuwste functies en verbeteringen in formulieren en documenten van de meest geavanceerde oplossing voor het beheer van digitale ervaringen ter wereld.
uuid: 179d372d-b7f6-4771-8349-fc6b7854efac
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 0e949429-cd5f-4301-aa72-14803cdfab00
docset: aem65
translation-type: tm+mt
source-git-commit: 726163106ddb80600eaa7cc09b1a2e9b035a223e

---


# Overzicht van nieuwe functies| AEM 6.5-formulieren{#new-features-summary-aem-forms}

## Transactierapporten {#transaction-reports}

Met transactierapporten kunt u het aantal verzonden formulieren, verwerkte documenten en gerenderde documenten vastleggen en bijhouden. Het doel van het volgen van deze transacties is een geïnformeerde beslissing te nemen over het gebruik van producten en het opnieuw in evenwicht brengen van investeringen in hardware en software. Voorbeelden van transacties zijn:

* Verzending van een adaptief formulier, een HTML5-formulier of een formulierset
* Vertoning van een gedrukte versie of webversie van een interactieve communicatie
* Een document omzetten van de ene bestandsindeling naar de andere

Voor informatie over het vormen van en het gebruiken van transactierapporten, zie het Overzicht [van de Rapporten van de](../../forms/using/transaction-reports-overview.md)Transactie.

![Een voorbeeldtransactierapport](assets/surface_transaction_reporting.png)

## Interactieve communicatie {#interactive-communications}

**Patronen voor gegevensweergave definiëren**

Interactieve auteurs van communicatie kunnen nu [gegevenspatronen](create-interactive-communication.md#datadisplaypatterns) definiëren voor velden, variabelen en formuliergegevensmodelelementen. Bijvoorbeeld datum-, valuta- of telefoonnotaties.

**Nieuwe typen grafieken gebruiken**

U kunt grafieken van het [Kwadrant en grafieken met veelvoudige reeksen](../../forms/using/chart-component-interactive-communications.md) aan Interactieve Mededelingen nu toevoegen.

**Kolommen in een tabel sorteren**

U kunt kolommen van een lijst [in Interactieve Mededeling nu](../../forms/using/create-interactive-communication.md#sortcolumns) sorteren. U kunt tabelkolommen binden en sorteren met statische tekst of gegevensmodelobjecten.

**Nieuwe componenten in een webkanaal gebruiken**

U kunt nu knopcomponenten en scheidingscomponenten aan het webkanaal toevoegen. Zie De component Button [toevoegen aan het webkanaal](../../forms/using/create-interactive-communication.md#add-button-component-to-the-web-channel) en de [scheidingscomponent in het webkanaal](../../forms/using/create-interactive-communication.md#separatorcomponent)voor meer informatie.

**Lay-outmodus om het formaat van componenten te wijzigen**

U kunt nu op de wijze [van de](../../forms/using/resize-using-layout-mode.md) Lay-out schakelen resize componenten in het kanaal van het Web gebruikend een interface WYSIWYG.

**Verbeteringen in bruikbaarheid**

De interactieve auteurs van de Communicatie kunnen nu diverse makkelijk te gebruiken verrichtingen gebruiken terwijl het creëren van correspondentie. De lijst van concrete acties omvat:

* [Handelingen voor ongedaan maken uitvoeren in afdruk- en webkanalen](../../forms/using/create-interactive-communication.md#undoredoactions)
* [Variabelen in een documentfragment toevoegen met @-symbool](../../forms/using/texts-interactive-communications.md#searchvariables)
* [Gegevensmodelelementen toevoegen aan een documentfragment met @-symbool](../../forms/using/texts-interactive-communications.md#searchdatamodelproperties)
* [Een webkanaal verwijderen of toevoegen aan een bestaande interactieve communicatie](../../forms/using/create-interactive-communication.md#edit-interactive-communication-properties)
* [Gegevensbronelementen binden met velden en variabelen met behulp van handelingen voor slepen en neerzetten](../../forms/using/create-interactive-communication.md#binddatasourceelements)
* [Niet-gebonden velden en variabelen markeren tijdens het ontwerpen van interactieve communicatie](../../forms/using/create-interactive-communication.md#distinguishunboundfields)
* [Extra handelingen zoals kopiëren, groeperen of meer uitvoeren op overgeërfde componenten in een webkanaal](../../forms/using/create-interactive-communication.md#componenttoolbar)

**Verbeteringen in synchronisatieproces**

De webkanaallay-out die automatisch wordt gegenereerd met het kanaal Afdrukken is op verschillende manieren verbeterd.

![Interactieve communicatieteksten](assets/interactive-communication-charts.png)

## Adaptieve formulieren {#adaptive-forms}

### Digitale handtekeningen op basis van de cloud van Adobe Sign gebruiken in Adaptive Forms {#use-adobe-sign-s-cloud-based-digital-signatures-in-adaptive-forms}

[Digitale handtekeningen](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) op basis van cloud&#39;s of externe handtekeningen zijn een nieuwe generatie digitale handtekeningen die werken op verschillende computers, mobiele apparaten en het web. Ze voldoen aan de hoogste standaarden voor verificatie van ondertekenaars. U kunt nu een adaptief formulier [](../../forms/using/working-with-adobe-sign.md) ondertekenen met digitale handtekeningen op basis van de cloud.

#### Een adaptief formulier of interactieve communicatie insluiten in toepassingen voor één pagina voor AEM-sites {#embed-an-adaptive-form-or-interactive-communcation-in-aem-sites-single-page-applications}

Met AEM Forms kunt u [naadloos een adaptief formulier](../../forms/using/embed-adaptive-form-aem-sites-spa.md) of interactieve communicatie insluiten in een toepassing voor één pagina (SPA) voor AEM-sites. Het ingesloten adaptieve formulier en de interactieve communicatie zijn volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd communiceren met het adaptieve formulier of de interactieve communicatie.

#### Kolommen van Adaptief formulier sorteren {#sort-columns-of-adaptive-form-tables}

U kunt elke kolom van een tabel [Adaptief formulier oplopend of aflopend](../../forms/using/adaptive-forms-tables.md#sortcolumnstable) sorteren. U kunt sorteren toepassen op tabelkolommen met statische tekst, eigenschappen van gegevensmodelobjecten of een combinatie van eigenschappen van statische tekst en gegevensmodelobjecten.

#### De beschikbaarheid van adaptieve formuliersjablonen beperken tot specifieke paden {#restrict-the-availability-of-adaptive-forms-templates-to-specific-paths}

Aangepaste formulieren hebben ondersteuning toegevoegd voor de eigenschap cq:allowedPaths. De eigenschap [beperkt de beschikbaarheid van adaptieve Forms-sjablonen tot specifieke paden](../../forms/using/creating-adaptive-form.md#main-pars-text).

#### Selectievakjes dynamisch toevoegen aan het adaptieve formulier {#add-check-boxes-to-the-adaptive-form-dynamically}

U kunt nu regels definiëren om selectievakjes dynamisch [toe te](../../forms/using/rule-editor.md#setpropertyrule) voegen aan het adaptieve formulier op basis van een aangepaste functie, een formulierobject of een objecteigenschap.

## AEM-workflows {#aem-workflows}

### Variabelen gebruiken in AEM-workflows {#use-variables-in-aem-workflows}

Met variabelen kunnen workflowstappen metagegevens tijdens runtime bevatten en doorgeven. U kunt verschillende typen variabelen maken om verschillende typen gegevens op te slaan. Bijvoorbeeld gehele getallen, tekenreeksen, documenten of exemplaren van het formuliergegevensmodel. Typisch, gebruikt u een variabele of een inzameling van variabelen wanneer u een besluit moet nemen dat op de waarde wordt gebaseerd die het houdt of informatie opslaat die u later in een proces nodig hebt.

Variabelen zijn een uitbreiding van de [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) -interface die beschikbaar is in de vorige versie. Hiermee kunt u tijd besparen die is besteed aan het ontwikkelen van aangepaste ECMAScript-code die wordt gebruikt om metagegevenswaarden op te halen en bij te werken. U kunt de MetaDataMap-interface en ECMAScript-code blijven gebruiken om metagegevens te bewerken. Het gebruik van variabelen via MetaDataMap en ECMAScript biedt onder andere de volgende voordelen:

* Waarden die zijn opgeslagen in een variabele over de gehele workflow dynamisch opslaan, bijwerken en gebruiken zonder dat aangepaste code nodig is
* Waarden rechtstreeks ophalen en bijwerken naar een formuliergegevensmodel en gegevensbestand (XML/JSON) van een verzonden formulier
* Voltooide documenten in een variabele opslaan om de documentverwerking uit te voeren

De stap Ga naar OF Splitsen en alle workflowstappen van AEM Forms ondersteunen variabelen. Met de MetaDataMap-interface hebt u toegang tot variabelen in workflowstappen die geen native ondersteuning voor variabelen bevatten. Zie [Variabelen in AEM-workflows](../../forms/using/variable-in-aem-workflows.md)voor meer informatie.

![Een variabele instellen voor in een workflow](assets/variable.png)

#### Een workflow met verschillende adaptieve formulieren gebruiken {#use-a-workflow-with-different-adaptive-forms}

U kunt een adaptief formulier [opgeven voor het toewijzen van een taak](../../forms/using/aem-forms-workflow-step-reference.md#assign-task-step) en een document met een recordstap van formuliergerichte workflows in de runtime. Hiermee kan een workflow met verschillende adaptieve formulieren werken. U kunt de methode kiezen om een adaptief formulier te selecteren tijdens het ontwerpen van de workflow. Het adaptieve formulier kan zich bevinden op een absoluut pad, worden verzonden als een payload naar de workflow of beschikbaar zijn op een pad dat is berekend met een variabele.

#### Uitgebreide logboekmogelijkheden van op formulieren gerichte workflowstappen gebruiken {#use-enhanced-logging-capabilities-of-forms-centric-workflow-steps}

Logboekmogelijkheden van op formulieren gerichte workflowstappen zijn gestandaardiseerd. Nu produceren alle werkstroomstappen op basis van formulieren gestandaardiseerde logbestanden. De foutopsporingssnelheid wordt hierdoor verbeterd.

## Gegevensintegratie {#data-integration}

U kunt nu:

* [Valideer invoergegevens](../../forms/using/work-with-form-data-model.md#automated-validation-of-input-data) op basis van een lijst met beperkingen. Hiermee zorgt u ervoor dat alleen geldige gegevens naar de gegevensbron worden verzonden.
* [Overschrijf standaardeindpunt](../../forms/using/configure-data-sources.md#configure-soap-web-services) dat in een WSDL (de Taal van de Beschrijving van de Diensten van het Web) wordt bepaald dossier.

* [Overschrijf het standaardschema](../../forms/using/configure-data-sources.md#configure-restful-web-services) , de host en het basispad [](../../forms/using/configure-data-sources.md#configure-restful-web-services) dat zijn gedefinieerd in het definitiebestand van de wagen.

## Platform- en beveiligingsupdates {#platform-and-security-updates}

### Belangrijkste platformupdates {#major-platform-updates}

AEM Forms kan worden ingesteld met elke combinatie van ondersteunde besturingssystemen, toepassingsservers, databases, databasestuurprogramma&#39;s, JDK, LDAP-servers en e-mailservers. De belangrijkste wijzigingen in [ondersteunde platforms](../../forms/using/aem-forms-jee-supported-platforms.md)zijn:

<table>
 <tbody>
  <tr>
   <td>Component</td>
   <td>Ondersteuning verwijderd</td>
  </tr>
  <tr>
   <td>Besturingssystemen</td>
   <td>
    <ul>
     <li>Microsoft Windows Server 2012 R2</li>
     <li>IBM AIX*</li>
     <li>Sun Solaris*</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Toepassingsservers<br /> </td>
   <td>
    <ul>
     <li>Oracle Weblogic</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Databases</td>
   <td>
    <ul>
     <li>IBM DB2 <br /> </li>
     <li>Oracle RAC</li>
    </ul> </td>
  </tr>
  <tr>
   <td>LDAP-servers</td>
   <td>
    <ul>
     <li>Microsoft Active Directory 2012</li>
     <li>Novell eDirectory 8.8.7 </li>
     <li>IBM Lotus Domino 8.5.0 </li>
    </ul> </td>
  </tr>
  <tr>
   <td>E-mailservers</td>
   <td>
    <ul>
     <li>IBM Lotus Domino 8.5.0 </li>
    </ul> </td>
  </tr>
  <tr>
   <td>Connectors</td>
   <td>
    <ul>
     <li>Connector voor Microsoft SharePoint 2013</li>
     <li>Connector voor EMC Documentum 7.0</li>
    </ul> </td>
  </tr>
  <tr>
   <td>AEM Forms-app<br /> </td>
   <td>
    <ul>
     <li>Ondersteuning voor Windows 8.1</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Java </td>
   <td>
    <ul>
     <li>Java 11</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

* Neem contact op met de Technische Ondersteuning van Adobe voor informatie over het migreren naar een ander platform

#### Nieuwe op HTML5 gebaseerde gebruikersinterface {#new-html-based-uis}

In lijn met de geplande EOL van Adobe Flash Player en de algemene richting voor het migreren van Flash-inhoud naar open standaarden, heeft AEM 6.5 Forms de op Flash gebaseerde UI van Health Monitor, Process Management, Reader Extension en Category Management UI van AEM Forms in JEE Administration Console vervangen door de op HTML5 gebaseerde UI.

#### Beveiligingsverbeteringen {#security-improvements}

* AEM 6.5 Forms on JEE administration console UI is nu gebaseerd op Apache Struts 2.5.
* AEM 6.5 Forms gebruikt nu jQuery naar 3.2.1 en jQuery UI 1.12.1. Zie, [verbeteringsdocumentatie](/help/forms/home.md) voor het effect van de verandering.

#### Toegankelijkheidsverbeteringen {#accessibility-improvements}

Met AEM 6.5-formulieren is de toegankelijkheid van de AEM Forms Workspace verbeterd.
