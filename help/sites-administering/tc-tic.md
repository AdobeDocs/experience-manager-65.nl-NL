---
title: Het Kader voor de Integratie van de Vertaling vormen
description: Leer hoe u het Translation Integration Framework in Adobe Experience Manager configureert.
contentOwner: Guillaume Carlino
feature: Language Copy
exl-id: 7562754b-d9fd-441b-8ae5-c7eebe458cef
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eb4c6ab188cc79eab66647433e60ba97eba6f257
workflow-type: tm+mt
source-wordcount: '1483'
ht-degree: 0%

---

# Het Kader voor de Integratie van de Vertaling vormen{#configuring-the-translation-integration-framework}

Het vertaalintegratiekader integreert met vertaaldiensten van derden om de vertaling van AEM inhoud te ordenen.

* Maak verbinding met uw vertaalserviceprovider.
* Creeer een configuratie van het Kader van de Integratie van de Vertaling.
* Koppel de cloudconfiguraties aan uw pagina&#39;s.

Voor een overzicht van de eigenschappen van de inhoudsomzetting in AEM, zie [ Vertaal Inhoud voor Meertalige Plaatsen ](/help/sites-administering/translation.md).

## Verbinding maken met een vertaalserviceprovider {#connecting-to-a-translation-service-provider}

Maak een cloudconfiguratie die AEM verbindt met uw vertaalserviceprovider. AEM biedt standaard de mogelijkheid verbinding te maken met Microsoft Translator.
De volgende vertaalverkopers verstrekken een implementatie van nieuwe API voor de Vertaalprojecten. Koppelingen voor meer informatie over de integratie:

* [ Translations.com ](https://exchange.adobe.com/experiencecloud.details.90104.globallink-connect-plus-for-aem.html)
* [ Lionbridge ](https://exchange.adobe.com/experiencecloud.details.100064.lionbridge-connector-for-experience-manager-63.html)
* [ Memsource ](https://exchange.adobe.com/apps/ec/103166/memsource-connector-for-adobe-experience-manager)
* [ de Wolk van XTM ](https://exchange.adobe.com/apps/ec/105037/xtm-connect-for-adobe-experience-manager)
* [ Lingotek ](https://exchange.adobe.com/apps/ec/90088/lingotek-collaborative-translation-platform)
* [ RWS ](https://exchange.adobe.com/apps/ec/108277/rws-language-cloud)
* [ Smartling ](https://www.smartling.com/software/integrations/adobe-experience-manager/)
* Microsoft (Microsoft Translator is vooraf geïnstalleerd in AEM)

>[!NOTE]
>
>Bekijk de volgende pagina&#39;s voor de meest recente lijst met aanbieders van vertalingen voor mensen en machines:
>
>* [ AEM Menselijke Vertaling ](https://exchange.adobe.com/apps/browse/ec?page=1&amp;partnerLevel=All&amp;product=AEM&amp;q=aem+human+translation&amp;sort=RELEVANCE)
>* [ AEM de Vertaling van de Machine ](https://exchange.adobe.com/apps/browse/ec?q=AEM+machine+translation&amp;product=All&amp;partnerLevel=All&amp;sort=RELEVANCE)
>

Nadat u een schakelaarpakket installeert, kunt u een wolkenconfiguratie voor de schakelaar creëren. Doorgaans moet u uw referenties opgeven voor verificatie bij de vertaalservice. Voor informatie over het toevoegen van een wolkenconfiguratie voor de Vertaalschakelaar van Microsoft, zie [ Integrerend met de Vertaler van Microsoft ](/help/sites-administering/tc-msconf.md).

Indien nodig kunt u meerdere cloudconfiguraties voor dezelfde aansluiting maken. U kunt bijvoorbeeld één configuratie maken voor elk van de accounts of projecten die u bij dezelfde leverancier hebt.

Nadat u een verbinding vormt, kunt u de configuratie tot stand brengen van het kader van de vertaalintegratie die het gebruikt.

## Een configuratie voor vertaalintegratie maken {#creating-a-translation-integration-configuration}

Maak een configuratie van het vertaalintegratieframework om op te geven hoe u uw inhoud wilt vertalen. De configuratie bevat de volgende informatie:

* Welke vertaalserviceprovider moet worden gebruikt.
* Of het vertalen van mensen of machines moet worden uitgevoerd.
* Of andere inhoud die aan een pagina of element is gekoppeld, zoals codes, moet worden vertaald.

Nadat u een kaderconfiguratie creeert, associeert u de wolkenconfiguratie met de pagina&#39;s die u volgens de configuratie wilt vertalen. Wanneer het vertaalproces wordt gestart, gaat de vertaalworkflow verder volgens de bijbehorende frameworkconfiguratie.

Wanneer verschillende gedeelten van uw website verschillende vertaalvereisten hebben, kunt u overeenkomstig meerdere frameworkconfiguraties maken. Een meertalige website bevat bijvoorbeeld kopieën in de Engelse, Spaanse en Japanse taal. De eigenaar van de site gebruikt twee verschillende vertaalserviceproviders voor Spaanse en Japanse vertalingen. Daarom worden twee configuraties van het kader gevormd. Elke configuratie gebruikt een verschillende leverancier van vertaaldiensten.

Nadat u een kader van de vertaalintegratie vormt, kunt u het [ associëren met de pagina&#39;s ](/help/sites-administering/tc-prep.md) die het gebruiken.

**Nota:** voor een overzicht van de eigenschappen van de inhoudsomzetting in AEM, zie [ Vertaal Inhoud voor Meertalige Plaatsen ](/help/sites-administering/translation.md).

Eén configuratie van het framework bepaalt hoe pagina-inhoud, community-inhoud en elementen moeten worden omgezet.
![ chlimage_1-386 ](assets/translation-config-65.jpg)

### Eigenschappen van siteconfiguratie {#sites-configuration-properties}

De eigenschappen Sites bepalen hoe de vertaling van pagina-inhoud wordt uitgevoerd.

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Vertaalworkflow</td>
   <td><p>Selecteer de vertaalmethode die het framework uitvoert voor site-inhoud:</p>
    <ul>
     <li>Machine Translation: de vertaalprovider voert de vertaling uit met automatische vertaling in real-time.</li>
     <li>Menselijke vertaling: de inhoud wordt naar de vertaler gestuurd om door vertalers te worden vertaald. </li>
     <li>Niet vertalen: inhoud wordt niet verzonden voor vertaling. Hiermee slaat u bepaalde vertakkingen met inhoud over die niet worden vertaald, maar wel kunnen worden bijgewerkt met de meest recente inhoud.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Vertaalbureau</td>
   <td>Selecteer de vertaalprovider voor de vertaling. Een leverancier verschijnt in de lijst wanneer hun overeenkomstige schakelaar wordt geïnstalleerd.</td>
  </tr>
  <tr>
   <td>Inhoudscategorie</td>
   <td>(Alleen machinevertaling) Een categorie die de inhoud beschrijft die u wilt vertalen. De categorie kan van invloed zijn op de keuze van terminologie en woordgebruik bij het vertalen van inhoud.</td>
  </tr>
  <tr>
   <td>Componenttekenreeksen omzetten</td>
   <td>Selecteer deze optie om componenttekenreeksen te vertalen van componenten die aan de pagina zijn gekoppeld.</td>
  </tr>
  <tr>
   <td>Tags vertalen</td>
   <td>Selecteer deze optie om codes te vertalen die aan de pagina zijn gekoppeld.</td>
  </tr>
  <tr>
   <td>Pagina Assets vertalen</td>
   <td><p>Selecteer hoe u elementen wilt vertalen die vanuit het bestandssysteem aan componenten worden toegevoegd of waarnaar vanuit Assets wordt verwezen:</p>
    <ul>
     <li>Niet vertalen: pagina-elementen worden niet vertaald.</li>
     <li>Het gebruiken van het vertaalwerkschema van Plaatsen: Assets wordt behandeld volgens de configuratieeigenschappen op het lusje van Plaatsen.</li>
     <li>Assets-vertaalworkflow gebruiken: Assets wordt verwerkt volgens de configuratie van de eigenschappen op het tabblad Assets.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Vertaling automatisch uitvoeren</td>
   <td>Selecteer deze optie om vertaaltaken automatisch uit te voeren nadat er vertaalprojecten zijn gemaakt. U hebt geen mogelijkheid om de vertaaltaak te beoordelen en te vergroten wanneer u deze optie selecteert.</td>
  </tr>
 </tbody>
</table>

### Eigenschappen van Gemeenschappen {#communities-configuration-properties}

De eigenschappen van Gemeenschappen bepalen hoe de vertaling van user-generated inhoud wordt uitgevoerd. Voor het vertalen van door de gebruiker gegenereerde inhoud wordt altijd machinevertaling gebruikt. Voor meer informatie, zie [ Vertaal Gebruiker Gegenereerde Inhoud ](/help/communities/translate-ugc.md).

| Eigenschap | Beschrijving |
|---|---|
| Vertaalbureau | Selecteer de vertaalprovider voor de vertaling. De provider waarvoor cloudconfiguraties worden gemaakt, wordt in de lijst weergegeven. |
| Inhoudscategorie | A category that describes the content that you are translating. De categorie kan van invloed zijn op de keuze van terminologie en woordgebruik bij het vertalen van inhoud. |
| Een landinstelling kiezen die u als algemene Share-winkel wilt gebruiken | (Optioneel) Als u een landinstelling selecteert voor het opslaan van UGC, worden posts van alle taalkopieën in één algemeen gesprek weergegeven. Door overeenkomst, kies de scène voor de [ basistaal ](/help/communities/sites-console.md#translation) voor de website. Als u Geen gemeenschappelijke winkel kiest, wordt de algemene vertaling uitgeschakeld. Globale vertaling is standaard uitgeschakeld. |

### Assets-configuratieeigenschappen {#assets-configuration-properties}

Assets-eigenschappen bepalen hoe elementen moeten worden geconfigureerd. Voor meer informatie over het vertalen van activa, zie [ Creërend de Kopieën van de Taal voor Assets ](/help/assets/translation-projects.md).

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Vertaalworkflow</td>
   <td><p>Selecteer het type vertaling dat het framework uitvoert voor elementen:</p>
    <ul>
     <li>Machinevertaling: de vertaalprovider voert de vertaling direct uit met behulp van machinevertaling.</li>
     <li>Menselijke vertaling: inhoud wordt automatisch naar de vertaalprovider verzonden om handmatig te worden vertaald. </li>
     <li>Niet omzetten: Assets wordt niet verzonden voor vertaling.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Vertaalbureau</td>
   <td>Selecteer de vertaalprovider voor de vertaling. Een leverancier verschijnt in de lijst wanneer hun overeenkomstige schakelaar wordt geïnstalleerd.</td>
  </tr>
  <tr>
   <td>Inhoudscategorie</td>
   <td>(Alleen machinevertaling) Een categorie die de inhoud beschrijft die u wilt vertalen. De categorie kan van invloed zijn op de keuze van terminologie en woordgebruik bij het vertalen van inhoud.</td>
  </tr>
  <tr>
   <td>Assets vertalen</td>
   <td>Selecteer deze optie om elementen op te nemen in het vertaalproject. </td>
  </tr>
  <tr>
   <td>Metagegevens vertalen</td>
   <td>Selecteer deze optie om metagegevens van elementen te vertalen.</td>
  </tr>
  <tr>
   <td>Tags vertalen</td>
   <td>Selecteer deze optie om tags te vertalen die aan het element zijn gekoppeld.</td>
  </tr>
  <tr>
   <td>Vertaling automatisch uitvoeren</td>
   <td>Selecteer deze optie om vertaaltaken automatisch uit te voeren nadat er vertaalprojecten zijn gemaakt. U hebt geen gelegenheid om de vertaalbaan te herzien of te behandelen wanneer u deze optie selecteert.</td>
  </tr>
 </tbody>
</table>

1. Klik in de zijbalk op Opties > Bewerkingen > Wolk > Cloud Servicen.
1. In het gebied van de Integratie van de Vertaling, bepaalt de vraag of om het even welke configuraties zijn gecreeerd welke verbinding verschijnt:

   * Als er geen configuraties zijn gemaakt, klikt u op Nu configureren.
   * Als er al configuraties zijn, klikt u op Configuraties tonen en vervolgens op de koppeling + naast Beschikbare configuraties.

1. Typ een naam voor de configuratie en klik vervolgens op Maken.
1. Configureer de eigenschappen op het tabblad Sites, Communities en Assets en klik vervolgens op OK.

## Pagina&#39;s voor omzetting configureren {#configuring-pages-for-translation}

Als u de vertaling van uw bronpagina&#39;s in andere talen wilt configureren, koppelt u de pagina&#39;s aan de volgende cloudconfiguraties:

* De wolkenconfiguratie die AEM met uw vertaalleverancier verbindt.
* Het kader voor vertaalintegratie dat de details van de vertaling vormt.

De cloudconfiguratie van het vertaalintegratieframework identificeert de cloudconfiguratie die moet worden gebruikt om verbinding te maken met de serviceprovider. Wanneer u een bronpagina aan een configuratie van de kaderwolk associeert, moet de pagina met de configuratie van de de dienstverlener wolk worden geassocieerd die de configuratie van de kaderwolk gebruikt.

Wanneer u een pagina aan een wolkenconfiguratie associeert, erven de nakomelingen van de pagina de vereniging. Als u bijvoorbeeld de pagina /content/geometrixx/nl/products aan een Translation Integration Framework koppelt, worden de pagina Producten en alle onderliggende pagina&#39;s vertaald volgens het framework.

Indien nodig, kunt u de koppeling op een afstammende pagina overschrijven. De inhoud van een website gaat bijvoorbeeld vooral over kleding. Eén vertakking met pagina&#39;s beschrijft het bedrijf echter. De hoofdpagina van de site is gekoppeld aan een vertaalintegratieframework dat automatische vertaling opgeeft met de categorie Koud. De tak die het bedrijf beschrijft gebruikt een kader dat machinevertaling gebruikend de Algemene categorie uitvoert.

Verder, voor om het even welke gemeenschappen [ SCF componenten ](/help/communities/scf.md) op de pagina&#39;s, zal de gebruiker geproduceerde inhoud (UGC) de capaciteit voor gebruikers omvatten om inhoud te vertalen. Voor meer informatie, zie [ Vertaling van Gebruiker Gegenereerde Inhoud ](/help/communities/translate-ugc.md).

### Een pagina koppelen aan een vertaalbureau {#associating-a-page-with-a-translation-provider}

Koppel een pagina aan de vertaalprovider die u gebruikt om de pagina en afstammende pagina&#39;s te vertalen.

1. Selecteer in de Sites-console de pagina die u wilt configureren en klik op Eigenschappen weergeven.
1. Klik op Bewerken en klik vervolgens op het tabblad Cloud Servicen.
1. Klik op Configuratie toevoegen > Translation Integration.
1. Selecteer de te gebruiken vertaalprovider en klik op Gereed.

### Pagina&#39;s koppelen aan een vertaalintegratieframework {#associating-pages-with-a-translation-integration-framework}

Koppel een pagina aan het vertaalintegratieframework dat definieert hoe u de vertaling van de pagina en afstammende pagina&#39;s wilt uitvoeren.

1. Selecteer in de Sites-console de pagina die u wilt configureren en klik op Eigenschappen weergeven.
1. Klik op Bewerken en klik vervolgens op het tabblad Cloud Servicen.
1. Klik op Configuratie toevoegen > Translation Integration.
1. Selecteer het te gebruiken kader van de vertaalintegratie, en klik dan Gedaan.
