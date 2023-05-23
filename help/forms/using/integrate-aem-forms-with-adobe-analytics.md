---
title: Hoe kan AEM Forms met Adobe Analytics worden geïntegreerd?
description: AEM Forms is geïntegreerd met Adobe Analytics om prestatiegegevens voor gepubliceerde formulieren vast te leggen en bij te houden.
docset: aem65
exl-id: 030fe9f2-cd41-4290-b8a6-2f9ade6b5789
source-git-commit: 45ca98ffb68e1e31e2f45f352e86f5aa1b6f0f00
workflow-type: tm+mt
source-wordcount: '1605'
ht-degree: 0%

---

# Analyse met [!DNL Adobe Launch] {#analyticsusingadobelaunch}

AEM Forms kan worden geïntegreerd met [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/overview.html?lang=en) waarmee u prestatiegegevens voor gepubliceerde formulieren kunt vastleggen en bijhouden. Het doel achter het analyseren van deze metriek is bedrijfsgebruikers toe te laten om inzicht in eindgebruikergedrag te verwerven en de ervaring van het gegevensvangst te optimaliseren. U kunt gedrag van zowel aangemelde als niet-aangemelde (anonieme) gebruikers vastleggen en volgen via Adobe Analytics for Adaptive Forms.

U kunt analyses ook uitvoeren gebruikend het Kader van de Cloud Service. Voor meer informatie over hoe te om AEM Forms met het Kader van de Cloud Service te integreren, zie [Analyse met gebruik van Cloud Service Framework](/help/forms/using/configure-analytics-forms-documents.md). Het belangrijkste voordeel van het gebruiken van de Lancering van Adobe over Analytics die het Kader van de Cloud Service gebruikt is dat u douanefouten, naast deze uit de doodebeurtenissen kunt ook bepalen. De aangepaste gebeurtenissen worden bepaald gebruikend regelredacteur of klantenclientlibs en aan gebeurtenissen in kaart gebracht in [!DNL Adobe Analytics].

Nadat u de in dit artikel vermelde handelingen hebt uitgevoerd, kunt u rapporten configureren en weergeven in [!DNL Adobe Analytics], zoals in de volgende video wordt getoond:

>[!VIDEO](https://video.tv.adobe.com/v/337262)

U kunt [!DNL Adobe Analytics] om interactiepatronen en problemen te ontdekken waarmee gebruikers worden geconfronteerd wanneer ze adaptieve formulieren gebruiken. Uit de doos, [!DNL Adobe Analytics] volgt en slaat informatie over de volgende gebeurtenissen op:

* **Renderen**: Aantal keren dat een formulier wordt geopend.

* **Verzenden**: Aantal keer dat een formulier wordt verzonden.

* **Abandon**: Aantal keren dat de gebruikers het formulier verlaten zonder het in te vullen.

* **Fout**: Aantal fouten aangetroffen in het deelvenster en in de velden van het deelvenster.

* **Help**: Het aantal keren dat een gebruiker de Help van een deelvenster en de velden van het deelvenster opent.

* **Veld bezoeken**: Aantal keren dat een gebruiker een veld in het formulier bezoekt.

* **Opslaan**: Aantal keren dat gebruikers een formulier opslaan op de Forms Portal.

Naast deze gebeurtenissen uit de box kunt u ook aangepaste gebeurtenissen definiëren.

Het volgende cijfer illustreert de acties die u moet uitvoeren alvorens rapporten in te bekijken [!DNL Adobe Analytics]:

![Overzicht van analysemogelijkheden](/help/forms/using/assets/analyticsworkflow.png)

## 1. Configureren [!DNL Adobe Analytics] {#Configure-adobe-analytics}

Voor het configureren [!DNL Adobe Analytics], maak:

* Een Adobe ID om u aan te melden bij [Adobe Experience Cloud](https://experience.adobe.com/#/home).
* A [rapportsuite](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html).


### AEM Forms installeren en [!DNL Adobe Analytics] extensions {#install-extensions}

Voer de volgende stappen uit om AEM Forms en [Adobe Analytics](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/analytics/overview.html) extensies:

1. Meld u aan bij Adobe Experience Cloud en selecteer de gewenste naam voor het bedrijf.

1. Tikken **[!UICONTROL Launch/Data Collection]** en tikken **[!UICONTROL Go to Launch/Data Collection]**.

1. Tikken **[!UICONTROL New property]** en geeft u een naam voor de configuratie op.

1. Geef een domeinnaam op en tik op **[!UICONTROL Save]** om de eigenschap op te slaan.

1. Tik op de configuratienaam die beschikbaar is in de lijst Tageigenschappen.

1. In de **[!UICONTROL Authoring]** sectie, tikken **[!UICONTROL Extensions]**.

1. Tikken **[!UICONTROL Catalog]** en tikken **[!UICONTROL Install]** voor de **[!UICONTROL Adobe Experience Manager Forms]** extensie. **[!UICONTROL Adobe Experience Manager Forms]** wordt weergegeven in de lijst met geïnstalleerde extensies die beschikbaar is in het dialoogvenster **Geïnstalleerd** tab.

1. Tikken **[!UICONTROL Install]** voor de **[!UICONTROL Adobe Analytics]** extensie.
1. Selecteer de naam van de rapportsuite in het dialoogvenster **[!UICONTROL Development Report Suites]**, **[!UICONTROL Staging Report Suites]**, en **[!UICONTROL Product Report Suites]** vervolgkeuzelijsten en tikken **[!UICONTROL Save]** om de extensie op te slaan.

### Gegevenselementen configureren {#configure-data-elements}

U kunt om het even welke gevormde gegevenselementen in een regel selecteren die voor een gebeurtenis wordt gecreeerd. Wanneer een gebeurtenis plaatsvindt op een adaptief formulier, stuurt AEM Forms deze gegevenselementen naar [!DNL Adobe Analytics].

Nadat u de **[!UICONTROL Adobe Experience Manager Forms]** kunt u de volgende gegevenselementen maken:

<table>
 <tbody>
  <tr>
   <td>FieldName</th>
   <td>FieldTitle</th>
   <td>FormInstance</th>
  </tr>
  <tr>
   <td>FormName<br /> </td>
   <td>FormTitle<br /> </td>
   <td>PageName</td>
  </tr>
  <tr>
   <td>PageURL<br /> </td>
   <td>PanelTitle<br /> </td>
   <td>TimeSpent</td>
  </tr>
 </tbody>
</table>

Voer de volgende stappen uit om gegevenselementen te configureren:

1. In de **[!UICONTROL Authoring]** sectie, tikken **[!UICONTROL Data Elements]**.

1. Tik op **[!UICONTROL Create New Data Element]**.

1. Geef een naam op voor het gegevenselement. Bijvoorbeeld het gegevenstype Formuliertitel voor het gegevenstype FormTitle.

1. Opgeven **[!UICONTROL Adobe Experience Manager Forms]** als de naam van de extensie.

1. Selecteer **[!UICONTROL Data Element Type]**.

1. Tikken **[!UICONTROL Save]** om het gegevenselement op te slaan.

   >[!VIDEO](https://video.tv.adobe.com/v/337472)

### Regels configureren {#configure-rules}

Voer de volgende stappen uit om regels te maken op basis van de **[!UICONTROL Adobe Experience Manager Forms]** extensie:

1. In de **[!UICONTROL Authoring]** sectie, tikken **[!UICONTROL Rules]**.

1. Tik op **[!UICONTROL Create New Rule]**.

1. Geef een naam voor de regel op. Formulier verzenden bijvoorbeeld om formulierverzendingen op te nemen.

1. In de **[!UICONTROL Events]** sectie, tikken **[!UICONTROL Add]**.

1. Opgeven **[!UICONTROL Adobe Experience Manager Forms]** als de naam van de extensie.

1. Selecteer het gebeurtenistype. De invoer voor de **[!UICONTROL Name]** wordt automatisch ingevuld op basis van het geselecteerde gebeurtenistype.

1. Tikken **[!UICONTROL Keep Changes]** om de gebeurtenis op te slaan.

1. In de **[!UICONTROL Actions]** sectie, tikken **[!UICONTROL Add]**.

1. Opgeven **[!UICONTROL Adobe Analytics]** als de naam van de extensie.

1. Selecteren **[!UICONTROL Set Variables]** als het Type van Actie. De volgende opties zijn beschikbaar in de vervolgkeuzelijst:

   * **[!UICONTROL Set Variables]**: Gebruik dit actietype om het gebeurtenistype te bepalen waarvoor de geselecteerde gegevenselementen van AEM Forms naar worden verzonden [!DNL Adobe Analytics].

   * **[!UICONTROL Send Beacon]**: Gebruik dit actietype om gegevens van AEM Forms naar te verzenden [!DNL Adobe Analytics].

   * **[!UICONTROL Clear Variables]**: Gebruik dit actietype om het gegevensspoor te wissen zodat de gebeurtenis slechts eenmaal wordt geregistreerd [!DNL Adobe Analytics].

      De aanbevolen aanpak is het gebruik van de **[!UICONTROL Set Variables]** actietype om de gebeurtenis en gegevenselementen te vormen, dan gebruik **[!UICONTROL Send Beacon]** om gegevens te verzenden, en dan te gebruiken **[!UICONTROL Clear Variables]** om het gegevensspoor te wissen.

1. In de **[!UICONTROL Props]** de sectie, in kaart brengen de opties van de rapportreeks beschikbaar in de drop-down lijst met de gegevenselementen die gebruikend worden bepaald [Gegevenselementen configureren](#configure-data-elements).

   Bijvoorbeeld om te verzenden **Formuliertitel** gegevenselement van AEM Forms naar [!DNL Adobe Analytics] wanneer u een formulier verzendt:
   1. In de **[!UICONTROL Props]** selecteert u een proxy voor Formuliertitel in de rapportsuite en tikt u vervolgens op ![Databasepictogram](/help/forms/using/assets/database-icon.svg) om deze toe te wijzen aan Formuliertitel die is gemaakt in [Gegevenselementen configureren](#configure-data-elements).

      ![definiëren-eigenschappen](/help/forms/using/assets/define-props.png)

   1. Tikken **[!UICONTROL Add Another]** om meer gegevenselementen aan de lijst toe te voegen.

1. In de **[!UICONTROL Events]** selecteert u een gebeurtenis uit de opties in de rapportsuite en tikt u op **[!UICONTROL Keep Changes]**.

1. In de **[!UICONTROL Actions]** sectie, tikken + en specificeren **[!UICONTROL Adobe Analytics]** als de naam van de extensie.

1. Selecteren **[!UICONTROL Send Beacon]** als het Type van Actie. Selecteer in het rechterdeelvenster de optie **[!UICONTROL s.t()]** gegevens verzenden naar [!DNL Adobe Analytics] en behandelt het als paginaweergave of **[!UICONTROL s.tl()]** gegevens verzenden naar [!DNL Adobe Analytics] en niet behandelen als paginaweergave. Tik op **[!UICONTROL Keep Changes]**.

1. In de **[!UICONTROL Actions]** sectie, tikken + en specificeren **[!UICONTROL Adobe Analytics]** als de naam van de extensie.

1. Selecteren **[!UICONTROL Clear Variables]** als het Type van Actie. Tik op **[!UICONTROL Keep Changes]**. Nadat u deze stappen hebt uitgevoerd, **[!UICONTROL Actions]** wordt weergegeven als:
   ![Configuratie van handelingen](/help/forms/using/assets/actions-config.png)

   De **[!UICONTROL Actions]** op basis van uw vereisten. U kunt bijvoorbeeld twee **Band verzenden** stappen in een stroom Handelingen om gegevens te verzenden naar [!DNL Adobe Analytics] en behandelt het als paginaweergave in één stap en verzendt gegevens naar [!DNL Adobe Analytics] en deze in de tweede stap niet als paginaweergave behandelen.

   ![Configuratie van handelingen](/help/forms/using/assets/actions-config-2.png)

1. Tikken **[!UICONTROL Save]** om de regel op te slaan.

   U kunt regels maken voor alle gebeurtenistypen, zoals Verlaten, Fout, Veldbezoek, Help, Rendering, Opslaan en Verzenden.

   >[!VIDEO](https://video.tv.adobe.com/v/337425)


### Stroom publiceren {#publish-flow}

Nadat u de gegevenselementen hebt gemaakt en deze in regels hebt gebruikt, publiceert u de configuratie voor het verzamelen van formuliergegevens in [!DNL Adobe Analytics].

Voer de volgende stappen uit om de configuratie te publiceren:

1. In de **[!UICONTROL Publishing]** sectie, tikken **[!UICONTROL Publishing Flow]**.

1. Tikken **[!UICONTROL Add Library]** en geeft u een naam op en selecteert u de omgeving voor de bibliotheek.

1. Tikken **[!UICONTROL Add All Changed Resources]** en tik vervolgens op **[!UICONTROL Save & Build to Development]**.

1. In de **[!UICONTROL Development]** sectie, tikken ![Meer opties](/help/forms/using/assets/more-options-icon.svg) en tik vervolgens op **[!UICONTROL Approve & Publish to Production]**.

1. Bevestig de wijzigingen en de publicatiestroom wordt binnenkort weergegeven in het dialoogvenster **[!UICONTROL Published]** sectie.

![Stroom publiceren](/help/forms/using/assets/publish-flow.png)

## 2. AEM Forms configureren {#configure-aem-forms}

Voordat u de Adobe Launch-configuratie maakt, moet u een [Adobe IMS-configuratie met Adobe Launch als cloudoplossing](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/connect-aem-launch-adobe-io.html).

### Adobe-startconfiguratie maken {#create-adobe-launch-configuration}

Voer de volgende stappen uit om een configuratie van de Adobe Lancering tot stand te brengen:

1. Ga in de AEM Forms Author-instantie naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Launch Configurations]**.

1. Selecteer een map om de configuratie te maken en tik op **[!UICONTROL Create]**.

1. Geef een titel voor de configuratie op in het dialoogvenster **[!UICONTROL Title]** veld.

1. Selecteer [gekoppelde Adobe IMS-configuratie](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/connect-aem-launch-adobe-io.html).

1. Selecteer de naam van het bedrijf dat tijdens het [Adobe Analytics configureren](#Configure-adobe-analytics).

1. Selecteer de naam van de eigenschap die is gemaakt tijdens [Adobe Analytics configureren](#install-extensions).

1. Tik op **[!UICONTROL Save & Close]**.

1. Publiceer de configuratie.

### Inschakelen [!DNL Adobe Analytics] voor een adaptief formulier {#enable-analytics-adaptive-form}

Te gebruiken [!DNL Adobe Launch] configuratie in een bestaand adaptief formulier:

1. Ga in de AEM Forms Author-instantie naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteer het adaptieve formulier en tik op **[!UICONTROL Properties]**.
1. In de **[!UICONTROL Basic]** selecteert u de [configuratiecontainer](#create-adobe-launch-configuration) wordt gebruikt tijdens het maken van de Adobe Launch-configuratie.
1. Tik op **[!UICONTROL Save & Close]**. Het adaptieve formulier is ingeschakeld voor [!DNL Adobe Analytics].
1. Publiceer het formulier.

Nadat u [!DNL Adobe Analytics] voor een adaptief formulier kunt u [validate](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html?lang=en#validate-the-page-view-beacon) als er een geschikte gegevensgebeurtenisstroom is tussen AEM Forms en [!DNL Adobe Analytics]. De integratie van AEM Forms met Adobe Analytics is voltooid. U kunt nu [configureren en weergeven van rapporten in Adobe Analytics](#view-reports-adobe-analytics).

>[!NOTE]
>In geval van beide [Analyse met gebruik van Cloud Service Framework](/help/forms/using/configure-analytics-forms-documents.md) en **Analyse met Adobe Launch** functies tegelijk ingeschakeld zijn, **Analyse met Adobe Launch** heeft voorrang.

### Regels maken om aangepaste gebeurtenissen vast te leggen (optioneel) {#capture-custom-events}

Maak regels voor specifieke velden van een adaptief formulier met de regeleditor om analysegegevens van een adaptief formulier te verzenden naar [!DNL Adobe Analytics].

In een proces in twee fasen definieert u een regel voor een veld in een adaptieve vorm. De regel verzendt een gebeurtenis. De naam van de gebeurtenis wordt toegewezen aan een aangepaste vastleggebeurtenis in het programma Adobe Launch.

U kunt als volgt regels maken met de regeleditor:

1. Tik op het veld en selecteer ![Regeleditor](/help/forms/using/assets/rule-editor-icon.svg) om de pagina van de regelredacteur te openen.
1. Een voorwaarde definiëren in het dialoogvenster [!UICONTROL When] van de regel.
1. In de [!UICONTROL Then] van de regel selecteert u **[!UICONTROL Dispatch Event]** van de **[!UICONTROL Select Action]** vervolgkeuzelijst.
1. Geef de naam van de gebeurtenis op in het dialoogvenster **[!UICONTROL Type Event Name]** veld.

Als de geboortedatum bijvoorbeeld vóór een bepaalde datum ligt, verzendt AEM Forms de **Beveiliging** gebeurtenis.

![Verzendgebeurtenis](/help/forms/using/assets/security-event.png)

De gebeurtenis toewijzen aan een aangepaste vastleggebeurtenis in [!DNL Adobe Analytics]:

1. [Een regel maken](#configure-rules).

1. In de **[!UICONTROL Events]** sectie, tikken **[!UICONTROL Add]**.

1. Opgeven **[!UICONTROL Adobe Experience Manager Forms]** als de naam van de extensie.

1. Selecteren **[!UICONTROL Capture Custom Event]** van de **[!UICONTROL Event Type]** vervolgkeuzelijst.

1. Geef de naam op van de gebeurtenis die u in stap 4 hebt opgegeven tijdens het maken van een regel met de regeleditor.

1. Tikken **Wijzigingen behouden** en voert de overige handelingen uit die in [Regels configureren](#configure-rules).

## 3. Rapporten configureren en weergeven in [!DNL Adobe Analytics] {#view-reports-adobe-analytics}

Nadat u een adaptief formulier hebt geconfigureerd voor het verzenden van gebeurtenisgegevens naar [!DNL Adobe Analytics]kunt u rapporten bekijken in [!DNL Adobe Analytics]:

1. Tikken ![Product selecteren](/help/forms/using/assets/select-analytics.png) en selecteert u **[!UICONTROL Analytics]**.

1. Tikken **[!UICONTROL Create Project]** en selecteert u **[!UICONTROL Blank project]**.

1. Selecteer de naam van de rapportsuite in de vervolgkeuzelijst rechtsboven in de vrije vorm.

1. Opgeven **Formuliertitel** in de **[!UICONTROL Search dimension items]** tekst om alle formuliertitels weer te geven.

1. Zet de titel van het aangepaste formulier neer op de knop **[!UICONTROL Drop a segment here (or any other component)]** tekstvak.

1. Van de **[!UICONTROL Metrics]** -sectie, zet de gebeurtenissen neer om bij te houden **[!UICONTROL Drop a metric here (or any other component)]** tekstvak.

1. Tikken ![Visualisaties](/help/forms/using/assets/visualization-icon.svg) en zet u een diagramtype neer in de sectie Vrije vorm. Op dezelfde manier kunt u veelvoudige grafiektypes aan de sectie van de Vrije vorm toevoegen.

1. Tik op Ctrl + S en geef een naam op om het project op te slaan.

Voor gedetailleerde informatie over het weergeven van rapporten over formulieranalyses raadpleegt u [AEM Forms-analyserapporten weergeven en begrijpen](../../forms/using/view-understand-aem-forms-analytics-reports.md).
