---
title: Verzendrevisoren koppelen aan een formulier
seo-title: Verzendrevisoren koppelen aan een formulier
description: Leer hoe u revisoren voor verzending aan een formulier in AEM Forms kunt koppelen. Gekoppelde revisoren reviseren een formulier dat via de portal Formulieren is verzonden.
seo-description: Leer hoe u revisoren voor verzending aan een formulier in AEM Forms kunt koppelen. Gekoppelde revisoren reviseren een formulier dat via de portal Formulieren is verzonden.
uuid: 58c8c8fb-9262-4c37-b9b2-e46fe21b77d9
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 71d1aa10-d191-49bc-a50f-1098324f1cfe
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Verzendrevisoren koppelen aan een formulier {#associating-submission-reviewers-with-a-form}

Wanneer u een formulier maakt, kunt u gebruikers die de verzendingen van het formulier bekijken, via de portal Formulieren opgeven en feedback geven. Uw organisatie kan feedback verzamelen en de ingediende formulieren opnieuw bewerken.

Met AEM Forms kunt u een revisorgroep aan een formulier koppelen. Gebruikers die aan een revisiegroep van een formulier zijn toegevoegd, zien de verzendingen van dit formulier en geven feedback.

Revisieersgroepen die aan een formulier zijn toegewezen, kunnen alleen de verzendingen van het opgegeven formulier bekijken.

## Vereiste {#prerequisite}

### De eigenschap Groepen van de revisor voor verzending inschakelen voor adaptieve formulieren met de editor voor het metagegevensschema {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Als u een revisorgroep aan een formulier wilt koppelen, bewerkt u het metagegevensschema van adaptieve formulieren. Standaard kunt u geen revisorgroep toevoegen aan een verzonden formulier.

Het schema voor metagegevens bewerken:

1. Klik in de modus Schrijver onder Experience Manager op **Gereedschappen** > **Middelen** > **Metagegevensschema&#39;s**.
1. Navigeer op de pagina Schema-formulieren naar **Formulieren** > **Formulieren die zijn geschreven in AEM.**

   De URL van de pagina is:

   ```html
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/forms/aem-authored
   ```

1. Selecteer **Adaptief formulier** en klik op **Bewerken**.
1. Klik op **Geavanceerd** op de pagina Formulier bewerken.
1. Sleep op het tabblad Geavanceerd de component **Tekst** enkele regel die beschikbaar is onder Formulier samenstellen.
1. Selecteer de toegevoegde tekstcomponent om zijn montages te zien.

   Voer onder Instellingen `./jcr:content/metadata/form-submission-reviewer-group` in het veld Toewijzen aan eigenschap in.

   Het groepsveld Verzendrevisor in de eigenschappen Geavanceerd van het adaptieve formulier wordt ingeschakeld met de naam die u opgeeft onder Veld Label.

## Verzendrevisoren koppelen aan een formulier {#associating-submission-reviewers-with-a-form-1}

Als u revisoren wilt koppelen aan een adaptief formulier, maakt u een revisorgroep en voegt u gebruikers toe. Voeg de gemaakte revisorgroep toe onder het veld revisor voor formulierverzending in de geavanceerde eigenschappen van het formulier.
Met gebruikersgroepen kunt u verschillende sets revisoren aan verschillende adaptieve formulieren koppelen. Met deze functie voorkomt u dat een niet-geautoriseerde gebruiker een verzendcontrole uitvoert.

Voordat u de volgende stappen uitvoert, raadpleegt u [Vereiste](../../forms/using/adding-reviewers-form.md#prerequisite).

Als u een groep wilt maken en er leden aan wilt toevoegen, navigeert u naar **Gereedschappen** > **Bewerkingen** > **Beveiliging** > **Groepen**.
Voor meer informatie, zie het Beleid van de [Gebruiker en de Diensten](/help/sites-administering/security.md).
Zorg ervoor dat u de groep toevoegt u als lid van de uit-van-de-doos gebruikersgroep creeert: **formulieren-verzend-revisoren**. Deze gebruikersgroep wordt geleverd met AEM Forms en zorgt ervoor dat gebruikers worden toegevoegd als revisoren voor verzending.

Gebruikersgroepen koppelen aan een adaptief formulier:

1. Navigeer in de ontwerpmodus naar **Formulieren** > **Formulieren en documenten**.
1. Gebruik de optie **Selecteren **Selecteer om een aangepast formulier te selecteren en klik op Eigenschappen **** weergeven.
1. Klik in het venster Eigenschappen van het formulier op **Bewerken** en klik vervolgens op **GEAVANCEERD**.
1. Voer de groep in het groepsveld voor de revisorgroep voor verzending in en klik op **Gereed**.

   Het veld Subrevisorgroep wordt weergegeven met de naam die u hebt opgegeven in het bewerkte metagegevensschema van adaptieve formulieren.

>[!NOTE]
>
>Repliceer gebruikers en formulieren om ervoor te zorgen dat de gebruikers en formulieren beschikbaar zijn bij de externe implementatie van AEM Forms.
>
>Zorg ervoor dat alle gebruikers worden gerepliceerd als reviserende leden van de gebruikersgroepen in de externe implementatie.

