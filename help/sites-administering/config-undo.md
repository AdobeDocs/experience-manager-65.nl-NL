---
title: Ongedaan maken configureren voor paginabewerking
seo-title: Ongedaan maken configureren voor paginabewerking
description: Leer hoe u ondersteuning voor Ongedaan maken voor paginabewerking in AEM configureert.
seo-description: Leer hoe u ondersteuning voor Ongedaan maken voor paginabewerking in AEM configureert.
uuid: e5a49587-a2a6-41d5-b449-f7a8f7e4cee6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 3cc7efc5-bcb2-41c9-b78b-308f6b7a298e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---


# Ongedaan maken configureren voor paginabewerking{#configuring-undo-for-page-editing}

De [OSGi-service](/help/sites-deploying/configuring-osgi.md) **CQ-dag Ongedaan maken configuratie** ( `com.day.cq.wcm.undo.UndoConfigService`) stelt verschillende eigenschappen beschikbaar die het gedrag van de opdrachten Ongedaan maken en Opnieuw uitvoeren voor het bewerken van pagina&#39;s bepalen.

## Standaardconfiguratie {#default-configuration}

In een standaardinstallatie worden de standaardinstellingen gedefinieerd als eigenschappen op de `sling:OsgiConfig`node:

`/libs/wcm/core/config.author/com.day.cq.wcm.undo.UndoConfig`

Dit knooppunt bevat `cq.wcm.undo.whitelist`- en `cq.wcm.undo.blacklist`-eigenschappen. Voor de andere eigenschappen worden de standaardinstellingen gebruikt.

>[!CAUTION]
>
>U ***must*** verandert niets in `/libs` weg.
>
>Dit komt doordat de inhoud van `/libs` de volgende keer wordt overschreven dat u uw exemplaar bijwerkt (en dat kan worden overschreven wanneer u een hotfix- of functiepakket toepast).

## Ongedaan maken en Opnieuw configureren {#configuring-undo-and-redo}

U kunt deze OSGi de diensteigenschappen voor uw eigen instantie vormen.

>[!NOTE]
>
>Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [Het vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

De volgende lijst maakt een lijst van de eigenschappen zoals getoond in de console van het Web, die door de naam van de overeenkomstige parameter OSGi, samen met een beschrijving en de standaardwaarde (waar aangewezen) wordt gevolgd:

* **Enable**
() 
`cq.wcm.undo.enabled`)

   * **Omschrijving**: Hiermee wordt bepaald of auteurs van pagina&#39;s wijzigingen ongedaan kunnen maken en opnieuw kunnen uitvoeren.
   * **Standaard**:  `Selected`
   * **Type**:  `Boolean`

* **Path**
( 
`cq.wcm.undo.path`)

   * **Omschrijving**: Het repository pad voor het aanhouden van binaire gegevens voor ongedaan maken. Wanneer auteurs binaire gegevens zoals afbeeldingen wijzigen, blijft de oorspronkelijke versie van de gegevens hier behouden. Wanneer wijzigingen in binaire gegevens ongedaan worden gemaakt, worden deze binaire gegevens voor ongedaan maken hersteld naar de pagina.
   * **Standaard**:  `/var/undo`
   * **Type**:  `String`

   >[!NOTE]
   >
   >Standaard hebben alleen beheerders toegang tot het knooppunt `/var/undo`. Auteurs kunnen bewerkingen voor ongedaan maken en opnieuw uitvoeren op binaire inhoud alleen nadat zij machtigingen hebben gekregen om toegang te krijgen tot de binaire gegevens voor ongedaan maken.

* **Min. validity**
( 
`cq.wcm.undo.validity`)

   * **Omschrijving**: De minimale hoeveelheid tijd dat binair ongedaan maakt gegevens wordt opgeslagen, in uren. Na deze tijdsperiode, zijn de binaire gegevens beschikbaar voor schrapping, om schijfruimte te besparen.
   * **Standaard**:  `10`
   * **Type**:  `Integer`

* **Stappen**
( 
`cq.wcm.undo.steps`)

   * **Omschrijving**: Het maximumaantal paginahandelingen dat is opgeslagen in de historie voor ongedaan maken.
   * **Standaard**:  `20`
   * **Type**:  `Integer`

* **Persistence**
( 
`cq.wcm.undo.persistence`)

   * **Omschrijving**: De klasse die de historie ongedaan maakt. Er zijn twee persistentieklassen beschikbaar:

      * `CQ.undo.persistence.WindowNamePersistence`: Hiermee wordt de historie voortgezet met de eigenschap window.name.
      * `CQ.undo.persistence.CookiePersistance`: Houdt geschiedenis door het gebruiken van koekjes.
   * **Standaard**:  `CQ.undo.persistence.WindowNamePersistence`
   * **Type**:  `String`


* **Persistentiemodus**
( 
`cq.wcm.undo.persistence.mode`)

   * **Omschrijving**: Hiermee bepaalt u wanneer de historie ongedaan wordt gemaakt. Selecteer deze optie als u de historie voor ongedaan maken wilt behouden na elke paginabewerking. Schakel deze optie uit als u alleen wilt doorgaan wanneer een pagina opnieuw wordt geladen (de gebruiker navigeert bijvoorbeeld naar een andere pagina).

      Als u de historie voor ongedaan maken blijvend maakt, worden bronnen in de webbrowser gebruikt. Als de browser van uw gebruikers traag reageert op paginabewerkingen, probeert u de historie voor ongedaan maken bij het opnieuw laden van de pagina voort te zetten.

   * **Standaard**:  `Selected`
   * **Type**:  `Boolean`

* **Markeermodus**
( 
`cq.wcm.undo.markermode`)

   * **Omschrijving**: Hiermee wordt het visuele actiepunt opgegeven dat moet worden gebruikt om aan te geven welke alinea&#39;s worden beïnvloed wanneer een bewerking Ongedaan maken of Opnieuw wordt uitgevoerd. De volgende waarden zijn geldig:

      * flash: De selectie-indicator van de alinea&#39;s wordt tijdelijk knipperd.
      * selecteren: De alinea is geselecteerd.
   * **Standaard**:  `flash`
   * **Type**:  `String`


* **Goede componenten**
( 
`cq.wcm.undo.whitelist`)

   * **Omschrijving**: Een lijst met componenten die u wilt beïnvloeden door opdrachten voor ongedaan maken en opnieuw uitvoeren. Voeg componentpaden toe aan deze lijst wanneer deze correct werken met ongedaan maken/opnieuw uitvoeren. Een sterretje (&amp;ast;) toevoegen om een groep componenten op te geven:

      * Met de volgende waarde wordt de stichtingstekstcomponent opgegeven:

         `foundation/components/text`

      * Met de volgende waarde worden alle basiscomponenten opgegeven:

         `foundation/components/*`
   * Wanneer u een component die zich niet in deze lijst bevindt, ongedaan maakt of opnieuw uitvoert, wordt een bericht weergegeven dat aangeeft dat de opdracht onbetrouwbaar kan zijn.

   * **Standaard**: De eigenschap wordt gevuld met vele componenten die AEM bieden.
   * **Type**:  `String[]`


* **Ongeldige componenten**
( 
`cq.wcm.undo.blacklist`)

   * **Omschrijving**: Een lijst met componenten en/of componentbewerkingen die u niet wilt wijzigen door de opdracht Ongedaan maken. Voeg componenten en componentbewerkingen toe die zich niet correct gedragen met de opdracht Ongedaan maken:

      * Voeg een componentpad toe wanneer u geen bewerkingen van de component in de historie voor ongedaan maken wilt uitvoeren, bijvoorbeeld `collab/forum/components/post`
      * Voeg een dubbele punt (:) en een verrichting aan de weg toe wanneer u die specifieke verrichting wilt weglaten uit de undo geschiedenis (andere verrichtingen functioneren correct), bijvoorbeeld `collab/forum/components/post:insertParagraph.`

   >[!NOTE]
   >
   >Wanneer een bewerking in deze lijst staat, wordt deze nog toegevoegd aan de historie voor ongedaan maken. Gebruikers kunnen bewerkingen die eerder dan een bewerking **Onjuiste component** in de historie voor ongedaan maken bestaan, niet ongedaan maken.

   * De typische verrichtingsnamen zijn als volgt:

      * `insertParagraph`: De component wordt toegevoegd aan de pagina.
      * `removeParagraph`: De component wordt verwijderd.
      * `moveParagraph`: De alinea wordt naar een andere locatie verplaatst.
      * `updateParagraph`: De alinea-eigenschappen worden gewijzigd.
   * **Standaard**: De eigenschap wordt gevuld met verschillende componentbewerkingen.
   * **Type**:  `String[]`




