---
title: Regels gebruiken om URL's te transformeren
description: U kunt regelsets implementeren in dynamische media om URL's te transformeren. Regelsets zijn instructiesets die in een scripttaal (zoals JavaScript) zijn geschreven en die XML-gegevens evalueren en bepaalde handelingen uitvoeren als die gegevens aan bepaalde voorwaarden voldoen.
uuid: 9fed0c83-67b7-4483-a9b4-322e6a483449
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: abcff903-204b-4ab6-87d8-6f0ce63d7b41
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Regelsets gebruiken om URL&#39;s te transformeren {#using-rulesets-to-transform-urls}

U kunt regelsets implementeren in dynamische media om URL&#39;s te transformeren. Regelsets zijn instructiesets die in een scripttaal (zoals JavaScript) zijn geschreven en die XML-gegevens evalueren en bepaalde handelingen uitvoeren als die gegevens aan bepaalde voorwaarden voldoen. Elke regel bestaat uit ten minste één voorwaarde en ten minste één actie. Een regel evalueert de gegevens van XML tegen de voorwaarden, en als een voorwaarde wordt voldaan, dan neemt het de aangewezen actie. Voorbeelden van regelsets zijn:

* Een MIME-achtervoegsel toevoegen. Voor veel services en websites zijn afbeeldingsachtervoegsels vereist, zoals het toevoegen `.jpg` aan een URL.
* Een mappad naar de URL maken voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s).

   Zie [hoe het het Publiceren van Adobe Scene7 Systeem SEO](/help/assets/assets/s7_seo.pdf)steunt.

* Metagegevens toevoegen aan de URL voor SEO-doeleinden (Search Engine Optimization).

   Zie [hoe het het Publiceren van Adobe Scene7 Systeem SEO](/help/assets/assets/s7_seo.pdf)steunt.

* De positie van de inhoud instellen om een download te activeren.
* Vereenvoudig URL&#39;s met sjablonen voor beeldweergave voor personalisatie. U kunt `rgb{XX,YY,ZZ}` bijvoorbeeld de RTF-versie inschakelen `\redXX\greenYY\blueZZ`

* Vraag om bepaalde karakters om worden gecodeerd zoals `$`, `{`, en `}`, en bepaalde karakters om naar ImageServer worden gedecodeerd. Facebook werkt bijvoorbeeld niet goed met URL&#39;s die speciale tekens bevatten.

   Zie Speciale tekens [verwijderen uit URL&#39;s](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/remove-special-characters-urls.html).

In de context van Dynamic Media kunnen websites die een op XML gebaseerd systeem gebruiken voor het beheer van elementgegevens, XML-bestanden uploaden naar Dynamic Media. U kunt een van deze bestanden aanwijzen als het bestand met de regelset voor voorbewerking voor het bedienen van de dynamische media-elementen. Dit dossier herstructureert het standaard URL protocolformaat om aan de bedrijfslogica van systemen te voldoen die met Dynamische Media worden geïntegreerd. U geeft een XML-bestand op dat moet dienen als pad naar het definitiebestand voor de regel.

>[!CAUTION]
>
>Wees voorzichtig bij het gebruik van linialen; kunnen voorkomen dat inhoud van dynamische media op uw website wordt weergegeven.

Er zijn voorbeeldregels beschikbaar die u kunnen helpen uw eigen regels te maken.
Zie [Referentie](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/image_catalog/c_rule_set_reference.html)regelset.

Net als bij het maken van alle regelsets moet u ervoor zorgen dat uw XML-bestand geldig is voordat u het uploadt met een XML-validatieprogramma zoals xmlvalid.
Zie ook de regelreeksen van het [Oplossen van problemen](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/scene7-ruleset-troubleshooting.html).

Zorg er ook voor dat u eerst de regel test die is ingesteld in een testomgeving die geen invloed heeft op uw live productieomgeving.
Productieomgevingen en staging-omgevingen vereisen doorgaans verschillende logins.

* **NA-aanmeldingspagina voor** testomgeving: [https://s7sps1-staging.scene7.com/IpsWeb/](https://s7sps1-staging.scene7.com/IpsWeb/)
* **Aanmeldingspagina van de EMEA-testomgeving** : [https://s7sps3-staging.scene7.com/IpsWeb/](https://s7sps3-staging.scene7.com/IpsWeb/)
* **Aanmeldingspagina voor JAPAC-testomgeving** : [https://s7sps5-staging.scene7.com/IpsWeb/](https://s7sps5-staging.scene7.com/IpsWeb/)

Zie ook &#39;element&#39; [gebruiken in plaats van &#39;is&#39;-afbeelding in een regelset](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/ruleset-asset-instead-image.html).

**XML-regelsets implementeren:**

1. Meld u aan bij uw Dynamic Media Classic-account:

   [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Adobe heeft uw gegevens en aanmeldingsgegevens opgegeven op het moment van de provisioning. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.

1. Upload het bestand met de regelset als volgt:

   * Klik op **[!UICONTROL Uploaden]** op de algemene navigatiebalk.
   * Klik in de linkerbovenhoek van de pagina **[!UICONTROL Uploaden]** op **[!UICONTROL Bladeren]**.
   * Blader in het dialoogvenster **[!UICONTROL Openen]** naar het bestand met de regelset (XML).
   * Selecteer het bestand en klik op **[!UICONTROL Openen]**.
   * Selecteer rechts van de pagina **[!UICONTROL Uploaden]** een doelmap voor het bestand met regelsets.
   * Controleer of onder aan de pagina de optie **[!UICONTROL Publiceren na uploaden]** is ingeschakeld.
   * Klik in de rechterbenedenhoek van de pagina op **[!UICONTROL Uploaden]** verzenden.
   * Klik op **[!UICONTROL Taken]** op de algemene navigatiebalk om de status van de uploadtaak te controleren. Wanneer de kolom **[!UICONTROL Status]** op de pagina **[!UICONTROL Taak]** aangeeft Uploaden voltooid, gaat u door met de volgende stappen.

1. Klik op de navigatiebalk boven aan de pagina op **[!UICONTROL Instellingen > Toepassingsinstellingen > Publicatie-instelling > Afbeeldingsserver]**.
1. Ga naar de pagina Publiceren **[!UICONTROL van]** afbeeldingsserver onder de groep **[!UICONTROL Catalog Management]** en zoek het pad **[!UICONTROL voor het]** regelsetdefinitiebestand en klik op **[!UICONTROL Selecteren]**.
1. Op de **[!UICONTROL Uitgezochte pagina van het Dossier van de Definitie van de Reeks van de Regel (XML)]** , doorblader aan uw dossier van de regelreeks, dan in de laag-juiste hoek van de pagina, klik **[!UICONTROL Uitgezocht]**.
1. Klik in de rechterbenedenhoek van de pagina Setup op **[!UICONTROL Sluiten]**.
1. Voer een publicatietaak voor afbeeldingsservers uit.

   De regelvastgestelde voorwaarden worden toegepast op de aanvragen voor de live dynamische mediafbeeldenservers.

   Als u wijzigingen aanbrengt in het bestand met de regelset, worden de wijzigingen direct toegepast wanneer u het bijgewerkte bestand met de regelset opnieuw uploadt en publiceert.

