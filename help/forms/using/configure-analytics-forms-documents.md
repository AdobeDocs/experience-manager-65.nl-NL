---
title: Analyses en rapporten configureren
description: Leer hoe u Adobe Analytics configureert om interactiepatronen en problemen te detecteren waarmee gebruikers te maken krijgen bij het gebruik van adaptieve formulieren, adaptieve documenten en HTML5-formulieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
docset: aem65
exl-id: 72f0f8e3-e70b-4f78-aa0e-b31768b536f7
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 0%

---

# Analyse met gebruik van Cloud Service Framework {#analyticsusingcloudframework}

AEM Forms integreert met Analytics waarmee u prestatiegegevens voor uw gepubliceerde formulieren en documenten kunt vastleggen en bijhouden. Het doel van de analyse van deze gegevens is om geïnformeerde beslissingen te nemen op basis van gegevens over de wijzigingen die nodig zijn om formulieren of documenten bruikbaarder te maken.

>[!NOTE]
>
>De functie Analytics in AEM Forms is beschikbaar als onderdeel van het invoegpakket voor AEM Forms. Voor informatie over het installeren van het add-on pakket raadpleegt u [AEM Forms installeren en configureren](../../forms/using/installing-configuring-aem-forms-osgi.md).
>
>Naast het invoegpakket hebt u een Adobe Analytics-account en beheerdersrechten voor de AEM nodig. Voor informatie over de oplossing raadpleegt u [Adobe Analytics](https://www.adobe.com/solutions/digital-analytics.html).

U kunt ook analyses uitvoeren met de Adobe Launch. Ga voor meer informatie over hoe u AEM Forms kunt integreren met het starten van de Adobe naar [Analyse met Adobe starten](/help/forms/using/integrate-aem-forms-with-adobe-analytics.md).

## Overzicht {#overview}

U kunt Adobe Analytics gebruiken om interactiepatronen en problemen te detecteren waarmee gebruikers worden geconfronteerd bij het gebruik van adaptieve formulieren, HTML5-formulieren en interactieve communicatie. Uit de doos, volgt de analytische sporen van de Adobe en slaat informatie over de volgende parameters op:

* **Gemiddelde vultijd**: Gemiddelde tijd die u hebt doorgebracht om het formulier in te vullen.
* **Uitvoeringen**: Het aantal keren dat een formulier wordt geopend.
* **Concepten**: Het aantal keren dat een formulier in het concept wordt opgeslagen.
* **Indieningen**: Aantal keer dat een formulier wordt verzonden.
* **Afbreken**: Het aantal keren dat de gebruikers het formulier verlaten zonder het in te vullen.

U kunt Adobe Analytics aanpassen om meer parameters toe te voegen of te verwijderen. Het verslag bevat naast de bovenstaande informatie de volgende informatie over elk panel van de HTML5 en het adaptieve formulier:

* **Tijd**: Tijd die u in het deelvenster en in de velden van het deelvenster hebt doorgebracht.
* **Fout**: Aantal fouten aangetroffen in het deelvenster en in de velden van het deelvenster.
* **Help**: Het aantal keren dat een gebruiker Help van een deelvenster en de velden van het deelvenster opent.

## Rapportsuite maken {#creating-report-suite}

De analysegegevens worden opgeslagen in klant-specifieke bewaarplaatsen genoemd rapportreeksen. Als u een rapportenpakket wilt maken en Adobe Analytics wilt gebruiken, hebt u een geldig Adobe Marketing Cloud-account nodig. Controleer voordat u de volgende stappen uitvoert of u een geldige Adobe Marketing Cloud-account hebt.

Voer de volgende stappen uit om een rapportsuite te maken.

1. Aanmelden bij [https://sc.omniture.com/login/](https://sc.omniture.com/login/)
1. Selecteer in de Marketing Cloud **Beheerder** > **Admin Console** > **Rapportageopties**.
1. Selecteren **Nieuw maken** > **Rapportsuite** in Report Suite Manager.

   ![Nieuwe rapportsuite maken](assets/newreportsuite_new.png)

   Nieuwe rapportsuite maken

1. Controleer of de eerste vervolgkeuzelijst is ingesteld op **Maken van een sjabloon** en selecteer vervolgens **Handel**.
1. Zoek de **ID van rapportsuite** en voeg nieuwe rapportsuite-id toe. JJEsquire. Een rapportsuite-id wordt weergegeven onder het veld Report Suite-id. Het omvat een automatisch voorvoegsel, dat vaak de bedrijfsnaam is.
1. Nieuw toevoegen **Titel site**. JJEsquire Getting Started Suite. Deze titel wordt gebruikt binnen Analytics UI. Gebruik de rapportsuite-id in de code.
1. Selecteer een **Tijdzone** in de vervolgkeuzelijst. Alle gegevens die in deze rapportreeks komen worden geregistreerd gebaseerd op bepaalde tijdzone.
1. Laat de **Basis-URL** en **Standaardpagina** velden zijn leeg. Deze twee waarden worden alleen via de Adobe Marketing Cloud-interface gebruikt om een koppeling naar uw website te maken.
1. Laat de **Live-datum** vandaag. De Go Live Date bepaalt de dag waarop de rapportsuite wordt geactiveerd.
1. In de **Geschat aantal paginaweergaven per dag** veld, type 100. Met dit veld kunt u het aantal pagina&#39;s schatten dat u per dag voor uw website verwacht. Met deze schatting kan de Adobe de juiste hoeveelheid hardware instellen voor de verwerking van de gegevens die u wilt verzamelen.
1. Selecteer een **Basisvaluta** in de vervolgkeuzelijst. Alle valutagegevens die in deze rapportsuite worden ingevoerd, worden geconverteerd en opgeslagen in deze valutanotatie.
1. Klikken **Rapport maken** Suite. De pagina wordt vernieuwd met een bericht dat de rapportsuite is gemaakt.
1. Selecteer de nieuwe rapportsuite. Navigeren naar **Instellingen bewerken** > **Algemeen** > **Algemene accountinstellingen**.

   ![Algemene accountinstellingen](assets/geographic_settings.png)

   Algemene accountinstellingen

1. Schakel in het scherm Algemene accountinstellingen de optie **Geografische rapportage** en klik op **Opslaan.**
1. Navigeren naar **Instellingen bewerken** > **Verkeer** > **verkeersvariabelen**.
1. In de rapportreeks, vorm en laat volgende verkeersvariabelen toe.

   * **formName**: Identifier voor een adaptief formulier.
   * **formInstance**: Identifier van een adaptieve formulierinstantie. Padrapporten inschakelen voor deze variabele.
   * **fieldName**: Identifier van een adaptief formulierveld. Padrapporten inschakelen voor deze variabele.
   * **panelName**: Identifier van een adaptief formulierpaneel. Padrapporten inschakelen voor deze variabele.
   * **formTitle**: Titel van het formulier.
   * **fieldTitle**: Titel van het formulierveld.
   * **panelTitle**: Titel van het formuliervenster.
   * **analyticsVersion**: Versie van formulieranalyse.

1. Navigeren naar **Instellingen bewerken** > **Conversie** > **Gebeurtenissen geslaagd**. Definieer en schakel de volgende succesgebeurtenissen in:

   | Gebeurtenis geslaagd | Type |
   |---|---|
   | opgeven | Teller |
   | renderen | Teller |
   | panelVisit | Teller |
   | fieldVisit | Teller |
   | opslaan | Teller |
   | fout | Teller |
   | help | Teller |
   | indienen | Teller |
   | timeSpent | Numeriek |

   >[!NOTE]
   >
   >Een gebeurtenisnummer en prop-nummer dat wordt gebruikt voor het configureren van AEM Forms-analysemogelijkheden moeten verschillen van het gebeurtenisnummer en het prop-nummer dat in de analyse wordt gebruikt [AEM](/help/sites-administering/adobeanalytics.md) configuratie.

1. Afmelden bij Adobe Marketing Cloud-account.

## Configuratie van Cloud Service maken {#creating-cloud-service-configuration}

Configuratie van Cloud Servicen is informatie over uw Adobe Analytics-account. Met de configuratie kan Adobe Experience Manager (AEM) verbinding maken met Adobe Analytics. Maak een aparte configuratie voor elke analytische account die u gebruikt.

1. Meld u als beheerder aan bij de AEM auteur-instantie.
1. Klik in de linkerbovenhoek op **Adobe Experience Manager** > **Gereedschappen** ![hamerpictogram](/help/forms/using/assets/tools.png) > **Cloud Servicen** > **Oudere Cloud Servicen**.
1. Zoeken **Adobe Analytics** pictogram. Klikken **Configuraties tonen** en ga vervolgens door met klikken **[+]** om nieuwe configuratie toe te voegen.

   Als u een nieuwe gebruiker bent, klikt u op **Nu configureren**.

1. Voeg een Titel toe aan uw nieuwe configuratie (het invullen van het gebied van de Naam is facultatief). Bijvoorbeeld, Mijn analytische configuratie. Klikken **Maken**.

1. Wanneer het deelvenster Bewerken wordt geopend op de configuratiepagina, vult u de velden in:

   * **Bedrijf**: De naam van je bedrijf zoals vermeld op Adobe Analytics.
   * **Gebruikersnaam**: De naam die wordt gebruikt voor aanmelding bij Adobe Analytics.
   * **Wachtwoord**: Het Adobe Analytics-wachtwoord voor de bovenstaande account.
   * **Datacenter**: Het datacenter van uw Adobe Analytics-account.

1. Klikken **Verbinding maken met Analytics**. Er wordt een dialoogvenster weergegeven met het bericht dat de verbinding is gelukt. Klikken **OK**.

## Kader voor Cloud Service maken {#creating-cloud-service-framework}

Een Adobe Analytics-framework is een set toewijzingen tussen Adobe Analytics-variabelen en AEM. Gebruik een framework om te configureren hoe uw formulieren gegevens invullen in Adobe Analytics-rapporten. Frameworks zijn gekoppeld aan een Adobe Analytics-configuratie. U kunt veelvoudige kaders voor elke configuratie tot stand brengen.

1. Klik op de AEM cloudserviceconsole op **Configuraties tonen**, onder Adobe Analytics.
1. Klik op de knop **[+]** naast de configuratie Analytics.

   ![Adobe Analytics-configuratie](assets/adobe-analytics-cloud-services.png)

   Adobe Analytics-configuratie

1. Typ a **Titel** en **Naam** voor het framework kiest u **Adobe Analytics** Framework en klik op **Maken**. Het framework wordt geopend voor bewerking.
1. Klik in de sectie Rapportsets van de zijpod op **Item toevoegen** en selecteert u vervolgens de rapportsuite-id (bijvoorbeeld JJEsquire) waarmee het framework werkt.
1. Naast de ID van de Reeks van het Rapport, selecteer de serverinstanties die u informatie naar de Reeks van het Rapport wilt verzenden.

   ![information_to_send_to_report_suite](assets/information_to_send_to_report_suite.png)

1. Sleep een **Component Formulieranalyse** van de **overige** categorie van Sidekick naar het kader.
1. Als u analytische variabelen wilt toewijzen aan variabelen die in de component zijn gedefinieerd, sleept u een variabele van AEM Content Finder naar een veld in de component tracking.

   ![AEM variabelen toewijzen aan Adobe Analytics-variabelen](assets/analytics_new.png)

1. Activeer het framework met het **tabblad Pagina** Klik in sidekick op **Framework activeren**.

## Configuratieservice voor AEM Forms Analytics configureren {#configuring-aem-forms-analytics-configuration-service}

1. Voor auteurinstantie, open AEM Manager van de Configuratie van de Console van het Web bij `https://<server>:<port>;/system/console/configMgr`.
1. AEM Forms Analytics Configuration zoeken en openen

   ![AEM Forms Analytics Configuration-service](assets/analytics_configuration.png)

   AEM Forms Analytics Configuration-service

1. Geef de juiste waarden op voor de volgende velden en klik op **Opslaan**.

   * **Framework SiteCatalyst**: Selecteer het framework/de configuratie die u in de sectie Set up a framework for tracking hebt gedefinieerd.
   * **Beginwaarde van tekstspatiëring**: Geef de duur in seconden op waarna het veldbezoek moet worden bijgehouden. De standaardwaarde is 0. Wanneer de waarde groter is dan 0 (nul), worden twee afzonderlijke volggebeurtenissen verzonden naar de Adobe Analytics-server. De eerste gebeurtenis geeft de analyseserver de opdracht het verlaten veld niet meer te volgen. De tweede gebeurtenis wordt verzonden nadat de opgegeven tijdsduur is verstreken. De tweede gebeurtenis geeft de analyseserver de opdracht het bezochte veld te volgen. Het gebruik van twee afzonderlijke gebeurtenissen helpt de tijd die aan een veld wordt doorgebracht nauwkeurig te meten. Wanneer de waarde 0 (nul) is, wordt een enkele volggebeurtenis verzonden naar de Adobe Analytics-server.

   * **Overzicht van synchronisatie van analyserapporten**: Geef de expressie voor uitsnijden op voor het ophalen van rapporten uit Adobe Analytics. De standaardwaarde is 0 0 2? &#42; &#42;.

   * **Time-out testrapport:** Geef de tijdsduur in seconden op, waarna de server moet reageren op het analyserapport. De standaardtijd is 120 seconden.

   >[!NOTE]
   >
   >Het kan tot 10 seconden meer aan onderbrekingsrapport nemen haal verrichting toen het gespecificeerde aantal seconden.

1. Herhaal stap 1-3 op publicatieinstantie om analyses te configureren.

Nu kunt u analyses inschakelen voor formulieren en een analyserapport genereren.

## Analyses inschakelen voor een formulier of document {#enabling-analytics-for-a-form-or-document}

1. Aanmelden bij AEM portal `https://[hostname]:'port'`.
1. Klikken **Forms > Forms &amp; Documents** selecteert u een formulier of document en klikt u op **Analyse inschakelen**. De analysemogelijkheden zijn ingeschakeld.

   ![Analyses inschakelen voor een formulier of document](assets/enable-analytics-1.png)

   Analyses inschakelen voor een formulier

   **A.** Knop Analyse inschakelen **B.** Geselecteerd formulier

   Voor gedetailleerde informatie over het weergeven van rapporten over formulieranalyses raadpleegt u [AEM Forms-analyserapporten weergeven en begrijpen](../../forms/using/view-understand-aem-forms-analytics-reports.md).
