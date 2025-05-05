---
title: Verzendrevisoren koppelen aan een formulier
description: Leer hoe u revisoren voor verzending kunt koppelen aan een formulier in AEM Forms. Gekoppelde revisoren reviseren een formulier dat via de portal Formulieren is verzonden.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 46e7b858-44d1-41c8-9f44-4e959e593dc1
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Verzendrevisoren koppelen aan een formulier {#associating-submission-reviewers-with-a-form}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

Wanneer u een formulier maakt, kunt u gebruikers die de verzendingen van het formulier bekijken, via de portal Formulieren opgeven en feedback geven. Uw organisatie kan feedback verzamelen en de ingediende formulieren opnieuw bewerken.

Met AEM Forms kunt u een revisorgroep aan een formulier koppelen. Gebruikers die aan een revisiegroep van een formulier zijn toegevoegd, zien de verzendingen van dit formulier en geven feedback.

Revisieersgroepen die aan een formulier zijn toegewezen, kunnen alleen de verzendingen van het opgegeven formulier bekijken.

## Vereiste {#prerequisite}

### De eigenschap Groepen van de revisor voor verzending inschakelen voor adaptieve formulieren met de editor voor het metagegevensschema {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Als u een revisorgroep aan een formulier wilt koppelen, bewerkt u het metagegevensschema van adaptieve formulieren. Standaard kunt u geen revisorgroep toevoegen aan een verzonden formulier.

Het schema voor metagegevens bewerken:

1. Op de auteurswijze, onder Experience Manager, klik **Hulpmiddelen** > **Assets** > **Schema&#39;s van Meta-gegevens**.
1. In de pagina van Forms van het Schema, navigeer aan **Forms** > **Forms die in AEM wordt geschreven.**

   De URL van de pagina is:

   ```html
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/forms/aem-authored
   ```

1. Selecteer **Aangepaste Vorm** en klik **uitgeven**.
1. In de Edit pagina van de Vorm, klik **Geavanceerd**.
1. In het Geavanceerde lusje, belemmering-en-daling de **Enige component van de Tekst van de Lijn** beschikbaar onder Bouw Vorm.
1. Selecteer de toegevoegde tekstcomponent om zijn montages te zien.

   Voer onder Instellingen `./jcr:content/metadata/form-submission-reviewer-group` in het veld Toewijzen aan eigenschap in.

   Het groepsveld Verzendrevisor in de eigenschappen Geavanceerd van het adaptieve formulier wordt ingeschakeld met de naam die u opgeeft onder Veld Label.

## Verzendrevisoren koppelen aan een formulier {#associating-submission-reviewers-with-a-form-1}

Als u revisoren wilt koppelen aan een adaptief formulier, maakt u een revisorgroep en voegt u gebruikers toe. Voeg de gemaakte revisorgroep toe onder het veld revisor voor formulierverzending in de geavanceerde eigenschappen van het formulier.
Met gebruikersgroepen kunt u verschillende sets revisoren aan verschillende adaptieve formulieren koppelen. Met deze functie voorkomt u dat een niet-geautoriseerde gebruiker een verzendcontrole uitvoert.

Alvorens u de volgende stappen uitvoert, zie [ Vereiste ](../../forms/using/adding-reviewers-form.md#prerequisite).

Om een groep tot stand te brengen en leden aan het toe te voegen, navigeer aan **Hulpmiddelen** > **Verrichtingen** > **Veiligheid** > **Groepen**.
Voor meer informatie, zie [ Beleid van de Gebruiker en de Diensten ](/help/sites-administering/security.md).
Zorg ervoor dat u de groep toevoegt u als lid van de uit-van-de-doos gebruikersgroep creeert: **vorm-voorlegging-recensenten**. Deze gebruikersgroep wordt geleverd bij AEM Forms en zorgt ervoor dat gebruikers worden toegevoegd als revisoren voor verzending.

Gebruikersgroepen koppelen aan een adaptief formulier:

1. Op de auteurswijze, navigeer aan **Forms** > **Forms &amp; Documenten**.
1. Gebruik **Select &#x200B;** optie om een adaptieve vorm te selecteren, en **Eigenschappen van de Mening** te klikken.
1. In het venster van Eigenschappen van de vorm, geeft de klik **&#x200B;**&#x200B;uit, en klikt dan **GEAVANCEERD**.
1. Ga de groep op het gebied van de de vraagcontroleersgroep in, en klik **Gereed**.

   Het veld Subrevisorgroep wordt weergegeven met de naam die u hebt opgegeven in het bewerkte metagegevensschema van adaptieve formulieren.

>[!NOTE]
>
>Repliceer gebruikers en formulieren om ervoor te zorgen dat de gebruikers en formulieren beschikbaar zijn in de externe implementatie van AEM Forms.
>
>Zorg ervoor dat alle gebruikers worden gerepliceerd als reviserende leden van de gebruikersgroepen in de externe implementatie.
