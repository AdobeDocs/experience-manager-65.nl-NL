---
title: Beheren [!DNL Adobe Stock] middelen
description: Zoek, haal, vergunning, en beheer [!DNL Adobe Stock] activa van binnen [!DNL Adobe Experience Manager]. Gebruik de in licentie gegeven activa als elk ander digitaal actief.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 12c56c27c7f97f1029c757ec6d28f482516149d0
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 3%

---


# [!DNL Adobe Stock] middelen gebruiken in [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

Organisaties kunnen hun [!DNL Adobe Stock]-ondernemingsplan integreren met [!DNL Experience Manager Assets] om ervoor te zorgen dat gelicentieerde middelen breed beschikbaar zijn voor hun creatieve en marketingprojecten, met de krachtige mogelijkheden voor middelenbeheer van [!DNL Experience Manager].

[!DNL Adobe Stock] biedt ontwerpers en bedrijven toegang tot miljoenen kwalitatief hoogstaande, gekrulde, royaltyvrije foto&#39;s, vectoren, illustraties, video&#39;s, sjablonen en 3D-middelen voor al hun creatieve projecten. [!DNL Experience Manager] gebruikers kunnen snel  [!DNL Adobe Stock] elementen zoeken, voorvertonen en licentiëren die zijn opgeslagen in  [!DNL Experience Manager], zonder de  [!DNL Experience Manager] interface te verlaten.

## Vereisten {#prerequisites}

De integratie vereist een [onderneming [!DNL Adobe Stock] plan](https://stockenterprise.adobe.com/).

## [!DNL Experience Manager] en [!DNL Adobe Stock] {#integrate-aem-and-adobe-stock} integreren

Om communicatie tussen [!DNL Experience Manager] en [!DNL Adobe Stock] toe te staan, creeer een configuratie IMS en een [!DNL Adobe Stock] configuratie in [!DNL Experience Manager].

>[!NOTE]
>
>Alleen [!DNL Experience Manager]-beheerders en [!DNL Admin Console]-beheerders voor een organisatie kunnen de integratie uitvoeren omdat hiervoor beheerdersrechten vereist zijn.

### Een IMS-configuratie {#create-an-ims-configuration} maken

1. Navigeer in de gebruikersinterface [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Klik op **[!UICONTROL Create]** en selecteer **[!UICONTROL Cloud Solution]** > **[!UICONTROL Adobe Stock]**.
1. U kunt een bestaand certificaat opnieuw gebruiken of **[!UICONTROL Create new certificate]** selecteren.
1. Klik op **[!UICONTROL Create certificate]**. Download de openbare sleutel wanneer deze is gemaakt. Klik op **[!UICONTROL Next]**.
1. Voeg de gedownloade openbare sleutel aan uw [!DNL Adobe Developer Console] de dienstrekening toe. Klik op **[!UICONTROL Next]**. Laat het scherm [!UICONTROL Adobe IMS Technical Account Configuration] open om de waarden over enkele ogenblikken weer te geven.
1. Toegang [Adobe Developer Console](https://console.adobe.io). Zorg ervoor dat uw account beheerdersmachtigingen heeft voor de organisatie waarvoor de integratie is vereist.
1. Klik **[!UICONTROL Create new project]** en klik **[!UICONTROL Add API]**. Selecteer **[!UICONTROL Adobe Stock]** in de lijst met API&#39;s die voor u beschikbaar zijn. Selecteer [!UICONTROL OAUTH 2.0 Web]. Configureer en kopieer de verschillende gepresenteerde waarden.
1. Geef in [!DNL Experience Manager] de waarden op in de velden **[!UICONTROL Title]**, **[!UICONTROL Authorization Server]**, **[!UICONTROL API Key]**, **[!UICONTROL Client Secret]** en **[!UICONTROL Payload]**. Zie [JWT-verificatie snel start](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md) voor gedetailleerde informatie over deze waarden.

<!-- TBD: Update the URL to update the terminology when AIO team updates their documentation URL. Logged issue github.com/AdobeDocs/adobeio-auth/issues/63.
-->

### [!DNL Adobe Stock]-configuratie maken in [!DNL Experience Manager] {#create-adobe-stock-configuration-in-aem}

1. Navigeer in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Klik **[!UICONTROL Create]** om een configuratie tot stand te brengen en het te associëren met uw bestaande Configuratie IMS. Selecteer `PROD` als milieuparameter.
1. Laat in het veld **[!UICONTROL Licensed Assets Path]** de huidige locatie ongewijzigd. Wijzig niet de locatie waar u de [!DNL Adobe Stock] elementen wilt opslaan.
1. Voltooi het maken door alle vereiste eigenschappen toe te voegen. Klik op **[!UICONTROL Save & Close]**.
1. Voeg [!DNL Experience Manager] gebruikers of groepen toe die een licentie voor de elementen kunnen verkrijgen.

>[!NOTE]
>
>Als er veelvoudige [!DNL Adobe Stock] configuraties zijn, selecteer de gewenste configuratie in [!UICONTROL User Preferences] paneel. Als u het deelvenster wilt openen vanaf de startpagina van [!DNL Experience Manager], klikt u op het gebruikerspictogram en vervolgens op **[!UICONTROL User Preferences]** > **[!UICONTROL Stock Configuration]**.

## [!DNL Adobe Stock]-middelen gebruiken en beheren in [!DNL Experience Manager] {#usemanage}

Met behulp van deze mogelijkheid kunnen organisaties hun gebruikers toestaan te werken met [!DNL Adobe Stock] middelen in [!DNL Experience Manager Assets]. Vanuit de [!DNL Experience Manager]-gebruikersinterface kunnen gebruikers zoeken in [!DNL Adobe Stock]-middelen en een licentie voor de vereiste middelen aanschaffen.

Zodra een [!DNL Adobe Stock] element in [!DNL Experience Manager] vergunning wordt gegeven, kan het als typisch activa worden gebruikt en worden beheerd. In [!DNL Experience Manager] kunnen de gebruikers de elementen zoeken en voorvertonen; de elementen kopiëren en publiceren; delen van de activa op [!DNL Brand Portal]; toegang tot en gebruik de middelen via [!DNL Experience Manager] desktop app; enzovoort.

![Zoeken naar  [!DNL Adobe Stock] elementen en filterresultaten vanuit uw  [!DNL Adobe Experience Manager] werkruimte](assets/adobe-stock-search-results-workspace.png)

*Afbeelding: Zoek naar  [!DNL Adobe Stock] activa en filterresultaten van uw  [!DNL Experience Manager] interface.*

**A.Elementen** zoeken die vergelijkbaar zijn met de elementen waarvan de  [!DNL Adobe Stock] id is opgegeven. **B.** Zoek naar assets die overeenkomen met de vorm of afdrukstand die u hebt geselecteerd. **C.** Zoeken naar een of meer ondersteunde elementtypen  **D.** Het deelvenster  **E.** Licentie openen of samenvouwen en het geselecteerde element opslaan in  [!DNL Experience Manager] **F.** Het element opslaan in  [!DNL Experience Manager] het watermerk  **G.**   [!DNL Adobe Stock]   ****   [!DNL Adobe Stock]   ****   **** Elementen op de website ontdekken die vergelijkbaar zijn met het geselecteerde element.H.De geselecteerde middelen op de websiteI.ZoekresultatenAantal geselecteerde middelen op J.Switch tussen de kaartweergave en de lijstweergave

### Elementen {#find-assets} zoeken

Uw [!DNL Experience Manager] gebruikers, kunnen activa in zowel [!DNL Experience Manager] als [!DNL Adobe Stock] zoeken. Wanneer de zoeklocatie niet beperkt is tot [!DNL Adobe Stock], worden de zoekresultaten van [!DNL Experience Manager] en [!DNL Adobe Stock] weergegeven.

* Als u naar [!DNL Adobe Stock] elementen wilt zoeken, klikt u op **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** > **[!UICONTROL Search Adobe Stock]**.

* Als u wilt zoeken naar elementen in [!DNL Adobe Stock] en [!DNL Experience Manager Assets], klikt u op Zoeken ![search](assets/do-not-localize/search_icon.png).

U kunt ook `Location: Adobe Stock` in de zoekbalk typen om [!DNL Adobe Stock] elementen te selecteren. [!DNL Experience Manager] biedt geavanceerde filtermogelijkheden voor de gezochte middelen, die gebruikers toestaan om op de vereiste activa snel nul-binnen op de filters te gebruiken, zoals types van gesteunde activa, beeldrichtlijn, en vergunning gegeven staat.

>[!NOTE]
>
>Elementen die worden doorzocht vanaf [!DNL Adobe Stock] worden alleen weergegeven in [!DNL Experience Manager]. [!DNL Adobe Stock] elementen worden pas opgehaald en opgeslagen in de  [!DNL Experience Manager] opslagplaats nadat een gebruiker een  [assetor-](/help/assets/aem-assets-adobe-stock.md#saveassets) licentie  [heeft opgeslagen en een middel](/help/assets/aem-assets-adobe-stock.md#licenseassets) heeft opgeslagen. Elementen die al zijn opgeslagen in [!DNL Experience Manager] worden weergegeven en gemarkeerd voor eenvoudige referentie en toegang. Bovendien worden de [!DNL Stock]-elementen met extra metagegevens opgeslagen om de bron aan te geven als [!DNL Stock].

![Filters zoeken in  [!DNL Experience Manager] en gemarkeerde  [!DNL Adobe Stock] elementen in zoekresultaten](assets/aem-search-filters2.jpg)

*Afbeelding: Zoekfilters in  [!DNL Experience Manager] en gemarkeerde  [!DNL Adobe Stock] elementen in zoekresultaten.*

### De vereiste elementen opslaan en weergeven {#saveassets}

Selecteer een middel dat u in [!DNL Experience Manager] wilt bewaren. Klik [!UICONTROL Save] in de toolbar bij de bovenkant en verstrek de naam en de plaats van de activa. De elementen zonder licentie worden lokaal met een watermerk opgeslagen.

De volgende keer dat u naar elementen zoekt, worden de opgeslagen elementen gemarkeerd met een badge om aan te geven dat dergelijke elementen beschikbaar zijn in [!DNL Experience Manager Assets].

>[!NOTE]
>
>De onlangs toegevoegde elementen geven een nieuwe badge weer in plaats van een badge met licentie.

### Licentie-elementen {#licenseassets}

Gebruikers kunnen [!DNL Adobe Stock]-middelen in licentie geven door gebruik te maken van de quota van hun [!DNL Adobe Stock]-ondernemingsplan. Wanneer u een licentie voor een element aanschaft, wordt het zonder watermerk opgeslagen en is het beschikbaar voor zoeken en gebruiken in [!DNL Experience Manager Assets].

![Dialoogvenster voor het in licentie geven en opslaan van  [!DNL Adobe Stock] middelen in  [!DNL Experience Manager Assets]](assets/aem-stock_licenseandsave.jpg)

*Afbeelding: Dialoogvenster voor het in licentie geven en opslaan van  [!DNL Adobe Stock] middelen in  [!DNL Experience Manager Assets].*

### Toegang tot metagegevens en elementeigenschappen {#access-metadata-and-asset-properties}

Gebruikers kunnen de metagegevens openen en voorvertonen, inclusief de metagegevenseigenschappen [!DNL Adobe Stock] voor de elementen die zijn opgeslagen in [!DNL Experience Manager], en **[!UICONTROL License References]** toevoegen voor een element. De updates voor de licentieverwijzing worden echter niet gesynchroniseerd tussen [!DNL Experience Manager]- en [!DNL Adobe Stock]-website.

Gebruikers kunnen de eigenschappen van zowel gelicentieerde als niet-gelicentieerde activa zien.

![Metagegevens en licentieverwijzingen van opgeslagen elementen weergeven en openen](assets/metadata_properties.jpg)

*Afbeelding: Metagegevens en licentieverwijzingen van opgeslagen elementen weergeven en openen.*

## Bekende beperkingen {#known-limitations}

* **Waarschuwing voor redactionele afbeelding wordt niet weergegeven**: Wanneer gebruikers een licentie voor een afbeelding verlenen, kunnen ze niet controleren of een afbeelding alleen voor gebruik als redactie is. Om mogelijk misbruik te voorkomen, kunnen de beheerders de toegang tot redactionele activa van de Admin Console uitschakelen.

* **Er wordt een onjuist licentietype weergegeven**: Het is mogelijk dat een onjuist licentietype wordt weergegeven  [!DNL Experience Manager] voor een element. Gebruikers kunnen zich aanmelden bij de [!DNL Adobe Stock]-website om het type licentie te zien.

* **Referentievelden en metagegevens worden niet gesynchroniseerd**: Wanneer een gebruiker een veld met een licentieverwijzing bijwerkt, wordt de informatie over de licentieverwijzing bijgewerkt in  [!DNL Experience Manager] maar niet op de  [!DNL Adobe Stock] website. Als de gebruiker de referentievelden op de [!DNL Adobe Stock]-website bijwerkt, worden de updates niet gesynchroniseerd in [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [Videozelfstudie over het  [!DNL Adobe Stock] gebruik van middelen met [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html)
>* [[!DNL Adobe Stock] Help bij bedrijfsplan](https://helpx.adobe.com/enterprise/using/adobe-stock-enterprise.html)
>* [[!DNL Adobe Stock] Veelgestelde vragen](https://helpx.adobe.com/stock/faq.html)

