---
title: Formulieren en documenten publiceren en de publicatie ervan opheffen
seo-title: Publishing and unpublishing forms and documents
description: U kunt publiceren en het publiceren van formulieren ongedaan maken. Gepubliceerde formulieren worden gerepliceerd in het publicatie-exemplaar.
seo-description: You can schedule publishing and unpublishing of forms. Published forms are replicated on the publish instance.
uuid: 0bad5608-b7a8-4599-81cc-2cd0a3dc7dd5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
content-strategy: max-2018
discoiquuid: 32a7a50c-74f4-49bc-a0bd-a9ec142527cb
docset: aem65
exl-id: f26c4268-7885-4e61-a258-219d98288548
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1385'
ht-degree: 0%

---

# Formulieren en documenten publiceren en de publicatie ervan opheffen{#publishing-and-unpublishing-forms-and-documents}

Met AEM Forms kunt u gemakkelijk formulieren maken, publiceren en verwijderen. Voor meer informatie over AEM Forms raadpleegt u [Inleiding tot het beheren van formulieren](../../forms/using/introduction-managing-forms.md).

De AEM Forms-server biedt twee instanties: Auteur en publiceer. De instantie Auteur is bedoeld voor het maken en beheren van formulierelementen en -bronnen. Publicatie-instantie is bedoeld om elementen en gerelateerde bronnen die beschikbaar zijn voor eindgebruikers, te behouden. U kunt XDP en PDF forms op de wijze van de Auteur invoeren. Zie voor meer informatie [XDP- en PDF-documenten ophalen in AEM Forms](../../forms/using/get-xdp-pdf-documents-aem.md).

## Ondersteunde elementen   {#supported-assets-nbsp}

AEM Forms ondersteunt de volgende typen elementen:

* Aangepaste formulieren
* Aangepaste documenten
* Adaptieve formulierfragmenten
* Thema&#39;s
* Formuliersjablonen (XFA-formulieren)
* PDF forms
* Document (vlakke PDF documenten)
* Formuliersets
* Bron (Afbeeldingen, Schema&#39;s, en Stylesheets)

In eerste instantie zijn alle elementen alleen beschikbaar in de instantie Auteur. Een beheerder of auteur van een formulier kan alle elementen publiceren, behalve bronnen.

Wanneer u een formulier selecteert en publiceert, worden de gerelateerde elementen en bronnen ook gepubliceerd. Afhankelijke activa worden echter niet gepubliceerd. In dit verband zijn gerelateerde activa en middelen activa die een gepubliceerd actief gebruikt of waarnaar wordt verwezen. Afhankelijke elementen zijn elementen die verwijzen naar een gepubliceerd element.

Het is mogelijk dat uw Adaptieve Forms gebruik maakt van bepaalde configuraties, instellingen en aanpassingen die niet automatisch worden gepubliceerd. U wordt aangeraden deze bronnen te publiceren of te activeren voordat u een adaptief formulier publiceert.

* Bewerkbare adaptieve formuliersjablonen
* Cloud Servicen configureren voor Adobe Sign, Typekit, reCAPTCHA en Form Data Models
* Configuraties met andere cloudservices worden alleen geactiveerd als de gebruiker beheerdersmachtigingen heeft.
* Aanpassingen. Het gaat hierbij onder meer om:

   * Aangepaste indelingen
   * Aangepaste weergaven
   * CSS-bestand - wordt gebruikt als invoer in dialoogvenster Eigenschappen van container van adaptieve formulieren
   * Clientbibliotheekcategorie - Wordt gebruikt als invoer in het dialoogvenster Eigenschappen van container van adaptieve formulieren
   * Een andere clientbibliotheek die mogelijk is opgenomen als onderdeel van een adaptieve formuliersjabloon.
   * Ontwerppaden

## Elementstatussen {#asset-states}

Middelen kunnen de volgende statussen hebben:

* **Niet gepubliceerd:** An asset that has never been published (The unpublished state is apply only to Forms assets. De activa van het Beheer van de correspondentie hebben geen Unpublished staat.)
* **Gepubliceerd**: Een middel dat is gepubliceerd en beschikbaar op de Publish instantie is
* **Gewijzigd**: Een actief dat na publicatie is gewijzigd

## Middelen publiceren {#publish-an-asset}

1. Meld u aan bij de AEM Forms-server.
1. Gebruik een van de volgende opties om een element te selecteren en te publiceren.

   1. Plaats de aanwijzer op een element en tik op **[!UICONTROL Publish]** ![aem6forms_globe](assets/aem6forms_globe.pngasset.png).
   1. Voer een van de volgende handelingen uit en tik op Publiceren:

      * Tik op **[!UICONTROL Enter Selection]** ![aem6forms_check-circle](assets/aem6forms_check-circle.png)en tikt u op het element. Het element is geselecteerd.
      * Als u zich in de lijstweergave bevindt, schakelt u het selectievakje van een element in. Het element is geselecteerd.
      * Tik op een element om de details ervan weer te geven.
      * De eigenschappen van een element weergeven door op Weergave-eigenschappen te tikken ![viewproperties](assets/viewproperties.png).

      >[!NOTE]
      >
      >Selecteer geen meerdere elementen. Het tegelijk publiceren van meerdere elementen wordt niet ondersteund.


1. Wanneer het publicatieproces wordt gestart, wordt een bevestigingsvenster weergegeven met alle gerelateerde elementen en bronnen. Tik in het dialoogvenster dat gerelateerde elementen bevat op **[!UICONTROL Publish]**. Het element wordt gepubliceerd en het dialoogvenster Elementen publiceren wordt weergegeven.

   >[!NOTE]
   >
   >Voor de adaptieve formulieren wordt naast de gerelateerde elementen ook de paginanaam Adaptief formulier weergegeven.

   ![Een bevestigingsdialoogvenster met alle gerelateerde middelen en middelen](assets/p4.png)

   Een bevestigingsdialoogvenster met alle gerelateerde middelen en middelen.

   >[!NOTE]
   >
   >Als Forms Manager de gebruiker geen toestemming geeft om de vermelde elementen te publiceren, is de handeling Publiceren uitgeschakeld. Middelen waarvoor extra machtigingen vereist zijn, worden rood weergegeven.

   Nadat een element is gepubliceerd, worden de metagegevenseigenschappen van het element gekopieerd naar de instantie Publiceren en wordt de status van het element gewijzigd in Gepubliceerd. De status van de afhankelijke elementen die worden gepubliceerd, wordt ook gewijzigd in Gepubliceerd.

   Nadat u middelen hebt gepubliceerd, kunt u de Forms Portal gebruiken om alle elementen op een webpagina weer te geven. Zie voor meer informatie [Inleiding tot het publiceren van formulieren op een portal](../../forms/using/introduction-publishing-forms.md).

## Alle Correspondence Management Assets publiceren {#publish-all-the-correspondence-management-assets}

Met AEM Forms kunt u alle Correspondence Management-elementen op een server in één keer publiceren. De gepubliceerde activa omvatten alle activa van het Beheer van de Correspondentie en verwante gebiedsdelen.

Voer de volgende stappen uit om alle Correspondence Management-elementen op een server te publiceren:

1. Meld u aan bij de AEM Forms-server.
1. Tikken **Adobe Experience Manager** in de algemene navigatiebalk.
1. Tikken ![gereedschappen](assets/tools.png)en tikt u vervolgens op **Forms**.
1. Tikken **Correspondentenbeheermiddelen publiceren**.

   ![publish-cmp-assets](assets/publish-cmp-assets.png)

   De pagina Alle correspondentiebeheermiddelen publiceren wordt weergegeven en geeft de informatie weer over de laatste keer dat werd geprobeerd om het proces voor het beheer van correspondentie publiceren uit te voeren.

   ![publish-last-run-details](assets/publish-last-run-details.png)

1. Tikken **Publiceren** en tik in het bevestigingsbericht op **OK**.

   Nadat een batchproces is voltooid, kunt u de details van de laatste uitvoering weergeven. Dit omvat informatie zoals de login van de Beheerder en als de partij met succes of ontbrak.

   >[!NOTE]
   >
   >Het publicatieproces kan niet worden geannuleerd nadat het is gestart. Zorg er tijdens het proces Publiceren ook voor dat u geen elementen maakt, verwijdert, wijzigt of publiceert, en dat u de bewerking Alle correspondentiebeheermiddelen exporteren niet start.

## Publiceren en verwijderen voor Forms en documenten automatiseren {#automate-publishing-and-unpublishing-for-forms-amp-documents}

Met AEM Forms kunt u de publicatie van middelen en het ongedaan maken van publicaties voor Forms en Documenten plannen. U kunt het schema opgeven in de Metagegevenseditor. Zie voor meer informatie over het beheren van metagegevens van formulieren [Metagegevens van formulieren beheren.](../../forms/using/manage-form-metadata.md)

Voer de volgende stappen uit om de datum en het tijdstip van publicatie en het verwijderen van de publicatie van Forms &amp; Documents-elementen te plannen:

1. Middelen selecteren en tikken **[!UICONTROL View Properties]**. De pagina Eigenschappen van metagegevens wordt geopend.
1. Tik op de pagina Eigenschappen van metagegevens op **[!UICONTROL Advanced]** en tikt u vervolgens op **[!UICONTROL Edit]** ![illustrator_penciltool_cur_edit_2_17](assets/illustratorcc_penciltool_cur_edit_2_17.png).
1. In de **[!UICONTROL Publish On Time]** en **[!UICONTROL Publish Off Time]** selecteert u de datum en tijd.\
   Tikken **[!UICONTROL Done]** ![aem6forms_check](assets/aem6forms_check.png).

## Een element verwijderen {#unpublish-an-asset}

1. Selecteer een middel dat wordt gepubliceerd en tik **[!UICONTROL Unpublish]** ![ongedaan maken](assets/unpublish.png).
1. Gebruik een van de volgende opties om elementen te selecteren en de publicatie ervan ongedaan te maken.

   1. Plaats de aanwijzer op een element en tik op **[!UICONTROL Unpublish]** ![ongedaan maken](assets/unpublish.png).
   1. Voer een van de volgende handelingen uit en tik op Publiceren ongedaan maken:

      * Tik op **[!UICONTROL Enter Selection]** ![aem6forms_check-circle](assets/aem6forms_check-circle.png)en tikt u op het element. Het element is geselecteerd.

      * Als u zich in de lijstweergave bevindt, houdt u de muisaanwijzer boven een element en tikt u op ![selectassetcheckmark](assets/selectassetcheckmark.png) . Het element is geselecteerd.

      * Tik op een element om de details ervan weer te geven.
      * De eigenschappen van een element weergeven door op Weergave-eigenschappen te tikken ![viewproperties](assets/viewproperties.png).

1. Wanneer het Unpublish-proces wordt gestart, wordt een bevestigingsvenster weergegeven. Tik op **[!UICONTROL Unpublish]**.

   >[!NOTE]
   >
   >Alleen het geselecteerde element is ongepubliceerd en de onderliggende elementen en de bijbehorende elementen waarnaar wordt verwezen, zijn niet gepubliceerd.

## Een element of letter terugzetten naar de vorige gepubliceerde versie {#revert-an-asset-or-letter-to-the-previously-published-version}

Elke keer dat u een element of brief publiceert nadat u deze hebt bewerkt, wordt een versie van het element of de letter gemaakt. U kunt een element of een letter terugzetten naar een eerder gepubliceerde versie. Dit kan nodig zijn als er iets mis gaat met de huidige versie van het element of document.

>[!NOTE]
>
>Keer geen brief aan een laatst gepubliceerde staat terug als om het even welk afhankelijk element dat in die gepubliceerde brief wordt gebruikt van het systeem wordt geschrapt.

1. Middelen selecteren en tikken **[!UICONTROL Revert to Previously Published Version]** ![reverttopreviousouslypublishedversion](assets/reverttopreviouslypublishedversion.png).
1. Voordat het element wordt teruggedraaid, verschijnt er een bevestigingsvenster. Tik op **[!UICONTROL Revert]**.

   Het element of de letter wordt teruggedraaid naar de eerder gepubliceerde versie.

## Een element verwijderen {#delete-an-asset}

>[!NOTE]
>
>Als u een element verwijdert, wordt dit verwijderd uit de publicatie-instantie. Wanneer u elementen verwijdert, verwijdert u ook de versiehistorie, met uitzondering van de basisversie.

1. Middelen selecteren en tikken **[!UICONTROL Delete]** ![delete](assets/delete.png).

   >[!NOTE]
   >
   >De optie Verwijderen is ook beschikbaar als u elementdetails weergeeft door op een element te tikken of als u de eigenschappen van een element weergeeft door op Weergave-eigenschappen te tikken ![viewproperties](assets/viewproperties.png).

1. Voordat het element wordt verwijderd, verschijnt er een bevestigingsvenster. Tik op **[!UICONTROL Delete]**.

   >[!NOTE]
   >
   >Alleen het geselecteerde element wordt verwijderd en de afhankelijke elementen worden niet verwijderd. Tik op Verwijzingen naar een element om de verwijzingen naar dat element te controleren ![verwijzingen](assets/references.png) en selecteer vervolgens een element.
   >
   >
   >Als het element dat u wilt verwijderen, een onderliggend element van een ander element is, wordt het niet verwijderd. Als u een dergelijk element wilt verwijderen, verwijdert u verwijzingen van dit element uit andere elementen en probeert u het vervolgens opnieuw.

## Beschermde adaptieve formulieren {#protected-adaptive-forms}

U kunt verificatie inschakelen voor formulieren waartoe geselecteerde gebruikers toegang moeten hebben. Wanneer u verificatie voor uw formulieren inschakelt, zien gebruikers een aanmeldingsscherm voordat ze deze openen. Alleen gebruikers met referenties die zijn geautoriseerd, hebben toegang tot de formulieren.

Om verificatie voor uw formulieren in te schakelen:

1. Open configMgr in de publicatieinstantie in uw browser.\
   URL: `https://<hostname>:<PublishPort>/system/console/configMgr`

1. Klik in de configuratie van de Adobe Experience Manager-webconsole op **Apache Sling Authentication Service** om het te vormen.
1. Gebruik in het dialoogvenster Apache Sling Authentication Service dat wordt weergegeven de optie **+** om paden toe te voegen.\
   Wanneer u een pad toevoegt, wordt de verificatieservice ingeschakeld voor formulieren in dat pad.
