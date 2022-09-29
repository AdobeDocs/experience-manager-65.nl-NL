---
title: Integratie met Salesforce
seo-title: Integrating with Salesforce
description: Leer over het integreren van AEM met Salesforce.
seo-description: Learn about integrating AEM with Salesforce.
uuid: 3d6a249d-082f-4a10-b255-96482ccd2c65
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: bee7144e-4276-4e81-a3a0-5b7273af34fe
docset: aem65
exl-id: 0f3aaa0a-ccfb-4162-97a6-ee5485595d28
source-git-commit: c7958efbc4557ab3e50732da59faabf4e36c3844
workflow-type: tm+mt
source-wordcount: '1564'
ht-degree: 0%

---


# Integratie met Salesforce {#integrating-with-salesforce}

De integratie van Salesforce met AEM biedt beheermogelijkheden voor leads en maakt gebruik van de bestaande mogelijkheden die Salesforce uit de doos biedt. U kunt AEM configureren om leads te posten naar Salesforce en componenten maken die rechtstreeks vanuit Salesforce toegang hebben tot gegevens.

Dankzij de bidirectionele en uitbreidbare integratie tussen AEM en Salesforce:

* Organisaties die volledig gegevens gebruiken en bijwerken om de klantervaring te verbeteren.
* Betrokkenheid van marketing tot verkoopactiviteiten.
* Organisaties die automatisch gegevens verzenden en ontvangen van een Salesforce-datastore.

In dit document wordt het volgende beschreven:

* hoe te om Cloud Services te vormen Salesforce (vorm AEM om met Salesforce te integreren).
* hoe te om Salesforce Lead/Contactinformatie in de Context van de Cliënt en voor Personalisatie te gebruiken.
* hoe u het workflowmodel van Salesforce gebruikt om AEM gebruikers te plaatsen als leidt tot salesforce.
* hoe te om een component tot stand te brengen die gegevens van Salesforce toont.

## Het vormen AEM om met Salesforce te integreren {#configuring-aem-to-integrate-with-salesforce}

Om AEM te vormen om met Salesforce te integreren, moet u een verre toegangstoepassing in Salesforce eerst vormen. Dan vormt u de salesforce wolkendienst om aan deze verre toegangstoepassing te richten.

>[!NOTE]
>
>U kunt een gratis ontwikkelaarsaccount maken in Salesforce.

Om AEM te vormen om met Salesforce te integreren:

>[!CAUTION]
>
>U moet de [Salesforce-API](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=salesforce*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=2&amp;package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcom.adobe.cq.mcm.salesforce.content-1.0.4.zip) integratiepakket voordat u verdergaat met de procedure. Voor meer informatie over het werken met pakketten raadpleegt u de [Werken met pakketten](/help/sites-administering/package-manager.md#package-share) pagina.

1. Navigeer in AEM naar **Cloud Services**. Klik in Services van derden op **Nu configureren** in **Salesforce**.

   ![chlimage_1-70](assets/chlimage_1-70.png)

1. Een nieuwe configuratie maken, bijvoorbeeld **ontwikkelaar**.

   >[!NOTE]
   >
   >De nieuwe configuratie wordt omgeleid naar een nieuwe pagina: **http://localhost:4502/etc/cloudservices/salesforce/developer.html**. Dit is de nauwkeurige zelfde waarde die u in Callback URL moet specificeren terwijl het creëren van de verre toegangstoepassing in Salesforce. Deze waarden moeten overeenkomen.

1. Meld u aan bij uw salesforce-account (of als u er geen hebt, maakt u er een bij [https://developer.force.com](https://developer.force.com).)
1. Navigeer in Salesforce naar **Maken** > **Apps** om te gaan naar **Verbonden apps** (in eerdere versies van salesforce was de workflow **Implementeren** > **Externe toegang**).
1. Klikken **Nieuw** om AEM te verbinden met Salesforce.

   ![chlimage_1-71](assets/chlimage_1-71.png)

1. Voer de **Aangesloten toepassingsnaam**, **API-naam**, en **E-mailadres**. Selecteer **OAuth-instellingen inschakelen** selectievakje en voer de **URL voor terugbellen** en voeg een OAuth werkingsgebied (bijvoorbeeld, volledige toegang) toe. De callback-URL ziet er ongeveer als volgt uit: `http://localhost:4502/etc/cloudservices/salesforce/developer.html`

   Wijzig de servernaam/het poortnummer en de paginanaam in overeenstemming met uw configuratie.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Klikken **Opslaan** om de salesforce-configuratie op te slaan. Salesforce maakt een **consumentensleutel** en **consumentengeheim**, die u nodig hebt voor AEM configuratie.

   ![chlimage_1-73](assets/chlimage_1-73.png)

   >[!NOTE]
   >
   >Mogelijk moet u enkele minuten wachten (tot 15 minuten) voordat de externe toegangstoepassing in Salesforce wordt geactiveerd.

1. Navigeer in AEM naar **Cloud Services** en navigeer naar de salesforce-configuratie die u eerder hebt gemaakt (bijvoorbeeld **ontwikkelaar**). Klikken **Bewerken** en ga de klantensleutel en het klantengeheim van salesforce.com in.

   ![chlimage_1-15](assets/chlimage_1-15.jpeg)

   | Aanmeldings-URL | Dit is het Salesforce Authorization Endpoint. De waarde ervan wordt vooraf ingevuld en is in de meeste gevallen beschikbaar. |
   |---|---|
   | Klantsleutel | Ga de waarde in die van de pagina van de Registratie van de Toepassing van de Verre Toegang in salesforce.com wordt verkregen |
   | Klantgeheim | Ga de waarde in die van de pagina van de Registratie van de Toepassing van de Verre Toegang in salesforce.com wordt verkregen |

1. Klikken **Verbinding maken met Salesforce** om verbinding te maken. Salesforce vraagt dat u uw configuratie toestaat om met verkoopkracht te verbinden.

   ![chlimage_1-74](assets/chlimage_1-74.png)

   In AEM wordt een bevestigingsvenster geopend met de mededeling dat u verbinding hebt gemaakt.

1. Ga naar de hoofdpagina van uw website en klik op **Pagina-eigenschappen**. Selecteer vervolgens **Cloud Services** en toevoegen **Salesforce** en selecteer de juiste configuratie (bijvoorbeeld **ontwikkelaar**).

   ![chlimage_1-75](assets/chlimage_1-75.png)

   Nu kunt u het workflowmodel gebruiken om leads naar Salesforce te posten en componenten te maken die toegang hebben tot gegevens van Salesforce.

## AEM gebruikers exporteren als Salesforce Leads {#exporting-aem-users-as-salesforce-leads}

Als u een AEM gebruiker als verkoopkrachtlood wilt uitvoeren, moet u het werkschema vormen om lood te posten aan verkoopkracht.

Als u AEM gebruikers wilt exporteren als leider van Salesforce:

1. Ga naar de Salesforce-workflow op `http://localhost:4502/workflow` door met de rechtermuisknop op de workflow te klikken **Salesforce.com Export** en klikken **Start**.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Selecteer de AEM gebruiker die u als lead wilt maken als de **Payload** voor deze workflow (home -> gebruikers). Zorg ervoor dat u het profielknooppunt van de gebruiker selecteert omdat het informatie bevat zoals **givenName**, **familyName**, enzovoort, die zijn toegewezen aan Salesforce lead **FirstName** en **LastName** velden.

   ![chlimage_1-77](assets/chlimage_1-77.png)

   >[!NOTE]
   >
   >Voordat u met deze workflow begint, moeten er bepaalde verplichte velden zijn voor publicatie op Salesforce in AEM loodknooppunt. Dit zijn **givenName**, **familyName**, **bedrijf** en **email**. Voor een volledige lijst met toewijzingen tussen AEM gebruiker en Salesforce lead raadpleegt u [Configuratie toewijzen tussen AEM gebruiker en Slaesforce lead.](#mapping-configuration-between-aem-user-and-salesforce-lead)

1. Klikken **OK**. De gebruikersinformatie wordt uitgevoerd naar salesforce.com. U kunt het verifiëren bij salesforce.com.

   >[!NOTE]
   >
   >In de foutlogboeken wordt weergegeven of een lead wordt geïmporteerd. Controleer het foutenlogboek voor meer informatie.

### De exportworkflow van Salesforce.com configureren {#configuring-the-salesforce-com-export-workflow}

U kunt het werkschema van de Uitvoer moeten vormen Salesforce.com om het aan de correcte configuratie aan te passen Salesforce.com of andere veranderingen aan te brengen.

Om de Salesforce.com- uitvoerwerkschema te vormen:

1. Ga naar `http://localhost:4502/cf#/etc/workflow/models/salesforce-com-export.html.`

   ![chlimage_1-16](assets/chlimage_1-16.jpeg)

1. Open de stap Export van Salesforce.com en selecteer de **Argumenten** en selecteert u de juiste configuratie en klikt u op **OK**. Schakel het selectievakje in als u wilt dat de workflow een lead opnieuw maakt die in Salesforce is verwijderd.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Klikken **Opslaan** om uw wijzigingen op te slaan.

   ![chlimage_1-79](assets/chlimage_1-79.png)

### Toewijzingsconfiguratie tussen AEM gebruiker en Salesforce Lead {#mapping-configuration-between-aem-user-and-salesforce-lead}

Om de huidige toewijzingsconfiguratie tussen een AEM gebruiker en een lood te bekijken of uit te geven Salesforce, open de Manager van de Configuratie: `https://<hostname>:<port>/system/console/configMgr` en zoek naar **Configuratie van toewijzing van Salesforce-leads**.

1. Open de Manager van de Configuratie door te klikken **Webconsole** of rechtstreeks naar `https://<hostname>:<port>/system/console/configMgr.`
1. Zoeken naar **Configuratie van toewijzing van Salesforce-leads**.

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Wijzig desgewenst toewijzingen. De standaardtoewijzing volgt het patroon **aemUserAttribute=sfLeadAttribute**. Klikken **Opslaan** om uw wijzigingen op te slaan.

## Contextarchief van Salesforce-client configureren {#configuring-salesforce-client-context-store}

De salesforce opslag van de cliëntcontext toont extra informatie over de momenteel het programma geopende gebruiker dan wat reeds binnen AEM beschikbaar is. Deze aanvullende informatie wordt door Salesforce opgehaald, afhankelijk van de verbinding van de gebruiker met Salesforce.

Om dit te doen, moet u het volgende vormen:

1. Koppel een AEM gebruiker aan een Salesforce-id via de Salesforce Connect-component.
1. Voeg de gegevens van het Profiel Salesforce in de pagina van de cliëntcontext toe om te vormen welke eigenschappen u wilt zien.
1. (Optioneel) Bouw een segment dat de gegevens uit de Salesforce Client Context Store gebruikt.

### Een AEM gebruiker koppelen met een Salesforce-id {#linking-an-aem-user-with-a-salesforce-id}

U moet een AEM gebruiker met een Salesforce-id toewijzen om deze in de clientcontext te laden. In een echt scenario, zou u gebaseerd op bekende gebruikersgegevens met bevestiging verbinden. Voor aantoonbare doeleinden gebruikt u in deze procedure de opdracht **Salesforce Connect** component.

1. Navigeer naar een website in AEM, meld u aan en sleep de **Salesforce Connect** van het hulpwerktuig.

   >[!NOTE]
   >
   >Als de **Salesforce Connect** component is niet beschikbaar, ga naar **Ontwerp** weergeven en selecteren om deze beschikbaar te maken in **Bewerken** weergeven.

   ![chlimage_1-17](assets/chlimage_1-17.jpeg)

   Wanneer u de component naar de pagina sleept, wordt het weergegeven **Koppeling naar Salesforce=Off**.

   ![chlimage_1-81](assets/chlimage_1-81.png)

   >[!NOTE]
   >
   >Dit onderdeel is uitsluitend bedoeld voor demonstratiedoeleinden. Voor scenario&#39;s in de praktijk, zou er een ander proces zijn om gebruikers met lood te verbinden/aan te passen.

1. Nadat u de component op de pagina hebt gesleept, opent u deze om de component te configureren. Selecteer de configuratie, het type contact en de Salesforce-lead of -contactpersoon en klik op **OK**.

   ![chlimage_1-82](assets/chlimage_1-82.png)

   AEM verbindt de gebruiker met het contact of de lood Salesforce.

   ![chlimage_1-83](assets/chlimage_1-83.png)

### Salesforce-gegevens toevoegen aan clientcontext {#adding-salesforce-data-to-client-context}

U kunt gebruikersgegevens van Salesforce in de Context van de Cliënt laden voor verpersoonlijking te gebruiken:

1. Open de clientcontext die u wilt uitbreiden door daar te navigeren, bijvoorbeeld `http://localhost:4502/etc/clientcontext/default/content.html.`

   ![chlimage_1-18](assets/chlimage_1-18.jpeg)

1. Sleep de **Salesforce-profielgegevens** naar de clientcontext.

   ![chlimage_1-19](assets/chlimage_1-19.jpeg)

1. Dubbelklik op de component om deze te openen. Selecteren **Item toevoegen** en selecteert u een eigenschap in de vervolgkeuzelijst. Voeg zoveel eigenschappen toe als u wilt en selecteer **OK**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Nu, ziet u Salesforce-specifieke eigenschappen van Salesforce die in de cliëntcontext worden getoond.

   ![chlimage_1-85](assets/chlimage_1-85.png)

### Een segment maken met gegevens uit de Salesforce Client Context Store {#building-a-segment-using-data-from-salesforce-client-context-store}

U kunt een segment bouwen dat gegevens van de Opslag van de Context van de Cliënt Salesforce gebruikt. Dit doet u als volgt:

1. Navigeer naar segmentatie in AEM door naar **Gereedschappen** > **Segmentering** of naar [http://localhost:4502/miscadmin#/etc/segmentation](http://localhost:4502/miscadmin#/etc/segmentation).
1. Maak of werk een segment bij om gegevens van Salesforce op te nemen. Zie voor meer informatie [Segmentering](/help/sites-administering/campaign-segmentation.md).

## Zoekleads {#searching-leads}

AEM schepen met een voorbeeldcomponent Search die volgens de gegeven criteria in Salesforce zoekopdrachten uitvoert. Met deze component kunt u zien hoe u de Salesforce REST API kunt gebruiken om te zoeken naar Salesforce-objecten. U moet een pagina met een configuratie verbinden Salesforce om een vraag aan salesforce.com te activeren.

>[!NOTE]
>
>Dit is een voorbeeldcomponent die u toont hoe te om Salesforce REST API te gebruiken om voorwerpen van Salesforce te vragen. Gebruik dit als voorbeeld om complexere componenten te maken op basis van uw behoeften.

Deze component gebruiken:

1. Navigeer naar de pagina waarop u deze configuratie wilt gebruiken. Pagina-eigenschappen openen en selecteren **Cloud Services.** Klikken **Services toevoegen** en selecteert u **Salesforce** en de juiste configuratie en klik op **OK**.

   ![chlimage_1-20](assets/chlimage_1-20.jpeg)

1. Sleep de Salesforce-zoekcomponent naar de pagina (mits deze is ingeschakeld). Ga naar de ontwerpmodus en voeg deze toe aan het desbetreffende gebied om de modus in te schakelen.)

   ![chlimage_1-21](assets/chlimage_1-21.jpeg)

1. Open de component van het Onderzoek en specificeer de onderzoeksparameters en klik **OK.**

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. AEM geeft de in de zoekcomponent opgegeven leads weer die aan de opgegeven criteria voldoen.

   ![chlimage_1-87](assets/chlimage_1-87.png)
