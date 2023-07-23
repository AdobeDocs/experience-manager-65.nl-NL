---
title: Inleiding tot een formulierreeks die uit meerdere stappen bestaat
seo-title: Introduction to multi-step form sequence
description: Met AEM Forms kunt u een reeks formulierdeelvensters definiëren waarin gebruikers door een adaptief formulier moeten navigeren en dit moeten invullen.
seo-description: With AEM Forms, you can define a sequence of form panel in which you want users to navigate and fill an adaptive form.
uuid: db1aac25-fe69-4e43-88d1-4a15389b507f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 0f335ea0-504f-4cc0-b97b-c3fc715bcc2e
docset: aem65
feature: Adaptive Forms
exl-id: 1333c6cb-15cc-429b-a13e-5d23afdee69a
source-git-commit: e7a3558ae04cd6816ed73589c67b0297f05adce2
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# Inleiding tot een formulierreeks die uit meerdere stappen bestaat{#introduction-to-multi-step-form-sequence}

<span class="preview"> Adobe raadt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-layout-of-an-adaptive-form/introduction-form-sequence.html) |
| AEM 6,5 | Dit artikel |


Met adaptieve formulieren kunnen auteurs van formulieren in meerdere stappen gegevens vastleggen in alle eenvoud. De klasse wordt geleverd met ingebouwde ondersteuning voor het maken van meerdere deelvensters en het koppelen van elk deelvenster aan verschillende navigatiepatronen. Auteurs van formulieren kunnen formuliervelden groeperen in logische secties en een groep weergeven als deelvenster. De algemene navigatie tussen deelvensters wordt bepaald door de indeling van het deelvenster. Auteurs kunnen ervoor kiezen om deelvensters in verschillende lay-outs te rangschikken, bijvoorbeeld door de wizard-lay-out opeenvolgend te gebruiken of op een ad-hocmanier met de lay-out Tabbed. Voor informatie over paneellay-outs raadpleegt u [Indelingsmogelijkheden van adaptieve formulieren](../../forms/using/layout-capabilities-adaptive-forms.md).

In een typisch voorbeeld van het invullen van formulieren zijn er meer stappen nodig dan alleen het vastleggen van gegevens. Een volledig formulier dat wordt verzonden, kan andere stappen bevatten, zoals het digitaal ondertekenen van het formulier, het controleren van de informatie die is ingevuld in het formulier, het verwerken van betalingen, enzovoort. Het verschilt van geval tot geval.

Als uw gebruikscase een reeks stappen voor het vastleggen van gegevens verplicht stelt of als er regels zijn die bepaalde stappen moeten volgen, biedt AEM Forms een manier om die gemeenschappelijke structuur in alle formulieren af te dwingen. De vooraf ingestelde implementatie van de formulierstructuur definieert de reeks stappen voor een formulier. ![Voorbeeld van een formulierreeks die uit meerdere stappen bestaat](assets/formpipeline.png)

Voorbeeld van een formulierreeks die uit meerdere stappen bestaat

We gebruiken een voorbeeld waarbij u een reeks moet maken voor het invullen, verifiëren, ondertekenen en bevestigen van een formulier. U kunt een dergelijke reeks als volgt maken:

1. Definieer een formuliersjabloon en voeg het vereiste deelvenster toe. Let op: er moet één deelvenster zijn voor elke stap in de reeks. U kunt echter wel subdeelvensters in een deelvenster opnemen.

   In dit voorbeeld kunt u de volgende deelvensters toevoegen:

   * **Vullen**: Het bevat formuliervelden voor het vastleggen van gegevens. Hier kunt u geneste subdeelvensters opnemen om secties te maken voor verschillende soorten informatie, zoals persoonlijke gegevens, familiegegevens, financiële gegevens enzovoort.

   * **Verifiëren**: Het bevat de **Verifiëren** component die kan worden gebruikt in een op XFA gebaseerde adaptieve vorm. De gegevens die in het deelvenster Vulling zijn vastgelegd, worden in de modus Alleen-lezen weergegeven, zodat ze kunnen worden geverifieerd.

   * **E-sign**: Het bevat de **Ondertekenen** component die kan worden gebruikt in een op XFA gebaseerde adaptieve vorm. het biedt de volgende ondertekeningsservices:

      * Adobe Document Cloud eSign-services
      * Krabbelhandtekening

   * **Bevestiging**: Het bevat de **Samenvatting** een bericht wordt weergegeven waarin de verzending van het formulier wordt bevestigd nadat een gebruiker het formulier heeft ondertekend en de stap Bevestigen (overzicht) in de reeks heeft bereikt. De auteurs kunnen de tekst van de Summiere component vormen, een dank u bericht tonen, een verbinding aan de geproduceerde PDF tonen, etc.

1. De lay-out van het hoofddeelvenster selecteren als **[!UICONTROL Wizard]**.
1. Voer de overige stappen uit om de formuliersjabloon te maken. Zie voor meer informatie [Een aangepaste aangepaste formuliersjabloon maken](../../forms/using/custom-adaptive-forms-templates.md).

Nadat u de formuliervolgorde in de formuliersjabloon hebt gedefinieerd, kunt u er formulieren mee maken die de basisstructuur hebben gedefinieerd als de ingestelde reeks. U kunt het formulier echter altijd aan uw wensen aanpassen.
