---
title: Gebruikersinterface selecteren
seo-title: Gebruikersinterface selecteren
description: Vorm welke interface u zult gebruiken om in AEM te werken
seo-description: Vorm welke interface u zult gebruiken om in AEM te werken
uuid: ab127f2f-2f8a-4398-90dd-c5d48eed9e53
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: e418d330-f234-411d-8cad-3fd9906dcbee
docset: aem65
translation-type: tm+mt
source-git-commit: 2d7492cdee9f7f730dfa6ad2ffae396b3a737b15
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 1%

---


# Uw interface selecteren{#selecting-your-ui}

Hoewel de aanraking-toegelaten UI nu de standaardUI is en eigenschappariteit bijna met het beleid en het uitgeven van plaatsen is bereikt, kunnen er tijden zijn wanneer de gebruiker op [klassieke UI](/help/sites-classic-ui-authoring/classicui.md) wil schakelen. Hiervoor zijn verschillende opties beschikbaar.

>[!NOTE]
>
>Voor details over de status van eigenschappariteit met klassieke UI, zie [Aanraakeigenschappen pariteit UI](/help/release-notes/touch-ui-features-status.md) document.

Er zijn verschillende locaties waar u kunt definiëren welke interface moet worden gebruikt:

* [Het vormen van standaard UI voor uw ](#configuring-the-default-ui-for-your-instance)
instantieThis zal het gebrek UI plaatsen om bij gebruikerslogin te worden getoond, hoewel de gebruiker dit kan kunnen kunnen met voeten treden en een verschillende UI voor hun rekening of huidige zitting selecteren.

* [Door Klassieke UI-authoring voor uw ](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account)
account in te stellen, wordt de gebruikersinterface als standaard gebruikt bij het bewerken van pagina&#39;s, hoewel de gebruiker dit kan overschrijven en een andere gebruikersinterface kan selecteren voor hun account of huidige sessie.

* [Het schakelen naar klassieke UI voor huidige ](#switching-to-classic-ui-for-the-current-session)
sessionThis schakelt naar klassieke UI voor de huidige zitting.

* Bij het ontwerpen van [pagina&#39;s maakt het systeem bepaalde overschrijvingen met betrekking tot de interface](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>Diverse opties voor het schakelen naar klassieke UI zijn niet onmiddellijk beschikbaar uit-van-de-doos, zij moeten specifiek voor uw instantie worden gevormd.
>
>Zie [Toegang tot klassieke UI inschakelen](/help/sites-administering/enable-classic-ui.md) voor meer informatie.

>[!NOTE]
>
>Instanties die zijn bijgewerkt vanaf een vorige versie behouden de klassieke interface voor het ontwerpen van pagina&#39;s.
>
>Na upgrade wordt het ontwerpen van pagina&#39;s niet automatisch overgeschakeld op de interface met aanraakbediening, maar u kunt dit configureren met de [OSGi-configuratie](/help/sites-deploying/configuring-osgi.md) van de **WCM Authoring UI Mode Service** ( `AuthoringUIMode` service). Zie [UI-overschrijvingen voor de Editor](#ui-overrides-for-the-editor).

## Standaardinterface configureren voor uw instantie {#configuring-the-default-ui-for-your-instance}

Een systeembeheerder kan UI vormen die bij opstarten en login door [Toewijzing van de Wortel](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping) te gebruiken wordt gezien.

Dit kan door gebruikersgebreken of zittingsmontages worden met voeten getreden.

## Klassieke UI-authoring instellen voor uw account {#setting-classic-ui-authoring-for-your-account}

Elke gebruiker kan tot zijn/haar [gebruikersvoorkeur](/help/sites-authoring/user-properties.md#userpreferences) toegang hebben om te bepalen als hij/zij klassieke UI voor paginaontwerp (in plaats van het gebrek UI) wenst te gebruiken.

Dit kan door zittingsmontages worden met voeten getreden.

## Overschakelen naar klassieke UI voor de Huidige Zitting {#switching-to-classic-ui-for-the-current-session}

Als gebruikers de interface met aanraakbediening gebruiken, kunnen ze terugkeren naar de klassieke interface (alleen bureaublad). Er zijn verscheidene methodes om op klassieke UI voor de huidige zitting over te schakelen:

* **Navigatiekoppelingen**

   >[!CAUTION]
   >
   >Deze optie voor het schakelen naar klassieke UI is niet onmiddellijk beschikbaar uit-van-de-doos, moet het specifiek voor uw instantie worden gevormd.
   >
   >
   >Zie [Toegang tot klassieke UI inschakelen](/help/sites-administering/enable-classic-ui.md) voor meer informatie.

   Als dit wordt toegelaten, wanneer u muis over een toepasselijke console, een pictogram (symbool van een monitor) verschijnt, zal het tikken van/het klikken dit de aangewezen plaats in klassieke UI openen.

   Bijvoorbeeld, de verbindingen van **Sites** aan **plaatadmin**:

   ![syui-01](assets/syui-01.png)

* **URL**

   De klassieke UI kan worden betreden gebruikend URL voor het welkomstscherm bij `welcome.html`. Bijvoorbeeld:

   `https://localhost:4502/welcome.html`

   >[!NOTE]
   >
   >De interface met aanraakbediening is toegankelijk via `sites.html`. Bijvoorbeeld:
   >
   >
   >`https://localhost:4502/sites.html`

### Overschakelen naar klassieke interface bij het bewerken van een pagina {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>Deze optie voor het schakelen naar klassieke UI is niet onmiddellijk beschikbaar uit-van-de-doos, moet het specifiek voor uw instantie worden gevormd.
>
>Zie [Toegang tot klassieke UI inschakelen](/help/sites-administering/enable-classic-ui.md) voor meer informatie.

Indien ingeschakeld is **Open de klassieke UI** beschikbaar in het dialoogvenster **Paginagegevens**:

![syui-02](assets/syui-02.png)

### UI-overschrijvingen voor de Editor {#ui-overrides-for-the-editor}

De instellingen die door een gebruiker of systeembeheerder zijn gedefinieerd, kunnen door het systeem worden overschreven bij het ontwerpen van pagina&#39;s.

* Bij het ontwerpen van pagina&#39;s:

   * Het gebruik van de klassieke editor wordt geforceerd wanneer de pagina wordt geopend met `cf#` in de URL. Bijvoorbeeld:
      `https://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * Het gebruik van de aanraakeditor wordt geforceerd wanneer u `/editor.html` in de URL gebruikt of wanneer u een aanraakapparaat gebruikt. Bijvoorbeeld:
      `https://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* Elke forcering is tijdelijk en is alleen geldig voor de browsersessie

   * Een cookieset wordt ingesteld afhankelijk van het feit of touch-enabled ( `editor.html`) of classic ( `cf#`) wordt gebruikt.

* Bij het openen van pagina&#39;s via `siteadmin` wordt gecontroleerd of:

   * Het cookie
   * Een gebruikersvoorkeur
   * Als geen van beide bestaan, zal het aan de definities in [OSGi configuratie](/help/sites-deploying/configuring-osgi.md) van **WCM Authoring UI Mode Service** ( `AuthoringUIMode` dienst) in gebreke blijven.

>[!NOTE]
>
>Als [een gebruiker reeds een voorkeur voor pagina creatie](#settingthedefaultauthoringuiforyouraccount) heeft bepaald, zal dat niet worden met voeten getreden door het bezit te veranderen OSGi.

>[!CAUTION]
>
>Vanwege het gebruik van cookies, zoals hierboven beschreven, wordt het niet aanbevolen om:
>
>* Handmatig de URL bewerken - Een niet-standaard URL kan leiden tot een onbekende situatie en een gebrek aan functionaliteit.
>* Beide editors tegelijk openen, bijvoorbeeld in afzonderlijke vensters.

