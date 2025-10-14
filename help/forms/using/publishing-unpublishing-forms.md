---
title: Formulieren en documenten publiceren en de publicatie ervan opheffen
description: U kunt publiceren en het publiceren van formulieren ongedaan maken. Gepubliceerde formulieren worden gerepliceerd in het publicatie-exemplaar.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
content-strategy: max-2018
docset: aem65
exl-id: f26c4268-7885-4e61-a258-219d98288548
solution: Experience Manager, Experience Manager Forms
feature: Correspondence Management
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1374'
ht-degree: 0%

---

# Formulieren en documenten publiceren en de publicatie ervan opheffen{#publishing-and-unpublishing-forms-and-documents}

Met AEM Forms kunt u gemakkelijk formulieren maken, publiceren en verwijderen. Voor meer informatie over AEM Forms, zie [&#x200B; Inleiding aan het beheren van vormen &#x200B;](../../forms/using/introduction-managing-forms.md).

De AEM Forms-server biedt twee instanties: Auteur en Publish. De instantie Auteur is bedoeld voor het maken en beheren van formulierelementen en -bronnen. Publish-instantie is bedoeld om middelen en gerelateerde bronnen beschikbaar te houden voor eindgebruikers. U kunt XDP en PDF forms op de wijze van de Auteur invoeren. Voor meer informatie, zie [&#x200B; Krijgend documenten XDP en PDF in AEM Forms &#x200B;](../../forms/using/get-xdp-pdf-documents-aem.md).

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
* Aanpassingen Het gaat hierbij onder meer om:

   * Aangepaste indelingen
   * Aangepaste weergaven
   * CSS-bestand - wordt gebruikt als invoer in dialoogvenster Eigenschappen van container van adaptieve formulieren
   * Clientbibliotheekcategorie - Wordt gebruikt als invoer in het dialoogvenster Eigenschappen van container van adaptieve formulieren
   * Een andere clientbibliotheek die mogelijk is opgenomen als onderdeel van de sjabloon Adaptief formulier.
   * Ontwerppaden

## Elementstatussen {#asset-states}

Middelen kunnen de volgende statussen hebben:

* **Niet gepubliceerd:** een activa die nooit is gepubliceerd (de niet gepubliceerde staat is slechts op de activa van Forms van toepassing. De activa van het Beheer van de correspondentie hebben geen Unpublished staat.)
* **Gepubliceerd**: Een middel dat is gepubliceerd en beschikbaar op de instantie van Publish is
* **Gewijzigd**: An activa die na wordt gepubliceerd worden gewijzigd

## Publish een middel {#publish-an-asset}

1. Log in bij de AEM Forms-server.
1. Gebruik een van de volgende opties om een element te selecteren en te publiceren.

   1. Beweeg de wijzer over een activa en selecteer **[!UICONTROL Publish]** ![&#x200B; aem6forms_globe &#x200B;](assets/aem6forms_globe.pngasset.png).
   1. Voer een van de volgende handelingen uit en selecteer vervolgens Publish:

      * Als u in de kaartmening bent, selecteer **[!UICONTROL Enter Selection]** ![&#x200B; aem6forms_check-circle &#x200B;](assets/aem6forms_check-circle.png), en selecteer de activa. Het element is geselecteerd.
      * Als u zich in de lijstweergave bevindt, schakelt u het selectievakje van een element in. Het element is geselecteerd.
      * Selecteer een element om de details ervan weer te geven.
      * De eigenschappen van de vertoning van activa door de Eigenschappen van de Mening ![&#x200B; viewproperties &#x200B;](assets/viewproperties.png) te tikken.

      >[!NOTE]
      >
      >Selecteer geen meerdere elementen. Het tegelijkertijd publiceren van meerdere elementen wordt niet ondersteund.

1. Wanneer het Publish-proces wordt gestart, wordt een bevestigingsvenster weergegeven met alle gerelateerde middelen en middelen. Selecteer **[!UICONTROL Publish]** in het dialoogvenster dat gerelateerde elementen bevat. Het element wordt gepubliceerd en het dialoogvenster Publish Assets Success wordt weergegeven.

   >[!NOTE]
   >
   >Voor de adaptieve formulieren wordt naast de gerelateerde elementen ook de paginanaam Adaptief formulier weergegeven.

   ![&#x200B; de bevestigingsdialoog van A met alle verwante activa en middelen &#x200B;](assets/p4.png)

   Een bevestigingsdialoogvenster met alle gerelateerde middelen en middelen.

   >[!NOTE]
   >
   >Als Forms Manager de gebruiker geen toestemming geeft om de vermelde elementen te publiceren, is de Publish-actie uitgeschakeld. Middelen waarvoor extra machtigingen vereist zijn, worden rood weergegeven.

   Nadat een element is gepubliceerd, worden de metagegevenseigenschappen van het element naar de Publish-instantie gekopieerd en wordt de status van het element gewijzigd in Published. De status van de afhankelijke elementen die worden gepubliceerd, wordt ook gewijzigd in Gepubliceerd.

   Nadat u middelen hebt gepubliceerd, kunt u de Forms Portal gebruiken om alle elementen op een webpagina weer te geven. Voor meer informatie, zie [&#x200B; Inleiding aan het publiceren van vormen op een portaal &#x200B;](../../forms/using/introduction-publishing-forms.md).

## Publish all the Correspondent Management Assets {#publish-all-the-correspondence-management-assets}

Met AEM Forms kunt u alle Correspondence Management-elementen op een server in één keer publiceren. De gepubliceerde activa omvatten alle activa van het Beheer van de Correspondentie en verwante gebiedsdelen.

Voer de volgende stappen uit om alle Correspondence Management-elementen op een server te publiceren:

1. Log in bij de AEM Forms-server.
1. Selecteer **Adobe Experience Manager** in de globale navigatiebar.
1. Selecteer ![&#x200B; hulpmiddelen &#x200B;](assets/tools.png), en selecteer dan **Forms**.
1. Selecteer **Publish Correspondence Management Assets**.

   ![&#x200B; publiceren-cmp-activa &#x200B;](assets/publish-cmp-assets.png)

   De pagina Publish All Correspondence Management Assets wordt weergegeven en geeft de informatie weer over de laatste keer dat het Publish Correspondence Management Assets-proces is gestart.

   ![&#x200B; publiceren-last-looppas-details &#x200B;](assets/publish-last-run-details.png)

1. Selecteer **Publish** en, in het bevestig bericht, uitgezocht **O.K.**.

   Nadat een batchproces is voltooid, kunt u de details van de laatste uitvoering weergeven. Dit omvat informatie zoals de login van de Beheerder en als de partij met succes of ontbrak.

   >[!NOTE]
   >
   >Het Publish-proces kan niet worden geannuleerd nadat het is gestart. Zorg er tijdens de Publish-bewerking ook voor dat u geen elementen maakt, verwijdert, wijzigt of publiceert of dat u de bewerking Assets van het beheer van alle correspondentie exporteert.

## Publiceren en verwijderen voor Forms en documenten automatiseren {#automate-publishing-and-unpublishing-for-forms-amp-documents}

Met AEM Forms kunt u de publicatie van middelen en het ongedaan maken van publicaties voor Forms en Documenten plannen. U kunt het schema opgeven in de Metagegevenseditor. Voor meer informatie over het beheren van vormmeta-gegevens, zie [&#x200B; het Leiden vormmeta-gegevens.](../../forms/using/manage-form-metadata.md)

Voer de volgende stappen uit om de datum en het tijdstip van publicatie en het verwijderen van de publicatie van Forms &amp; Documents-elementen te plannen:

1. Selecteer een element en selecteer **[!UICONTROL View Properties]** . De pagina Eigenschappen van metagegevens wordt geopend.
1. In de pagina van de Eigenschappen van Meta-gegevens, selecteer **[!UICONTROL Advanced]**, en selecteer dan **[!UICONTROL Edit]** ![&#x200B; illustrator_penciltool_cur_edit_2_17 &#x200B;](assets/illustratorcc_penciltool_cur_edit_2_17.png).
1. Selecteer in de velden **[!UICONTROL Publish On Time]** en **[!UICONTROL Publish Off Time]** de datum en tijd.\
   Selecteer **[!UICONTROL Done]** ![&#x200B; aem6forms_check &#x200B;](assets/aem6forms_check.png).

## Een element verwijderen {#unpublish-an-asset}

1. Selecteer een activa die wordt gepubliceerd en **[!UICONTROL Unpublish]** ![&#x200B; uitgezocht unpublish &#x200B;](assets/unpublish.png).
1. Gebruik een van de volgende opties om elementen te selecteren en de publicatie ervan ongedaan te maken.

   1. Verplaats de wijzer over een activa en selecteer **[!UICONTROL Unpublish]** ![&#x200B; unpublish &#x200B;](assets/unpublish.png).
   1. Voer een van de volgende handelingen uit en selecteer vervolgens Publiceren ongedaan maken:

      * Als u in de kaartmening bent, selecteer **[!UICONTROL Enter Selection]** ![&#x200B; aem6forms_check-circle &#x200B;](assets/aem6forms_check-circle.png), en selecteer de activa. Het element is geselecteerd.

      * Als u in de lijstmening bent, houd over een activa en selecteer ![&#x200B; selectassetcheckmark &#x200B;](assets/selectassetcheckmark.png). Het element is geselecteerd.

      * Selecteer een element om de details ervan weer te geven.
      * De eigenschappen van de vertoning van activa door de Eigenschappen van de Mening ![&#x200B; viewproperties &#x200B;](assets/viewproperties.png) te tikken.

1. Wanneer het Unpublish-proces wordt gestart, wordt een bevestigingsvenster weergegeven. Selecteer **[!UICONTROL Unpublish]** .

   >[!NOTE]
   >
   >Alleen het geselecteerde element is ongepubliceerd en de onderliggende elementen en de bijbehorende elementen waarnaar wordt verwezen, zijn niet gepubliceerd.

## Een element of letter terugzetten naar de vorige gepubliceerde versie {#revert-an-asset-or-letter-to-the-previously-published-version}

Elke keer dat u een element of brief publiceert nadat u deze hebt bewerkt, wordt een versie van het element of de letter gemaakt. U kunt een element of een letter terugzetten naar een eerder gepubliceerde versie. Dit kan nodig zijn als er iets mis gaat met de huidige versie van het element of document.

>[!NOTE]
>
>Keer geen brief aan een laatst gepubliceerde staat terug als om het even welk afhankelijk element dat in die gepubliceerde brief wordt gebruikt van het systeem wordt geschrapt.

1. Selecteer een activa en selecteer **[!UICONTROL Revert to Previously Published Version]** ![&#x200B; reverttopreviousslypublishedversion &#x200B;](assets/reverttopreviouslypublishedversion.png).
1. Voordat het element wordt teruggedraaid, verschijnt er een bevestigingsvenster. Selecteer **[!UICONTROL Revert]** .

   Het element of de letter wordt teruggedraaid naar de eerder gepubliceerde versie.

## Een element verwijderen {#delete-an-asset}

>[!NOTE]
>
>Als u een element verwijdert, wordt dit verwijderd uit de publicatie-instantie. Wanneer u elementen verwijdert, verwijdert u ook de versiehistorie, met uitzondering van de basisversie.

1. Selecteer een activa en selecteer **[!UICONTROL Delete]** ![&#x200B; schrapping &#x200B;](assets/delete.png).

   >[!NOTE]
   >
   >De optie van de Schrapping is ook beschikbaar wanneer u activa details door activa te tikken of u toont de eigenschappen van een activa door de viewproperties van de Mening ![&#x200B; te tikken &#x200B;](assets/viewproperties.png).

1. Voordat het element wordt verwijderd, verschijnt er een bevestigingsvenster. Selecteer **[!UICONTROL Delete]** .

   >[!NOTE]
   >
   >Alleen het geselecteerde element wordt verwijderd en de afhankelijke elementen worden niet verwijderd. Om verwijzingen van een activa te controleren, selecteer ![&#x200B; verwijzingen &#x200B;](assets/references.png) en selecteer dan een activa.
   >
   >
   >Als het element dat u wilt verwijderen, een onderliggend element van een ander element is, wordt het niet verwijderd. Als u een dergelijk element wilt verwijderen, verwijdert u verwijzingen van dit element uit andere elementen en probeert u het vervolgens opnieuw.

## Beschermde adaptieve formulieren {#protected-adaptive-forms}

U kunt verificatie inschakelen voor formulieren waartoe geselecteerde gebruikers toegang moeten hebben. Wanneer u verificatie voor uw formulieren inschakelt, zien gebruikers een aanmeldingsscherm voordat ze deze openen. Alleen gebruikers met referenties die zijn geautoriseerd, hebben toegang tot de formulieren.

Om verificatie voor uw formulieren in te schakelen:

1. Open configMgr in de publicatieinstantie in uw browser.\
   URL: `https://<hostname>:<PublishPort>/system/console/configMgr`

1. In de Configuratie van de Console van Adobe Experience Manager, klik **Apache die de Dienst van de Authentificatie van de Verkoop** om het te vormen.
1. In het dialoogvenster Apache Sling Authentication Service dat wordt weergegeven, gebruikt u de knop **+** om paden toe te voegen.\
   Wanneer u een pad toevoegt, wordt de verificatieservice ingeschakeld voor formulieren in dat pad.
