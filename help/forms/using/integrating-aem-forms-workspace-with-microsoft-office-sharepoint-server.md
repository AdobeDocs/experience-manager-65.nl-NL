---
title: AEM-formulierwerkruimte integreren met Microsoft Office SharePoint Server
seo-title: AEM-formulierwerkruimte integreren met Microsoft Office SharePoint Server
description: 'U kunt AEM-formulierwerkruimte integreren met Microsoft Office SharePoint Server. '
seo-description: 'U kunt AEM-formulierwerkruimte integreren met Microsoft Office SharePoint Server. '
uuid: 69d51bdf-729f-4eea-8fae-1e2b8aacaae6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 8990b422-f4f6-4080-871a-33cdf7ca6455
docset: aem65
translation-type: tm+mt
source-git-commit: 21623c615ebe69226cfaf84baf4cfb1717b449f4

---


# AEM-formulierwerkruimte integreren met Microsoft Office SharePoint Server{#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

**- Eisen**

**De vereiste kennis** alvorens u de Werkruimte van Vormen AEM aan de Server van SharePoint kunt toevoegen, moet u toegang tot de Server van SharePoint met de aangewezen voorrechten hebben, en u moet URL kennen om tot Werkruimte toegang te hebben. In de onderstaande stappen wordt ervan uitgegaan dat u bekend bent met SharePoint Server. Voor meer informatie over de Delen van het Web in de Server van SharePoint, zie de Delen van het Web in Windows SharePoint Services.

**Gebruikersniveau** Beginnen

U kunt de Werkruimte van Vormen AEM als Deel van het Web in de Server van Microsoft Office SharePoint (bijvoorbeeld, de Server 2007 van SharePoint van Microsoft Office) gebruiken. Gebruikers hebben toegang tot de AEM Forms Workspace door verbinding te maken met uw SharePoint-server via een webbrowser voor een uniforme ervaring. In dit artikel, leert u de basisstappen om AEM de Werkruimte van Vormen als Deel van het Web in de Server van Microsoft Office SharePoint te tonen. U kunt de in dit artikel beschreven stappen uitvoeren om een uniforme ervaring te bieden, zodat gebruikers die verbinding maken met uw SharePoint-server toegang hebben tot de AEM Forms Workspace vanaf dezelfde poort.

>[!NOTE]
>
>De stappen die in dit artikel worden vermeld zijn de specifieke Server 2007 van Microsoft SharePoint. U kunt HTML-werkruimte ook configureren met andere ondersteunde versies van Microsoft SharePoint.

## De werkruimte van AEM-formulieren integreren met Microsoft Office SharePoint Server 2007 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

Voer de volgende stappen uit om de Werkruimte van Vormen AEM in een Deel van het Web te integreren:

1. In Webbrowser, navigeer aan de plaats van SharePoint zoals, `https://[myMOSSserver]:44299/default.aspx` waar de naam of het IP adres van de server van SharePoint `[myMOSSserver]` is.

   >[!NOTE]
   >
   >44299 is het standaardpoortnummer voor de SharePoint-server. Het poortnummer is afhankelijk van uw installatie van SharePoint Server.

1. Klik in de rechterbovenhoek van de webpagina op **Site-handelingen** en selecteer Pagina **** bewerken.
1. Klik op de knop **Een webonderdeel** toevoegen.
1. Selecteer onder Dialoogvenster Dialoogvenster Webonderdelen toevoegen - Webpagina onder Dialoogvenster **Paginaviewer en klik vervolgens op** Toevoegen ****.
1. Klik in het vak Webonderdeel van de paginaviewer op **Bewerken** en selecteer Gedeeld webonderdeel **** wijzigen.

   >[!NOTE]
   >
   >Het vakje van het Deel van het Web van de Kijker van de Pagina verschijnt onder de **Add een knoop van het Deel** van het Web die u in stap 3 zoals aangetoond in de volgende illustratie (Figuur 1) klikte:

   ![Het vakje van het Deel van het Web van de Kijker van de pagina in de server van SharePoint van Microsoft Office.](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   Figuur 1. - Het vakje van het Deel van het Web van de Kijker van de Pagina in de server van Microsoft Office SharePoint.

1. Voer op de pagina Paginaviewer de volgende taken uit:

   1. Typ in het vak Koppeling de URL van de AEM Forms Workspace, bijvoorbeeld `https://[AEM_forms_Server]:8080/lc/ws` waar de IP of naam van de AEM-formulierserver `[AEM_forms_Server]` staat.
   1. Klik op **Weergave** en wijzig de hoogte, breedte en titel zodat u de volledige gebruikersinterface van de werkruimte kunt zien. U kunt de hoogte en breedte bijvoorbeeld instellen op respectievelijk 6 en 11 inch.
   1. Klik op Koppeling **** testen. Er wordt een nieuw webbrowservenster weergegeven met Workspace erin.
   1. (Optioneel) Klik op **Lay-out** en wijzig de lay-out van de werkruimte in het webonderdeel.
   1. (Optioneel) Klik op **Geavanceerd** en wijzig andere instellingen, zoals de beschrijving en of Workspace in het webonderdeel kan worden geminimaliseerd of gesloten.

      Klik op **Toepassen**.

1. Klik op **Bewerkmodus** afsluiten en controleer of u toegang hebt tot de werkruimte.

Nadat u de bovenstaande stappen hebt uitgevoerd, ziet uw SharePoint-site eruit zoals in de volgende afbeelding (Afbeelding 2):

![AEM-werkruimte voor formulieren geïntegreerd met Microsoft Office SharePoint-server](assets/aem-forms-workspace.jpg)

Figuur 2 - AEM vormt Werkruimte die met de Server van Microsoft Office SharePoint wordt geïntegreerd

