---
title: AEM Forms-analyserapporten weergeven en begrijpen
description: AEM Forms integreert met Adobe Analytics en biedt u een overzicht en gedetailleerde analyses van uw gepubliceerde adaptieve formulieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
docset: aem65
exl-id: c5a4e6f6-f331-41e9-a0a9-51a30df6e2cd
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---

# AEM Forms-analyserapporten weergeven en begrijpen {#view-and-understand-aem-forms-analytics-reports}

Adobe Experience Manager Forms is geïntegreerd met Adobe Analytics waarmee u prestatiegegevens voor gepubliceerde formulieren en documenten kunt vastleggen en bijhouden. Het doel van de analyse van deze gegevens is om geïnformeerde beslissingen te nemen op basis van gegevens over de wijzigingen die nodig zijn om formulieren of documenten bruikbaarder te maken.

## Analyses instellen {#setting-up-analytics}

De functie Analytics in AEM Forms is beschikbaar als onderdeel van het invoegpakket voor AEM Forms. Voor informatie over het installeren van het add-on pakket raadpleegt u [AEM Forms installeren en configureren](../../forms/using/installing-configuring-aem-forms-osgi.md).

Naast het invoegpakket hebt u een Adobe Analytics-account nodig. Voor informatie over de oplossing raadpleegt u [Adobe Analytics](https://www.adobe.com/solutions/digital-analytics.html).

Als u het AEM Forms-add-onpakket en een Adobe Analytics-account hebt, integreert u Adobe Analytics-account met AEM Forms en schakelt u het bijhouden van gegevens in uw formulieren of documenten in zoals beschreven in [Analyses en rapporten configureren](../../forms/using/configure-analytics-forms-documents.md).

### Hoe gebruikersinteractiegegevens worden vastgelegd {#how-user-interaction-information-is-recorded}

Wanneer een gebruiker met het formulier werkt, worden de interacties opgenomen en naar de Analyseserver verzonden. De volgende lijst wijst op servervraag voor diverse gebruikersactiviteiten:

* 2 gesprekken per veld per bezoek
* 1 voor een bezoek aan een panel
* 1 voor opslaan
* 2 voor verzending
* 2 voor opslaan
* 1 voor hulp
* 1 voor elke validatiefout
* 1 voor Formulieruitvoering + 1 voor standaardvenster: bezoek + 1 voor standaardbezoek aan het eerste veld
* 2 voor Formulier verlaten

>[!NOTE]
>
>Deze lijst is niet limitatief.

### Analyserapporten weergeven {#summary-report}

Voer de volgende stappen uit om analyserapporten weer te geven:

1. Meld u aan bij het portaal AEM op `https://[hostname]:'port'`
1. Klikken **Forms > Forms &amp; Documents**.
1. Selecteer het formulier waarvoor u de analyserapporten wilt weergeven.
1. Selecteren **Meer > Analyserapporten**.

![analyserapport](assets/analyticsreport.png)

**A.** Analyserapport, opdracht

AEM Forms geeft analyserapporten voor het formulier en voor elk deelvenster in het formulier weer, zoals hieronder wordt weergegeven.

![Samenvattend verslag van een adaptief formulier](assets/analyticsdashboard_callout.png)

**A.** Conversies **B.** Overzicht op formulierniveau **C.** Overzicht op paneelniveau **D.** Browsers van bezoekers - filter **E.** Besturingssysteem van bezoekers - filter **F.** Taal van bezoekers - filter

Standaard wordt het analyserapport voor de laatste zeven dagen weergegeven. U kunt rapporten weergeven voor de laatste 15 dagen, de laatste één maand enzovoort, of u kunt een datumbereik opgeven.

>[!NOTE]
>
>De opties zoals Laatste 7 dagen en Laatste 15 dagen bevatten geen gegevens voor de dag waarop u het analyserapport genereert. Om de gegevens van de huidige dag te omvatten, moet u de datumwaaier met inbegrip van de huidige dag specificeren en dan het rapport in werking stellen.

![date-range](assets/date-range.png)

### Omzettingen grafiek voor adaptieve en HTML5 vormen {#conversions-graph-for-adaptive-and-html-forms}

De omzettingsgrafiek op formulierniveau geeft u inzicht in hoe het formulier de volgende prestatiekernindicatoren (KPI&#39;s) uitvoert:

* **Uitvoeringen**: Het aantal keren dat een formulier wordt geopend
* **Bezoekers**: Het aantal bezoekers van het formulier
* **Indieningen**: Aantal keer dat het formulier wordt ingediend

![conversiegrafiek](assets/conversion-graph.png)

### Analyserapport voor adaptieve en HTML5-formulieren {#analytics-report-for-adaptive-and-html-forms}

In de overzichtssectie op formulierniveau kunt u zien hoe het formulier de volgende prestatiekernindicatoren (KPI&#39;s) uitvoert:

* **Gemiddelde vultijd**: Gemiddelde tijd die is besteed aan het invullen van het formulier. Wanneer gebruikers tijd aan het formulier besteden maar niet verzenden, wordt die tijd niet in deze berekening opgenomen.
* **Uitvoeringen**: Aantal keer dat het formulier is gegenereerd of geopend
* **Concepten**: Aantal keer dat het formulier is opgeslagen als concept
* **Indieningen**: Aantal keer dat het formulier is ingediend
* **Afbreken**: Het aantal keren dat gebruikers het formulier hebben ingevuld en vervolgens het formulier hebben verlaten zonder het formulier in te vullen
* **Unieke bezoekers**: Het aantal keren dat het formulier wordt weergegeven door unieke bezoekers. Voor meer informatie over unieke bezoekers raadpleegt u [Unieke bezoekers, bezoeken en klantengedrag](https://helpx.adobe.com/analytics/kb/unique-visitors-visitor-behavior.html).

![Samenvattingsanalyserapport op formulierniveau](assets/analytics-report.png)

### Deelvensterrapport {#bottom-summary-report}

In het overzichtsgedeelte op paneelniveau vindt u de volgende informatie over elk deelvenster in het formulier:

* **Gemiddelde vultijd**: Gemiddelde tijd die het panel heeft doorgebracht, ongeacht of het formulier is ingediend
* **Fouten aangetroffen**: Gemiddeld aantal fouten dat de gebruikers hebben aangetroffen in de velden in een deelvenster. Fouten die worden aangetroffen, worden gevonden door het totale aantal fouten in een veld te delen door het aantal uitvoeringen van het formulier.
* **Help geopend**: Gemiddeld aantal keren dat gebruikers de Help in de context hebben geopend voor de velden in het deelvenster. De hulp Toegelaten wordt bereikt door het totale aantal tijden te delen de Hulp voor een gebied door aantal vertoningen van vorm wordt betreden.

#### Gedetailleerd deelvensterrapport {#detailed-panel-report}

U kunt ook details voor elk deelvenster weergeven door in het deelvensterrapport op de naam van een deelvenster te klikken.

![Gedetailleerd deelvensterrapport](assets/panel-report-detailed.png)

Het gedetailleerde rapport bevat waarden voor alle velden in het deelvenster.

Het paneelrapport heeft drie lusjes:

* **Tijdrapport**(Standaard): geeft de tijd in aantal seconden weer die is besteed aan het invullen van elk veld in het deelvenster
* **Foutrapport**: Hiermee geeft u het aantal fouten weer dat gebruikers hebben aangetroffen bij het invullen van de velden
* **Help-rapport**: Aantal keren dat de Help voor een bepaald veld is geopend

U kunt tussen de deelvensters navigeren als er meerdere deelvensters beschikbaar zijn.

### Filters: browser, besturingssysteem en taal {#filters-browser-os-and-language}

In de tabellen Browserdistributie, OS Distribution en Taaldistributie worden de uitvoeringen, bezoekers en verzendingen weergegeven volgens browsers, OS en Taal van formuliergebruikers. In deze tabellen worden standaard maximaal vijf items weergegeven. U kunt op Meer tonen klikken om meer items weer te geven en op Minder tonen klikken om terug te keren naar de normale vijf of minder items.

Als u de analysegegevens verder wilt filteren, klikt u op een item in een van de tabellen. Als u bijvoorbeeld op Google Chrome klikt in de tabel Browserdistributie, wordt het rapport opnieuw weergegeven met gegevens die betrekking hebben op de Google Chrome-browser, zoals hieronder:

![Filter toegepast op Analyserapport - Google Chrome ](assets/filter-1.png)

Als u het paneelrapport na het toepassen van een filter bekijkt, worden de gegevens van het paneelrapport ook getoond volgens de toegepaste filter.

Nadat een filter is toegepast:

* De distributietabellen worden read-only, aangezien slechts één filter tegelijk kan worden toegepast.
* De tabel van het toegepaste filter verdwijnt.
* U kunt op de knop Sluiten (hieronder gemarkeerd) klikken om het toegepaste filter te verwijderen.

![Knop Sluiten om het toegepaste filter te verwijderen](assets/close-filter.png)

### A/B-tests {#a-b-testing}

Als u A/B tests hebt toegelaten en opstelling voor de vorm, heeft de rapportpagina een drop-down u kunt gebruiken om het A/B testende rapport te tonen. In het testrapport A/B worden de prestaties van twee versies van het formulier vergeleken terwijl u het instelt.

Zie voor meer informatie over A/B testen [A/B-test voor adaptieve formulieren maken en beheren](../../forms/using/ab-testing-adaptive-forms.md).
