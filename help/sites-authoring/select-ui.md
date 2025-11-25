---
title: Uw gebruikersinterface selecteren in AEM
description: Configureer welke interface u gebruikt om in Adobe Experience Manager 6.5 te werken.
exl-id: 01cab3c3-4c0d-44d9-b47c-034de9a08cb1
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 1%

---

# Gebruikersinterface selecteren{#selecting-your-ui}

De UI met aanraakbediening van Adobe Experience Manager (AEM) is nu de standaardinterface en de pariteit met functies is bijna bereikt met het beheer en bewerken van sites. Nochtans, kunnen er tijden zijn wanneer de gebruiker aan [&#x200B; klassieke UI &#x200B;](/help/sites-classic-ui-authoring/classicui.md) wil schakelen. Hiervoor zijn verschillende opties beschikbaar.

>[!NOTE]
>
>Voor details op het statuut van eigenschappariteit met klassieke UI, zie het [&#x200B; document van de Pariteit van de Eigenschap van 0&rbrace; Aanraakinterface.](/help/release-notes/touch-ui-features-status.md)

Er zijn verschillende locaties waar u kunt definiëren welke interface moet worden gebruikt:

* [&#x200B; Vormend het gebrek UI voor uw instantie &#x200B;](#configuring-the-default-ui-for-your-instance)
Hiermee wordt de standaardinterface ingesteld die bij de gebruikersaanmelding wordt weergegeven. De gebruiker kan dit overschrijven en een andere interface selecteren voor zijn of haar account of huidige sessie.

* [&#x200B; Plaatsende Klassieke Authoring UI voor uw rekening &#x200B;](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account)
Hiermee wordt de interface ingesteld op de standaardinterface bij het bewerken van pagina&#39;s, hoewel de gebruiker deze kan overschrijven en een andere interface kan selecteren voor hun account of huidige sessie.

* [&#x200B; Omschakeling aan klassieke UI voor de huidige zitting &#x200B;](#switching-to-classic-ui-for-the-current-session)
Schakelt over naar de klassieke UI voor de huidige sessie.

* Voor het geval van [&#x200B; pagina creatie, maakt het systeem bepaalde met voeten treedt in verband met UI &#x200B;](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>Diverse opties voor het schakelen naar klassieke UI zijn niet onmiddellijk beschikbaar uit-van-de-doos, zij moeten voor uw instantie worden gevormd.
>
>Zie [&#x200B; Toelatend Toegang tot Klassieke UI &#x200B;](/help/sites-administering/enable-classic-ui.md) voor meer informatie.

>[!NOTE]
>
>Instanties die zijn bijgewerkt vanaf een vorige versie behouden de klassieke gebruikersinterface voor het ontwerpen van pagina&#39;s.
>
>Na verbetering, wordt de pagina authoring niet automatisch geschakeld aan aanraking-toegelaten UI, maar u kunt dit vormen gebruikend de [&#x200B; configuratie OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) van de **WCM Authoring UI van de Wijze van de Wijze** ( `AuthoringUIMode` dienst). Zie [&#x200B; met voeten treedt UI voor de Redacteur &#x200B;](#ui-overrides-for-the-editor).

## De standaardinterface voor uw instantie configureren {#configuring-the-default-ui-for-your-instance}

Een systeembeheerder kan UI vormen die bij opstarten en login door [&#x200B; Toewijzing van de Wortel te gebruiken &#x200B;](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping) wordt gezien.

Dit kan door gebruikersgebreken of zittingsmontages worden met voeten getreden.

## Klassieke UI-authoring instellen voor uw account {#setting-classic-ui-authoring-for-your-account}

Elke gebruiker kan tot hun eigen [&#x200B; gebruikersvoorkeur &#x200B;](/help/sites-authoring/user-properties.md#userpreferences) toegang hebben om te bepalen als zij klassieke UI voor paginaontwerp, in plaats van het gebrek UI willen gebruiken.

Dit kan door zittingsmontages worden met voeten getreden.

## Schakelen naar klassieke gebruikersinterface voor de huidige sessie {#switching-to-classic-ui-for-the-current-session}

Als u de interface met aanraakbediening gebruikt, kunnen desktopgebruikers de klassieke interface (alleen bureaublad) weer gebruiken. Er zijn verscheidene methodes om op klassieke UI voor de huidige zitting over te schakelen:

* **de Verbindingen van de Navigatie**

  >[!CAUTION]
  >
  >Deze optie voor het schakelen naar klassieke UI is niet onmiddellijk beschikbaar uit-van-de-doos, moet het voor uw instantie worden gevormd.
  >
  >
  >Zie [&#x200B; Toelatend Toegang tot Klassieke UI &#x200B;](/help/sites-administering/enable-classic-ui.md) voor meer informatie.

  Als dit wordt toegelaten, wanneer u muis over een toepasselijke console beweegt, verschijnt een pictogram (een monitorsymbool). Als u hierop tikt of erop klikt, wordt de juiste locatie in de klassieke gebruikersinterface geopend.

  Bijvoorbeeld, de verbindingen van **Plaatsen** aan **plaats admin**:

  ![&#x200B; syui-01 &#x200B;](assets/syui-01.png)

* **URL**

  De klassieke interface is toegankelijk via de URL voor het welkomstscherm op `welcome.html` . Bijvoorbeeld:

  `https://localhost:4502/welcome.html`

  >[!NOTE]
  >
  >De interface met aanraakbediening is toegankelijk via `sites.html` . Bijvoorbeeld:
  >
  >
  >`https://localhost:4502/sites.html`

### Schakelen naar klassieke gebruikersinterface bij het bewerken van een pagina {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>Deze optie voor het schakelen naar klassieke UI is niet onmiddellijk beschikbaar uit-van-de-doos, moet het voor uw instantie worden gevormd.
>
>Zie [&#x200B; Toelatend Toegang tot Klassieke UI &#x200B;](/help/sites-administering/enable-classic-ui.md) voor meer informatie.

Indien toegelaten, **open Klassieke UI** van de **dialoog van de Informatie van de Pagina** beschikbaar is:

![&#x200B; syui-02 &#x200B;](assets/syui-02.png)

### UI-overschrijvingen voor de Editor {#ui-overrides-for-the-editor}

De montages die door een gebruiker of systeembeheerder worden bepaald kunnen door het systeem worden met voeten getreden als er paginacreatie is.

* Bij het ontwerpen van pagina&#39;s:

   * Het gebruik van de klassieke editor wordt geforceerd wanneer u de pagina opent met `cf#` in de URL. Bijvoorbeeld:
     `https://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * Het gebruik van de aanraakeditor wordt geforceerd wanneer u `/editor.html` in de URL gebruikt of wanneer u een aanraakapparaat gebruikt. Bijvoorbeeld:
     `https://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* Elke forcering is tijdelijk en is alleen geldig voor de browsersessie

   * Een cookieset wordt ingesteld afhankelijk van het feit of touch-enabled ( `editor.html`) of classic ( `cf#` ) wordt gebruikt.

* Wanneer u pagina&#39;s opent via `siteadmin` , wordt gecontroleerd of het volgende bestaat:

   * Het cookie
   * Een gebruikersvoorkeur
   * Als geen van beide bestaan, blijft het aan de definities in de [&#x200B; configuratie OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) van de **WCM Authoring UI Mode Service** ( `AuthoringUIMode` dienst) worden geplaatst.

>[!NOTE]
>
>Als [&#x200B; een gebruiker reeds een voorkeur voor pagina creatie &#x200B;](#settingthedefaultauthoringuiforyouraccount) heeft bepaald, die niet door het bezit te veranderen OSGi wordt met voeten getreden.

>[!CAUTION]
>
>Vanwege het gebruik van cookies, zoals hierboven beschreven, wordt het niet aanbevolen om:
>
>* Handmatig de URL bewerken - Een niet-standaard URL kan leiden tot een onbekende situatie en een gebrek aan functionaliteit.
>* Beide editors tegelijk openen, bijvoorbeeld in afzonderlijke vensters.
