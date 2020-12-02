---
title: Formulieren en documenten publiceren en de publicatie ervan opheffen
seo-title: Formulieren en documenten publiceren en de publicatie ervan opheffen
description: U kunt publiceren en het publiceren van formulieren ongedaan maken. Gepubliceerde formulieren worden gerepliceerd in het publicatie-exemplaar.
seo-description: U kunt publiceren en het publiceren van formulieren ongedaan maken. Gepubliceerde formulieren worden gerepliceerd in het publicatie-exemplaar.
uuid: 0bad5608-b7a8-4599-81cc-2cd0a3dc7dd5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
content-strategy: max-2018
discoiquuid: 32a7a50c-74f4-49bc-a0bd-a9ec142527cb
docset: aem65
translation-type: tm+mt
source-git-commit: f9ed171c188a4dfb71f12ae9c98105a4c1895542
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 0%

---


# Formulieren en documenten publiceren en de publicatie ervan opheffen{#publishing-and-unpublishing-forms-and-documents}

Met AEM Forms kunt u gemakkelijk formulieren maken, publiceren en verwijderen. Zie [Inleiding tot het beheren van formulieren](../../forms/using/introduction-managing-forms.md) voor meer informatie over AEM Forms.

De AEM Forms-server biedt twee instanties: Auteur en publiceer. De instantie Auteur is bedoeld voor het maken en beheren van formulierelementen en -bronnen. Publicatie-instantie is bedoeld om elementen en gerelateerde bronnen die beschikbaar zijn voor eindgebruikers, te behouden. U kunt XDP en PDF forms op de wijze van de Auteur invoeren. Zie [XDP- en PDF-documenten ophalen in AEM Forms](../../forms/using/get-xdp-pdf-documents-aem.md) voor meer informatie.

## Ondersteunde elementen   {#supported-assets-nbsp}

AEM Forms ondersteunt de volgende typen elementen:

* Aangepaste formulieren
* Aangepaste documenten
* Adaptieve formulierfragmenten
* Thema&#39;s
* Formuliersjablonen (XFA-formulieren)
* PDF forms
* Document (vlakke PDF-documenten)
* Formuliersets
* Bron (Afbeeldingen, Schema&#39;s, en Stylesheets)

In eerste instantie zijn alle elementen alleen beschikbaar in de instantie Auteur. Een beheerder of auteur van een formulier kan alle elementen publiceren, behalve bronnen.

Wanneer u een formulier selecteert en publiceert, worden de gerelateerde elementen en bronnen ook gepubliceerd. Afhankelijke activa worden echter niet gepubliceerd. In dit verband zijn gerelateerde activa en middelen activa die een gepubliceerd actief gebruikt of waarnaar wordt verwezen. Afhankelijke elementen zijn elementen die verwijzen naar een gepubliceerd element.

Het is mogelijk dat uw Adaptieve Forms bepaalde configuraties, instellingen en aanpassingen gebruikt die niet automatisch worden gepubliceerd. U wordt aangeraden deze bronnen te publiceren of te activeren voordat u een adaptief formulier publiceert.

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

* **Niet-gepubliceerd:** Een element dat nooit is gepubliceerd (de niet-gepubliceerde status is alleen van toepassing op Forms-elementen. De activa van het Beheer van de correspondentie hebben geen Unpublished staat.)
* **Gepubliceerd**: Een middel dat is gepubliceerd en beschikbaar op de Publish instantie is
* **Gewijzigd**: Een actief dat na publicatie is gewijzigd

## Middelen {#publish-an-asset} publiceren

1. Meld u aan bij de AEM Forms-server.
1. Gebruik een van de volgende opties om een element te selecteren en te publiceren.

   1. Plaats de aanwijzer op een element en tik **[!UICONTROL Publish]** ![aem6forms_globe](assets/aem6forms_globe.pngasset.png).
   1. Voer een van de volgende handelingen uit en tik op Publiceren:

      * Tik in de kaartweergave op **[!UICONTROL Enter Selection]** ![aem6forms_check-circle](assets/aem6forms_check-circle.png) en tik op het element. Het element is geselecteerd.
      * Als u zich in de lijstweergave bevindt, schakelt u het selectievakje van een element in. Het element is geselecteerd.
      * Tik op een element om de details ervan weer te geven.
      * Geef de eigenschappen van een element weer door te tikken op Weergave-eigenschappen ![viewproperties](assets/viewproperties.png).

      >[!NOTE]
      >
      >Selecteer geen meerdere elementen. Het tegelijkertijd publiceren van meerdere elementen wordt niet ondersteund.


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

   Nadat u middelen hebt gepubliceerd, kunt u de Forms Portal gebruiken om alle elementen op een webpagina weer te geven. Zie [Inleiding tot het publiceren van formulieren op een portal](../../forms/using/introduction-publishing-forms.md) voor meer informatie.

## Alle Correspondence Management Assets {#publish-all-the-correspondence-management-assets} publiceren

Met AEM Forms kunt u alle Correspondence Management-elementen op een server in één keer publiceren. De gepubliceerde activa omvatten alle activa van het Beheer van de Correspondentie en verwante gebiedsdelen.

Voer de volgende stappen uit om alle Correspondence Management-elementen op een server te publiceren:

1. Meld u aan bij de AEM Forms-server.
1. Tik **Adobe Experience Manager** in de algemene navigatiebalk.
1. Tik op ![gereedschappen](assets/tools.png) en tik vervolgens op **Forms**.
1. Tik **Correspondentiebeheermiddelen publiceren**.

   ![publish-cmp-assets](assets/publish-cmp-assets.png)

   De pagina Alle correspondentiebeheermiddelen publiceren wordt weergegeven en geeft de informatie weer over de laatste keer dat werd geprobeerd om het proces voor het beheer van correspondentie publiceren uit te voeren.

   ![publish-last-run-details](assets/publish-last-run-details.png)

1. Tik **Publiceren** en tik in het bevestigingsbericht **OK**.

   Nadat een batchproces is voltooid, kunt u de details van de laatste uitvoering weergeven. Dit omvat informatie zoals de login van de Beheerder en als de partij met succes of ontbrak.

   >[!NOTE]
   >
   >Het publicatieproces kan niet worden geannuleerd nadat het is gestart. Zorg er tijdens het proces Publiceren ook voor dat u geen elementen maakt, verwijdert, wijzigt of publiceert, en dat u de bewerking Alle correspondentiebeheermiddelen exporteren niet start.

## Publiceren en verwijderen automatiseren voor Forms &amp; Documenten {#automate-publishing-and-unpublishing-for-forms-amp-documents}

Met AEM Forms kunt u de publicatie van middelen en het ongedaan maken van publicaties voor Forms en Documenten plannen. U kunt het schema opgeven in de Metagegevenseditor. Zie [Metagegevens van formulieren beheren voor meer informatie over het beheren van formuliermetagegevens.](../../forms/using/manage-form-metadata.md)

Voer de volgende stappen uit om de datum en het tijdstip van publicatie en het verwijderen van de publicatie van Forms &amp; Documents-elementen te plannen:

1. Selecteer een element en tik **[!UICONTROL View Properties]**. De pagina Eigenschappen van metagegevens wordt geopend.
1. Tik op **[!UICONTROL Advanced]** **[!UICONTROL Edit]** ![illustrator_penciltool_cur_edit_2_17](assets/illustratorcc_penciltool_cur_edit_2_17.png) op de pagina Eigenschappen van metagegevens.
1. Selecteer in de velden **[!UICONTROL Publish On Time]** en **[!UICONTROL Publish Off Time]** de datum en tijd.\
   Tik **[!UICONTROL Done]** ![aem6forms_check](assets/aem6forms_check.png).

## Een element {#unpublish-an-asset} verwijderen

1. Selecteer een middel dat wordt gepubliceerd en tik **[!UICONTROL Unpublish]** ![unpublish](assets/unpublish.png).
1. Gebruik een van de volgende opties om elementen te selecteren en de publicatie ervan ongedaan te maken.

   1. Plaats de aanwijzer op een element en tik **[!UICONTROL Unpublish]** ![unpublish](assets/unpublish.png).
   1. Voer een van de volgende handelingen uit en tik op Publiceren ongedaan maken:

      * Tik in de kaartweergave op **[!UICONTROL Enter Selection]** ![aem6forms_check-circle](assets/aem6forms_check-circle.png) en tik op het element. Het element is geselecteerd.

      * Als u zich in de lijstweergave bevindt, houdt u de muisaanwijzer boven een element en tikt u op ![selectassetcheckmark](assets/selectassetcheckmark.png). Het element is geselecteerd.

      * Tik op een element om de details ervan weer te geven.
      * Geef de eigenschappen van een element weer door te tikken op Weergave-eigenschappen ![viewproperties](assets/viewproperties.png).

1. Wanneer het Unpublish-proces wordt gestart, wordt een bevestigingsvenster weergegeven. Tik op **[!UICONTROL Unpublish]**.

   >[!NOTE]
   >
   >Alleen het geselecteerde element is ongepubliceerd en de onderliggende elementen en de bijbehorende elementen waarnaar wordt verwezen, zijn niet gepubliceerd.

## Een element of letter terugzetten naar de vorige gepubliceerde versie {#revert-an-asset-or-letter-to-the-previously-published-version}

Elke keer dat u een element of brief publiceert nadat u deze hebt bewerkt, wordt een versie van het element of de letter gemaakt. U kunt een element of een letter terugzetten naar een eerder gepubliceerde versie. Dit kan nodig zijn als er iets mis gaat met de huidige versie van het element of document.

>[!NOTE]
>
>Keer geen brief aan een laatst gepubliceerde staat terug als om het even welk afhankelijk element dat in die gepubliceerde brief wordt gebruikt van het systeem wordt geschrapt.

1. Selecteer een element en tik **[!UICONTROL Revert to Previously Published Version]** ![revertto previousslypublishedversion](assets/reverttopreviouslypublishedversion.png).
1. Voordat het element wordt teruggedraaid, verschijnt er een bevestigingsvenster. Tik op **[!UICONTROL Revert]**.

   Het element of de letter wordt teruggedraaid naar de eerder gepubliceerde versie.

## Middelen {#delete-an-asset} verwijderen

>[!NOTE]
>
>Als u een element verwijdert, wordt dit verwijderd uit de publicatie-instantie. Wanneer u elementen verwijdert, verwijdert u ook de versiehistorie, met uitzondering van de basisversie.

1. Selecteer een element en tik **[!UICONTROL Delete]** ![delete](assets/delete.png).

   >[!NOTE]
   >
   >De optie Verwijderen is ook beschikbaar wanneer u elementdetails weergeeft door op een element te tikken of door op Weergave-eigenschappen ![viewproperties](assets/viewproperties.png) te tikken.

1. Voordat het element wordt verwijderd, verschijnt er een bevestigingsvenster. Tik op **[!UICONTROL Delete]**.

   >[!NOTE]
   >
   >Alleen het geselecteerde element wordt verwijderd en de afhankelijke elementen worden niet verwijderd. Tik op ![references](assets/references.png) en selecteer vervolgens een element om de referenties van een element te controleren.
   >
   >
   >Als het element dat u wilt verwijderen, een onderliggend element van een ander element is, wordt het niet verwijderd. Als u een dergelijk element wilt verwijderen, verwijdert u verwijzingen van dit element uit andere elementen en probeert u het vervolgens opnieuw.

## Beschermde adaptieve formulieren {#protected-adaptive-forms}

U kunt verificatie inschakelen voor formulieren waartoe geselecteerde gebruikers toegang moeten hebben. Wanneer u verificatie voor uw formulieren inschakelt, zien gebruikers een aanmeldingsscherm voordat ze deze openen. Alleen gebruikers met referenties die zijn geautoriseerd, hebben toegang tot de formulieren.

Om verificatie voor uw formulieren in te schakelen:

1. Open configMgr in de publicatieinstantie in uw browser.\
   URL: `https://<hostname>:<PublishPort>/system/console/configMgr`

1. Klik in de configuratie van de Adobe Experience Manager-webconsole op **Apache Sling Authentication Service** om deze te configureren.
1. In het dialoogvenster Apache Sling Authentication Service dat wordt weergegeven, gebruikt u de knop **+** om paden toe te voegen.\
   Wanneer u een pad toevoegt, wordt de verificatieservice ingeschakeld voor formulieren in dat pad.
