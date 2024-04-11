---
title: Uw gebruikersinterface selecteren in AEM
description: Configureer welke interface u gebruikt om in Adobe Experience Manager 6.5 te werken.
exl-id: 01cab3c3-4c0d-44d9-b47c-034de9a08cb1
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 1%

---

# Gebruikersinterface selecteren{#selecting-your-ui}

De UI met aanraakbediening van Adobe Experience Manager (AEM) is nu de standaardinterface en de pariteit van functies is bijna bereikt met het beheer en bewerken van sites. Er kunnen echter momenten zijn waarop de gebruiker naar de [klassieke gebruikersinterface](/help/sites-classic-ui-authoring/classicui.md). Hiervoor zijn verschillende opties beschikbaar.

>[!NOTE]
>
>Voor details over de status van eigenschappariteit met klassieke UI, zie [Pariteit aanraakinterface](/help/release-notes/touch-ui-features-status.md) document.

Er zijn verschillende locaties waar u kunt definiëren welke interface moet worden gebruikt:

* [De standaardinterface voor uw instantie configureren](#configuring-the-default-ui-for-your-instance)
Hiermee wordt de standaardinterface ingesteld die bij de gebruikersaanmelding wordt weergegeven. De gebruiker kan dit overschrijven en een andere interface selecteren voor zijn of haar account of huidige sessie.

* [Klassieke UI-authoring instellen voor uw account](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account)
Hiermee wordt de interface ingesteld op de standaardinterface bij het bewerken van pagina&#39;s, hoewel de gebruiker deze kan overschrijven en een andere interface kan selecteren voor hun account of huidige sessie.

* [Overschakelen naar de klassieke UI voor de huidige zitting](#switching-to-classic-ui-for-the-current-session)
Schakelt over naar de klassieke UI voor de huidige sessie.

* Voor het geval van [pagina het ontwerpen, maakt het systeem bepaalde met betrekking tot UI met voeten treedt](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>Diverse opties voor het schakelen naar klassieke UI zijn niet onmiddellijk beschikbaar uit-van-de-doos, zij moeten voor uw instantie worden gevormd.
>
>Zie [Toegang tot klassieke gebruikersinterface inschakelen](/help/sites-administering/enable-classic-ui.md) voor meer informatie .

>[!NOTE]
>
>Instanties die zijn bijgewerkt vanaf een vorige versie behouden de klassieke gebruikersinterface voor het ontwerpen van pagina&#39;s.
>
>Na de upgrade wordt het ontwerpen van pagina&#39;s niet automatisch overgeschakeld op de interface met aanraakbediening, maar u kunt dit configureren met de [OSGi-configuratie](/help/sites-deploying/configuring-osgi.md) van de **WCM Authoring UI Mode Service** ( `AuthoringUIMode` service). Zie [UI-overschrijvingen voor de Editor](#ui-overrides-for-the-editor).

## De standaardinterface voor uw instantie configureren {#configuring-the-default-ui-for-your-instance}

Een systeembeheerder kan UI vormen die bij opstarten en login door te gebruiken wordt gezien [Hoofdtoewijzing](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping).

Dit kan door gebruikersgebreken of zittingsmontages worden met voeten getreden.

## Klassieke UI-authoring instellen voor uw account {#setting-classic-ui-authoring-for-your-account}

Elke gebruiker heeft toegang tot zijn [gebruikersvoorkeuren](/help/sites-authoring/user-properties.md#userpreferences) om te bepalen als zij klassieke UI voor paginaontwerp, in plaats van standaardUI willen gebruiken.

Dit kan door zittingsmontages worden met voeten getreden.

## Schakelen naar klassieke gebruikersinterface voor de huidige sessie {#switching-to-classic-ui-for-the-current-session}

Als u de interface met aanraakbediening gebruikt, kunnen desktopgebruikers de klassieke interface (alleen bureaublad) weer gebruiken. Er zijn verscheidene methodes om op klassieke UI voor de huidige zitting over te schakelen:

* **Navigatiekoppelingen**

  >[!CAUTION]
  >
  >Deze optie voor het schakelen naar klassieke UI is niet onmiddellijk beschikbaar uit-van-de-doos, moet het voor uw instantie worden gevormd.
  >
  >
  >Zie [Toegang tot klassieke gebruikersinterface inschakelen](/help/sites-administering/enable-classic-ui.md) voor meer informatie .

  Als dit wordt toegelaten, wanneer u muis over een toepasselijke console beweegt, verschijnt een pictogram (een monitorsymbool). Als u hierop tikt of erop klikt, wordt de juiste locatie in de klassieke gebruikersinterface geopend.

  De koppelingen van **Sites** tot **sitebeheerder**:

  ![syui-01](assets/syui-01.png)

* **URL**

  De klassieke interface is toegankelijk via de URL voor het welkomstscherm op `welcome.html`. Bijvoorbeeld:

  `https://localhost:4502/welcome.html`

  >[!NOTE]
  >
  >De interface met aanraakbediening is toegankelijk via `sites.html`. Bijvoorbeeld:
  >
  >
  >`https://localhost:4502/sites.html`

### Schakelen naar klassieke gebruikersinterface bij het bewerken van een pagina {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>Deze optie voor het schakelen naar klassieke UI is niet onmiddellijk beschikbaar uit-van-de-doos, moet het voor uw instantie worden gevormd.
>
>Zie [Toegang tot klassieke gebruikersinterface inschakelen](/help/sites-administering/enable-classic-ui.md) voor meer informatie .

Indien ingeschakeld, **De klassieke gebruikersinterface openen** is beschikbaar via **Pagina-informatie** dialoogvenster:

![syui-02](assets/syui-02.png)

### UI-overschrijvingen voor de Editor {#ui-overrides-for-the-editor}

De montages die door een gebruiker of systeembeheerder worden bepaald kunnen door het systeem worden met voeten getreden als er paginacreatie is.

* Bij het ontwerpen van pagina&#39;s:

   * Het gebruik van de klassieke editor is geforceerd wanneer u de pagina opent met `cf#` in de URL. Bijvoorbeeld:
     `https://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

   * Het gebruik van de aanraakeditor is geforceerd bij gebruik `/editor.html` in de URL of wanneer u een aanraakapparaat gebruikt. Bijvoorbeeld:
     `https://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* Elke forcering is tijdelijk en is alleen geldig voor de browsersessie

   * Een cookie-set wordt ingesteld afhankelijk van of touch-technologie ( `editor.html`) of klassiek ( `cf#`) wordt gebruikt.

* Wanneer u pagina&#39;s opent via `siteadmin`wordt gecontroleerd of er sprake is van:

   * Het cookie
   * Een gebruikersvoorkeur
   * Als geen van beide bestaan, blijft het in gebreke aan de definities die in [OSGi-configuratie](/help/sites-deploying/configuring-osgi.md) van de **WCM Authoring UI Mode Service** ( `AuthoringUIMode` service).

>[!NOTE]
>
>Indien [een gebruiker heeft al een voorkeur voor het ontwerpen van pagina&#39;s gedefinieerd](#settingthedefaultauthoringuiforyouraccount), dat niet wordt met voeten getreden door het bezit te veranderen OSGi.

>[!CAUTION]
>
>Vanwege het gebruik van cookies, zoals hierboven beschreven, wordt het niet aanbevolen om:
>
>* Handmatig de URL bewerken - Een niet-standaard URL kan leiden tot een onbekende situatie en een gebrek aan functionaliteit.
>* Beide editors tegelijk openen, bijvoorbeeld in afzonderlijke vensters.
