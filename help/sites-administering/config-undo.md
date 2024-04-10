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

De [OSGi-service](/help/sites-deploying/configuring-osgi.md)  **Configuratie Ongedaan maken CQ WCM-dag** ( `com.day.cq.wcm.undo.UndoConfigService`) bevat diverse eigenschappen die het gedrag bepalen van de opdrachten Ongedaan maken en Opnieuw voor het bewerken van pagina&#39;s.

## Standaardconfiguratie {#default-configuration}

In een standaardinstallatie worden de standaardinstellingen gedefinieerd als eigenschappen op de `sling:OsgiConfig`knooppunt:

`/libs/wcm/core/config.author/com.day.cq.wcm.undo.UndoConfig`

Dit knooppunt bevat `cq.wcm.undo.whitelist` en `cq.wcm.undo.blacklist` eigenschappen, voor de andere eigenschappen worden de standaardwaarden gebruikt.

>[!CAUTION]
>
>U ***moet*** niets wijzigen in het dialoogvenster `/libs` pad.
>
>Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven wanneer u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).

## Ongedaan maken en Opnieuw configureren {#configuring-undo-and-redo}

U kunt deze OSGi de diensteigenschappen voor uw eigen instantie vormen.

>[!NOTE]
>
>Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor meer details en de aanbevolen werkwijzen.

De volgende lijst maakt een lijst van de eigenschappen zoals getoond in de console van het Web, die door de naam van de overeenkomstige parameter OSGi, samen met een beschrijving en de standaardwaarde (waar aangewezen) wordt gevolgd:

* **Inschakelen**
( `cq.wcm.undo.enabled`)

   * **Beschrijving**: Hiermee wordt bepaald of auteurs van pagina wijzigingen ongedaan kunnen maken en opnieuw kunnen uitvoeren.
   * **Standaard**: `Selected`
   * **Type**: `Boolean`

* **Pad**
( `cq.wcm.undo.path`)

   * **Beschrijving**: Het opslagpad voor het blijvend binair ongedaan maken van gegevens. Wanneer auteurs binaire gegevens zoals afbeeldingen wijzigen, blijft de oorspronkelijke versie van de gegevens hier behouden. Wanneer wijzigingen in binaire gegevens ongedaan worden gemaakt, worden deze binaire gegevens voor ongedaan maken hersteld naar de pagina.
   * **Standaard**: `/var/undo`
   * **Type**: `String`

  >[!NOTE]
  >
  >Standaard hebben alleen beheerders toegang tot de `/var/undo` knooppunt. Auteurs kunnen bewerkingen voor ongedaan maken en opnieuw uitvoeren op binaire inhoud alleen nadat zij machtigingen hebben gekregen om toegang te krijgen tot de binaire gegevens voor ongedaan maken.

* **Min. geldigheid**
( `cq.wcm.undo.validity`)

   * **Beschrijving**: De minimale hoeveelheid tijd die binair ongedaan maakt gegevens wordt opgeslagen, in uren. Na deze tijdsperiode, zijn de binaire gegevens beschikbaar voor schrapping, om schijfruimte te besparen.
   * **Standaard**: `10`
   * **Type**: `Integer`

* **Stappen**
( `cq.wcm.undo.steps`)

   * **Beschrijving**: Het maximum aantal paginahandelingen dat is opgeslagen in de historie voor ongedaan maken.
   * **Standaard**: `20`
   * **Type**: `Integer`

* **Persistentie**
( `cq.wcm.undo.persistence`)

   * **Beschrijving**: De klasse die de historie ongedaan maakt. Er zijn twee persistentieklassen beschikbaar:

      * `CQ.undo.persistence.WindowNamePersistence`: Hiermee wordt de geschiedenis voortgezet met de eigenschap window.name.
      * `CQ.undo.persistence.CookiePersistance`: Houdt de geschiedenis vast met behulp van cookies.

   * **Standaard**: `CQ.undo.persistence.WindowNamePersistence`
   * **Type**: `String`

* **Persistentie, modus**
( `cq.wcm.undo.persistence.mode`)

   * **Beschrijving**: hiermee wordt bepaald wanneer de historie ongedaan wordt gemaakt. Selecteer deze optie als u de historie voor ongedaan maken wilt behouden na elke paginabewerking. Schakel deze optie uit als u alleen wilt doorgaan wanneer een pagina opnieuw wordt geladen (de gebruiker navigeert bijvoorbeeld naar een andere pagina).

     Als u de historie voor ongedaan maken blijvend maakt, worden bronnen in de webbrowser gebruikt. Als de browser van uw gebruikers traag reageert op paginabewerkingen, probeert u de historie voor ongedaan maken bij het opnieuw laden van de pagina voort te zetten.

   * **Standaard**: `Selected`
   * **Type**: `Boolean`

* **Markeerteken, modus**
( `cq.wcm.undo.markermode`)

   * **Beschrijving**: Hiermee wordt de visuele actielijn opgegeven die moet worden gebruikt om aan te geven welke alinea&#39;s worden beïnvloed wanneer een bewerking Ongedaan maken of Opnieuw wordt uitgevoerd. De volgende waarden zijn geldig:

      * flash: de selectie-indicator van de alinea&#39;s wordt tijdelijk knipperd.
      * Selecteer: De alinea is geselecteerd.

   * **Standaard**: `flash`
   * **Type**: `String`

* **Goede componenten**
( `cq.wcm.undo.whitelist`)

   * **Beschrijving**: Een lijst met componenten waarop opdrachten voor Ongedaan maken en Opnieuw moeten worden toegepast. Voeg componentpaden toe aan deze lijst wanneer deze correct werken met ongedaan maken/opnieuw uitvoeren. Een sterretje (&amp;ast;) toevoegen om een groep componenten op te geven:

      * Met de volgende waarde wordt de stichtingstekstcomponent opgegeven:

        `foundation/components/text`

      * Met de volgende waarde worden alle basiscomponenten opgegeven:

        `foundation/components/*`

   * Wanneer u een component die zich niet in deze lijst bevindt, ongedaan maakt of opnieuw uitvoert, wordt een bericht weergegeven dat aangeeft dat de opdracht onbetrouwbaar kan zijn.

   * **Standaard**: De eigenschap wordt gevuld met vele componenten die AEM bieden.
   * **Type**: `String[]`

* **Beschadigde componenten**
( `cq.wcm.undo.blacklist`)

   * **Beschrijving**: Een lijst met componenten en/of componentbewerkingen die u niet wilt wijzigen door de opdracht Ongedaan maken. Voeg componenten en componentbewerkingen toe die zich niet correct gedragen met de opdracht Ongedaan maken:

      * Voeg een componentpad toe wanneer u bijvoorbeeld geen bewerkingen van de component in de historie voor ongedaan maken wilt uitvoeren. `collab/forum/components/post`
      * Voeg een dubbele punt (:) en een verrichting aan de weg toe wanneer u die specifieke verrichting wilt weglaten uit undo geschiedenis (andere verrichtingen functioneren correct), bijvoorbeeld `collab/forum/components/post:insertParagraph.`

  >[!NOTE]
  >
  >Wanneer een bewerking in deze lijst staat, wordt deze nog toegevoegd aan de historie voor ongedaan maken. Gebruikers kunnen bewerkingen die eerder dan een **Ongeldige component** in de historie voor ongedaan maken.

   * De typische verrichtingsnamen zijn als volgt:

      * `insertParagraph`: De component wordt toegevoegd aan de pagina.
      * `removeParagraph`: De component wordt verwijderd.
      * `moveParagraph`: De alinea wordt verplaatst naar een andere locatie.
      * `updateParagraph`: De alinea-eigenschappen worden gewijzigd.

   * **Standaard**: De eigenschap wordt gevuld met verschillende componentbewerkingen.
   * **Type**: `String[]`
