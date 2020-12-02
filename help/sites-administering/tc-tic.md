---
title: Het framework voor vertaalintegratie configureren
seo-title: Het framework voor vertaalintegratie configureren
description: Leer hoe te om het Kader van de Integratie van de Vertaling te vormen.
seo-description: Leer hoe te om het Kader van de Integratie van de Vertaling te vormen.
uuid: 5ecfe154-732f-4a13-96f8-92f55023c54d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 200f51ab-f9bf-4989-91af-c3904fc673e5
translation-type: tm+mt
source-git-commit: 49b18b780c87501dcb2d9a00930da8eb5e51cff2
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 0%

---


# Het vormen van het Kader van de Integratie van de Vertaling{#configuring-the-translation-integration-framework}

Het vertaalintegratiekader integreert met vertaaldiensten van derden om de vertaling van AEM inhoud te ordenen.

* Verbind met uw vertaaldienstverlener.
* Creeer een configuratie van het Kader van de Integratie van de Vertaling.
* Koppel de cloudconfiguraties aan uw pagina&#39;s.

Zie [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md) voor een overzicht van de functies voor het vertalen van inhoud in AEM.

## Verbinding maken met een vertaalserviceprovider {#connecting-to-a-translation-service-provider}

Maak een cloudconfiguratie die AEM verbindt met uw vertaalserviceprovider. AEM biedt standaard de mogelijkheid verbinding te maken met Microsoft Translator.
De volgende vertaalverkopers verstrekken een implementatie van nieuwe API voor de Vertaalprojecten. Koppelingen voor meer informatie over de integratie:

* [Translations.com](https://exchange.adobe.com/experiencecloud.details.90104.globallink-connect-plus-for-aem.html) (Adobe Exchange Premier Partner)
* [Clay Tablet Technologieën](https://exchange.adobe.com/experiencecloud.details.90064.clay-tablet-translation-for-experience-manager.html)
* [Lionbridge](https://exchange.adobe.com/experiencecloud.details.100064.lionbridge-connector-for-experience-manager-63.html)
* [Memsource](https://exchange.adobe.com/experiencecloud.details.103166.memsource-connector-for-adobe-experience-manager.html)
* [Wolken](https://exchange.adobe.com/experiencecloud.details.90019.html)
* [CrossLang NV](https://exchange.adobe.com/experiencecloud.details.90049.crosslang-xtm-for-adobe-experience-manager.html)
* [Lingotek](https://exchange.adobe.com/experiencecloud.details.90088.lingotek-collaborative-translation-platform.html)
* [Smartling](https://exchange.adobe.com/experiencecloud.details.90101.smartling-connector-for-adobe-experience-manager.html)
* [SDL](https://exchange.adobe.com/experiencecloud.details.100110.sdl-translation-management.html)
* [Systran](https://exchange.adobe.com/experiencecloud.details.90233.systran-for-adobe-experience-manager.html)
* [Altlang](https://exchange.adobe.com/experiencecloud.details.90222.altlang.html)
* Microsoft (Microsoft Translator is vooraf geïnstalleerd in AEM)

>[!NOTE]
>
>Bekijk de volgende pagina&#39;s voor de meest recente lijst met aanbieders van vertalingen voor mensen en machines:
>
>
>* [AEM menselijke vertaling](https://www.adobe.com/go/aem-human-translation-connectors)
>* [AEM machinevertaling](https://www.adobe.com/go/aem-machine-translation-connectors)

>



Nadat u een schakelaarpakket installeert, kunt u een wolkenconfiguratie voor de schakelaar tot stand brengen. Doorgaans moet u uw referenties opgeven voor verificatie bij de vertaalservice. Voor informatie over het toevoegen van een wolkenconfiguratie voor de schakelaar van de Vertaler van Microsoft, zie [Integrating met de Vertaler van Microsoft](/help/sites-administering/tc-msconf.md).

Indien nodig kunt u meerdere cloudconfiguraties voor dezelfde aansluiting maken. U kunt bijvoorbeeld één configuratie maken voor elk van de accounts of projecten die u bij dezelfde leverancier hebt.

Nadat u een verbinding vormt, kunt u de configuratie tot stand brengen van het kader van de vertaalintegratie die het gebruikt.

## Een configuratie voor vertaalintegratie maken {#creating-a-translation-integration-configuration}

Maak een configuratie van het vertaalintegratieframework om op te geven hoe u uw inhoud wilt vertalen. De configuratie bevat de volgende informatie:

* Welke vertaalserviceprovider moet worden gebruikt.
* Of het vertalen van mensen of machines moet worden uitgevoerd.
* Of andere inhoud die aan een pagina of element is gekoppeld, zoals codes, moet worden vertaald.

Nadat u een kaderconfiguratie creeert, associeert u de wolkenconfiguratie met de pagina&#39;s die u volgens de configuratie wilt vertalen. Wanneer het vertaalproces wordt gestart, gaat de vertaalworkflow verder volgens de bijbehorende frameworkconfiguratie.

Wanneer verschillende gedeelten van uw website verschillende vertaalvereisten hebben, kunt u overeenkomstig meerdere frameworkconfiguraties maken. Een meertalige website bevat bijvoorbeeld kopieën in de Engelse, Spaanse en Japanse taal. De eigenaar van de site gebruikt twee verschillende vertaalserviceproviders voor Spaanse en Japanse vertalingen. Daarom worden twee configuraties van het kader gevormd. Elke configuratie gebruikt een verschillende leverancier van vertaaldiensten.

Nadat u een kader van de vertaalintegratie vormt, kunt u [het met de pagina&#39;s ](/help/sites-administering/tc-prep.md) associëren die het gebruiken.

**Opmerking:** Zie Inhoud  [omzetten voor meertalige sites](/help/sites-administering/translation.md) voor een overzicht van de functies voor het vertalen van inhoud in AEM.

Eén configuratie van het framework bepaalt hoe pagina-inhoud, community-inhoud en elementen moeten worden omgezet.
![chlimage_1-386](assets/translation-config-65.jpg)

### Site Configuration Properties {#sites-configuration-properties}

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
     <li>Machine transleren: De vertaalprovider voert de vertaling in real-time uit met automatische vertaling.</li>
     <li>Menselijke vertaling: De inhoud wordt naar de vertaalprovider verzonden en door vertalers vertaald. </li>
     <li>Niet vertalen: Inhoud wordt niet verzonden voor vertaling. Hiermee slaat u bepaalde vertakkingen met inhoud over die niet worden vertaald, maar wel kunnen worden bijgewerkt met de meest recente inhoud.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Vertaalbureau</td>
   <td>Selecteer de vertaalprovider om de vertaling uit te voeren. Een leverancier verschijnt in de lijst wanneer hun overeenkomstige schakelaar wordt geïnstalleerd.</td>
  </tr>
  <tr>
   <td>Inhoudscategorie</td>
   <td>(Alleen machinevertaling) Een categorie die de inhoud beschrijft die u wilt vertalen. De categorie kan van invloed zijn op de keuze van terminologie en woordgebruik bij het vertalen van inhoud.</td>
  </tr>
  <tr>
   <td>Tags vertalen</td>
   <td>Selecteer deze optie om codes te vertalen die aan de pagina zijn gekoppeld.</td>
  </tr>
  <tr>
   <td>Pagina-elementen vertalen</td>
   <td><p>Selecteer hoe u elementen wilt vertalen die vanuit het bestandssysteem aan componenten worden toegevoegd of waarnaar vanuit Middelen wordt verwezen:</p>
    <ul>
     <li>Niet vertalen: Pagina-elementen worden niet omgezet.</li>
     <li>Workflow voor het vertalen van sites gebruiken: De activa worden behandeld volgens de configuratieeigenschappen op het lusje van Plaatsen.</li>
     <li>Workflow voor het vertalen van middelen gebruiken: Elementen worden verwerkt volgens de configuratie van de eigenschappen op het tabblad Middelen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Vertaling automatisch uitvoeren</td>
   <td>Selecteer deze optie om vertaaltaken automatisch uit te voeren nadat er vertaalprojecten zijn gemaakt. U hebt geen mogelijkheid om de vertaaltaak te beoordelen en te vergroten wanneer u deze optie selecteert.</td>
  </tr>
 </tbody>
</table>

### Eigenschappen van Community-configuratie {#communities-configuration-properties}

De eigenschappen van Gemeenschappen bepalen hoe de vertaling van user-generated inhoud wordt uitgevoerd. Voor het vertalen van door de gebruiker gegenereerde inhoud wordt altijd machinevertaling gebruikt. Zie [Door gebruiker gegenereerde inhoud vertalen](/help/communities/translate-ugc.md) voor meer informatie.

| Eigenschap | Beschrijving |
|---|---|
| Vertaalbureau | Selecteer de vertaalprovider om de vertaling uit te voeren. De provider waarvoor cloudconfiguraties worden gemaakt, wordt in de lijst weergegeven. |
| Inhoudscategorie | A category that describes the content that you are translating. De categorie kan van invloed zijn op de keuze van terminologie en woordgebruik bij het vertalen van inhoud. |
| Een landinstelling kiezen die u als algemene Share-winkel wilt gebruiken | (Optioneel) Als u een landinstelling selecteert voor het opslaan van UGC, worden posts van alle taalkopieën in één algemeen gesprek weergegeven. Kies bij conventie de landinstelling voor de [basistaal](/help/communities/sites-console.md#translation) voor de website. Als u Geen gemeenschappelijke winkel kiest, wordt de algemene vertaling uitgeschakeld. Globale vertaling is standaard uitgeschakeld. |

### Eigenschappen voor middelenconfiguratie {#assets-configuration-properties}

De eigenschappen van activa bepalen hoe te om activa te vormen. Zie [Taalkopieën maken voor elementen](/help/assets/translation-projects.md) voor meer informatie over het vertalen van elementen.

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
     <li>Machine transleren: De vertaalprovider voert de vertaling direct uit met behulp van computervertaling.</li>
     <li>Menselijke vertaling: Inhoud wordt automatisch naar de vertaalprovider verzonden om handmatig te worden vertaald. </li>
     <li>Niet vertalen: Elementen worden niet verzonden voor vertaling.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Vertaalbureau</td>
   <td>Selecteer de vertaalprovider om de vertaling uit te voeren. Een leverancier verschijnt in de lijst wanneer hun overeenkomstige schakelaar wordt geïnstalleerd.</td>
  </tr>
  <tr>
   <td>Inhoudscategorie</td>
   <td>(Alleen machinevertaling) Een categorie die de inhoud beschrijft die u wilt vertalen. De categorie kan van invloed zijn op de keuze van terminologie en woordgebruik bij het vertalen van inhoud.</td>
  </tr>
  <tr>
   <td>Elementen vertalen</td>
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

1. Klik of tik in de zijbalk op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. In het gebied van de Integratie van de Vertaling, bepaalt of om het even welke configuraties zijn gecreeerd welke verbinding verschijnt:

   * Als er geen configuraties zijn gemaakt, klikt u of tikt u op Nu configureren.
   * Als er al configuraties zijn, klikt of tikt u op Configuraties tonen en klikt of tikt u op de +-koppeling naast Beschikbare configuraties.

1. Typ een naam voor de configuratie en klik op Maken of tik op Maken.
1. Configureer de eigenschappen op het tabblad Sites, Communities en Assets en klik of tik op OK.

## Pagina&#39;s configureren voor vertaling {#configuring-pages-for-translation}

Als u de vertaling van uw bronpagina&#39;s in andere talen wilt configureren, koppelt u de pagina&#39;s aan de volgende cloudconfiguraties:

* De wolkenconfiguratie die AEM met uw vertaalleverancier verbindt.
* Het vertaalintegratieframework dat de details van de vertaling configureert.

Merk op dat de cloudconfiguratie van het vertaalintegratieframework de cloudconfiguratie identificeert die moet worden gebruikt om verbinding te maken met de serviceprovider. Wanneer u een bronpagina aan een configuratie van de kaderwolk associeert, moet de pagina met de configuratie van de de dienstverlener wolk worden geassocieerd die de configuratie van de kaderwolk gebruikt.

Wanneer u een pagina aan een wolkenconfiguratie associeert, erven de nakomelingen van de pagina de vereniging. Als u bijvoorbeeld de pagina /content/geometrixx/nl/products aan een Translation Integration Framework koppelt, worden de pagina Producten en alle onderliggende pagina&#39;s vertaald volgens het framework.

Indien nodig kunt u de koppeling op een afstammende pagina overschrijven. De inhoud van een website gaat bijvoorbeeld vooral over kleding. Eén vertakking met pagina&#39;s beschrijft het bedrijf echter. De hoofdpagina van de site is gekoppeld aan een vertaalintegratieframework dat automatische vertaling opgeeft met de categorie Koud. De tak die het bedrijf beschrijft gebruikt een kader dat machinevertaling gebruikend de Algemene categorie uitvoert.

Verder, voor om het even welke gemeenschappen [SCF componenten](/help/communities/scf.md) op de pagina&#39;s, zal de gebruiker geproduceerde inhoud (UGC) de capaciteit voor gebruikers omvatten om inhoud te vertalen. Zie [Vertaling van door de gebruiker gegenereerde inhoud](/help/communities/translate-ugc.md) voor meer informatie.

### Een pagina koppelen aan een vertaalbureau {#associating-a-page-with-a-translation-provider}

Koppel een pagina aan de vertaalprovider die u gebruikt om de pagina en afstammende pagina&#39;s te vertalen.

1. Selecteer in de Sites-console de pagina die u wilt configureren en klik of tik op Weergave-eigenschappen.
1. Klik op Bewerken of tik op Bewerken en klik op het tabblad Cloud Services.
1. Klik of tik Add Configuratie > Vertaalintegratie.
1. Selecteer de vertaalprovider die u wilt gebruiken en klik op Gereed of tik op Gereed.

### Pagina&#39;s koppelen aan een vertaalintegratieframework {#associating-pages-with-a-translation-integration-framework}

Koppel een pagina aan het vertaalintegratieframework dat definieert hoe u de vertaling van de pagina en afstammende pagina&#39;s wilt uitvoeren.

1. Selecteer in de Sites-console de pagina die u wilt configureren en klik of tik op Weergave-eigenschappen.
1. Klik op Bewerken of tik op Bewerken en klik op het tabblad Cloud Services.
1. Klik of tik Add Configuratie > Vertaalintegratie.
1. Selecteer het vertaalintegratieframework dat u wilt gebruiken en klik op Gereed of tik op Gereed.

