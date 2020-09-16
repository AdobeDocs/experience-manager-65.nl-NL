---
title: ' [!DNL Adobe Stock] Elementen beheren in [!DNL Adobe Experience Manager Assets].'
description: Zoek, haal, vergunning, en [!DNL Adobe Stock] beheer activa van binnen [!DNL Adobe Experience Manager]. Gebruik de in licentie gegeven activa als elk ander digitaal actief.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 2ac848fa360ad87ff4f87efc38ae1361ae890cb2
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 2%

---


# Elementen gebruiken [!DNL Adobe Stock] in [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

Organisaties kunnen hun [!DNL Adobe Stock] ondernemingsplan integreren [!DNL Experience Manager Assets] om ervoor te zorgen dat gelicentieerde middelen breed beschikbaar zijn voor hun creatieve en marketingprojecten, met de krachtige mogelijkheden voor middelenbeheer van [!DNL Experience Manager].

[!DNL Adobe Stock] biedt ontwerpers en bedrijven toegang tot miljoenen kwalitatief hoogstaande, gekrulde, royaltyvrije foto&#39;s, vectoren, illustraties, video&#39;s, sjablonen en 3D-middelen voor al hun creatieve projecten. [!DNL Experience Manager] gebruikers kunnen snel [!DNL Adobe Stock] elementen zoeken, voorvertonen en licentiëren die in [!DNL Experience Manager]de [!DNL Experience Manager] interface zijn opgeslagen.

## Vereisten {#prerequisites}

Voor de integratie is een Adobe Stock- [ondernemingsplan](https://stockenterprise.adobe.com/)vereist.

## Integreer [!DNL Experience Manager] en [!DNL Adobe Stock] {#integrate-aem-and-adobe-stock}

Om communicatie tussen [!DNL Experience Manager] en [!DNL Adobe Stock]toe te staan, creeer een configuratie IMS en een [!DNL Adobe Stock] configuratie in [!DNL Experience Manager].

>[!NOTE]
>
>Alleen [!DNL Experience Manager] beheerders en [!DNL Admin Console] beheerders van een organisatie kunnen de integratie uitvoeren omdat hiervoor beheerdersrechten zijn vereist.

### Create an IMS configuration {#create-an-ims-configuration}

1. In the [!DNL Experience Manager] user interface, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Klik op **[!UICONTROL Create]** en selecteer **[!UICONTROL Cloud Solution]** > **[!UICONTROL Adobe Stock]**.
1. U kunt een bestaand certificaat opnieuw gebruiken of selecteren **[!UICONTROL Create new certificate]**.
1. Klik op **[!UICONTROL Create certificate]**. Download de openbare sleutel wanneer deze is gemaakt. Klik op **[!UICONTROL Next]**.
1. Voeg de gedownloade openbare sleutel toe aan uw [!DNL Adobe Developer Console] serviceaccount. Klik op **[!UICONTROL Next]**. Laat het [!UICONTROL Adobe IMS Technical Account Configuration] scherm open om de waarden over enkele ogenblikken weer te geven.
1. Toegang tot [Adobe Developer Console](https://console.adobe.io). Zorg ervoor dat uw account beheerdersmachtigingen heeft voor de organisatie waarvoor de integratie is vereist.
1. Klik **[!UICONTROL Create new project]** en klik **[!UICONTROL Add API]**. Selecteer een optie **[!UICONTROL Adobe Stock]** in de lijst met API&#39;s die voor u beschikbaar zijn. Selecteer [!UICONTROL OAUTH 2.0 Web]. Configureer en kopieer de verschillende gepresenteerde waarden.
1. In [!DNL Experience Manager] provide the values in the fields titled **[!UICONTROL Title]**, **[!UICONTROL Authorization Server]**, **[!UICONTROL API Key]**, **[!UICONTROL Client Secret]**, and **[!UICONTROL Payload]**. Zie [JWT-verificatie snel starten](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md)voor meer informatie over deze waarden.

<!-- TBD: Update the URL to update the terminology when AIO team updates their documentation URL. Logged issue github.com/AdobeDocs/adobeio-auth/issues/63.
-->

### Configuratie maken [!DNL Adobe Stock] in [!DNL Experience Manager] {#create-adobe-stock-configuration-in-aem}

1. Navigeer in het [!DNL Experience Manager]venster naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Klik **[!UICONTROL Create]** om een configuratie tot stand te brengen en het te associëren met uw bestaande Configuratie IMS. Selecteren `PROD` als omgevingsparameter.
1. Laat in **[!UICONTROL Licensed Assets Path]** het veld de locatie ongewijzigd. Wijzig de locatie waar u de [!DNL Adobe Stock] elementen wilt opslaan niet.
1. Voltooi het maken door alle vereiste eigenschappen toe te voegen. Klik op **[!UICONTROL Save & Close]**.
1. Voeg [!DNL Experience Manager] gebruikers of groepen toe die een licentie voor de elementen kunnen verkrijgen.

>[!NOTE]
>
>Als er meerdere [!DNL Adobe Stock] configuraties zijn, selecteert u de gewenste configuratie in het deelvenster Gebruikersvoorkeuren. Als u het deelvenster vanaf de startpagina van de Experience Manager wilt openen, klikt u op het gebruikerspictogram en vervolgens op **[!UICONTROL User Preferences]** > **[!UICONTROL Stock Configuration]**).

## [!DNL Adobe Stock] Elementen gebruiken en beheren in [!DNL Experience Manager] {#usemanage}

Met deze mogelijkheid kunnen organisaties hun gebruikers toestaan te werken met [!DNL Adobe Stock] middelen in [!DNL Experience Manager Assets]. Vanuit de [!DNL Experience Manager] gebruikersinterface kunnen gebruikers zoeken naar [!DNL Adobe Stock] middelen en een licentie voor de vereiste middelen aanschaffen.

Als een [!DNL Adobe Stock] [!DNL Experience Manager]actief eenmaal in licentie is gegeven, kan het worden gebruikt en beheerd als een typisch actief. De gebruikers kunnen bovendien de elementen zoeken en voorvertonen. [!DNL Experience Manager]de elementen kopiëren en publiceren; delen van de activa op [!DNL Brand Portal]; toegang tot en gebruik de middelen via [!DNL Experience Manager] bureaubladtoepassing; enzovoort.

![Zoeken naar Adobe Stock-middelen en filterresultaten vanuit uw Adobe Experience Manager-werkruimte](assets/adobe-stock-search-results-workspace.png)

*Afbeelding: Zoek naar[!DNL Adobe Stock]activa en filterresultaten van uw[!DNL Experience Manager]interface.*

**A.** Zoek elementen die vergelijkbaar zijn met de elementen waarvan de id is opgegeven. [!DNL Adobe Stock] **B.** Zoek naar assets die overeenkomen met de vorm of afdrukstand die u hebt geselecteerd. **C.** Zoek naar één van meer gesteunde activa types **D.** Open of vouwt het venster Filters **E.** Licentie toewijzen en het geselecteerde element opslaan in [!DNL Experience Manager] **F.** Sla het element op in [!DNL Experience Manager] combinatie met watermerk **G.** Verken elementen op [!DNL Adobe Stock] websites die lijken op de geselecteerde elementen **H.** Bekijk de geselecteerde middelen op [!DNL Adobe Stock] website **I.** Aantal geselecteerde elementen uit de zoekresultaten **J.** Schakelen tussen de kaartweergave en de lijstweergave

### Elementen zoeken {#find-assets}

Uw [!DNL Experience Manager] gebruikers kunnen naar elementen zoeken, zowel in [!DNL Experience Manager] als [!DNL Adobe Stock]. Wanneer de zoeklocatie niet beperkt is tot [!DNL Adobe Stock], worden de zoekresultaten van [!DNL Experience Manager] en [!DNL Adobe Stock] weergegeven.

* Als u naar [!DNL Adobe Stock] elementen wilt zoeken, klikt u op **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** > **[!UICONTROL Search Adobe Stock]**.

* Als u naar elementen wilt zoeken [!DNL Adobe Stock] en [!DNL Experience Manager Assets]klikt u op ![Zoeken](assets/do-not-localize/search_icon.png).

U kunt ook `Location: Adobe Stock` [!DNL Adobe Stock] in de zoekbalk typen om elementen te selecteren. [!DNL Experience Manager] biedt geavanceerde filtermogelijkheden voor de gezochte middelen, die gebruikers toestaan om op de vereiste activa snel nul-binnen op de filters te gebruiken, zoals types van gesteunde activa, beeldrichtlijn, en vergunning gegeven staat.

>[!NOTE]
>
>Assets searched from [!DNL Adobe Stock] are just displayed in [!DNL Experience Manager]. [!DNL Adobe Stock] elementen worden pas opgehaald en opgeslagen in de [!DNL Experience Manager] opslagplaats nadat een gebruiker een middel [of](/help/assets/aem-assets-adobe-stock.md#saveassets) licenties heeft [opgeslagen en een middel](/help/assets/aem-assets-adobe-stock.md#licenseassets)heeft opgeslagen. Assets that are already stored in [!DNL Experience Manager] are displayed and highlighted for ease of reference and access. Also, the [!DNL Stock] assets are saved with some additional metadata to indicate the source as [!DNL Stock].

![Zoekfilters in Experience Manager en gemarkeerde Adobe Stock-elementen in zoekresultaten](assets/aem-search-filters2.jpg)

*Afbeelding: Zoekfilters in[!DNL Experience Manager]en gemarkeerde[!DNL Adobe Stock]elementen in zoekresultaten.*

### De vereiste elementen opslaan en weergeven {#saveassets}

Selecteer een element waarin u wilt opslaan [!DNL Experience Manager]. Klik [!UICONTROL Save] in de toolbar bij de bovenkant en verstrek de naam en de plaats van de activa. De elementen zonder licentie worden lokaal met een watermerk opgeslagen.

De volgende keer dat u naar elementen zoekt, worden de opgeslagen elementen gemarkeerd met een badge om aan te geven dat dergelijke elementen beschikbaar zijn in [!DNL Experience Manager Assets].

>[!NOTE]
>
>De onlangs toegevoegde elementen geven een nieuwe badge weer in plaats van een badge met licentie.

### Licentie-elementen {#licenseassets}

Gebruikers kunnen [!DNL Adobe Stock] middelen in licentie geven met behulp van het quotum van hun [!DNL Adobe Stock] ondernemingsplan. Wanneer u een licentie voor een element aanschaft, wordt het zonder watermerk opgeslagen en kunt u het zoeken en gebruiken in [!DNL Experience Manager Assets].

![Dialoogvenster voor het in licentie geven en opslaan van Adobe Stock-middelen in Experience Manager Assets](assets/aem-stock_licenseandsave.jpg)

*Afbeelding: Dialoogvenster voor het in licentie geven en opslaan van[!DNL Adobe Stock]middelen in[!DNL Experience Manager Assets].*

### Metagegevens en elementen openen {#access-metadata-and-asset-properties}

Gebruikers kunnen de metagegevens openen en voorvertonen, inclusief de [!DNL Adobe Stock] metagegevenseigenschappen voor de elementen die zijn opgeslagen in [!DNL Experience Manager]en toevoegen **[!UICONTROL License References]** voor een element. De updates van de licentieverwijzing worden echter niet gesynchroniseerd tussen [!DNL Experience Manager] en de [!DNL Adobe Stock] website.

Gebruikers kunnen de eigenschappen van zowel gelicentieerde als niet-gelicentieerde activa zien.

![Metagegevens en licentieverwijzingen van opgeslagen elementen weergeven en openen](assets/metadata_properties.jpg)

*Afbeelding: Metagegevens en licentieverwijzingen van opgeslagen elementen weergeven en openen.*

## Bekende beperkingen {#known-limitations}

* **Waarschuwing voor redactionele afbeelding wordt niet weergegeven**: Wanneer gebruikers een licentie voor een afbeelding verlenen, kunnen ze niet controleren of een afbeelding alleen voor gebruik als redactie is. Om mogelijk misbruik te voorkomen, kunnen de beheerders de toegang tot redactionele activa van de Admin Console uitschakelen.

* **Er wordt een onjuist licentietype weergegeven**: Het is mogelijk dat een onjuist licentietype wordt weergegeven [!DNL Experience Manager] voor een element. Gebruikers kunnen zich aanmelden bij de [!DNL Adobe Stock] website om het type licentie te zien.

* **Referentievelden en metagegevens worden niet gesynchroniseerd**: Wanneer een gebruiker een veld met een licentieverwijzing bijwerkt, wordt de informatie over de licentieverwijzing bijgewerkt in, [!DNL Experience Manager] maar niet op de [!DNL Adobe Stock] website. Als de gebruiker de referentievelden op de [!DNL Adobe Stock] website bijwerkt, worden de updates ook niet gesynchroniseerd [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [Videozelfstudie over het gebruik van Adobe Stock-elementen met Experience Manager Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/creative-workflows/adobe-stock.html)
>* [Adobe Stock Enterprise Plan Help](https://helpx.adobe.com/enterprise/using/adobe-stock-enterprise.html)
>* [Veelgestelde vragen over Adobe Stock](https://helpx.adobe.com/stock/faq.html)

