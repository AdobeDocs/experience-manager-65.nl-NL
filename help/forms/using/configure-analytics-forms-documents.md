---
title: Analyses en rapporten configureren
seo-title: Analyses en rapporten configureren
description: Leer hoe u Adobe Analytics configureert om interactiepatronen en problemen te detecteren waarmee gebruikers worden geconfronteerd bij het gebruik van adaptieve formulieren, adaptieve documenten en HTML5-formulieren.
seo-description: Leer hoe u Adobe Analytics configureert om interactiepatronen en problemen te detecteren waarmee gebruikers worden geconfronteerd bij het gebruik van adaptieve formulieren, adaptieve documenten en HTML5-formulieren.
uuid: ac5d1300-f303-40e8-a33e-4859a54ac10d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
discoiquuid: 96a77980-4213-4779-a540-00905ea8f7e3
docset: aem65
translation-type: tm+mt
source-git-commit: 5aa2fe48578633cbe5e4324f9e956e1dbbdab8af
workflow-type: tm+mt
source-wordcount: '1533'
ht-degree: 0%

---


# Analyses en rapporten configureren{#configuring-analytics-and-reports}

AEM Forms is geïntegreerd met Adobe Analytics waarmee u prestatiegegevens voor gepubliceerde formulieren en documenten kunt vastleggen en bijhouden. Het doel van de analyse van deze gegevens is om geïnformeerde beslissingen te nemen op basis van gegevens over de wijzigingen die nodig zijn om formulieren of documenten bruikbaarder te maken.

>[!NOTE]
>
>De functie Analytics in AEM Forms is beschikbaar als onderdeel van het invoegpakket voor AEM Forms. Zie [AEM Forms installeren en configureren](../../forms/using/installing-configuring-aem-forms-osgi.md) voor informatie over het installeren van het invoegpakket.
>
>Naast het invoegpakket hebt u een Adobe Analytics-account en beheerdersrechten voor de AEM nodig. Zie [Adobe Analytics](https://www.adobe.com/solutions/digital-analytics.html) voor informatie over de oplossing.

## Overzicht {#overview}

U kunt Adobe Analytics gebruiken om interactiepatronen en problemen te detecteren waarmee gebruikers worden geconfronteerd bij het gebruik van adaptieve formulieren, HTML5-formulieren en interactieve communicatie. Uit de doos, volgt de analysemogelijkheden van Adobe en slaat informatie over de volgende parameters op:

* **Gemiddelde vultijd**: Gemiddelde tijd die u hebt doorgebracht om het formulier in te vullen.
* **Uitvoeringen**: Aantal keren dat een formulier wordt geopend.
* **Concepten**: Het aantal keren dat een formulier in de conceptstatus wordt opgeslagen.
* **Indieningen**: Aantal keer dat een formulier wordt verzonden.
* **Afbreken**: Aantal keren dat de gebruikers het formulier verlaten zonder het in te vullen.

U kunt Adobe Analytics aanpassen om meer parameters toe te voegen of te verwijderen. Naast de bovenstaande informatie bevat het rapport de volgende informatie over elk deelvenster van het HTML5- en adaptieve formulier:

* **Tijd**: De tijd die u aan het deelvenster en de velden van het deelvenster hebt doorgebracht.
* **Fout**: Aantal fouten aangetroffen in het deelvenster en in de velden van het deelvenster.
* **Help**: Het aantal keren dat een gebruiker de Help van een deelvenster en de velden van het deelvenster opent.

## Rapportsuite {#creating-report-suite} maken

De analysegegevens worden opgeslagen in klant-specifieke bewaarplaatsen genoemd rapportreeksen. Als u een rapportenpakket wilt maken en Adobe Analytics wilt gebruiken, hebt u een geldig Adobe Marketing Cloud-account nodig. Controleer voordat u de volgende stappen uitvoert of u een geldige Adobe Marketing Cloud-account hebt.

Voer de volgende stappen uit om een rapportsuite te maken.

1. Aanmelden bij [https://sc.omniture.com/login/](https://sc.omniture.com/login/)
1. Selecteer **Admin** > **Admin Console** > **Rapporten** in de Marketing Cloud.
1. Selecteer **Nieuw maken** > **Reeks rapporteren** in RapportSuite Manager.

   ![Nieuwe rapportsuite maken](assets/newreportsuite_new.png)

   Nieuwe rapportsuite maken

1. Zorg ervoor dat de eerste vervolgkeuzelijst is ingesteld op **Maken via een sjabloon** en selecteer **Handel**.
1. Zoek het veld **Suite-id rapporteren** en voeg een nieuwe rapportsuite-id toe. Bijvoorbeeld JJEsquire. Een rapportsuite-id wordt weergegeven onder het veld ID van rapportsuite. Het omvat een automatisch voorvoegsel, dat vaak de bedrijfsnaam is.
1. Nieuwe **Titel van site** toevoegen. JJEsquire Getting Started Suite. Deze titel wordt gebruikt binnen Analytics UI. Gebruik de rapportsuite-id in de code.
1. Selecteer een **Tijdzone** van dropdown. Alle gegevens die in deze rapportreeks komen worden geregistreerd gebaseerd op bepaalde tijdzone.
1. Laat de velden **Basis-URL** en **Standaardpagina** leeg. Deze twee waarden worden alleen via de Adobe Marketing Cloud-interface gebruikt om een koppeling naar uw website te maken.
1. Laat **Go Live Date** op vandaag ingesteld. De Go Live Date bepaalt de dag waarop de rapportsuite wordt geactiveerd.
1. Typ 100 in het veld **Geschatte paginaweergaven per dag**. Met dit veld kunt u het aantal pagina&#39;s schatten dat u per dag voor uw website verwacht. Deze schatting stelt Adobe in staat de juiste hoeveelheid hardware in te stellen om de gegevens te verwerken die u wilt verzamelen.
1. Selecteer een **Basisvaluta** in het vervolgkeuzemenu. Alle valutagegevens die in deze rapportsuite worden ingevoerd, worden geconverteerd en opgeslagen in deze valutaopmaak.
1. Klik **Rapport maken** Suite. De pagina wordt vernieuwd met een bericht dat de rapportsuite is gemaakt.
1. Selecteer de nieuwe rapportsuite. Navigeer naar **Instellingen bewerken** > **Algemeen** > **Algemene accountinstellingen**.

   ![Algemene accountinstellingen](assets/geographic_settings.png)

   Algemene accountinstellingen

1. Schakel in het scherm Algemene accountinstellingen de optie **Geography Reporting** in en klik op **Opslaan.**
1. Navigeer naar **Instellingen bewerken** > **Verkeer** > **Verkeersvariabelen**.
1. In de rapportreeks, vorm en laat volgende verkeersvariabelen toe.

   * **formName**: Identificatiecode voor een adaptief formulier.
   * **formInstance**: Identifier van een adaptief formulierexemplaar. Padrapporten inschakelen voor deze variabele.
   * **fieldName**: Identifier van een adaptief formulierveld. Padrapporten inschakelen voor deze variabele.
   * **panelName**: Identifier van een adaptief formulierpaneel. Padrapporten inschakelen voor deze variabele.
   * **formTitle**: Titel van het formulier.
   * **fieldTitle**: Titel van het formulierveld.
   * **panelTitle**: Titel van het formuliervenster.
   * **analyticsVersion**: Versie van formulieranalyse.

1. Navigeer naar **Instellingen bewerken** > **Conversie** > **Gebeurtenissen met succes**. Definieer en schakel de volgende succesgebeurtenissen in:

   | Gebeurtenis geslaagd | Type |
   |---|---|
   | opgeven | Teller |
   | renderen | Teller |
   | panelVisit | Teller |
   | fieldVisit | Teller |
   | save | Teller |
   | error | Teller |
   | help | Teller |
   | submit | Teller |
   | timeSpent | Numeriek |

   >[!NOTE]
   >
   >Een gebeurtenisnummer en prop-nummer waarmee AEM Forms-analysemogelijkheden worden geconfigureerd, moeten verschillen van het gebeurtenisnummer en het prop-nummer dat in de configuratie [AEM analytics](/help/sites-administering/adobeanalytics.md) wordt gebruikt.

1. Afmelden bij Adobe Marketing Cloud-account.

## Configuratie van Cloud Service {#creating-cloud-service-configuration} maken

Configuratie van Cloud Servicen is informatie over uw Adobe Analytics-account. Met de configuratie kan Adobe Experience Manager (AEM) verbinding maken met Adobe Analytics. Maak een aparte configuratie voor elke analytische account die u gebruikt.

1. Meld u als beheerder aan bij de AEM auteur-instantie.
1. Klik in de linkerbovenhoek op **Adobe Experience Manager** > **Gereedschappen** ![](/help/forms/using/assets/tools.png) > **Cloud Services** > **Oudere Cloud Services**.
1. Zoek **Adobe Analytics**-pictogram. Klik **Configuraties tonen** en ga dan te werk om **[+]** te klikken om nieuwe configuratie toe te voegen.

   Als u een eerste gebruiker bent, klik **vorm nu**.

1. Voeg een Titel toe aan uw nieuwe configuratie (het invullen van het gebied van de Naam is facultatief). Bijvoorbeeld, Mijn analytische configuratie. Klik **Maken**.

1. Wanneer het deelvenster Bewerken wordt geopend op de configuratiepagina, vult u de velden in:

   * **Bedrijf**: De naam van je bedrijf zoals vermeld op Adobe Analytics.
   * **Gebruikersnaam**: De naam die wordt gebruikt om u aan te melden bij Adobe Analytics.
   * **Wachtwoord**: Het Adobe Analytics-wachtwoord voor de bovenstaande account.
   * **Datacenter**: Het datacenter van uw Adobe Analytics-account.

1. Klik **Verbinding maken met Analytics**. Er wordt een dialoogvenster weergegeven met het bericht dat de verbinding is gelukt. Klik **OK**.

## Kader {#creating-cloud-service-framework} voor Cloud Servicen maken

Een Adobe Analytics-framework is een set toewijzingen tussen Adobe Analytics-variabelen en AEM. Gebruik een framework om te configureren hoe uw formulieren gegevens invullen in Adobe Analytics-rapporten. Frameworks zijn gekoppeld aan een Adobe Analytics-configuratie. U kunt veelvoudige kaders voor elke configuratie tot stand brengen.

1. Klik op **Configuraties tonen** onder Adobe Analytics op de AEM-console voor cloudservices.
1. Klik op de koppeling **[+]** naast de configuratie Analytics.

   ![Adobe Analytics-configuratie](assets/adobe-analytics-cloud-services.png)

   Adobe Analytics-configuratie

1. Typ een **Title** en **Name** voor het framework, selecteer **Adobe Analytics** Framework en klik op **Create**. Het framework wordt geopend voor bewerking.
1. In de sectie van de Reeksen van het Rapport van de zijpeul, klik **voeg Punt** toe, dan gebruik drop-down om identiteitskaart van de Reeks van het Rapport (bijvoorbeeld, JJEsquire) te selecteren waarmee het kader zal interactie aangaan.
1. Naast de ID van de Reeks van het Rapport, selecteer de serverinstanties die u informatie naar de Reeks van het Rapport wilt verzenden.

   ![information_to_send_to_report_suite](assets/information_to_send_to_report_suite.png)

1. Sleep een **component Formulieranalyse** van de categorie **other** van SideKick naar het framework.
1. Als u analytische variabelen wilt toewijzen aan variabelen die in de component zijn gedefinieerd, sleept u een variabele van AEM Content Finder naar een veld in de component tracking.

   ![AEM variabelen toewijzen aan Adobe Analytics-variabelen](assets/analytics_new.png)

1. Activeer het framework met de **pagina tab** in sidekick en klik op **Framework activeren**.

## Configuratieservice voor AEM Forms Analytics {#configuring-aem-forms-analytics-configuration-service} configureren

1. Voor auteursinstantie, open AEM Manager van de Configuratie van de Console van het Web bij `https://<server>:<port>;/system/console/configMgr`.
1. AEM Forms Analytics Configuration zoeken en openen

   ![AEM Forms Analytics Configuration-service](assets/analytics_configuration.png)

   AEM Forms Analytics Configuration-service

1. Geef de juiste waarden op voor de volgende velden en klik op **Opslaan**.

   * **SiteCatalyst-kader**: Selecteer het framework/de configuratie die u in de sectie Set up a framework for tracking hebt gedefinieerd.
   * **Basislijn** voor bijhouden van veldtijd: Geef de duur in seconden op waarna het veldbezoek moet worden bijgehouden. De standaardwaarde is 0. Wanneer de waarde groter is dan 0 (nul), worden twee afzonderlijke volggebeurtenissen verzonden naar de Adobe Analytics-server. De eerste gebeurtenis geeft de analyseserver de opdracht het verlaten veld niet meer te volgen. De tweede gebeurtenis wordt verzonden nadat de opgegeven tijdsduur is verstreken. De tweede gebeurtenis geeft de analyseserver de opdracht het bezochte veld te volgen. Het gebruik van twee afzonderlijke gebeurtenissen helpt de tijd die aan een veld wordt doorgebracht nauwkeurig te meten. Wanneer de waarde 0 (nul) is, wordt een enkele volggebeurtenis verzonden naar de Adobe Analytics-server.

   * **Overzicht van synchronisatie van analyserapporten**: Uitsnijdexpressie opgeven voor het ophalen van rapporten uit Adobe Analytics. De standaardwaarde is 0 0 2? * * *.

   * **Time-out testrapport:** geef de tijdsduur in seconden op die de server moet wachten om te reageren op het analyserapport. De standaardtijd is 120 seconden.
   >[!NOTE]
   >
   >Het kan tot 10 seconden meer aan onderbrekingsrapport nemen haal verrichting toen het gespecificeerde aantal seconden.

1. Herhaal stap 1-3 op publicatieinstantie om analyses te configureren.

Nu kunt u analyses inschakelen voor formulieren en een analyserapport genereren.

## Analyses inschakelen voor een formulier of document {#enabling-analytics-for-a-form-or-document}

1. Meld u aan bij AEM portal op `https://[hostname]:'port'`.
1. Klik op **Forms > Forms &amp; Documents**, selecteer een formulier of document en klik op **Analyse inschakelen**. De analysemogelijkheden zijn ingeschakeld.

   ![Analyses inschakelen voor een formulier of document](assets/enable-analytics-1.png)

   Analyses inschakelen voor een formulier

   **A.** Knop Analyse inschakelen  **B.** Geselecteerd formulier

   Zie [AEM Forms-analyserapporten weergeven en begrijpen](../../forms/using/view-understand-aem-forms-analytics-reports.md) voor gedetailleerde informatie over het weergeven van formulieranalyserapporten.

