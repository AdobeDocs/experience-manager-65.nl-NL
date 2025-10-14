---
title: Ongedaan maken configureren voor paginabewerking
description: Leer hoe u ondersteuning voor Ongedaan maken voor paginabewerking in AEM configureert.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: 2cf3ac3f-ee17-480d-a32a-c57631502693
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---

# Ongedaan maken configureren voor paginabewerking{#configuring-undo-for-page-editing}

De [&#x200B; dienst OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) **Dag CQ WCM maakt Configuratie** ongedaan ( `com.day.cq.wcm.undo.UndoConfigService`) blootstelt verscheidene eigenschappen die het gedrag van ongedaan controleren en opnieuw bevelen voor het uitgeven van pagina&#39;s.

## Standaardconfiguratie {#default-configuration}

In een standaardinstallatie worden de standaardmontages bepaald als eigenschappen op de `sling:OsgiConfig` knoop:

`/libs/wcm/core/config.author/com.day.cq.wcm.undo.UndoConfig`

Dit knooppunt bevat `cq.wcm.undo.whitelist` - en `cq.wcm.undo.blacklist` -eigenschappen. Voor de andere eigenschappen worden de standaardinstellingen gebruikt.

>[!CAUTION]
>
>U ***moet*** niets in de `/libs` weg veranderen.
>
>De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van de instantie wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).

## Ongedaan maken en Opnieuw configureren {#configuring-undo-and-redo}

U kunt deze OSGi de diensteigenschappen voor uw eigen instantie vormen.

>[!NOTE]
>
>Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [&#x200B; Vormend OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

De volgende lijst maakt een lijst van de eigenschappen zoals getoond in de console van het Web, die door de naam van de overeenkomstige parameter OSGi, samen met een beschrijving en de standaardwaarde (waar aangewezen) wordt gevolgd:

* **laat toe**
( `cq.wcm.undo.enabled`)

   * **Beschrijving**: Bepaalt of de paginaauteurs veranderingen ongedaan kunnen maken en opnieuw doen.
   * **Gebrek**: `Selected`
   * **Type**: `Boolean`

* **Weg**
( `cq.wcm.undo.path`)

   * **Beschrijving**: De bewaarplaatspad voor het persisteren binair maakt gegevens ongedaan. Wanneer auteurs binaire gegevens zoals afbeeldingen wijzigen, blijft de oorspronkelijke versie van de gegevens hier behouden. Wanneer wijzigingen in binaire gegevens ongedaan worden gemaakt, worden deze binaire gegevens voor ongedaan maken hersteld naar de pagina.
   * **Gebrek**: `/var/undo`
   * **Type**: `String`

  >[!NOTE]
  >
  >Standaard hebben alleen beheerders toegang tot het knooppunt `/var/undo` . Auteurs kunnen bewerkingen voor ongedaan maken en opnieuw uitvoeren op binaire inhoud alleen nadat zij machtigingen hebben gekregen om toegang te krijgen tot de binaire gegevens voor ongedaan maken.

* **Min. validity**
( `cq.wcm.undo.validity` )

   * **Beschrijving**: De minimumhoeveelheid tijd dat binair gegevens ongedaan maakt wordt opgeslagen, in uren. Na deze tijdsperiode, zijn de binaire gegevens beschikbaar voor schrapping, om schijfruimte te besparen.
   * **Gebrek**: `10`
   * **Type**: `Integer`

* **Stappen**
( `cq.wcm.undo.steps`)

   * **Beschrijving**: Het maximumaantal paginaacties die in undo geschiedenis worden opgeslagen.
   * **Gebrek**: `20`
   * **Type**: `Integer`

* **persistentie**
( `cq.wcm.undo.persistence`)

   * **Beschrijving**: De klasse die voortduurt maakt geschiedenis ongedaan. Er zijn twee persistentieklassen beschikbaar:

      * `CQ.undo.persistence.WindowNamePersistence`: hiermee wordt de historie voortgezet met de eigenschap window.name.
      * `CQ.undo.persistence.CookiePersistance`: behoudt de geschiedenis met behulp van cookies.

   * **Gebrek**: `CQ.undo.persistence.WindowNamePersistence`
   * **Type**: `String`

* **Persistence wijze**
( `cq.wcm.undo.persistence.mode`)

   * **Beschrijving**: Bepaalt wanneer undo de geschiedenis wordt voortgeduurd. Selecteer deze optie als u de historie voor ongedaan maken wilt behouden na elke paginabewerking. Schakel deze optie uit als u alleen wilt doorgaan wanneer een pagina opnieuw wordt geladen (de gebruiker navigeert bijvoorbeeld naar een andere pagina).

     Als u de historie voor ongedaan maken blijvend maakt, worden bronnen in de webbrowser gebruikt. Als de browser van uw gebruikers traag reageert op paginabewerkingen, probeert u de historie voor ongedaan maken bij het opnieuw laden van de pagina voort te zetten.

   * **Gebrek**: `Selected`
   * **Type**: `Boolean`

* **wijze van de Teller**
( `cq.wcm.undo.markermode`)

   * **Beschrijving**: Specificeert het visuele richtsnoer om te gebruiken voor het erop wijzen van welke paragrafen worden beïnvloed wanneer ongedaan maakt of opnieuw doet voorkomt. De volgende waarden zijn geldig:

      * flash: de selectie-indicator van de alinea&#39;s wordt tijdelijk knipperd.
      * Selecteer: De alinea is geselecteerd.

   * **Gebrek**: `flash`
   * **Type**: `String`

* **Goede componenten**
( `cq.wcm.undo.whitelist`)

   * **Beschrijving**: Een lijst van componenten die u door wilt worden beïnvloed ongedaan maken en bevelen opnieuw doen. Voeg componentpaden toe aan deze lijst wanneer deze correct werken met ongedaan maken/opnieuw uitvoeren. Een sterretje (&ast;) toevoegen om een groep componenten op te geven:

      * Met de volgende waarde wordt de stichtingstekstcomponent opgegeven:

        `foundation/components/text`

      * Met de volgende waarde worden alle basiscomponenten opgegeven:

        `foundation/components/*`

   * Wanneer u een component die zich niet in deze lijst bevindt, ongedaan maakt of opnieuw uitvoert, wordt een bericht weergegeven dat aangeeft dat de opdracht onbetrouwbaar kan zijn.

   * **Gebrek**: Het bezit wordt bevolkt met vele componenten die AEM verstrekt.
   * **Type**: `String[]`

* **Onjuiste componenten**
( `cq.wcm.undo.blacklist`)

   * **Beschrijving**: Een lijst van componenten en/of componentenverrichtingen die u niet wilt worden beïnvloed door undo bevel. Voeg componenten en componentbewerkingen toe die zich niet correct gedragen met de opdracht Ongedaan maken:

      * Voeg een componentpad toe als u bijvoorbeeld geen bewerkingen van de component in de historie voor ongedaan maken wilt uitvoeren. `collab/forum/components/post`
      * Een dubbele punt (:) en een bewerking aan het pad toevoegen wanneer u wilt dat die specifieke bewerking wordt weggelaten uit de historie voor ongedaan maken (andere bewerkingen functioneren correct), bijvoorbeeld `collab/forum/components/post:insertParagraph.`

  >[!NOTE]
  >
  >Wanneer een bewerking in deze lijst staat, wordt deze nog toegevoegd aan de historie voor ongedaan maken. De gebruikers kunnen geen verrichtingen ongedaan maken die vroeger dan a **Onjuiste Component** verrichting in undo geschiedenis bestaan.

   * De typische verrichtingsnamen zijn als volgt:

      * `insertParagraph`: De component wordt toegevoegd aan de pagina.
      * `removeParagraph`: de component wordt verwijderd.
      * `moveParagraph`: de alinea wordt naar een andere locatie verplaatst.
      * `updateParagraph`: De alinea-eigenschappen worden gewijzigd.

   * **Gebrek**: Het bezit wordt bevolkt met verscheidene componentenverrichtingen.
   * **Type**: `String[]`
