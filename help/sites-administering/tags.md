---
title: Tags beheren
seo-title: Tags beheren
description: Leer hoe u tags in AEM beheert.
seo-description: Leer hoe u tags in AEM beheert.
uuid: 77e1280a-feea-4edd-94b6-4fb825566c42
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
discoiquuid: 69253ee9-8c28-436b-9331-6fb875f64cba
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd
workflow-type: tm+mt
source-wordcount: '1769'
ht-degree: 0%

---


# Labels {#administering-tags} beheren

Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. U kunt ze beschouwen als trefwoorden of labels (metagegevens) waarmee inhoud sneller kan worden gevonden als resultaat van een zoekopdracht.

In Adobe Experience Manager (AEM) kan een tag een eigenschap zijn van

* een inhoudsknooppunt voor een pagina (zie [Tags gebruiken](/help/sites-authoring/tags.md))

* een metagegevensknooppunt voor een element (zie [Metagegevens voor digitale elementen beheren](/help/assets/metadata.md))

Naast pagina&#39;s en elementen worden tags gebruikt voor AEM Communities-functies

* door gebruiker gegenereerde inhoud (zie [UGC-codes coderen)](/help/communities/tag-ugc.md)

* Middelen van Enablement (zie [Tagging Enablement Resources](/help/communities/functions.md#catalog-function))

## Tagkenmerken {#tag-features}

Enkele eigenschappen van markeringen binnen AEM omvatten:

* Tags kunnen in verschillende naamruimten worden gegroepeerd. Dergelijke hiërarchieën maken het mogelijk taxonomieën te bouwen. Deze taxonomieën zijn wereldwijd in AEM.
* De belangrijkste beperking voor nieuwe tags is dat deze uniek moeten zijn binnen een specifieke naamruimte.
* De titel van een tag mag geen scheidingstekens voor het pad van de tag bevatten (en deze worden ook niet weergegeven als deze aanwezig zijn)

   * dubbele punt `:` - hiermee definieert u de naamruimtetag
   * forward slash `/` - afbakent subtags

* Tags kunnen door auteurs en bezoekers van de site worden toegepast. Ongeacht de maker van de tags worden alle typen tags beschikbaar gemaakt voor selectie, zowel bij het toewijzen aan een pagina als bij het zoeken.
* Tags kunnen worden gemaakt en de bijbehorende taxonomie kan worden gewijzigd door leden van de groep &quot;tagbeheerders&quot; en leden die wijzigingsrechten hebben op `/content/cq:tags`.

   * Een tag die onderliggende tags bevat, wordt aangeduid als een containertag
   * Een tag die geen containertag is, wordt aangeduid als een bladtag
   * Een naamruimte van een tag is een bladtag of een containertag

* Tags worden door de [zoekcomponent](https://helpx.adobe.com/experience-manager/core-components/using/quick-search.html) gebruikt om het zoeken naar inhoud te vergemakkelijken.
* Tags worden gebruikt door de [Taser-component](https://helpx.adobe.com/experience-manager/core-components/using/teaser.html), die de labelcloud van een gebruiker controleert om doelinhoud te leveren.
* Als labelen een belangrijk aspect van uw inhoud is

   * zorg ervoor dat de labels worden verpakt met de pagina&#39;s die deze gebruiken
   * zorg ervoor [tagmachtigingen](#setting-tag-permissions) leestoegang inschakelen

## Tagingsconsole {#tagging-console}

De Tagingconsole wordt gebruikt om tags en hun taxonomieën te maken en te beheren. Een van de doelstellingen is om te voorkomen dat er veel gelijksoortige tags zijn die in wezen op hetzelfde betrekking hebben: bijvoorbeeld pagina&#39;s of schoeisel en schoenen.

Tags worden beheerd door groeperen in naamruimten, het gebruik van bestaande tags evalueren voordat u nieuwe tags maakt en opnieuw ordenen zonder dat de tag wordt losgekoppeld van de inhoud waarnaar momenteel wordt verwezen.

De tagconsole openen:

* op auteur
* aanmelden met beheerdersrechten
* van globale navigatie

   * select **`Tools`**
   * selecteren **`General`**
   * selecteren **`Tagging`**

![managing_tags_usingThetagasministrationconsole](assets/managing_tags_usingthetagasministrationconsolea.png)

### Een naamruimte maken {#creating-a-namespace}

Als u een nieuwe naamruimte wilt maken, selecteert u het pictogram **`Create Namespace`**.

De naamruimte is zelf een tag en hoeft geen subtags te bevatten. Als u echter een taxonomie wilt blijven maken, [maakt u subtags](#creating-tags). Dit kunnen bladtags of containertags zijn.

![chlimage_1-183](assets/chlimage_1-183a.png) ![creating_tags_andnamespaces](assets/creating_tags_andnamespacesa.png)

* **Titel**

   *(vereist)* Een weergavetoewijzing voor de naamruimte.

* **Naam**
   *(optioneel)* Een naam voor de naamruimte. Als er geen waarde wordt opgegeven, wordt een geldige knooppuntnaam gemaakt op basis van de titel. Zie [TagID](/help/sites-developing/framework.md#tagid).

* **Beschrijving**

   *(optioneel)* Een beschrijving van de naamruimte.

Zodra de vereiste informatie is ingevoerd

* Selecteer **Maken**

### Bewerkingen op codes {#operations-on-tags}

Als u een naamruimte of andere tag selecteert, worden de volgende bewerkingen beschikbaar gesteld:

* [Eigenschappen weergeven](#viewing-tag-properties)
* [Verwijzingen](#showing-tag-references)
* [Tag maken](#creating-tags)
* [Bewerken](#editing-tags)
* [Verplaatsen](#moving-tags)
* [Samenvoegen](#merging-tags)
* [Publicatie](#publishing-tags)
* [Publiceren ongedaan maken](#unpublishing-tags)
* [Verwijderen](#deleting-tags)

![chlimage_1-184](assets/chlimage_1-184.png)

Wanneer het browservenster niet breed genoeg is om alle pictogrammen weer te geven, worden de meest rechtse pictogrammen gegroepeerd onder een **`... More`**-pictogram. Hierin wordt een vervolgkeuzelijst van de verborgen bewerkingspictogrammen weergegeven wanneer deze zijn geselecteerd.

![chlimage_1-185](assets/chlimage_1-185.png)

### Een naamruimtetag selecteren {#selecting-a-namespace-tag}

Wanneer deze optie voor het eerst is geselecteerd en de naamruimte geen tags bevat, worden de eigenschappen rechts weergegeven, anders worden de onderliggende tags weergegeven. Elke geselecteerde tag geeft de tags in de tag weer of de eigenschappen ervan als deze geen onderliggende tags bevat.

Als u de tag voor bewerkingen wilt selecteren en meerdere selecties wilt maken, selecteert u alleen het pictogram naast de titel. Als u de titel selecteert, worden alleen eigenschappen weergegeven of wordt de tag geopend om de inhoud ervan weer te geven.

![chlimage_1-186](assets/chlimage_1-186.png) ![chlimage_1-187](assets/chlimage_1-187.png)

### Tageigenschappen {#viewing-tag-properties} weergeven

![chlimage_1-188](assets/chlimage_1-188.png)

Wanneer een naamruimte of andere tag wordt geselecteerd en u het pictogram **`View Properties`** selecteert, wordt informatie over `name`, het tijdstip van laatste bewerking en het aantal verwijzingen weergegeven. Indien gepubliceerd, de tijd het werd gepubliceerd en identiteitskaart van de uitgever wordt getoond. Deze informatie wordt in een kolom links van de tagkolommen weergegeven.

![chlimage_1-109](assets/chlimage_1-189.png)

### Tagverwijzingen tonen {#showing-tag-references}

![chlimage_1-190](assets/chlimage_1-190.png)

Als u een naamruimte of andere tag selecteert, wordt door het pictogram **References** de inhoud aangeduid waarop de tag is toegepast.

De eerste weergave is een aantal toegepaste labels.

![chlimage_1-111](assets/chlimage_1-191.png)

Als u de pijl rechts van de telling selecteert, worden de referentienamen weergegeven.

Het pad naar de verwijzing wordt als knopinfo weergegeven wanneer u de muisaanwijzer op een verwijzing plaatst.

![chlimage_1-112](assets/chlimage_1-192.png)

### Codes {#creating-tags} maken

![chlimage_1-193](assets/chlimage_1-193.png)

Wanneer een naamruimte of andere tag is geselecteerd (door het pictogram naast de titel te selecteren), kan een onderliggende tag voor de huidige tag worden gemaakt door het pictogram **`Create Tag`** te selecteren.

![chlimage_1-194](assets/chlimage_1-194.png)

* **Titel**
*(vereist) *Een weergavetotel voor de tag.

* **Naam**
* (optioneel) *Een naam voor de tag. Als er geen waarde wordt opgegeven, wordt een geldige knooppuntnaam gemaakt op basis van de titel. Zie [TagID](/help/sites-developing/framework.md#tagid).

* **Beschrijving**
* (optioneel) *Een beschrijving van de tag.

Zodra de vereiste informatie is ingevoerd

* Selecteer **Maken**

### Labels {#editing-tags} bewerken

![chlimage_1-195](assets/chlimage_1-195.png)

Wanneer een naamruimte of andere tag is geselecteerd, is het mogelijk de Titel, Beschrijving te wijzigen en de titel te lokaliseren door het pictogram **`Edit`**te selecteren.

Nadat de bewerkingen zijn aangebracht, selecteert u **Opslaan**.

Zie de sectie over [Tags beheren in verschillende talen](#managing-tags-in-different-languages) voor meer informatie over het toevoegen van taalvertalingen.

![chlimage_1-196](assets/chlimage_1-196.png)

### Labels {#moving-tags} verplaatsen

![chlimage_1-197](assets/chlimage_1-197.png)

Wanneer een naamruimte of een andere tag is geselecteerd en u het pictogram **`Move`** selecteert, kunnen tagbeheerders en ontwikkelaars de taxonomie opschonen door de tag naar een nieuwe locatie te verplaatsen of de naam ervan te wijzigen. Wanneer de geselecteerde tag een containertag is, worden bij het verplaatsen van de tag ook alle onderliggende tags verplaatst.

>[!NOTE]
>
>Aanbevolen wordt dat Auteurs alleen [edit](#editing-tags) de tag `title` mogen uitvoeren en geen tags mogen verplaatsen of hernoemen.

![chlimage_1-198](assets/chlimage_1-198.png)

* **Pad**

   *(Alleen-lezen)* Het huidige pad naar de geselecteerde tag.

* **Ga**
naar Bladeren naar het nieuwe pad waaronder u de tag wilt verplaatsen.

* **Als Naam wijzigen**
inAanvankelijk wordt de huidige 
`name`van de tag. Er kan een nieuwe `name`worden ingevoerd.

* selecteren **Opslaan**

### Codes {#merging-tags} samenvoegen

![chlimage_1-199](assets/chlimage_1-199.png)

U kunt tags samenvoegen wanneer een taxonomie duplicaten bevat. Wanneer label A wordt samengevoegd met label B, worden alle pagina&#39;s met label A getagd met label B en is label A niet meer beschikbaar voor auteurs.

Wanneer een naamruimte of andere tag is geselecteerd en u het pictogram **Samenvoegen** selecteert, wordt een deelvenster geopend waarin het pad waarin moet worden samengevoegd, kan worden geselecteerd.

![chlimage_1-200](assets/chlimage_1-200.png)

* **Pad**

   *(Alleen-lezen)* Het pad van de geselecteerde tag die moet worden samengevoegd met een andere tag.

* **Met Samenvoegen**
inBladeren selecteert u het pad van de tag waarin u wilt samenvoegen.

>[!NOTE]
>
>Na de samenvoeging bestaat het oorspronkelijk geselecteerde **pad** (vrijwel) niet meer.
>
>Wanneer een tag waarnaar wordt verwezen wordt verplaatst of samengevoegd, wordt de tag niet fysiek verwijderd, zodat verwijzingen behouden kunnen blijven.

### Codes {#publishing-tags} publiceren

![chlimage_1-201](assets/chlimage_1-201.png)

Als er een naamruimte of andere tag is geselecteerd, selecteert u het pictogram **Publiceren** om de tag te activeren in de publicatieomgeving. Net als bij pagina-inhoud wordt alleen de geselecteerde tag gepubliceerd, ongeacht of het een containertag is of niet.

Als u een taxonomie (een naamruimte en subtags) wilt publiceren, kunt u het beste een [pakket](/help/sites-administering/package-manager.md) van de naamruimte maken (zie [Taxonomy Root Node](/help/sites-developing/framework.md#taxonomy-root-node)). Zorg ervoor dat u [machtigingen ](#setting-tag-permissions) toepast op de naamruimte voordat u het pakket maakt.

### Publicatie van labels {#unpublishing-tags} ongedaan maken

![chlimage_1-202](assets/chlimage_1-202.png)

Wanneer een naamruimte of andere tag wordt geselecteerd en u het pictogram **Publiceren ongedaan maken** selecteert, wordt de tag in de ontwerpomgeving gedeactiveerd en uit de publicatieomgeving verwijderd. Net als bij de bewerking `Delete`als de geselecteerde tag een containertag is, worden alle onderliggende tags gedeactiveerd in de auteursomgeving en verwijderd uit de publicatieomgeving.

### Labels {#deleting-tags} verwijderen

![chlimage_1-203](assets/chlimage_1-203.png)

Wanneer een naamruimte of andere tag wordt geselecteerd en u het pictogram **Delete** selecteert, wordt de tag definitief verwijderd uit de auteursomgeving. Als de tag is gepubliceerd, wordt deze ook verwijderd uit de publicatieomgeving. Als de geselecteerde tag een containertag is, worden ook alle onderliggende tags verwijderd.

## Tagmachtigingen instellen {#setting-tag-permissions}

De toestemmingen van de markering zijn [&#39;veilig (door gebrek)&#39;](/help/sites-administering/production-ready.md); Een beste manier voor de publicatieomgeving waarvoor leesmachtigingen expliciet moeten worden toegestaan voor tags. Dit gebeurt in eerste instantie door een pakket van de tagnaamruimte te maken nadat de machtigingen bij de auteur zijn ingesteld en het pakket op alle publicatieinstanties te installeren.

* op auteurinstantie

   * aanmelden met beheerdersrechten
   * toegang krijgen tot de [Beveiligingsconsole](/help/sites-administering/security.md#accessing-user-administration-with-the-security-console);

      * blader bijvoorbeeld naar http://localhost:4502/useradmin
   * in de linkerruit, selecteer de groep (of de gebruiker) waarvoor [lees toestemming](/help/sites-administering/security.md#permissions) moet worden verleend
   * Zoek in het rechterdeelvenster het **Pad **naar de tagnaamruimte

      * bijvoorbeeld `/content/cq:tags/mycommunity`
   * Selecteer `checkbox`in **Read** kolom
   * selecteren **Opslaan**



![chlimage_1-204](assets/chlimage_1-204.png)

* ervoor zorgen dat alle publicatieexemplaren dezelfde machtigingen hebben

   * één methode is om een pakket[ van de naamruimte bij de auteur te maken](/help/sites-administering/package-manager.md#package-manager)

      * op `Advanced` tab, voor `AC Handling` selecteer `Overwrite`
   * het pakket herhalen

      * kies `Replicate` uit pakketbeheer


## Tags beheren in verschillende talen {#managing-tags-in-different-languages}

De eigenschap `title`van een tag kan in meerdere talen worden vertaald. Nadat de code is vertaald, wordt mogelijk de juiste tag `title`weergegeven volgens de taal van de gebruiker of de paginataal.

### Tagtitels definiëren in meerdere talen {#defining-tag-titles-in-multiple-languages}

Hieronder wordt beschreven hoe u de `title`tag **Dieren** van het Engels omzet in het Duits en Frans.

Selecteer eerst de tag onder de naamruimte **Stock Photography** en selecteer het pictogram **`Edit`**I (zie [Codes bewerken](#editing-tags)).

In het deelvenster Tag bewerken kunt u talen kiezen waarin de titel van de tag moet worden gelokaliseerd.

Terwijl elke taal is geselecteerd, wordt een tekstinvoervak weergegeven waarin de vertaalde titel kan worden ingevoerd.

Wanneer alle vertalingen zijn ingevoerd, selecteert u **Opslaan** om de bewerkingsmodus af te sluiten.

![chlimage_1-205](assets/chlimage_1-205.png)

In het algemeen wordt de taal die voor de tag wordt gekozen, ontleend aan de paginataal, indien beschikbaar. Wanneer de [ `tag` widget](/help/sites-developing/building.md#tagging-on-the-client-side) in andere gevallen wordt gebruikt (bijvoorbeeld in formulieren of in dialoogvensters), hangt de labeltaal af van de context.

In plaats van de instelling voor de paginataal te gebruiken, gebruikt de Tagingconsole de taalinstelling van de gebruiker. In de Tagingconsole wordt voor de tag &#39;Dieren&#39; de tag &#39;Animaux&#39; weergegeven voor een gebruiker die de taal in zijn gebruikerseigenschappen instelt op Frans.

Als u een nieuwe taal wilt toevoegen aan het dialoogvenster, raadpleegt u [Een nieuwe taal toevoegen aan het dialoogvenster Tag bewerken](/help/sites-developing/building.md#adding-a-new-language-to-the-edit-tag-dialog).

>[!NOTE]
>
>De tagcloud en de metatrefwoorden in de standaardpaginacomponent gebruiken de gelokaliseerde tag `titles`gebaseerd op de paginataal, indien beschikbaar.

## Bronnen {#resources}

* [Tags voor ontwikkelaars](/help/sites-developing/tags.md)

   Informatie over het coderingskader en het uitbreiden en opnemen van codes in aangepaste toepassingen.

* [Klassieke UI-tagconsole](/help/sites-administering/classic-console.md)

