---
title: Gerichte ervaringen maken in AEM Forms
seo-title: Create targeted experiences in AEM Forms
description: Gebruik Target in AEM Forms om aangepaste ervaringen voor beoogde klanten te maken.
seo-description: Use Target in AEM Forms to create customized experiences for targeted customers.
uuid: 174b6054-8fe3-4ab2-8afd-435e5dff9044
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
discoiquuid: 6cf54a08-d429-4a58-8429-a1cb784448d1
exl-id: fdc91054-3f7e-4cbf-bdfa-7d7a621747f1
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 0%

---

# Gerichte ervaringen maken in AEM Forms {#create-targeted-experiences-in-aem-forms}

## Adobe Target integreren met AEM Forms {#integrate-adobe-target-with-aem-forms}

Met Adobe Target geïntegreerd met AEM kunt u ervaringen creëren die zijn aangepast voor een doelgroep. Met Adobe Target kunt u A/B-tests maken, de reactie van de gebruiker meten en aangepaste webinhoud voor bepaalde gebruikers genereren. U kunt Adobe Target integreren met AEM Forms om afbeeldingscomponenten van adaptieve formulieren en interactieve communicatie als doel in te stellen.

Adobe Target configureren in AEM voor gebruik met adaptieve formulieren en interactieve communicatie, zie [Een doelconfiguratie maken in AEM](/help/sites-administering/target.md) en [Een framework toevoegen](/help/sites-administering/target.md).

>[!NOTE]
>
>Het richten werkt wanneer uw adaptieve vorm of interactieve mededeling gebruikend een gastheernaam of IP adres wordt teruggegeven. Dit mislukt wanneer uw adaptieve formulier of interactieve communicatie wordt gegenereerd met localhost.

## Doelactiviteit maken {#creating-a-target-activity}

1. Tikken **Adobe Experience Manager > Persoonlijkheid > Activiteiten**.

   `https://<hostname>:<port>/libs/cq/personalization/touch-ui/content/v2/activities.html`

1. Tik op de pagina Activiteiten op **Maken > Merk maken**.
1. U wordt gevraagd een sjabloon te kiezen en eigenschappen in te voeren.

   Selecteer een sjabloon, tik **Volgende.** Voer in de sectie Eigenschappen de titel van uw merk in en tik op **Maken.**
Uw merk wordt nu vermeld op de pagina Activiteiten.

1. Tik op uw merk op de pagina Activiteiten.
1. Tik in Master gebied van uw merk op **Maken** > **Activiteit maken**.

   Wanneer u een activiteit creeert, specificeert u zijn details, doel, en montages.

   De sectie Details bevat naam, doelengine en doel. Wanneer u Adobe Target selecteert als de doelengine, wordt de optie voor de configuratie van de doelcloud ingeschakeld. Kies uw doelwolkenconfiguratie, kies Type Activiteit, verstrek het doel van de activiteit, en tik **Volgende**. De interactieve Communicatie steunt slechts Ervaring richtend het type van Activiteit.

   In de sectie Doel kunt u gebruikerservaring toevoegen en deze een naam geven. Klikken **Ervaring toevoegen** de **Publiek selecteren** en **Naamervaring** opties. Tikken **Publiek selecteren** om een lijst met doelgroepen en hun bron te zien. Selecteer een publiek in de lijst Audience Name. Tikken **Ervaring toevoegen** om de ervaring een naam te geven en op **Volgende**.

   In het gedeelte Doelen en instellingen kunt u uw activiteiten plannen en er een prioriteit van maken. Plaats de begindatum, einddatum, en prioriteit van de activiteit, doel metrisch, extra metrisch en tikt **Opslaan**.

   De activiteit wordt nu vermeld in je merkpagina.

   >[!NOTE]
   >
   >U kunt de fout negeren &quot;Uw activiteit is opgeslagen maar niet gesynchroniseerd met Doel. Reden: De volgende ervaring heeft geen voorstellen&quot;, indien aangetroffen bij het opslaan van de activiteit.

1. Als u doel wilt inschakelen, bewerkt u het .jsp-bestand zodat clientbibliotheken worden opgenomen die in de sjabloon voor aangepaste formulieren worden gebruikt.

   Bij de implementatie buiten de box klikt u bijvoorbeeld op **Gereedschappen** >  **CRXDE Lite**.

   Typ /libs/fd/af/components/page/base/head.jsp in de adresbalk van CRXDE Lite om het bestand head.jsp te bewerken.

   Deze implementatie gebruikt simpleEnrollment malplaatje. In deze implementatie wijzigt u het bestand head.jsp om de volgende clientbibliotheken op te nemen:

   `<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>`

   `<cq:include path="clientcontext_optimized" resourceType="/libs/cq/personalization/components/clientcontext_optimized"/>`

   `<cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>`

1. Als u het doelframework voor adaptieve formulieren wilt inschakelen, navigeert u naar het formulier of de interactieve communicatie en opent u het in de bewerkingsmodus.

   Tik op een formulier of interactieve communicatie in de bewerkingsmodus om een formulier of interactieve communicatie te openen **Selecteren** en tik vervolgens op **Openen**.

   U kunt ook vier knoppen weergeven wanneer u de muisaanwijzer op het formulier of het interactieve communicatiepictogram plaatst zonder dat u dit selecteert. U kunt tikken op de knop **Bewerken** om het formulier te openen in de bewerkingsmodus.

1. Tik op de pagina-werkbalk op **Pagina-informatie** ![thema-opties](assets/theme-options.png) > **Eigenschappen openen**.
1. Kies op het tabblad Algemeen een configuratie voor het dialoogvenster **Adobe Target** veld. Tikken **Opslaan en sluiten**.

## Gecreeerde activiteit toepassen op een adaptieve formulierafbeelding of een interactieve communicatieafbeelding {#applying-created-activity-to-an-adaptive-form-image-or-an-interactive-communication-image}

1. Open het aangepaste formulier en de interactieve communicatie voor bewerking. Als u een interactieve mededeling opent, open het Kanaal van het Web.

1. Voeg in de ontwerpmodus van uw interactieve communicatie of adaptief formulier een afbeelding toe die u als doel wilt instellen.

   >[!NOTE]
   >
   >AEM Forms biedt alleen ondersteuning voor afbeeldingscomponenten. Zorg ervoor dat het deelvenster dat als host fungeert voor de afbeeldingscomponent geen andere component bevat en dat het aantal kolommen voor het deelvenster is ingesteld op 1.

1. Overschakelen van **Bewerken** tot **Doelstelling** in. De optie voor het schakelen tussen modi bevindt zich in de rechterbovenhoek.
1. Selecteer een **BRAND**, selecteert u **ACTIVITEIT** en tikken **Doelstelling starten**. De **Soorten publiek** wordt rechts van de editor weergegeven.

   ![gericht](assets/targeting-menu.png)

1. Selecteer een publiek in het menu **Soorten publiek** en tik op de afbeelding om deze te activeren. Er wordt een menu weergegeven. Tik in het menu op **Doel**. Tik op de afbeelding en tik op **Configureren**. Selecteer in het eigenschappenvenster de afbeelding die u voor het geselecteerde publiek wilt weergeven. Herhaal de stap voor alle doelgroepen. De doelgerichte ervaring wordt ingeschakeld voor de afbeelding in de interactieve communicatie of het adaptieve formulier.

## Controleren of de gemaakte activiteit synchroon is met de doelserver {#check-if-the-created-activity-syncs-with-the-target-server}

Een activiteit die voor het richten van syncs met de server van het Doel wordt gebruikt. Om te controleren of uw activiteit synchroon is met de doelserver, controleert u de status van uw activiteit op uw merkpagina.

Controleer of de status van de activiteit is gesynchroniseerd.

## Doelgedrag valideren {#validate-target-behavior}

Doelgedrag valideren:

* Gebruiken met `wcmmode preview` in de modus Schrijver
* Gebruiken met `wcmmode preview` en `wcmmode disabled` in de publicatiemodus

## Monitorgericht voor de afbeeldingscomponent {#monitor-targeting-for-the-image-component}

Publiceer uw afbeeldingen, activiteiten en adaptief formulier om de doelversie voor afbeeldingscomponenten op uw formulier te controleren.

## Problemen openen {#open-issues}

Visibility expression, set focus mislukt voor gerichte afbeeldingen op adaptieve formulieren.
