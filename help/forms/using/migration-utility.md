---
title: AEM Forms-elementen en -documenten migreren
description: Met het migratiehulpprogramma kunt u Adobe Experience Manager (AEM) Forms-middelen en -documenten migreren van AEM 6.3 Forms of eerdere versies naar AEM 6.4 Forms.
content-type: reference
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-strategy: max-2018
docset: aem65
role: Admin
exl-id: 0f9aab7d-8e41-449a-804b-7e1bfa90befd
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1736'
ht-degree: 0%

---

# AEM Forms-elementen en -documenten migreren{#migrate-aem-forms-assets-and-documents}

Het migratiehulpprogramma converteert het [Aangepaste Forms-middelen](../../forms/using/introduction-forms-authoring.md), [cloudconfiguraties](/help/sites-developing/extending-cloud-config.md), en [Correspondentenbeheermiddelen](/help/forms/using/cm-overview.md) van de indeling die in de eerdere versies werd gebruikt tot de indeling die in Adobe Experience Manager (AEM) 6.5 Forms werd gebruikt. Wanneer u het migratiehulpprogramma uitvoert, wordt het volgende gemigreerd:

* Aangepaste componenten voor aangepaste formulieren
* Aangepaste formulieren en correspondentiebeheersjablonen
* Cloud-configuraties
* Correspondentenbeheer en aangepaste formulieren

>[!NOTE]
>
>Als er een upgrade op een externe locatie is voor Correspondence Management-middelen, kunt u de migratie altijd uitvoeren wanneer u de middelen importeert. Voor de migratie van Correspondence Management moet het Forms-compatibiliteitspakket zijn geïnstalleerd.

## Migratieaanpak {#approach-to-migration}

U kunt [upgrade](../../forms/using/upgrade.md) naar de nieuwste versie van AEM Forms 6.5 van AEM Forms 6.4, 6.3 of 6.2 of een nieuwe installatie. Afhankelijk van of u uw vorige installatie upgradet of een nieuwe installatie hebt uitgevoerd, moet u een van de volgende handelingen uitvoeren:

**Als er een verbetering op zijn plaats is**

Als u een upgrade op locatie hebt uitgevoerd, beschikt de geüpgrade instantie al over de elementen en documenten. Voordat u de elementen en documenten kunt gebruiken, moet u echter de opdracht [AEMFD-compatibiliteitspakket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en) (inclusief het compatibiliteitspakket voor Correspondentenbeheer)

Vervolgens moet u de elementen en documenten bijwerken vóór [Het migratiehulpprogramma uitvoeren](#runningmigrationutility).

**Als er een installatie buiten de locatie is**

Als de installatie op de verkeerde plaats staat (vers), moet u de [AEMFD-compatibiliteitspakket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en) (inclusief het pakket Correspondence Management Compatibility).

Vervolgens moet u uw elementenpakket (zip of cmp) importeren in de nieuwe configuratie en de elementen en documenten vervolgens bijwerken vóór [Het migratiehulpprogramma uitvoeren](#runningmigrationutility). Adobe raadt u aan alleen na het uitvoeren van het migratiehulpprogramma middelen op de nieuwe installatie te maken.

Door [compatibiliteit met oudere versies](/help/sites-deploying/backward-compatibility.md) verandert, worden de plaatsen van een paar omslagen in crx-bewaarplaats veranderd. Exporteer en importeer afhankelijkheden (aangepaste bibliotheken en elementen) van vorige installatie handmatig naar een nieuwe omgeving.

## Voordat u verdergaat met de migratie {#prerequisites}

Voor Correspondentenbeheermiddelen:

* Voor de elementen die zijn geïmporteerd vanaf het vorige platform, wordt een eigenschap toegevoegd: **fd:versie=1.0**.
* Sinds AEM 6.1 Forms zijn opmerkingen niet beschikbaar in het tekstvak. De opmerkingen die eerder zijn toegevoegd, zijn beschikbaar in de elementen, maar niet automatisch in de interface. Pas de eigenschap extendedProperties in de AEM Forms-gebruikersinterface aan om de opmerkingen zichtbaar te maken.
* In sommige van de vorige versies zoals LiveCycle ES4, werd de tekst uitgegeven gebruikend Flex RichTextEditor, maar sinds AEM 6.1 Forms, wordt de redacteur van HTML gebruikt. Door deze rendering en de weergave van de lettertypen, tekengrootten en lettertypemarges kunnen deze afwijken van de vorige versies in de gebruikersinterface van de auteur. De letters zien er echter hetzelfde uit wanneer ze worden gerenderd.
* Lijsten in tekstmodules zijn verbeterd en worden nu anders weergegeven. Er kunnen visuele verschillen zijn. Adobe raadt u aan de letters te renderen en te zien waar u lijsten in tekstmodules gebruikt.
* Aangezien de modules met afbeeldingsinhoud worden omgezet in DAM-elementen en tijdens de migratie lay-outs en fragmenten worden toegevoegd aan formulieren, verandert de eigenschap Bijgewerkt op voor deze modules in beheer.
* De versiegeschiedenis van de elementen wordt niet gemigreerd en is niet beschikbaar na de migratie. De volgende versiegeschiedenis na migratie wordt gehandhaafd.
* De staat Klaar om te publiceren is afgekeurd sinds AEM 6.1 Forms, zodat worden alle activa in Klaar om staat te publiceren veranderd in Gewijzigde staat.
* Aangezien de gebruikersinterface in AEM Forms 6.3 wordt bijgewerkt, zijn de stappen voor het uitvoeren van de aanpassingen ook verschillend. Als u migreert van een versie die ouder is dan versie 6.3, voert u de aanpassing opnieuw uit.
* Layoutfragmenten worden verplaatst van `/content/apps/cm/layouts/fragmentlayouts/1001` tot `/content/apps/cm/modules/fragmentlayouts`. De verwijzing van het Woordenboek van gegevens in activa toont de weg van het Woordenboek van Gegevens in plaats van zijn naam.
* Alle tabruimten die worden gebruikt voor uitlijning in tekstmodules moeten worden aangepast. Zie voor meer informatie [Correspondentenbeheer - Tabspatiëring gebruiken voor het rangschikken van tekst](https://helpx.adobe.com/aem-forms/kb/cm-tab-spacing-limitations.html).
* Configuraties van de middelencomposer veranderen in Correspondence Management-configuraties.
* Elementen worden onder mappen met namen als Bestaande tekst en Bestaande lijst geplaatst.

## Het migratiehulpprogramma gebruiken {#using-the-migration-utility}

### Het migratiehulpprogramma uitvoeren {#runningmigrationutility}

Voer het migratiehulpprogramma uit voordat u de elementen wijzigt of elementen maakt. Adobe raadt u aan het hulpprogramma niet uit te voeren nadat u wijzigingen hebt aangebracht of elementen hebt gemaakt. Zorg ervoor dat de gebruikersinterface Correspondence Management of Adaptive Forms Assets niet is geopend tijdens het migratieproces.

Wanneer u het Hulpprogramma van de Migratie voor het eerst in werking stelt, wordt een logboek gecreeerd met de volgende weg en de naam: `\[aem-installation-directory]\cq-quickstart\logs\aem-forms-migration.log`. Dit logbestand wordt voortdurend bijgewerkt met Correspondence Management en Adaptive Forms-migratiegegevens, zoals het verplaatsen van middelen.

>[!NOTE]
>
>Voordat u het migratiehulpprogramma uitvoert, moet u controleren of u een back-up van uw crx-opslagplaats hebt gemaakt.

1. Meld u in een browsersessie als Admin aan bij de AEM Author-instantie.

1. Open de volgende URL in de browser:

   https://[*hostnaam*]:[*poort*]/[*context_path*]/libs/fd/foundation/gui/content/migration.html

   In de browser worden vier opties weergegeven:

   * Migratie van AEM Forms-middelen
   * Migratie van aangepaste Forms-componenten
   * Migratie van adaptieve Forms-sjablonen
   * Migratie van AEM Forms Cloud Configurations

1. Voer de volgende handelingen uit om de migratie uit te voeren:

   * Migreren **elementen**, selecteert u AEM Forms Assets Migration en selecteert u in het volgende scherm de optie **Migratie starten**. De volgende code wordt gemigreerd:

      * Aangepaste formulieren
      * Documentfragmenten
      * Thema&#39;s
      * Letters
      * Gegevenswoordenboeken

   >[!NOTE]
   >
   >Tijdens de migratie van middelen vindt u mogelijk waarschuwingsberichten zoals &quot;Conflict gevonden voor...&quot;. Dergelijke berichten geven aan dat de regels voor sommige componenten in adaptieve formulieren niet kunnen worden gemigreerd. Als de component bijvoorbeeld een gebeurtenis met zowel regels als scripts had, als regels optreden nadat een script is uitgevoerd, worden de regels voor de component niet gemigreerd. U kunt [dergelijke regels migreren door de regeleditor te openen](#migrate-rules) in adaptieve vorm.

   * Als u aangepaste componenten wilt migreren, selecteert u **Migratie van aangepaste Forms-componenten** en selecteert u op de pagina Custom Components Migration de optie **Migratie starten**. De volgende code wordt gemigreerd:

      * Aangepaste componenten geschreven voor Adaptive Forms
      * Eventuele componentbedekkingen.

   * Als u aangepaste formuliersjablonen wilt migreren, selecteert u **Adaptieve Forms-sjabloonmigratie** en selecteert u op de pagina Custom Components Migration de optie **Migratie starten**. De volgende code wordt gemigreerd:

      * Aangepaste formuliersjablonen die zijn gemaakt onder `/apps` of `/conf` AEM Sjablooneditor gebruiken.

   * AEM Forms Cloud Configuration-services migreren om het nieuwe, contextbewuste cloudservicepparadigma te gebruiken, dat de interface voor aanraakbediening bevat (onder `/conf`). Wanneer u AEM Forms Cloud Configuration Services migreert, kunt u de cloudservices in `/etc` worden verplaatst naar `/conf`. Als u geen aanpassingen voor cloudservices hebt die afhankelijk zijn van de verouderde paden (`/etc`), raadt de Adobe aan het migratiehulpprogramma uit te voeren nadat u de upgrade naar 6.5 hebt uitgevoerd; de aanraakinterface voor cloudconfiguratie te gebruiken voor verdere werkzaamheden. Als u een bestaande aanpassing van de cloudservices hebt, blijft u de klassieke interface gebruiken bij de geüpgrade installatie totdat de aanpassingen zijn bijgewerkt en worden uitgelijnd op de gemigreerde paden (`/conf`) en voert u vervolgens het migratiehulpprogramma uit.

   Migreren **AEM Forms-cloudservices**, die het volgende bevatten, selecteert u Migratie van AEM Forms Cloud Configuration (migratie naar cloudconfiguratie is onafhankelijk van het compatibiliteitspakket AEMFD). Selecteer Migratie van AEM Forms Cloud Configurations en selecteer vervolgens op de pagina Configuration Migration de optie **Migratie starten**:

   * Cloudservices formuliergegevensmodel

      * Bronpad: `/etc/cloudservices/fdm`
      * Doelpad: `/conf/global/settings/cloudconfigs/fdm`

   * Recaptcha

      * Bronpad: `/etc/cloudservices/recaptcha`
      * Doelpad: `/conf/global/settings/cloudconfigs/recaptcha`

   * Adobe Sign

      * Bronpad: `/etc/cloudservices/echosign`
      * Doelpad: `/conf/global/settings/cloudconfigs/echosign`

   * Typekit-cloudservices

      * Bronpad: `/etc/cloudservices/typekit`
      * Doelpad: `/conf/global/settings/cloudconfigs/typekit`

   Het browservenster geeft het volgende weer terwijl het migratieproces plaatsvindt:

   * Wanneer de elementen worden bijgewerkt: de elementen worden bijgewerkt.
   * Wanneer de migratie is voltooid: voltooide migratie voor elementen.

   Wanneer de looppas, het nut van de Migratie het volgende doet:

   * **Hiermee voegt u de codes toe aan de elementen**: Voegt het label &quot;Correspondence Management : Migrated Assets&quot; / &quot;Adaptive Forms : Migrated Assets&quot; toe. naar de gemigreerde elementen, zodat de gebruikers de gemigreerde elementen kunnen identificeren. Wanneer u het migratiehulpprogramma uitvoert, worden alle bestaande elementen in het systeem gemarkeerd als Gemigreerd.
   * **Hiermee genereert u tags**: Categorieën en subcategorieën die zich in het vorige systeem bevinden, worden gemaakt als tags en deze tags worden vervolgens in AEM gekoppeld aan de relevante Correspondentiebeheerelementen. Een categorie (claims) en een subcategorie (claims) van een lettertypesjabloon worden bijvoorbeeld gegenereerd als tags.

1. Nadat het migratiehulpprogramma is uitgevoerd, gaat u verder naar [huishoudelijke taken](#housekeepingtasks).

#### Regels migreren met de regeleditor {#migrate-rules}

Deze componenten kunnen worden gemigreerd door ze te openen in de Rule Editor in de Adaptive Forms Editor.

* Als u regels en scripts wilt migreren (niet vereist als u de upgrade uitvoert vanaf 6.3) in aangepaste componenten, selecteert u Aangepaste Forms-componentmigratie en selecteert u Migratie starten in het volgende scherm. De volgende code wordt gemigreerd:

   * Regels en Scripts die zijn gemaakt met een regeleditor (6.1 FP1 en hoger)

   * Scripts die zijn gemaakt met het tabblad Script in de gebruikersinterface van 6.1 en eerder

* Als u sjablonen wilt migreren (niet vereist als u een upgrade uitvoert van 6.3 en 6.4), selecteert u Adaptieve Forms-sjabloonmigratie en selecteert u Migratie starten in het volgende scherm. De volgende code wordt gemigreerd:

   * Oude sjablonen - de aangepaste formuliersjablonen die zijn gemaakt onder /apps met AEM 6.1 Forms of eerder. Dit geldt ook voor de scripts die zijn gedefinieerd in de sjablooncomponenten.

   * Nieuwe sjablonen - Aangepaste formuliersjablonen die zijn gemaakt met de sjablooneditor onder `/conf`. Dit omvat migratie van regels en manuscripten die gebruikend de regelredacteur worden gecreeerd.

### Bewaringstaken na het uitvoeren van het migratiehulpprogramma {#housekeepingtasks}

Nadat u het migratiehulpprogramma hebt uitgevoerd, moet u de volgende huishoudelijke taken uitvoeren:

1. Zorg ervoor dat de XFA-versie van lay-outs en fragmentlay-outs 3.3 of hoger is. Als u lay-outs en fragmentlay-outs van een oudere versie gebruikt, kunnen er problemen optreden bij het renderen van de letter. Voer de volgende stappen uit om een versie van een oudere XFA bij te werken naar de meest recente versie:

   1. [XFA downloaden als ZIP-bestand](../../forms/using/import-export-forms-templates.md#p-import-and-export-assets-in-correspondence-management-p) in de Forms-gebruikersinterface.
   1. Extraheer het bestand.
   1. Open het XFA-bestand in de nieuwste Designer en sla het op. De versie van XFA wordt bijgewerkt naar de nieuwste versie.
   1. Upload de XFA in de Forms-gebruikersinterface.

1. Publiceer alle elementen die vóór de migratie in het vorige systeem zijn gepubliceerd. Het migratiehulpprogramma werkt de elementen alleen bij in de instantie Auteur en als u de elementen wilt bijwerken in de instanties Publiceren, moet u de elementen publiceren.

1. In AEM Forms 6.4 en 6.5 zijn enkele rechten van de gebruikersgroepen gewijzigd. Als u wilt dat gebruikers XDP&#39;s en Adaptive Forms met scripts kunnen uploaden of een code-editor kunnen gebruiken, moet u ze toevoegen aan de gebruikersgroep voor formulieren. Op dezelfde manier kunnen de malplaatje-auteurs niet meer de coderedacteur in de Redacteur van de Regel gebruiken. Gebruikers kunnen een code-editor gebruiken door deze toe te voegen aan de af-template-script-writers-groep. Zie voor instructies over het toevoegen van gebruikers aan groepen [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md).
