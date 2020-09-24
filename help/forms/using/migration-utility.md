---
title: AEM Forms-elementen en -documenten migreren
seo-title: AEM Forms-elementen en -documenten migreren
description: Met het migratiehulpprogramma kunt u AEM Forms-middelen en -documenten migreren van AEM 6.3 Forms of eerdere versies naar AEM 6.4 Forms.
seo-description: Met het migratiehulpprogramma kunt u AEM Forms-middelen en -documenten migreren van AEM 6.3 Forms of eerdere versies naar AEM 6.4 Forms.
uuid: a3fdf940-7fc2-441c-91c8-ad66ba47e5f2
content-type: reference
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-strategy: max-2018
discoiquuid: 39dfef85-d047-4b6d-a0f5-92bd77df103b
docset: aem65
translation-type: tm+mt
source-git-commit: 46f2ae565fe4a8cfea49572eb87a489cb5d9ebd7
workflow-type: tm+mt
source-wordcount: '1809'
ht-degree: 0%

---


# AEM Forms-elementen en -documenten migreren{#migrate-aem-forms-assets-and-documents}

Het migratiehulpprogramma converteert de [Adaptieve Forms-middelen](../../forms/using/introduction-forms-authoring.md), [cloudconfiguraties](/help/sites-developing/extending-cloud-config.md)en [Correspondentiebeheermiddelen](/help/forms/using/cm-overview.md) van de indeling die in de eerdere versies werd gebruikt naar de indeling die in AEM 6.5 Forms werd gebruikt. Wanneer u migratiehulpprogramma uitvoert, worden de volgende onderdelen gemigreerd:

* Aangepaste componenten voor aangepaste formulieren
* Aangepaste formulieren en correspondentiebeheersjablonen
* Cloud-configuraties
* Correspondentenbeheer en aangepaste formulieren

>[!NOTE]
>
>Als de upgrade op een verkeerde plaats is uitgevoerd, kunt u de migratie voor Correspondence Management-middelen altijd uitvoeren wanneer u de middelen importeert. Voor migratie naar Correspondence Management moet het Forms-compatibiliteitspakket zijn geïnstalleerd.

## Migratieaanpak {#approach-to-migration}

U kunt [upgraden](../../forms/using/upgrade.md) naar de nieuwste versie van AEM Forms 6.5 vanuit AEM Forms 6.4, 6.3 of 6.2 of een nieuwe installatie uitvoeren. Afhankelijk van of u uw vorige installatie upgradet of een nieuwe installatie hebt uitgevoerd, moet u een van de volgende handelingen uitvoeren:

**In het geval van een upgrade ter plekke**

Als u een upgrade op locatie hebt uitgevoerd, beschikt de geüpgrade instantie al over de elementen en documenten. Voordat u de elementen en documenten kunt gebruiken, moet u echter het compatibiliteitspakket [](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) AEMFD installeren (inclusief het compatibiliteitspakket voor Correspondentiebeheer)

Vervolgens moet u de elementen en documenten bijwerken door het migratiehulpprogramma [](#runningmigrationutility)uit te voeren.

**In geval van installatie buiten de plaats**

Als de installatie op een verkeerde plaats staat (nieuw) voordat u de middelen en documenten kunt gebruiken, moet u het compatibiliteitspakket [](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) AEMFD installeren (inclusief het compatibiliteitspakket Correspondence Management).

Vervolgens moet u uw assetpakket (zip of cmp) importeren in de nieuwe installatie en vervolgens de elementen en documenten bijwerken door het migratiehulpprogramma [](#runningmigrationutility)uit te voeren. Adobe raadt u aan om pas na het uitvoeren van het migratiehulpprogramma nieuwe middelen op de nieuwe installatie te maken.

Door [achterwaartse compatibiliteitsgerelateerde](/help/sites-deploying/backward-compatibility.md) wijzigingen worden de locaties van een paar mappen in de crx-opslagplaats gewijzigd. Exporteer en importeer handmatig afhankelijkheden (aangepaste bibliotheken en elementen) van vorige installatie naar een nieuwe omgeving.

## Lees deze voordat u verdergaat met de migratie {#prerequisites}

Voor Correspondentenbeheermiddelen:

* Voor de elementen die zijn geïmporteerd vanaf het vorige platform, wordt een eigenschap toegevoegd: **fd:version=1.0**.
* Sinds AEM 6.1 Forms zijn opmerkingen niet beschikbaar in het tekstvak. De opmerkingen die eerder zijn toegevoegd, zijn beschikbaar in de elementen, maar niet automatisch in de interface. U moet de eigenschap extendedProperties aanpassen in de gebruikersinterface van AEM Forms om de opmerkingen zichtbaar te maken.
* In sommige van de vorige versies, zoals LiveCycle ES4, werd de tekst uitgegeven gebruikend Flex RichTextEditor, maar sinds AEM 6.1 Forms, wordt de redacteur van HTML gebruikt. Door deze weergave en weergave van de lettertypen kunnen de tekengrootten en lettertypemarges afwijken van de vorige versies in de gebruikersinterface van de auteur. De letters zien er echter hetzelfde uit wanneer ze worden gerenderd.
* Lijsten in tekstmodules zijn verbeterd en worden nu anders weergegeven. Er kunnen visuele verschillen zijn. Wij adviseren dat u teruggeeft en de brieven ziet waar u lijsten in tekstmodules gebruikt.
* Aangezien de modules met afbeeldingsinhoud worden omgezet in DAM-elementen en tijdens de migratie lay-outs en fragmenten worden toegevoegd aan formulieren, verandert de eigenschap Bijgewerkt op voor deze modules in beheer.
* De versiegeschiedenis van de elementen wordt niet gemigreerd en is niet beschikbaar na de migratie. De volgende versiegeschiedenis na migratie wordt gehandhaafd.
* De staat Klaar om te publiceren is afgekeurd sinds AEM 6.1 Forms, zodat worden alle activa in Klaar om staat te publiceren veranderd in Gewijzigde staat.
* Aangezien de gebruikersinterface in AEM Forms 6.3 wordt bijgewerkt, zijn de stappen voor het uitvoeren van de aanpassingen ook verschillend. U moet de aanpassing opnieuw uitvoeren als u van een versie voorafgaand aan 6.3 migreert.
* Layoutfragmenten worden verplaatst van /content/apps/cm/layouts/fragmentlayouts/1001 naar /content/apps/cm/modules/fragmentlayouts. De verwijzing van het Woordenboek van gegevens in activa toont weg van het Woordenboek van Gegevens in plaats van zijn naam.
* Alle tabruimten die worden gebruikt voor uitlijning in tekstmodules moeten worden aangepast. Zie [Correspondentiebeheer - Tabspatiëring gebruiken voor het rangschikken van tekst](https://helpx.adobe.com/aem-forms/kb/cm-tab-spacing-limitations.html)voor meer informatie.
* Configuraties van de middelencomposer veranderen in Correspondence Management-configuraties.
* Elementen worden onder mappen met namen als Bestaande tekst en Bestaande lijst geplaatst.

## Het migratiehulpprogramma gebruiken {#using-the-migration-utility}

### Het migratiehulpprogramma uitvoeren {#runningmigrationutility}

Voer het migratiehulpprogramma uit voordat u wijzigingen aanbrengt in de elementen of elementen maakt. We raden u aan het hulpprogramma niet uit te voeren nadat u wijzigingen hebt aangebracht of elementen hebt gemaakt. Zorg ervoor dat de gebruikersinterface Correspondence Management of Adaptive Forms Assets niet is geopend tijdens het migratieproces.

Wanneer u het Hulpprogramma van de Migratie voor het eerst in werking stelt, wordt een logboek gecreeerd met de volgende weg en de naam: \[aem-installation-directory]\cq-quickstart\logs\aem-forms-migration.log. Dit logboek wordt voortdurend bijgewerkt met Correspondence Management en Adaptive Forms-migratiegegevens, zoals het verplaatsen van middelen.

>[!NOTE]
>
>Voordat u het migratiehulpprogramma uitvoert, moet u controleren of u een back-up van uw crx-opslagplaats hebt gemaakt.

1. Meld u in een browsersessie aan bij AEM auteurinstantie als Admin.

1. Open de volgende URL in de browser:

   https://[*hostnaam*]:[*poort*]/[*context_pad*]/libs/fd/foundation/gui/content/migration.html

   In de browser worden vier opties weergegeven:

   * Migratie van AEM Forms-middelen
   * Migratie van aangepaste Forms-componenten
   * Migratie van adaptieve Forms-sjablonen
   * Migratie van AEM Forms Cloud Configurations

1. Voer de volgende handelingen uit om de migratie uit te voeren:

   * Tik op Migratie starten om **middelen** te migreren op AEM Forms Assets Migration en tik in het volgende scherm op **Start Migration**. De volgende code wordt gemigreerd:

      * Aangepaste formulieren
      * Documentfragmenten
      * Thema&#39;s
      * Letters
      * Gegevenswoordenboeken

   >[!NOTE]
   >
   >Tijdens de migratie van middelen vindt u mogelijk waarschuwingsberichten zoals &quot;Conflict gevonden voor...&quot;. Dergelijke berichten geven aan dat de regels voor sommige componenten in adaptieve formulieren niet kunnen worden gemigreerd. Als de component bijvoorbeeld een gebeurtenis met zowel regels als scripts had, als regels optreden nadat een script is uitgevoerd, worden de regels voor de component niet gemigreerd. Dergelijke regels kunnen echter worden gemigreerd door de regeleditor te openen in aangepaste formulierontwerpen.
   >
   >
   >Deze componenten kunnen worden gemigreerd door ze te openen in de Rule Editor in de Adaptive Forms Editor.
   >
   >
   >
   >    * Tik op Adaptive Forms Custom Components Migration en tik in het volgende scherm op Start Migration om regels en scripts te migreren (niet vereist als u vanaf 6.3 een upgrade uitvoert) in aangepaste componenten. De volgende code wordt gemigreerd:    >
      >
      >
      >        

      * Regels en Scripts die zijn gemaakt met een regeleditor (6.1 FP1 en hoger)
      >        * Scripts die zijn gemaakt met het tabblad Script in de gebruikersinterface van 6.1 en eerder
   >
   >
   >    * Tik op Adaptive Forms Template Migration en tik in het volgende scherm op Start Migration om sjablonen te migreren (niet vereist als u een upgrade uitvoert van 6.3 naar 6.4). De volgende code wordt gemigreerd:

      >
      >
      >
      >        


      * Oude sjablonen - de aangepaste formuliersjablonen die zijn gemaakt onder /apps met AEM 6.1 Forms of eerder. Dit geldt ook voor de scripts die zijn gedefinieerd in de sjablooncomponenten.
      >        * Nieuwe sjablonen - Aangepaste formuliersjablonen die zijn gemaakt met de sjablooneditor onder /conf. Dit omvat migratie van regels en manuscripten die gebruikend de regelredacteur worden gecreeerd.


   * Tik op **Aangepaste Forms Custom Components Migration** en tik op Migratie **** voor aangepaste onderdelen om aangepaste formulieren te migreren. De volgende code wordt gemigreerd:

      * Aangepaste componenten geschreven voor Adaptive Forms
      * Eventuele componentbedekkingen.
   * Tik op **Adaptive Forms Template Migration** en tik op de pagina Custom Components Migration (Migratie van aangepaste componenten) om adaptieve formuliersjablonen te migreren op **Start Migration**. De volgende code wordt gemigreerd:

      * Aangepaste formuliersjablonen die zijn gemaakt onder /apps of /conf met AEM Sjablooneditor.
   * Migreer AEM Forms Cloud Configuration-services om gebruik te maken van het nieuwe contextbewuste cloudservicepparadigma, dat de interface voor aanraakbediening bevat (onder /conf). Wanneer u AEM Forms Cloud Configuration Services migreert, worden de cloudservices in /etc verplaatst naar /conf. Als u geen aanpassingen van de cloudservices hebt die afhankelijk zijn van de oude paden (/etc), wordt u aangeraden het migratiehulpprogramma direct uit te voeren na de upgrade naar 6.5 en de aanraakinterface voor cloudconfiguratie te gebruiken voor verdere werkzaamheden. Als u een bestaande aanpassing van de cloudservices hebt, blijft u de klassieke interface gebruiken bij de geüpgrade installatie totdat de aanpassingen zijn bijgewerkt en worden uitgelijnd op de gemigreerde paden (/conf). Voer vervolgens het migratiehulpprogramma uit.

   Als u **AEM Forms-cloudservices**, waaronder de volgende, wilt migreren, tikt u op AEM Forms Cloud Configuration Migration (migratie van cloudconfiguratie is onafhankelijk van het compatibiliteitspakket voor AEMFD), tikt u op Migratie van AEM Forms Cloud Configurations en vervolgens op de pagina Configuration Migration (Migratie **starten**):

   * Cloudservices formuliergegevensmodel

      * Bronpad: /etc/cloudservices/fdm
      * Doelpad: /conf/global/settings/cloudconfigs/fdm
   * Recaptcha

      * Bronpad: /etc/cloudservices/recaptcha
      * Doelpad: /conf/global/settings/cloudconfigs/recaptcha
   * Adobe Sign

      * Bronpad: /etc/cloudservices/echosign
      * Doelpad: /conf/global/settings/cloudconfigs/echosign
   * Typekit-cloudservices

      * Bronpad: /etc/cloudservices/typekit
      * Doelpad: /conf/global/settings/cloudconfigs/typekit

   Het browservenster geeft het volgende weer terwijl het migratieproces plaatsvindt:

   * Wanneer de elementen worden bijgewerkt: Elementen zijn bijgewerkt.
   * Zodra de migratie is voltooid: Migratie van middelen is voltooid.

   Wanneer uitgevoerd, doet het nut van de Migratie het volgende:

   * **Hiermee voegt u de tags toe aan de elementen**: Hiermee voegt u het label Correspondentiebeheer toe: Gemigreerde activa&quot; / &quot;Aangepaste Forms: Gemigreerde activa&quot;. naar de gemigreerde elementen, zodat de gebruikers de gemigreerde elementen kunnen identificeren. Wanneer u het migratiehulpprogramma uitvoert, worden alle bestaande elementen in het systeem gemarkeerd als Gemigreerd.
   * **Genereert labels**: Categorieën en subcategorieën die zich in het vorige systeem bevinden, worden gemaakt als codes. Deze codes worden vervolgens gekoppeld aan de relevante Correspondence Management-elementen in AEM. Een categorie (claims) en een subcategorie (claims) van een lettertypesjabloon worden bijvoorbeeld gegenereerd als tags.

















1. Nadat het migratiehulpprogramma is voltooid, gaat u verder met de [huishoudelijke taken](#housekeepingtasks).

### Bewaringstaken na het uitvoeren van het migratiehulpprogramma {#housekeepingtasks}

Nadat u het migratiehulpprogramma hebt uitgevoerd, moet u de volgende huishoudelijke taken uitvoeren: [](../../forms/using/import-export-forms-templates.md)

1. Zorg ervoor dat de XFA-versie van lay-outs en fragmentlay-outs 3.3 of hoger is. Als u lay-outs en fragmentlay-outs van een oudere versie gebruikt, kunnen er problemen optreden bij het renderen van de letter. Voer de volgende stappen uit om de versie van een oudere XFA bij te werken naar de meest recente versie:

   1. [Download de XFA als een zip-bestand](../../forms/using/import-export-forms-templates.md#p-import-and-export-assets-in-correspondence-management-p) vanuit de Forms-gebruikersinterface.
   1. Extraheer het bestand.
   1. Open het XFA-bestand in de nieuwste Designer en sla het op. De versie van XFA wordt bijgewerkt naar de nieuwste versie.
   1. Upload de XFA in de Forms-gebruikersinterface.

1. Publiceer alle elementen die vóór de migratie in het vorige systeem zijn gepubliceerd. Het migratiehulpprogramma werkt de elementen alleen bij op de instantie van de auteur en om de elementen in de instantie(s) voor publicatie bij te werken, moet u de elementen publiceren.
1. In AEM Forms 6.4 en 6.5 zijn enkele rechten van de gebruikersgroepen gewijzigd. Als u wilt dat een van uw gebruikers XDP&#39;s en Adaptive Forms met scripts of code-editor kan uploaden, moet u ze toevoegen aan een gebruikersgroep voor formulieren. Op dezelfde manier kunnen de malplaatje-auteurs niet meer de coderedacteur in de Redacteur van de Regel gebruiken. Gebruikers kunnen alleen code-editor gebruiken als ze deze aan de af-template-script-writers-groep toevoegen. Voor instructies bij het toevoegen van gebruikers aan groepen, zie het [Leiden Gebruikers en Gebruikersgroepen](/help/communities/users.md).

