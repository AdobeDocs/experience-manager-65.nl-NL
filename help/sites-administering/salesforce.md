---
title: Integratie met Salesforce
description: Meer informatie over de integratie van Adobe Experience Manager (AEM) met Salesforce.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 0f3aaa0a-ccfb-4162-97a6-ee5485595d28
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1530'
ht-degree: 0%

---


# Integratie met Salesforce {#integrating-with-salesforce}

De integratie van Salesforce met Adobe Experience Manager (AEM) biedt beheermogelijkheden voor leads en gebruikt de bestaande mogelijkheden die Salesforce uit de doos biedt. U kunt AEM configureren om leads te posten naar Salesforce en componenten maken die rechtstreeks vanuit Salesforce toegang hebben tot gegevens.

Dankzij de bidirectionele en uitbreidbare integratie tussen AEM en Salesforce:

* Organisaties die volledig gebruikmaken van gegevens en deze aanpassen om de ervaring van klanten te verbeteren.
* Betrokkenheid van marketing tot verkoopactiviteiten.
* Organisaties die automatisch gegevens verzenden en ontvangen van een Salesforce-datastore.

In dit document wordt het volgende beschreven:

* hoe te om Cloud Servicen te vormen Salesforce (vorm AEM om met Salesforce te integreren).
* hoe u Salesforce Lead/Contact-informatie kunt gebruiken in Client Context en voor Personalization.
* hoe u het workflowmodel van Salesforce gebruikt om AEM gebruikers te plaatsen als leidt naar Salesforce.
* hoe te om een component tot stand te brengen die gegevens van Salesforce toont.

## AEM configureren voor integratie met Salesforce {#configuring-aem-to-integrate-with-salesforce}

Om AEM te vormen om met Salesforce te integreren, vormt u eerst een verre toegangstoepassing in Salesforce. Dan vormt u de de wolkendienst van Salesforce om aan deze verre toegangstoepassing te richten.

>[!NOTE]
>
>U kunt een gratis ontwikkelaarsaccount maken in Salesforce.

Om AEM te vormen om met Salesforce te integreren:

>[!CAUTION]
>
>Installeer het [ Salesforce API ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=salesforce*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=2&amp;package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcom.adobe.cq.mcm.salesforce.content-1.0.4.zip) integratiepakket alvorens u met de procedure verdergaat. Voor meer details op hoe te met pakketten te werken zie [ hoe te met de pagina van Pakketten ](/help/sites-administering/package-manager.md#package-share) werken.

1. In AEM, navigeer aan **Cloud Servicen**. In de Diensten van de Derde, klik **vormen nu** in **Salesforce**.

   ![ chlimage_1-70 ](assets/chlimage_1-70.png)

1. Creeer een configuratie, bijvoorbeeld, **ontwikkelaar**.

   >[!NOTE]
   >
   >De nieuwe configuratie richt aan een nieuwe pagina opnieuw: **http://localhost:4502/etc/cloudservices/salesforce/developer.html**. Dit is de nauwkeurige zelfde waarde die u in Callback URL moet specificeren terwijl het creëren van de verre toegangstoepassing in Salesforce. Deze waarden moeten overeenkomen.

1. Login aan uw rekening van Salesforce (of als u geen hebt, creeer in [ https://developer.salesforce.com ](https://developer.salesforce.com).)
1. In Salesforce, navigeer aan **creeer** > **Apps** om aan **Verbonden Apps** te krijgen (in vroegere versies van Salesforce, was het werkschema **opstellen** > **Verre Toegang**).
1. Klik **Nieuw** zodat kunt u AEM met Salesforce verbinden.

   ![ chlimage_1-71 ](assets/chlimage_1-71.png)

1. Ga de **Verbonden Naam van de App**, **API Naam**, en **E-mail van het Contact** in. Selecteer **toelaten OAuth de controledoos van Montages** en ga **terug URL** in en voeg een OAuth werkingsgebied (bijvoorbeeld, volledige toegang) toe. De callback-URL ziet er ongeveer als volgt uit: `http://localhost:4502/etc/cloudservices/salesforce/developer.html`

   Wijzig de servernaam/het poortnummer en de paginanaam in overeenstemming met uw configuratie.

   ![ chlimage_1-72 ](assets/chlimage_1-72.png)

1. Klik **sparen** om de configuratie te bewaren Salesforce. Salesforce leidt tot de sleutel van de a **consument** en **consumentengeheim**, die u voor AEM configuratie nodig hebt.

   ![ chlimage_1-73 ](assets/chlimage_1-73.png)

   >[!NOTE]
   >
   >Wacht enkele minuten (tot 15 minuten) voordat de externe toegangstoepassing in Salesforce wordt geactiveerd.

1. In AEM, navigeer aan **Cloud Servicen** en navigeer aan de configuratie Salesforce u vroeger (bijvoorbeeld, **ontwikkelaar**) creeerde. Klik **uitgeven** en ga de klantensleutel en het klantengeheim van salesforce.com in.

   ![ chlimage_1-15 ](assets/chlimage_1-15.jpeg)

   | URL aanmelding | Dit is het Salesforce Authorization Endpoint. De waarde ervan wordt vooraf ingevuld en is in de meeste gevallen beschikbaar. |
   |---|---|
   | Klantsleutel | Ga de waarde in die van de Verre pagina van de Registratie van de Toepassing van de Toegang in salesforce.com wordt verkregen |
   | Klantgeheim | Ga de waarde in die van de Verre pagina van de Registratie van de Toepassing van de Toegang in salesforce.com wordt verkregen |

1. Klik **verbinden met Salesforce** om te verbinden. Salesforce vraagt dat u uw configuratie toestaat om met Salesforce te verbinden.

   ![ chlimage_1-74 ](assets/chlimage_1-74.png)

   In AEM wordt een bevestigingsvenster geopend met de mededeling dat u verbinding hebt gemaakt.

1. Navigeer aan de wortelpagina van uw website en klik **Eigenschappen van de Pagina**. Dan selecteer **Cloud Servicen** en voeg **Salesforce** toe en selecteer de correcte configuratie (bijvoorbeeld, **ontwikkelaar**).

   ![ chlimage_1-75 ](assets/chlimage_1-75.png)

   Nu kunt u het workflowmodel gebruiken om leads naar Salesforce te posten en componenten te maken die toegang hebben tot gegevens van Salesforce.

## AEM gebruikers exporteren als Salesforce Leads {#exporting-aem-users-as-salesforce-leads}

Als u een AEM gebruiker wilt exporteren als Salesforce-lead, configureert u de workflow om leads naar Salesforce te posten.

Als u AEM gebruikers wilt exporteren als leider van Salesforce:

1. Navigeer aan het werkschema Salesforce bij `http://localhost:4502/workflow` door het werkschema **Salesforce.com de Uitvoer** met de rechtermuisknop aan te klikken en **Begin** te klikken.

   ![ chlimage_1-76 ](assets/chlimage_1-76.png)

1. Selecteer de AEM gebruiker die u als lood als **nuttige lading** voor dit werkschema (huis > gebruikers) wilt tot stand brengen. Ben zeker om de profielknoop van de gebruiker te selecteren aangezien het informatie als **givenName** bevat, en **familyName**, die aan 4} FirstName **en** **gebieden van Salesforce lood in kaart worden gebracht.**

   ![ chlimage_1-77 ](assets/chlimage_1-77.png)

   >[!NOTE]
   >
   >Voordat u met deze workflow begint, moeten er bepaalde verplichte velden zijn voor publicatie op Salesforce in AEM loodknooppunt. Dit zijn **givenName**, **familyName**, **bedrijf**, en **e-mail**. Om een volledige lijst van afbeeldingen tussen AEM gebruiker en lood Salesforce te zien, zie [ Configuratie van de Toewijzing tussen AEM gebruiker en lood Salesforce.](#mapping-configuration-between-aem-user-and-salesforce-lead)

1. Klik **OK**. De gebruikersgegevens worden geëxporteerd naar salesforce.com. U kunt dit controleren op salesforce.com.

   >[!NOTE]
   >
   >In de foutlogboeken ziet u of een lead wordt geïmporteerd. Controleer het foutenlogboek voor meer informatie.

### De Salesforce.com-workflow voor exporteren configureren {#configuring-the-salesforce-com-export-workflow}

Indien nodig, vorm het Salesforce.com werkschema van de Uitvoer om het aan de correcte configuratie Salesforce.com aan te passen, of andere veranderingen aan te brengen.

De Salesforce.com-exportworkflow configureren:

1. Navigeren naar `http://localhost:4502/cf#/etc/workflow/models/salesforce-com-export.html.`

   ![ chlimage_1-16 ](assets/chlimage_1-16.jpeg)

1. Open de stap van de Uitvoer Salesforce.com, selecteer de **Argumenten** tabel, en selecteer de correcte configuratie wordt geselecteerd en klikt **O.K.**. Schakel het selectievakje in als u wilt dat de workflow een lead opnieuw maakt die in Salesforce is verwijderd.

   ![ chlimage_1-78 ](assets/chlimage_1-78.png)

1. Klik **sparen** om uw veranderingen te bewaren.

   ![ chlimage_1-79 ](assets/chlimage_1-79.png)

### Toewijzingsconfiguratie tussen AEM gebruiker en Salesforce Lead {#mapping-configuration-between-aem-user-and-salesforce-lead}

Om de huidige kaartconfiguratie tussen een AEM gebruiker en een lood te bekijken of uit te geven Salesforce, open de Manager van de Configuratie: `https://<hostname>:<port>/system/console/configMgr` en onderzoek naar **Configuratie van de Afbeelding van de Lood van Salesforce**.

1. Open de Manager van de Configuratie door **Console van het Web** te klikken of rechtstreeks naar `https://<hostname>:<port>/system/console/configMgr.` te gaan
1. Onderzoek naar **Configuratie van de Toewijzing van de Lood van Salesforce**.

   ![ chlimage_1-80 ](assets/chlimage_1-80.png)

1. Wijzig desgewenst toewijzingen. De standaardafbeelding volgt het patroon **aemUserAttribute=sfLeadAttribute**. Klik **sparen** om uw veranderingen te bewaren.

## Contextarchief van Salesforce-client configureren {#configuring-salesforce-client-context-store}

De opslag van de de cliëntcontext van Salesforce toont extra informatie over de momenteel geregistreerde gebruiker dan wat reeds binnen AEM beschikbaar is. Deze aanvullende informatie wordt door Salesforce opgehaald, afhankelijk van de verbinding van de gebruiker met Salesforce.

Hiertoe configureert u het volgende:

1. Koppel een AEM gebruiker aan een Salesforce-id via de Salesforce Connect-component.
1. Voeg de gegevens van het Profiel Salesforce in de pagina van de cliëntcontext toe zodat kunt u vormen welke eigenschappen u wilt zien.
1. (Optioneel) Bouw een segment dat de gegevens uit de Salesforce Client Context Store gebruikt.

### Een AEM gebruiker koppelen met een Salesforce-id {#linking-an-aem-user-with-a-salesforce-id}

Wijs een AEM gebruiker met een identiteitskaart Salesforce toe zodat kunt u het in de cliëntcontext laden. In een echt scenario, zou u gebaseerd op bekende gebruikersgegevens met bevestiging verbinden. Voor demonstratiedoeleinden, in deze procedure, gebruikt u **Salesforce Connect** component.

1. Navigeer aan een website in AEM, teken binnen, en sleep en laat vallen **Salesforce verbindt** component van sidekick.

   >[!NOTE]
   >
   >Als **Salesforce verbindt** component niet beschikbaar is, ga naar de **mening van het Ontwerp** en selecteer het om het in **beschikbaar te maken geef** mening uit.

   ![ chlimage_1-17 ](assets/chlimage_1-17.jpeg)

   Wanneer u de component aan de pagina sleept, toont het **Verbinding aan Salesforce=Off**.

   ![ chlimage_1-81 ](assets/chlimage_1-81.png)

   >[!NOTE]
   >
   >Dit onderdeel is uitsluitend bedoeld voor demonstratiedoeleinden. Voor scenario&#39;s in de praktijk, zou er een ander proces zijn om gebruikers met lood te verbinden/aan te passen.

1. Nadat u de component op de pagina hebt gesleept, opent u deze om de component te configureren. Selecteer de configuratie, het type van contact, en de lood of het contact van Salesforce, en klik **O.K.**.

   ![ chlimage_1-82 ](assets/chlimage_1-82.png)

   AEM verbindt de gebruiker met het contact of de lood Salesforce.

   ![ chlimage_1-83 ](assets/chlimage_1-83.png)

### Salesforce-gegevens toevoegen aan clientcontext {#adding-salesforce-data-to-client-context}

U kunt gebruikersgegevens van Salesforce in de Context van de Cliënt laden voor verpersoonlijking te gebruiken:

1. Open de clientcontext die u wilt uitbreiden door daar te navigeren, bijvoorbeeld `http://localhost:4502/etc/clientcontext/default/content.html.`

   ![ chlimage_1-18 ](assets/chlimage_1-18.jpeg)

1. Sleep de **component van de Gegevens van het Profiel van 0} Salesforce {aan de cliëntcontext.**

   ![ chlimage_1-19 ](assets/chlimage_1-19.jpeg)

1. Open de component door erop te dubbelklikken. Selecteer **Punt** toevoegen en een bezit van de drop-down lijst selecteren. Voeg zo vele eigenschappen toe zoals u wilt en selecteer **O.K.**.

   ![ chlimage_1-84 ](assets/chlimage_1-84.png)

1. Nu, ziet u Salesforce-specifieke eigenschappen van Salesforce die in de cliëntcontext worden getoond.

   ![ chlimage_1-85 ](assets/chlimage_1-85.png)

### Een segment maken met gegevens uit de Salesforce Client Context Store {#building-a-segment-using-data-from-salesforce-client-context-store}

U kunt een segment bouwen dat gegevens van de Opslag van de Context van de Cliënt Salesforce gebruikt. Dit doet u als volgt:

1. Navigeer aan segmentatie in AEM of door **Hulpmiddelen** te gaan > **Segmentatie** of naar [ http://localhost:4502/miscadmin#/etc/segmentation ](http://localhost:4502/miscadmin#/etc/segmentation) te gaan.
1. Maak of werk een segment bij om gegevens van Salesforce op te nemen. Voor meer informatie, zie [ Segmentatie ](/help/sites-administering/campaign-segmentation.md).

## Zoekleads {#searching-leads}

AEM schepen met een voorbeeldcomponent Search die volgens de gegeven criteria in Salesforce zoekopdrachten uitvoert. Deze component laat zien hoe u de Salesforce REST API kunt gebruiken om te zoeken naar Salesforce-objecten. Om een vraag aan salesforce.com teweeg te brengen, verbind een pagina met een configuratie Salesforce.

>[!NOTE]
>
>Dit is een voorbeeldcomponent die u toont hoe te om Salesforce REST API te gebruiken om voorwerpen van Salesforce te vragen. Gebruik dit als voorbeeld om complexere componenten te maken op basis van uw behoeften.

Deze component gebruiken:

1. Navigeer naar de pagina waarop u deze configuratie wilt gebruiken. Open de pagina-eigenschappen en selecteer **Cloud Servicen.** klik **toevoegen de Diensten** en selecteren **Salesforce** en de aangewezen configuratie en klik **O.K.**.

   ![ chlimage_1-20 ](assets/chlimage_1-20.jpeg)

1. Sleep de Salesforce-zoekcomponent naar de pagina (mits deze is ingeschakeld). Ga naar de ontwerpmodus en voeg deze toe aan het desbetreffende gebied om de modus in te schakelen.)

   ![ chlimage_1-21 ](assets/chlimage_1-21.jpeg)

1. Open de component van het Onderzoek en specificeer de onderzoeksparameters en klik **O.K.**

   ![ chlimage_1-86 ](assets/chlimage_1-86.png)

1. AEM geeft de in de zoekcomponent opgegeven leads weer die aan de opgegeven criteria voldoen.

   ![ chlimage_1-87 ](assets/chlimage_1-87.png)
