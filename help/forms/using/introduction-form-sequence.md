---
title: Inleiding tot een formulierreeks die uit meerdere stappen bestaat
seo-title: Inleiding tot een formulierreeks die uit meerdere stappen bestaat
description: Met AEM Forms kunt u een reeks formulierdeelvensters definiëren waarin gebruikers door een adaptief formulier moeten navigeren en dit moeten invullen.
seo-description: Met AEM Forms kunt u een reeks formulierdeelvensters definiëren waarin gebruikers door een adaptief formulier moeten navigeren en dit moeten invullen.
uuid: db1aac25-fe69-4e43-88d1-4a15389b507f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 0f335ea0-504f-4cc0-b97b-c3fc715bcc2e
docset: aem65
translation-type: tm+mt
source-git-commit: 68ea2335a8466c3c23b766efb1a04b6a38d7f670
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---


# Inleiding tot een formulierreeks die uit meerdere stappen bestaat{#introduction-to-multi-step-form-sequence}

Met adaptieve formulieren kunnen auteurs van formulieren in meerdere stappen gegevens vastleggen in alle eenvoud. De klasse wordt geleverd met ingebouwde ondersteuning voor het maken van meerdere deelvensters en het koppelen van elk deelvenster aan verschillende navigatiepatronen. Auteurs van formulieren kunnen formuliervelden groeperen in logische secties en een groep weergeven als deelvenster. De algemene navigatie tussen deelvensters wordt bepaald door de indeling van het deelvenster. Auteurs kunnen ervoor kiezen om deelvensters in verschillende lay-outs te rangschikken, bijvoorbeeld door de wizard-lay-out opeenvolgend te gebruiken of op een ad-hocmanier met de lay-out Tabbed. Zie [Lay-outmogelijkheden van adaptieve formulieren](../../forms/using/layout-capabilities-adaptive-forms.md)voor informatie over deelvensterlay-outs.

In een typisch voorbeeld van het invullen van formulieren zijn er meer stappen nodig dan alleen het vastleggen van gegevens. Een volledig formulier dat wordt verzonden, kan andere stappen bevatten, zoals het digitaal ondertekenen van het formulier, het controleren van de informatie die is ingevuld in het formulier, het verwerken van betalingen, enzovoort. Het verschilt van geval tot geval.

Als uw gebruiksgeval een reeks stappen voor gegevens vastlegt of er verordeningen zijn die bepaalde te volgen stappen vereisen, verstrekt de Vormen van AEM een manier om die gemeenschappelijke structuur tussen vormen af te dwingen. De vooraf ingestelde implementatie van de formulierstructuur definieert de reeks stappen voor een formulier. ![Voorbeeld van een formulierreeks die uit meerdere stappen bestaat](assets/formpipeline.png)

Voorbeeld van een formulierreeks die uit meerdere stappen bestaat

We gebruiken een voorbeeld waarbij u een reeks moet maken voor het invullen, verifiëren, ondertekenen en bevestigen van een formulier. U kunt een dergelijke reeks als volgt maken:

1. Definieer een formuliersjabloon en voeg het vereiste deelvenster toe. Let op: er moet één deelvenster zijn voor elke stap in de reeks. U kunt echter wel subdeelvensters in een deelvenster opnemen.

   In dit voorbeeld kunt u de volgende deelvensters toevoegen:

   * **Vulling**: Het bevat formuliervelden voor het vastleggen van gegevens. Hier kunt u geneste subdeelvensters opnemen om secties te maken voor verschillende soorten informatie, zoals persoonlijke gegevens, familiegegevens, financiële gegevens enzovoort.

   * **Controleren**: Het bevat de component **Verify** die in een op XFA-Gebaseerde adaptieve vorm kan worden gebruikt. De gegevens die in het deelvenster Vulling zijn vastgelegd, worden in de modus Alleen-lezen weergegeven, zodat ze kunnen worden geverifieerd.

   * **E-handtekening**: Het bevat de **component Sign** die kan worden gebruikt in een op XFA gebaseerde adaptieve vorm. het biedt de volgende ondertekeningsservices:

      * Adobe Document Cloud eSign-services
      * Krabbelhandtekening
   * **Bevestiging**: Het bevat de component **Samenvatting** die een bericht weergeeft ter bevestiging van het verzenden van het formulier nadat een gebruiker het formulier heeft ondertekend en de stap Bevestigen (Samenvatting) in de reeks heeft bereikt. Auteurs kunnen de tekst van de component Summary configureren, een bedankbericht weergeven, een koppeling naar de gegenereerde PDF weergeven, enzovoort.


1. Selecteer de layout van het hoofddeelvenster als **[!UICONTROL Wizard]**.
1. Voer de overige stappen uit om de formuliersjabloon te maken. Zie Een aangepaste formuliersjabloon [](../../forms/using/custom-adaptive-forms-templates.md)maken voor meer informatie.

Nadat u de formuliervolgorde in de formuliersjabloon hebt gedefinieerd, kunt u er formulieren mee maken die de basisstructuur hebben gedefinieerd als de ingestelde reeks. U kunt het formulier echter altijd aan uw wensen aanpassen.

