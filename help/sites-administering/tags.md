---
title: Tags beheren
description: Leer hoe u tags beheert en beheert in Adobe Experience Manager.
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
exl-id: ff041ef0-e566-4373-818e-76680ff668d8
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1769'
ht-degree: 0%

---

# Tags beheren {#administering-tags}

Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. U kunt ze beschouwen als trefwoorden of labels (metagegevens) waarmee inhoud sneller kan worden gevonden als resultaat van een zoekopdracht.

In Adobe Experience Manager (AEM) kan een tag een eigenschap zijn van

* een inhoudsknooppunt voor een pagina (zie [Tags gebruiken](/help/sites-authoring/tags.md))

* een metagegevensknooppunt voor een element (zie [Metagegevens voor digitale elementen beheren](/help/assets/metadata.md))

Naast pagina&#39;s en elementen worden tags gebruikt voor AEM Communities-functies

* door de gebruiker gegenereerde inhoud (zie [Tags (UGC)](/help/communities/tag-ugc.md)

* Bronnen voor Enablement (zie [Tags toewijzen](/help/communities/functions.md#catalog-function))

## Functies voor tags {#tag-features}

Enkele eigenschappen van markeringen binnen AEM omvatten:

* Tags kunnen in verschillende naamruimten worden gegroepeerd. Dergelijke hiërarchieën maken het mogelijk taxonomieën te bouwen. Deze taxonomieën zijn wereldwijd in AEM.
* De belangrijkste beperking voor nieuwe tags is dat deze uniek moeten zijn binnen een specifieke naamruimte.
* De titel van een tag mag geen scheidingstekens voor het pad van de tag bevatten (en deze worden ook niet weergegeven als deze aanwezig zijn)

   * colon `:` - Hiermee wordt de naamruimtetag afgebakend
   * slash `/` - subtags afbakenen

* Tags kunnen door auteurs en bezoekers van de site worden toegepast. Ongeacht de maker van de tags worden alle typen tags beschikbaar gemaakt voor selectie, zowel bij het toewijzen aan een pagina als bij het zoeken.
* Tags kunnen worden gemaakt en de bijbehorende taxonomie kan worden gewijzigd door leden van de groep &quot;tagbeheerders&quot; en leden die wijzigingsrechten hebben op `/content/cq:tags`.

   * Een tag die onderliggende tags bevat, wordt aangeduid als een containertag
   * Een tag die geen containertag is, wordt aangeduid als een bladtag
   * Een tagnaamruimte is een bladtag of een containertag

* Tags worden gebruikt door de [component Zoeken](https://helpx.adobe.com/experience-manager/core-components/using/quick-search.html) om het zoeken naar inhoud te vergemakkelijken.
* Tags worden gebruikt door de [Teaglascomponent](https://helpx.adobe.com/experience-manager/core-components/using/teaser.html), die de tagcloud van een gebruiker controleert om gerichte inhoud te bieden.
* Als labelen een belangrijk aspect van uw inhoud is

   * zorg ervoor dat de labels worden verpakt met de pagina&#39;s die deze gebruiken
   * zorg ervoor dat [tagmachtigingen](#setting-tag-permissions) lezen inschakelen

## Tagingsconsole {#tagging-console}

De Tagingconsole wordt gebruikt om tags en hun taxonomieën te maken en te beheren. Een van de doelstellingen is om te voorkomen dat er veel gelijksoortige tags zijn die in wezen op hetzelfde ding betrekking hebben, bijvoorbeeld pagina&#39;s en pagina&#39;s of schoeisel en schoenen.

Tags worden beheerd door groeperen in naamruimten, het gebruik van bestaande tags evalueren voordat u nieuwe tags maakt en opnieuw ordenen zonder dat de tag wordt losgekoppeld van de inhoud waarnaar momenteel wordt verwezen.

De tagconsole openen:

* op auteur
* aanmelden met beheerdersrechten
* van globale navigatie

   * selecteren **`Tools`**
   * selecteren **`General`**
   * selecteren **`Tagging`**

![managing_tags_usingThetagasministrationconsole](assets/managing_tags_usingthetagasministrationconsolea.png)

### Een naamruimte maken {#creating-a-namespace}

Als u een naamruimte wilt maken, selecteert u de **`Create Namespace`** pictogram.

De naamruimte is zelf een tag en bevat geen subtags. Om een taxonomie te blijven creëren, [subtags maken](#creating-tags), die op hun beurt ofwel bladtags of containercodes kunnen zijn.

![chlimage_1-183](assets/chlimage_1-183a.png) ![maken_tags_naamruimten](assets/creating_tags_andnamespacesa.png)

* **Titel**
  *(vereist)* Een weergavetitel voor de naamruimte.

* **Naam**
  *(optioneel)* Een naam voor de naamruimte. Als er geen waarde wordt opgegeven, wordt een geldige knooppuntnaam gemaakt op basis van de titel. Zie [TagID](/help/sites-developing/framework.md#tagid).

* **Beschrijving**
  *(optioneel)* Een beschrijving van de naamruimte.

Zodra de vereiste informatie is ingevoerd

* selecteren **Maken**

### Bewerkingen op codes {#operations-on-tags}

Als u een naamruimte of andere tag selecteert, worden de volgende bewerkingen beschikbaar gesteld:

* [Eigenschappen weergeven](#viewing-tag-properties)
* [Verwijzingen](#showing-tag-references)
* [Tag maken](#creating-tags)
* [Bewerken](#editing-tags)
* [Verplaatsen](#moving-tags)
* [Samenvoegen](#merging-tags)
* [Publiceren](#publishing-tags)
* [Publiceren ongedaan maken](#unpublishing-tags)
* [Verwijderen](#deleting-tags)

![chlimage_1-184](assets/chlimage_1-184.png)

Wanneer het browservenster niet breed genoeg is om alle pictogrammen weer te geven, worden de meest rechtse pictogrammen gegroepeerd onder een **`... More`** pictogram, dat een vervolgkeuzelijst weergeeft van de verborgen bewerkingspictogrammen wanneer deze zijn geselecteerd.

![chlimage_1-185](assets/chlimage_1-185.png)

### Een naamruimtetag selecteren {#selecting-a-namespace-tag}

Wanneer deze optie voor het eerst is geselecteerd en de naamruimte geen tags bevat, worden de eigenschappen rechts weergegeven, anders worden de onderliggende tags weergegeven. Elke geselecteerde tag geeft de tags in de tag weer of de eigenschappen ervan als deze geen onderliggende tags bevat.

Als u de tag voor bewerkingen wilt selecteren en meerdere selecties wilt maken, selecteert u alleen het pictogram naast de titel. Als u de titel selecteert, worden alleen eigenschappen weergegeven of wordt de tag geopend om de inhoud ervan weer te geven.

![chlimage_1-186](assets/chlimage_1-186.png) ![chlimage_1-187](assets/chlimage_1-187.png)

### Tageigenschappen weergeven {#viewing-tag-properties}

![chlimage_1-188](assets/chlimage_1-188.png)

Wanneer een naamruimte of andere tag is geselecteerd, selecteert u de opdracht **`View Properties`** resulteert in de weergave van informatie over de `name`, tijd van laatste bewerking en aantal verwijzingen. Indien gepubliceerd, wordt de tijd het laatst werd gepubliceerd en identiteitskaart van de uitgever getoond. Deze informatie wordt in een kolom links van de tagkolommen weergegeven.

![chlimage_1-189](assets/chlimage_1-189.png)

### Tagverwijzingen weergeven {#showing-tag-references}

![chlimage_1-190](assets/chlimage_1-190.png)

Wanneer een naamruimte of andere tag is geselecteerd, selecteert u de opdracht **Verwijzingen** geeft aan op welke inhoud de tag is toegepast.

De eerste weergave is een aantal toegepaste labels.

![chlimage_1-191](assets/chlimage_1-191.png)

Als u de pijl rechts van de telling selecteert, worden de referentienamen weergegeven.

Het pad naar de verwijzing wordt weergegeven als knopinfo wanneer u de muisaanwijzer op een verwijzing plaatst.

![chlimage_1-192](assets/chlimage_1-192.png)

### Tags maken {#creating-tags}

![chlimage_1-193](assets/chlimage_1-193.png)

Wanneer een naamruimte of andere tag is geselecteerd (door het pictogram naast de titel te selecteren), kan een onderliggende tag voor de huidige tag worden gemaakt door de optie **`Create Tag`** pictogram.

![chlimage_1-194](assets/chlimage_1-194.png)

* **Titel**
*(vereist) *A display title for the tag.

* **Naam**
*(optioneel) *Een naam voor de tag. Als er geen waarde wordt opgegeven, wordt een geldige knooppuntnaam gemaakt op basis van de titel. Zie [TagID](/help/sites-developing/framework.md#tagid).

* **Beschrijving**
*(optioneel) *Een beschrijving van de tag.

Zodra de vereiste informatie is ingevoerd

* selecteren **Maken**

### Tags bewerken {#editing-tags}

![chlimage_1-195](assets/chlimage_1-195.png)

Wanneer een naamruimte of andere tag is geselecteerd, is het mogelijk de Titel, Beschrijving te wijzigen en de titel te lokaliseren door ** te selecteren`Edit`**pictogram.

Nadat de bewerkingen zijn aangebracht, selecteert u **Opslaan**.

Zie de sectie over het toevoegen van taalvertalingen voor meer informatie over het toevoegen van taalvertalingen [Tags beheren in verschillende talen](#managing-tags-in-different-languages).

![chlimage_1-196](assets/chlimage_1-196.png)

### Labels verplaatsen {#moving-tags}

![chlimage_1-197](assets/chlimage_1-197.png)

Wanneer een naamruimte of andere tag is geselecteerd, selecteert u de opdracht **`Move`** Met dit pictogram kunnen tagbeheerders en ontwikkelaars de taxonomie opschonen door de tag naar een nieuwe locatie te verplaatsen of de naam ervan te wijzigen. Wanneer de geselecteerde tag een containertag is, worden bij het verplaatsen van de tag ook alle onderliggende tags verplaatst.

>[!NOTE]
>
>Aanbevolen wordt dat auteurs alleen toestemming krijgen om [bewerken](#editing-tags) de tag `title`, niet om tags te verplaatsen of te hernoemen.

![chlimage_1-198](assets/chlimage_1-198.png)

* **Pad**
  *(alleen-lezen)* Het huidige pad naar de geselecteerde tag.

* **Verplaatsen naar**
Blader naar het nieuwe pad waaronder u de tag wilt verplaatsen.

* **Naam wijzigen in**
Hiermee wordt de huidige `name`van de tag. Een nieuwe `name`kan worden ingevoerd.

* selecteren **Opslaan**

### Tags samenvoegen {#merging-tags}

![chlimage_1-199](assets/chlimage_1-199.png)

U kunt tags samenvoegen wanneer een taxonomie duplicaten bevat. Wanneer label A wordt samengevoegd met label B, worden alle pagina&#39;s met label A getagd met label B en is label A niet meer beschikbaar voor auteurs.

Wanneer een naamruimte of andere tag is geselecteerd, selecteert u de opdracht **Samenvoegen** wordt een deelvenster geopend waarin het pad waarin u wilt samenvoegen, kan zijn geselecteerd.

![chlimage_1-200](assets/chlimage_1-200.png)

* **Pad**
  *(alleen-lezen)* Het pad van de geselecteerde tag die moet worden samengevoegd met een andere tag.

* **Samenvoegen in**
Blader naar het pad van de tag waarin u wilt samenvoegen.

>[!NOTE]
>
>Na het samenvoegen **Pad** oorspronkelijk geselecteerd zal (vrijwel) niet meer bestaan.
>
>Wanneer een tag waarnaar wordt verwezen wordt verplaatst of samengevoegd, wordt de tag niet fysiek verwijderd, zodat verwijzingen behouden kunnen blijven.

### Codes publiceren {#publishing-tags}

![chlimage_1-201](assets/chlimage_1-201.png)

Wanneer een naamruimte of andere tag is geselecteerd, selecteert u de opdracht **Publiceren** pictogram om de tag te activeren in de publicatieomgeving. Net als bij pagina-inhoud wordt alleen de geselecteerde tag gepubliceerd, ongeacht of het een containertag is of niet.

Als u een taxonomie (een naamruimte en subtags) wilt publiceren, kunt u het beste een [package](/help/sites-administering/package-manager.md) van de naamruimte (zie [Taxonomy Root Node](/help/sites-developing/framework.md#taxonomy-root-node)). Zorg ervoor dat u [machtigingen toepassen](#setting-tag-permissions) naar de naamruimte voordat het pakket wordt gemaakt.

### Publicatie van labels ongedaan maken {#unpublishing-tags}

![chlimage_1-202](assets/chlimage_1-202.png)

Wanneer een naamruimte of andere tag is geselecteerd, selecteert u de opdracht **Publiceren ongedaan maken** wordt de tag in de ontwerpomgeving gedeactiveerd en uit de publicatieomgeving verwijderd. Vergelijkbaar met de `Delete`bewerking, als de geselecteerde tag een containertag is, worden alle onderliggende tags gedeactiveerd in de auteursomgeving en verwijderd uit de publicatieomgeving.

### Tags verwijderen {#deleting-tags}

![chlimage_1-203](assets/chlimage_1-203.png)

Wanneer een naamruimte of andere tag is geselecteerd, selecteert u de opdracht **Verwijderen** Het pictogram verwijdert de tag definitief uit de auteursomgeving. Als de tag is gepubliceerd, wordt deze ook verwijderd uit de publicatieomgeving. Als de geselecteerde tag een containertag is, worden ook alle onderliggende tags verwijderd.

## Tagmachtigingen instellen {#setting-tag-permissions}

Tagmachtigingen zijn [&#39;secure (by default)&#39;](/help/sites-administering/production-ready.md); dit is een aanbevolen werkwijze voor de publicatieomgeving waarvoor leesmachtigingen expliciet zijn toegestaan voor tags. Dit gebeurt in eerste instantie door een pakket van de tagnaamruimte te maken nadat de machtigingen bij de auteur zijn ingesteld en het pakket op alle publicatieinstanties te installeren.

* op instantie van auteur

   * aanmelden met beheerdersrechten
   * toegang tot [Beveiligingsconsole](/help/sites-administering/security.md#accessing-user-administration-with-the-security-console),

      * blader bijvoorbeeld naar http://localhost:4502/useradmin

   * in het linkerdeelvenster selecteert u de groep (of gebruiker) waarvoor [leesmachtiging](/help/sites-administering/security.md#permissions) wordt verleend
   * Zoek in het rechterdeelvenster het **Pad **naar de tagnaamruimte

      * bijvoorbeeld: `/content/cq:tags/mycommunity`

   * Selecteer de `checkbox`in de **Lezen** kolom
   * selecteren **Opslaan**

![chlimage_1-204](assets/chlimage_1-204.png)

* ervoor zorgen dat alle publicatieexemplaren dezelfde machtigingen hebben

   * één aanpak is : [een pakket maken](/help/sites-administering/package-manager.md#package-manager) van de naamruimte bij de auteur

      * op `Advanced` tab, for `AC Handling` selecteren `Overwrite`

   * het pakket herhalen

      * kiezen `Replicate` vanuit pakketbeheer

## Tags beheren in verschillende talen {#managing-tags-in-different-languages}

De `title`De eigenschap van een tag kan in meerdere talen worden vertaald. Na de vertaling wordt de juiste tag `title`kan worden weergegeven volgens de taal van de gebruiker of de paginataal.

### Tagtitels definiëren in meerdere talen {#defining-tag-titles-in-multiple-languages}

Hieronder wordt beschreven hoe u de `title`van de tag **Dieren** van Engels naar Duits en Frans.

Begin door de markering onder te selecteren **Stock Photography** naamruimte en de ** selecteren`Edit`**pictogram (zie [Tags bewerken](#editing-tags) ).

In het deelvenster Tag bewerken kunt u talen kiezen waarin de titel van de tag moet worden gelokaliseerd.

Terwijl elke taal is geselecteerd, wordt een tekstinvoervak weergegeven waarin de vertaalde titel kan worden ingevoerd.

Wanneer alle vertalingen zijn ingevoerd, selecteert u **Opslaan** om de bewerkingsmodus af te sluiten.

![chlimage_1-205](assets/chlimage_1-205.png)

In het algemeen wordt de taal die voor de tag wordt gekozen, ontleend aan de paginataal, indien beschikbaar. Wanneer de [`tag` widget](/help/sites-developing/building.md#tagging-on-the-client-side) wordt in andere gevallen gebruikt (bijvoorbeeld in formulieren of in dialoogvensters), is de taal van de tag afhankelijk van de context.

In plaats van de instelling voor de paginataal te gebruiken, gebruikt de Tagingconsole de taalinstelling van de gebruiker. In de Tagingconsole wordt voor de tag &#39;Dieren&#39; de tag &#39;Animaux&#39; weergegeven voor een gebruiker die de taal in zijn gebruikerseigenschappen instelt op Frans.

Als u een nieuwe taal wilt toevoegen aan het dialoogvenster, raadpleegt u [Een nieuwe taal toevoegen aan het dialoogvenster Tag bewerken](/help/sites-developing/building.md#adding-a-new-language-to-the-edit-tag-dialog).

>[!NOTE]
>
>De tagcloud en de metatrefwoorden in de standaardpaginacomponent gebruiken de gelokaliseerde tag `titles`op basis van de paginataal, indien beschikbaar.

## Bronnen {#resources}

* [Tags voor ontwikkelaars](/help/sites-developing/tags.md)

  Informatie over het coderingsframework en het uitbreiden en opnemen van codes in aangepaste toepassingen.

* [Klassieke UI-tagconsole](/help/sites-administering/classic-console.md)
