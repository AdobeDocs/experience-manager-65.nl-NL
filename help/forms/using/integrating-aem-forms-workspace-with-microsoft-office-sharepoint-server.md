---
title: De werkruimte AEM formulieren integreren met Microsoft Office SharePoint Server
description: U kunt AEM formulierwerkruimte integreren met Microsoft Office SharePoint Server.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
exl-id: d080932f-d5fb-482d-9329-62da5df10362
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# De werkruimte AEM formulieren integreren met Microsoft Office SharePoint Server{#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

**- Eisen**

**Vereiste kennis**
Voordat u AEM Forms Workspace kunt toevoegen aan SharePoint Server, moet u toegang hebben tot SharePoint Server met de juiste rechten en moet u de URL kennen om toegang te krijgen tot Workspace. In de onderstaande stappen wordt ervan uitgegaan dat u bekend bent met SharePoint Server. Voor meer informatie over de Delen van het Web in de Server van SharePoint, zie de Delen van het Web in de Diensten van SharePoint van Vensters.

**Gebruikersniveau**
Begin

U kunt AEM Forms Workspace als een Web-onderdeel gebruiken in Microsoft Office SharePoint Server (bijvoorbeeld Microsoft Office SharePoint Server 2007). Gebruikers hebben toegang tot de AEM Forms Workspace door verbinding te maken met uw SharePoint Server via een webbrowser voor een uniforme ervaring. In dit artikel, leert u de basisstappen om de Werkruimte van AEM Forms als Deel van het Web in de Server van SharePoint van Microsoft Office te tonen. U kunt de in dit artikel beschreven stappen uitvoeren om een uniforme ervaring te bieden, zodat gebruikers die verbinding maken met uw SharePoint-server, vanaf dezelfde poort toegang hebben tot de AEM Forms Workspace.

>[!NOTE]
>
>De stappen die in dit artikel worden vermeld, zijn specifiek Microsoft SharePoint Server 2007. U kunt HTML Workspace ook configureren met andere ondersteunde versies van Microsoft SharePoint.

## AEM Forms Workspace integreren met Microsoft Office SharePoint Server 2007 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

Voer de volgende stappen uit om AEM Forms Workspace in een Deel van het Web te integreren:

1. Navigeer in een webbrowser naar de SharePoint-site, zoals: `https://[myMOSSserver]:44299/default.aspx` waar `[myMOSSserver]` is de naam of het IP-adres van de SharePoint-server.

   >[!NOTE]
   >
   >44299 is het standaardpoortnummer voor de SharePoint-server. Het poortnummer is afhankelijk van uw installatie van SharePoint Server.

1. Klik rechtsboven op de webpagina op **Site-handelingen** en selecteert u **Pagina bewerken**.
1. Klik op de knop **Een webonderdeel toevoegen** knop.
1. Selecteer onder Dialoogvenster Dialoogvenster Webonderdelen toevoegen - webpagina onder Dialoogvenster Dialoogvenster Diversen de optie **Webonderdeel van paginaviewer** en klik vervolgens op **Toevoegen**.
1. Klik in het vak Webonderdeel van de paginaviewer op **bewerken** en selecteert u **Gedeeld webonderdeel wijzigen**.

   >[!NOTE]
   >
   >Het vak Webonderdeel van de paginaviewer wordt weergegeven onder **Een webonderdeel toevoegen** knop waarop u in stap 3 hebt geklikt, zoals in de volgende afbeelding wordt getoond (Afbeelding 1):

   ![Paginaviewer, webonderdeel in Microsoft Office SharePoint-server.](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   Figuur 1. - Het vak Webonderdeel van paginaviewer op de Microsoft Office SharePoint-server.

1. Voer op de pagina Paginaviewer de volgende taken uit:

   1. Typ in het vak Koppeling de URL van de AEM Forms-werkruimte, zoals `https://[AEM_forms_Server]:8080/lc/ws` waar `[AEM_forms_Server]` vertegenwoordigt IP of Naam van de Server van AEM Forms.
   1. Klikken **Weergave** en wijzigt u de hoogte, breedte en titel, zodat u de volledige gebruikersinterface van de werkruimte kunt zien. U kunt de hoogte en breedte bijvoorbeeld instellen op respectievelijk 6 en 11 inch.
   1. Klikken **Koppeling testen**. Er wordt een nieuw webbrowservenster weergegeven met Workspace erin.
   1. (Optioneel) Klik op **Layout** en wijzig de lay-out van Werkruimte in het Deel van het Web.
   1. (Optioneel) Klik op **Geavanceerd** en wijzigt u andere instellingen, zoals de beschrijving en of Workspace geminimaliseerd of gesloten kan worden in het webonderdeel.

      Klikken **Toepassen**.

1. Klikken **Bewerkmodus afsluiten** en controleert u of u toegang hebt tot Workspace.

Nadat u de bovenstaande stappen hebt uitgevoerd, ziet uw SharePoint-site eruit zoals in de volgende afbeelding (Afbeelding 2):

![AEM Forms Workspace geïntegreerd met Microsoft Office SharePoint Server](assets/aem-forms-workspace.jpg)

Afbeelding 2 - AEM Forms Workspace geïntegreerd met Microsoft Office SharePoint Server
