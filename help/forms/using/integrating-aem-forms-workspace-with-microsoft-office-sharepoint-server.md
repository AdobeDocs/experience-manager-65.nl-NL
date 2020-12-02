---
title: De werkruimte van AEM formulieren integreren met Microsoft Office SharePoint Server
seo-title: De werkruimte van AEM formulieren integreren met Microsoft Office SharePoint Server
description: 'U kunt AEM formulierwerkruimte integreren met Microsoft Office SharePoint Server. '
seo-description: 'U kunt AEM formulierwerkruimte integreren met Microsoft Office SharePoint Server. '
uuid: 69d51bdf-729f-4eea-8fae-1e2b8aacaae6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 8990b422-f4f6-4080-871a-33cdf7ca6455
docset: aem65
translation-type: tm+mt
source-git-commit: 21623c615ebe69226cfaf84baf4cfb1717b449f4
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---


# De werkruimte van AEM formulieren integreren met Microsoft Office SharePoint Server{#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

**- Eisen**

**Vereiste**
kennisVoordat u AEM Forms Workspace aan SharePoint Server kunt toevoegen, moet u toegang tot de Server van SharePoint met de aangewezen voorrechten hebben, en u moet URL kennen om tot Werkruimte toegang te hebben. In de onderstaande stappen wordt ervan uitgegaan dat u bekend bent met SharePoint Server. Voor meer informatie over de Delen van het Web in de Server van SharePoint, zie de Delen van het Web in Windows SharePoint Services.

**Gebruikersniveau**
Beginnen

U kunt de Werkruimte van AEM Forms als Deel van het Web in de Server van Microsoft Office SharePoint (bijvoorbeeld, de Server 2007 van SharePoint van Microsoft Office) gebruiken. Gebruikers kunnen toegang krijgen tot de AEM Forms Workspace door verbinding te maken met uw SharePoint-server via een webbrowser voor een uniforme ervaring. In dit artikel, leert u de basisstappen om de Werkruimte van AEM Forms als Deel van het Web in de Server van Microsoft Office SharePoint te tonen. U kunt de in dit artikel beschreven stappen uitvoeren om een uniforme ervaring te bieden, zodat gebruikers die verbinding maken met uw SharePoint-server, vanaf dezelfde poort toegang hebben tot de AEM Forms Workspace.

>[!NOTE]
>
>De stappen die in dit artikel worden vermeld zijn de specifieke Server 2007 van Microsoft SharePoint. U kunt HTML-werkruimte ook configureren met andere ondersteunde versies van Microsoft SharePoint.

## AEM Forms Workspace integreren met Microsoft Office SharePoint Server 2007 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

Voer de volgende stappen uit om AEM Forms Workspace in een Deel van het Web te integreren:

1. In Webbrowser, navigeer aan de plaats van SharePoint zoals, `https://[myMOSSserver]:44299/default.aspx` waar `[myMOSSserver]` de naam of het IP adres van de server van SharePoint is.

   >[!NOTE]
   >
   >44299 is het standaardpoortnummer voor de SharePoint-server. Het poortnummer is afhankelijk van uw installatie van SharePoint Server.

1. Klik in de rechterbovenhoek van de webpagina op **Sitehandelingen** en selecteer **Pagina bewerken**.
1. Klik **Voeg een Deel van het Web** knoop toe.
1. In Add de Delen van het Web - de dialoogdoos van de Web-pagina, onder Dialoogvenster, selecteert **Deel van het Web van de Kijker van de Pagina** en klikt dan **Add**.
1. Klik in het vak Web-onderdeel van de paginaviewer op **edit** en selecteer **Gedeeld webdeel wijzigen**.

   >[!NOTE]
   >
   >Het vakje van het Deel van het Web van de Kijker van de Pagina verschijnt onder **voeg een Deel van het Web** knoop toe die u in stap 3 zoals aangetoond in de volgende illustratie (Figuur 1) klikte:

   ![Het vakje van het Deel van het Web van de Kijker van de pagina in de server van SharePoint van Microsoft Office.](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   Figuur 1. - Het vakje van het Deel van het Web van de Kijker van de Pagina in de server van Microsoft Office SharePoint.

1. Voer op de pagina Paginaviewer de volgende taken uit:

   1. Typ in het vak Koppeling de URL van de AEM Forms Workspace, bijvoorbeeld `https://[AEM_forms_Server]:8080/lc/ws`, waarbij `[AEM_forms_Server]` de IP of naam van de AEM formulierserver vertegenwoordigt.
   1. Klik **Vormgeving** en wijzig de hoogte, breedte en titel zodat u de volledige gebruikersinterface van de Werkruimte kunt zien. U kunt de hoogte en breedte bijvoorbeeld instellen op respectievelijk 6 en 11 inch.
   1. Klik **Verbinding van de Test**. Er wordt een nieuw webbrowservenster weergegeven met Workspace erin.
   1. (Optioneel) Klik op **Layout** en wijzig de lay-out van Werkruimte in webonderdeel.
   1. (Optioneel) Klik op **Geavanceerd** en wijzig andere instellingen, zoals de beschrijving en of Workspace geminimaliseerd of gesloten kan worden in het webonderdeel.

      Klik **Toepassen**.

1. Klik **Bewerkmodus afsluiten** en controleer of u toegang hebt tot de werkruimte.

Nadat u de bovenstaande stappen hebt uitgevoerd, ziet uw SharePoint-site eruit zoals in de volgende afbeelding (Afbeelding 2):

![AEM Forms Workspace geïntegreerd met Microsoft Office SharePoint Server](assets/aem-forms-workspace.jpg)

Afbeelding 2 - AEM Forms Workspace geïntegreerd met Microsoft Office SharePoint Server

