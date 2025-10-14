---
title: AEM Forms-elementen en -documenten migreren
description: Met het migratiehulpprogramma kunt u Adobe Experience Manager (AEM) Forms-middelen en -documenten migreren van AEM 6.3 Forms of eerdere versies naar AEM 6.4 Forms.
content-type: reference
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-strategy: max-2018
docset: aem65
role: Admin,User
exl-id: 0f9aab7d-8e41-449a-804b-7e1bfa90befd
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1736'
ht-degree: 0%

---

# AEM Forms-elementen en -documenten migreren{#migrate-aem-forms-assets-and-documents}

Het nut van de Migratie zet de [&#x200B; Aangepaste activa van Forms &#x200B;](../../forms/using/introduction-forms-authoring.md), [&#x200B; wolkenconfiguraties &#x200B;](/help/sites-developing/extending-cloud-config.md) om, en [&#x200B; de activa van het Beheer van de Correspondentie &#x200B;](/help/forms/using/cm-overview.md) van het formaat dat in de vroegere versies aan het formaat wordt gebruikt in Adobe Experience Manager (AEM) 6.5 Forms. Wanneer u het migratiehulpprogramma uitvoert, wordt het volgende gemigreerd:

* Aangepaste componenten voor aangepaste formulieren
* Aangepaste formulieren en correspondentiebeheersjablonen
* Cloud-configuraties
* Correspondentenbeheer en aangepaste formulieren

>[!NOTE]
>
>Als er een upgrade op een externe locatie is voor Correspondence Management-middelen, kunt u de migratie altijd uitvoeren wanneer u de middelen importeert. Voor de migratie van Correspondence Management moet het Forms-compatibiliteitspakket zijn geïnstalleerd.

## Migratieaanpak {#approach-to-migration}

U kunt [&#x200B; bevorderen &#x200B;](../../forms/using/upgrade.md) aan de recentste versie van AEM Forms 6.5 van AEM Forms 6.4, 6.3, of 6.2, of een nieuwe installatie. Afhankelijk van of u uw vorige installatie upgradet of een nieuwe installatie hebt uitgevoerd, moet u een van de volgende handelingen uitvoeren:

**als er een verbetering op zijn plaats** is

Als u een upgrade op locatie hebt uitgevoerd, beschikt de geüpgrade instantie al over de elementen en documenten. Nochtans, alvorens u de activa en de documenten kunt gebruiken, moet u het [&#x200B; pakket van de Verenigbaarheid AEMFD &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=nl-NL) (omvat het pakket van de Verenigbaarheid van het Beheer van de Correspondentie) installeren

Dan moet u de activa en de documenten door [&#x200B; bijwerken die het nut van de Migratie &#x200B;](#runningmigrationutility) in werking stellen.

**als er een uit-van-plaats installatie** is

Als het een uit plaats (verse) installatie is, alvorens u de activa en de documenten kunt gebruiken, moet u het [&#x200B; pakket van de Verenigbaarheid AEMFD &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=nl-NL) (omvat het pakket van de Verenigbaarheid van het Beheer van de Correspondentie) installeren.

Dan moet u uw activapakket (ZIP of cmp) op de nieuwe opstelling invoeren en dan de activa en de documenten bijwerken door [&#x200B; in werking te stellen het nut van de Migratie &#x200B;](#runningmigrationutility). Adobe raadt u aan alleen na het uitvoeren van het migratiehulpprogramma middelen op de nieuwe installatie te maken.

Wegens [&#x200B; achterwaartse op verenigbaarheid-verwant &#x200B;](/help/sites-deploying/backward-compatibility.md) veranderingen, worden de plaatsen van een paar omslagen in crx-bewaarplaats veranderd. Exporteer en importeer afhankelijkheden (aangepaste bibliotheken en elementen) van vorige installatie handmatig naar een nieuwe omgeving.

## Voordat u verdergaat met de migratie {#prerequisites}

Voor Correspondentenbeheermiddelen:

* Voor de activa die van het vorige platform worden ingevoerd, wordt een bezit toegevoegd: **fd:version=1.0**.
* Sinds AEM 6.1 Forms zijn opmerkingen niet beschikbaar in het tekstvak. De opmerkingen die eerder zijn toegevoegd, zijn beschikbaar in de elementen, maar niet automatisch in de interface. Pas de eigenschap extendedProperties in de AEM Forms-gebruikersinterface aan om de opmerkingen zichtbaar te maken.
* In sommige van de vorige versies zoals LiveCycle ES4, werd de tekst uitgegeven gebruikend Flex RichTextEditor, maar sinds AEM 6.1 Forms, wordt de redacteur van HTML gebruikt. Door deze rendering en de weergave van de lettertypen, tekengrootten en lettertypemarges kunnen deze afwijken van de vorige versies in de gebruikersinterface van de auteur. De letters zien er echter hetzelfde uit wanneer ze worden gerenderd.
* Lijsten in tekstmodules zijn verbeterd en worden nu anders weergegeven. Er kunnen visuele verschillen zijn. Adobe raadt u aan de letters te renderen en te zien waar u lijsten in tekstmodules gebruikt.
* Aangezien de modules met afbeeldingsinhoud worden omgezet in DAM-elementen en tijdens de migratie lay-outs en fragmenten worden toegevoegd aan formulieren, verandert de eigenschap Bijgewerkt op voor deze modules in beheer.
* De versiegeschiedenis van de elementen wordt niet gemigreerd en is niet beschikbaar na de migratie. De volgende versiegeschiedenis na migratie wordt gehandhaafd.
* De status Klaar voor Publish is afgekeurd sinds AEM 6.1 Forms. Alle elementen in de status Klaar voor Publish worden dus gewijzigd in Gewijzigde status.
* Aangezien de gebruikersinterface in AEM Forms 6.3 wordt bijgewerkt, zijn de stappen voor het uitvoeren van de aanpassingen ook verschillend. Als u migreert van een versie die ouder is dan versie 6.3, voert u de aanpassing opnieuw uit.
* Layoutfragmenten worden verplaatst van `/content/apps/cm/layouts/fragmentlayouts/1001` naar `/content/apps/cm/modules/fragmentlayouts` . De verwijzing van het Woordenboek van gegevens in activa toont de weg van het Woordenboek van Gegevens in plaats van zijn naam.
* Alle tabruimten die worden gebruikt voor uitlijning in tekstmodules moeten worden aangepast. Voor meer informatie, zie [&#x200B; Correspondentiebeheer - Gebruikend lusje het uit elkaar plaatsen voor het schikken van tekst &#x200B;](https://helpx.adobe.com/aem-forms/kb/cm-tab-spacing-limitations.html).
* Configuraties van de middelencomposer veranderen in Correspondence Management-configuraties.
* Assets wordt onder mappen geplaatst met namen zoals Bestaande tekst en Bestaande lijst.

## Het migratiehulpprogramma gebruiken {#using-the-migration-utility}

### Het migratiehulpprogramma uitvoeren {#runningmigrationutility}

Voer het migratiehulpprogramma uit voordat u de elementen wijzigt of elementen maakt. Adobe raadt u aan het hulpprogramma niet uit te voeren nadat u wijzigingen hebt aangebracht of elementen hebt gemaakt. Zorg ervoor dat de Correspondence Management- of Adaptive Forms Assets-gebruikersinterface niet is geopend tijdens het migratieproces.

Wanneer u het migratiehulpprogramma voor het eerst uitvoert, wordt een logboek gemaakt met het volgende pad en de volgende naam: `\[aem-installation-directory]\cq-quickstart\logs\aem-forms-migration.log` . Dit logbestand wordt voortdurend bijgewerkt met Correspondence Management en Adaptive Forms-migratiegegevens, zoals het verplaatsen van middelen.

>[!NOTE]
>
>Voordat u het migratiehulpprogramma uitvoert, moet u controleren of u een back-up van uw crx-opslagplaats hebt gemaakt.

1. Meld u in een browsersessie als Admin aan bij de AEM Author-instantie.

1. Open de volgende URL in de browser:

   https://[*hostname*]:[*haven*]/[*context_path*] /libs/fd/foundation/gui/content/migration.html

   In de browser worden vier opties weergegeven:

   * AEM Forms Assets-migratie
   * Migratie van aangepaste Forms-componenten
   * Migratie van adaptieve Forms-sjablonen
   * Migratie van AEM Forms Cloud Configurations

1. Voer de volgende handelingen uit om de migratie uit te voeren:

   * Om **activa** te migreren, de uitgezochte Migratie van AEM Forms Assets, en in het volgende scherm, de uitgezochte **Migratie van het Begin**. De volgende code wordt gemigreerd:

      * Aangepaste formulieren
      * Documentfragmenten
      * Thema&#39;s
      * Letters
      * Gegevenswoordenboeken

   >[!NOTE]
   >
   >Tijdens de migratie van middelen vindt u mogelijk waarschuwingsberichten zoals &quot;Conflict gevonden voor...&quot;. Dergelijke berichten geven aan dat de regels voor sommige componenten in adaptieve formulieren niet kunnen worden gemigreerd. Als de component bijvoorbeeld een gebeurtenis met zowel regels als scripts had, als regels optreden nadat een script is uitgevoerd, worden de regels voor de component niet gemigreerd. U kunt [&#x200B; dergelijke regels migreren door de regelredacteur &#x200B;](#migrate-rules) in het adaptieve vormontwerp te openen.

   * Om adaptieve componenten van de vormdouane te migreren, selecteer **Aangepaste Migratie van de Componenten van Forms van de Douane** en in de pagina van de Migratie van de Componenten van de Douane, de uitgezochte **Migratie van het Begin**. De volgende code wordt gemigreerd:

      * Aangepaste componenten geschreven voor Adaptive Forms
      * Eventuele componentbedekkingen.

   * Om adaptieve vormmalplaatjes te migreren, selecteer **Aangepaste Migratie van het Malplaatje van Forms** en in de pagina van de Migratie van de Componenten van de Douane, de uitgezochte **Migratie van het Begin**. De volgende code wordt gemigreerd:

      * Aangepaste formuliersjablonen die zijn gemaakt onder `/apps` of `/conf` met AEM Sjablooneditor.

   * Migreer AEM Forms Cloud Configuration-services om het nieuwe contextbewuste cloudservicepparadigma te gebruiken, dat de interface voor aanraakbediening bevat (onder `/conf`). Wanneer u AEM Forms Cloud Configuration-services migreert, worden de cloudservices in `/etc` verplaatst naar `/conf` . Als u geen aanpassingen van de wolkendiensten hebt die van de erfeniswegen (`/etc`) afhangen, adviseert de Adobe dat u het migratienut na bevordering aan 6.5 in werking stelt; gebruik wolkenconfiguratie Touch UI voor om het even welk verder werk. Als u om het even welke bestaande aanpassingen van de wolkendiensten hebt, blijf gebruikend klassieke UI op promotieconfiguratie tot de aanpassingen worden bijgewerkt om zich aan de gemigreerde wegen (`/conf`) te richten en dan het migratienut in werking te stellen.

   Om **de wolkendiensten van AEM Forms** te migreren, die het volgende omvatten, de uitgezochte Migratie van de Configuratie van de Wolk van AEM Forms (de migratie van de wolkenconfig is onafhankelijk van het pakket van de Verenigbaarheid AEMFD). Selecteer de Migratie van de Configuraties van de Wolk van AEM Forms en dan op de pagina van de Migratie van de Configuratie, de uitgezochte **Migratie van het Begin**:

   * Cloudservices formuliergegevensmodel

      * Source-pad: `/etc/cloudservices/fdm`
      * Doelpad: `/conf/global/settings/cloudconfigs/fdm`

   * Recaptcha

      * Source-pad: `/etc/cloudservices/recaptcha`
      * Doelpad: `/conf/global/settings/cloudconfigs/recaptcha`

   * Adobe Sign

      * Source-pad: `/etc/cloudservices/echosign`
      * Doelpad: `/conf/global/settings/cloudconfigs/echosign`

   * Typekit-cloudservices

      * Source-pad: `/etc/cloudservices/typekit`
      * Doelpad: `/conf/global/settings/cloudconfigs/typekit`

   Het browservenster geeft het volgende weer terwijl het migratieproces plaatsvindt:

   * Wanneer de middelen worden bijgewerkt: Assets wordt bijgewerkt.
   * Wanneer de migratie is voltooid: voltooide migratie voor elementen.

   Wanneer de looppas, het nut van de Migratie het volgende doet:

   * **voegt de markeringen aan de activa** toe: Voegt de markering &quot;Correspondence Management toe: Gemigreerde Assets&quot; / &quot;Aangepaste Forms: Gemigreerde Assets&quot;. naar de gemigreerde elementen, zodat de gebruikers de gemigreerde elementen kunnen identificeren. Wanneer u het migratiehulpprogramma uitvoert, worden alle bestaande elementen in het systeem gemarkeerd als Gemigreerd.
   * **produceert markeringen**: De categorieën en subcategorieën die in het vorige systeem aanwezig zijn worden gecreeerd als markeringen, en dan worden deze markeringen geassocieerd met de relevante activa van het Beheer van de Correspondentie in AEM. Een categorie (claims) en een subcategorie (claims) van een lettertypesjabloon worden bijvoorbeeld gegenereerd als tags.

1. Nadat het nut van de Migratie eindigt lopend, ga aan de [&#x200B; huishouden taken &#x200B;](#housekeepingtasks) te werk.

#### Regels migreren met de regeleditor {#migrate-rules}

Deze componenten kunnen worden gemigreerd door ze te openen in de Rule Editor in de Adaptive Forms Editor.

* Als u regels en scripts wilt migreren (niet vereist als u de upgrade uitvoert vanaf 6.3) in aangepaste componenten, selecteert u Aangepaste Forms-componentmigratie en selecteert u Migratie starten in het volgende scherm. De volgende code wordt gemigreerd:

   * Regels en Scripts die zijn gemaakt met een regeleditor (6.1 FP1 en hoger)

   * Scripts die zijn gemaakt met het tabblad Script in de gebruikersinterface van 6.1 en eerder

* Als u sjablonen wilt migreren (niet vereist als u een upgrade uitvoert van 6.3 en 6.4), selecteert u Adaptieve Forms-sjabloonmigratie en selecteert u Migratie starten in het volgende scherm. De volgende code wordt gemigreerd:

   * Oude sjablonen - de aangepaste formuliersjablonen die zijn gemaakt onder /apps met AEM 6.1 Forms of eerder. Dit geldt ook voor de scripts die zijn gedefinieerd in de sjablooncomponenten.

   * Nieuwe sjablonen - Aangepaste formuliersjablonen die zijn gemaakt met de sjablooneditor onder `/conf` . Dit omvat migratie van regels en manuscripten die gebruikend de regelredacteur worden gecreeerd.

### Bewaringstaken na het uitvoeren van het migratiehulpprogramma {#housekeepingtasks}

Nadat u het migratiehulpprogramma hebt uitgevoerd, moet u de volgende huishoudelijke taken uitvoeren:

1. Zorg ervoor dat de XFA-versie van lay-outs en fragmentlay-outs 3.3 of hoger is. Als u lay-outs en fragmentlay-outs van een oudere versie gebruikt, kunnen er problemen optreden bij het renderen van de letter. Voer de volgende stappen uit om een versie van een oudere XFA bij te werken naar de meest recente versie:

   1. [&#x200B; Download XFA als zip dossier &#x200B;](../../forms/using/import-export-forms-templates.md#p-import-and-export-assets-in-correspondence-management-p) van het gebruikersinterface van Forms.
   1. Extraheer het bestand.
   1. Open het XFA-bestand in de nieuwste Designer en sla het op. De versie van XFA wordt bijgewerkt naar de nieuwste versie.
   1. Upload de XFA in de Forms-gebruikersinterface.

1. Publish alle middelen die vóór de migratie in het vorige systeem zijn gepubliceerd. Het migratiehulpprogramma werkt de elementen alleen bij in de instantie Auteur en als u de elementen wilt bijwerken in de Publish-instanties, moet u de elementen publiceren.

1. In AEM Forms 6.4 en 6.5 zijn enkele rechten van de gebruikersgroepen gewijzigd. Als u wilt dat gebruikers XDP&#39;s en Adaptive Forms met scripts kunnen uploaden of een code-editor kunnen gebruiken, moet u ze toevoegen aan de gebruikersgroep voor formulieren. Op dezelfde manier kunnen de malplaatje-auteurs niet meer de coderedacteur in de Redacteur van de Regel gebruiken. Gebruikers kunnen een code-editor gebruiken door deze toe te voegen aan de af-template-script-writers-groep. Voor instructies bij het toevoegen van gebruikers aan groepen, zie [&#x200B; het Leiden Gebruikers en de Groepen van de Gebruiker &#x200B;](/help/communities/users.md).
