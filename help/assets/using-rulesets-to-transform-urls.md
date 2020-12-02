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
source-git-commit: 7e9dcebc654e63e171e2baacfe53081f58676f8d
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 3%

---


# Regelsets gebruiken om URL&#39;s {#using-rulesets-to-transform-urls} om te zetten

U kunt regelsets implementeren in dynamische media om URL&#39;s te transformeren. Regelsets zijn instructiesets die in een scripttaal (zoals JavaScript) zijn geschreven en die XML-gegevens evalueren en bepaalde handelingen uitvoeren als die gegevens aan bepaalde voorwaarden voldoen. Elke regel bestaat uit ten minste één voorwaarde en ten minste één actie. Een regel evalueert de gegevens van XML tegen de voorwaarden, en als een voorwaarde wordt voldaan, dan neemt het de aangewezen actie. Voorbeelden van regelsets zijn:

* Een MIME-achtervoegsel toevoegen. Voor veel services en websites zijn afbeeldingsachtervoegsels vereist, zoals het toevoegen van `.jpg` aan een URL.
* Een mappad naar de URL maken voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s).

   Zie [Hoe Adobe Scene7 Publishing System SEO](/help/assets/assets/s7_seo.pdf) ondersteunt.

* Metagegevens toevoegen aan de URL voor SEO-doeleinden (Search Engine Optimization).

   Zie [Hoe Adobe Scene7 Publishing System SEO](/help/assets/assets/s7_seo.pdf) ondersteunt.

* De positie van de inhoud instellen om een download te activeren.
* Vereenvoudig URL&#39;s met sjablonen voor beeldweergave voor personalisatie. Zet `rgb{XX,YY,ZZ}` bijvoorbeeld om in RTF-ready `\redXX\greenYY\blueZZ`

* Vraag om bepaalde tekens die moeten worden gecodeerd, zoals `$`, `{` en `}`, en bepaalde tekens die naar ImageServer moeten worden gedecodeerd. Facebook werkt bijvoorbeeld niet goed met URL&#39;s die speciale tekens bevatten.

   Zie [Speciale tekens verwijderen uit URL&#39;s](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/remove-special-characters-urls.html).

In de context van Dynamic Media kunnen websites die een op XML gebaseerd systeem gebruiken voor het beheer van elementgegevens, XML-bestanden uploaden naar Dynamic Media. U kunt een van deze bestanden aanwijzen als het bestand met de regelset voor voorbewerking voor het bedienen van de dynamische media-elementen. Dit dossier herstructureert het standaard URL protocolformaat om aan de bedrijfslogica van systemen te voldoen die met Dynamische Media worden geïntegreerd. U geeft een XML-bestand op dat moet dienen als pad naar het definitiebestand voor de regel.

>[!CAUTION]
>
>Wees voorzichtig bij het gebruik van linialen; kunnen voorkomen dat inhoud van dynamische media op uw website wordt weergegeven.

Er zijn voorbeeldregels beschikbaar die u kunnen helpen uw eigen regels te maken.
Zie [Referentie regelset](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/rule-set-reference/c-rule-set-reference.html).

Net als bij het maken van alle regelsets moet u ervoor zorgen dat uw XML-bestand geldig is voordat u het uploadt met een XML-validatieprogramma zoals xmlvalid.
Zie ook [Regelsets voor probleemoplossing](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/scene7-ruleset-troubleshooting.html).

Zorg er ook voor dat u eerst de regel test die is ingesteld in een testomgeving die geen invloed heeft op uw live productieomgeving.
Productieomgevingen en staging-omgevingen vereisen doorgaans verschillende logins.

* **NA het opvoeren van** milieu login pagina:  [https://s7sps1-staging.scene7.com/IpsWeb/](https://s7sps1-staging.scene7.com/IpsWeb/)
* **Staging** van aanmeldingspagina voor omgeving bij EMEA:  [https://s7sps3-staging.scene7.com/IpsWeb/](https://s7sps3-staging.scene7.com/IpsWeb/)
* **JAPAC-** pagina voor aanmelding bij omgeving:  [https://s7sps5-staging.scene7.com/IpsWeb/](https://s7sps5-staging.scene7.com/IpsWeb/)

Zie ook [Afbeelding &#39;element&#39; gebruiken in plaats van &#39;is&#39; in een regelset](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/ruleset-asset-instead-image.html).

**XML-regelsets implementeren:**

1. Meld u aan bij uw Dynamic Media Classic-account:

   [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Uw geloofsbrieven en opening van een sessie werden verstrekt door Adobe op het tijdstip van levering. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.

1. Upload het bestand met de regelset als volgt:

   * Klik op **[!UICONTROL Upload]** op de algemene navigatiebalk.
   * Klik op **[!UICONTROL Upload]** op de pagina in de linkerbovenhoek op **[!UICONTROL Browse]**.
   * Blader in het dialoogvenster **[!UICONTROL Open]** naar het bestand met de regelset (XML).
   * Selecteer het bestand en klik op **[!UICONTROL Open]**.
   * Selecteer rechts van de pagina **[!UICONTROL Upload]** een doelmap voor het bestand met regelsets.
   * Controleer of onder aan de pagina **[!UICONTROL Publish After Uploading]** is ingeschakeld.
   * Klik in de rechterbenedenhoek van de pagina op **[!UICONTROL Submit Upload]**.
   * Klik op **[!UICONTROL Jobs]** op de algemene navigatiebalk om de status van de uploadtaak te controleren. Wanneer de **[!UICONTROL Status]** kolom op **[!UICONTROL Job]** pagina zegt upload Gedaan, ga aan de volgende stappen verder.

1. Klik op **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server]** op de navigatiebalk boven aan de pagina.
1. Zoek op de pagina **[!UICONTROL Image Server Publish]** onder de groep **[!UICONTROL Catalog Management]** naar **[!UICONTROL Rule Set Definition File Path]** en klik vervolgens op **[!UICONTROL Select]**.
1. Blader op de pagina **[!UICONTROL Select Rule Set Definition File (XML)]** naar het bestand met de regelset en klik vervolgens in de rechterbenedenhoek van de pagina op **[!UICONTROL Select]**.
1. Klik in de rechterbenedenhoek van de pagina Setup op **[!UICONTROL Close]**.
1. Voer een publicatietaak voor afbeeldingsservers uit.

   De regelvastgestelde voorwaarden worden toegepast op de aanvragen voor de live Dynamic Media Image Servers.

   Als u wijzigingen aanbrengt in het bestand met de regelset, worden de wijzigingen direct toegepast wanneer u het bijgewerkte bestand met de regelset opnieuw uploadt en publiceert.

