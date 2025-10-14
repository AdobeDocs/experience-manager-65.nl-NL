---
title: Woordenboeken beheren met Vertaler
description: AEM biedt een console voor het beheer van de verschillende vertalingen van teksten die worden gebruikt in de gebruikersinterface van componenten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
exl-id: a8d50c09-72d0-406e-874e-50a985227a56
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '2318'
ht-degree: 0%

---

# Woordenboeken beheren met Vertaler{#using-translator-to-manage-dictionaries}

AEM biedt een console voor het beheer van de verschillende vertalingen van teksten die worden gebruikt in de gebruikersinterface van componenten. Deze console is beschikbaar op

`https://<hostname>:<port-number>/libs/cq/i18n/translator.html`

Gebruik het gereedschap Vertaler voor het beheren van Engelse tekenreeksen en de bijbehorende vertalingen. De woordenboeken worden gemaakt in de opslagplaats, bijvoorbeeld /apps/mijnproject/i18n.

Het gereedschap Vertaler en de woordenboeken die u beheert, zijn bedoeld voor het weergeven van de gebruikersinterface van de component in verschillende talen. Als u pagina of gebruiker geproduceerde inhoud wilt vertalen, zie [&#x200B; Vertaal Inhoud voor Meertalige Plaatsen &#x200B;](/help/sites-administering/translation.md) en [&#x200B; Vertaling van Gebruiker Gegenereerde Inhoud &#x200B;](/help/communities/translate-ugc.md).

>[!CAUTION]
>
>Bewerk alleen woordenboeken die voor uw project zijn gemaakt en zich onder `/apps` bevinden.
>
>AEM systeemwoordenboeken zijn ook beschikbaar in dit hulpmiddel. Wijzig de AEM systeemwoordenboeken niet omdat dit problemen kan veroorzaken met de interface van de AEM. Ook, kunnen de veranderingen bij verbetering worden verloren. AEM systeemwoordenboeken bevinden zich onder `/libs` .

>[!NOTE]
>
>Hoewel het Vertaalprogramma een klassieke interface UI heeft, wordt het gebruikt voor vertaling van uitdrukkingen ongeacht de interface waar die uitdrukkingen worden gevonden.

De vertaler geeft een overzicht van de teksten die in AEM met de verschillende taalvertalingen naast elkaar worden gebruikt:

![&#x200B; chlimage_1-205 &#x200B;](assets/chlimage_1-205.png)

U kunt de Engelse en vertaalde teksten zoeken, filteren en bewerken. U kunt woordenboeken ook exporteren naar de XLIFF-indeling om ze te vertalen en de vertalingen vervolgens weer importeren in de woordenboeken.

Het is ook mogelijk om de i18n-woordenboeken vanuit deze console toe te voegen aan een vertaalproject. U kunt een project maken of toevoegen aan een bestaand project.

1. Klik **Vertaal Woordenboek**.

   ![&#x200B; chlimage_1-206 &#x200B;](assets/chlimage_1-206.png)

1. Selecteer de optie Maken of Toevoegen, afhankelijk van uw behoefte. Er wordt een dialoogvenster geopend.

   ![&#x200B; chlimage_1-207 &#x200B;](assets/chlimage_1-207.png)

1. Vul de velden naar wens in en klik op OK. ![&#x200B; chlimage_1-208 &#x200B;](assets/chlimage_1-208.png)

1. U kunt **O.K.** nu klikken of het Woordenboek van het Doel zien.

   >[!NOTE]
   >
   >Voor meer informatie over vertaalprojecten, lees [&#x200B; het Leiden de Projecten van de Vertaling &#x200B;](/help/sites-administering/tc-manage.md).

## Woordenboek maken {#creating-a-dictionary}

Maak een woordenboek voor het beheer van uw gelokaliseerde UI-tekenreeksen. Nadat u een woordenboek hebt gemaakt, kunt u het gereedschap Vertaling gebruiken om het te beheren.

1. Met CRXDE Lite voegt u het basisknooppunt ( `sling:Folder` ) voor het nieuwe woordenboek toe als structuur voor de taaldefinities:

   ` /apps/<projectName>/i18n`

   Bijvoorbeeld: `/apps/myProject/i18n`

1. Voeg de vereiste taalstructuur toe onder deze hoofdmap. Bijvoorbeeld:

   ```shell
   /apps/myProject/i18n [sling:Folder]
       - de.json [nt:file] [mix:language]
           + jcr:language = de
       - fr.json [nt:file] [mix:language]
           + jcr:language = fr
   ```

   >[!NOTE]
   >
   >Dit is de structuur van de [&#x200B; Verschuivende i18n module &#x200B;](https://sling.apache.org/site/internationalization-support.html).

1. Het opnieuw laden van de vertaler en het woordenboekpad (bijvoorbeeld `/apps/myProject/i18n` ) is beschikbaar in de vervolgkeuzelijst op de werkbalk. Selecteer deze optie om tekenreeksen en de bijbehorende vertalingen toe te voegen.

   >[!NOTE]
   >
   >De vertaler slaat alleen vertalingen op voor talen die daadwerkelijk onder het pad staan (bijvoorbeeld `/apps/myProject/i18n` ).
   >
   >Zorg ervoor dat deze overeenkomen met de talen die worden weergegeven in het raster.

## Woordenboektekenreeksen beheren {#managing-dictionary-strings}

Gebruik het gereedschap Vertalen om de tekenreeksen in uw woordenboeken te beheren. U kunt Engelse tekenreeksen toevoegen, wijzigen en verwijderen en ook vertaalde tekenreeksen opgeven.

>[!CAUTION]
>
>Bewerk alleen woordenboeken die voor uw project zijn gemaakt en zich onder `/apps` bevinden.
>
>Wijzig de AEM systeemwoordenboeken niet omdat dit problemen kan veroorzaken met de interface van de AEM. Ook, kunnen de veranderingen bij verbetering worden verloren. AEM systeemwoordenboeken bevinden zich onder `/libs` .

### Tekenreeksen toevoegen, wijzigen en verwijderen {#adding-changing-and-removing-strings}

Voeg Engelse tekenreeksen toe aan een woordenboek dat door uw component is geïnternationaliseerd. Voeg alleen tekenreeksen toe die zijn geïnternationaliseerd, zodat u geen bronnen verspilt door tekenreeksen te vertalen die niet worden gebruikt.

De tekenreeksen die u aan een woordenboek toevoegt, moeten exact overeenkomen met de tekenreeks die in de code is opgegeven. Als de standaard Engelse tekenreeks die in de code wordt gebruikt, niet overeenkomt met de Engelse tekenreeks in een woordenboek, wordt de vertaalde tekenreeks niet weergegeven in de gebruikersinterface wanneer dat nodig is. Tekenreeksen zijn hoofdlettergevoelig.

**het verstrekken van Vertaalwenken**

Gebruik de eigenschap Commenet van de woordenboektekenreeks om de vertaler informatie te geven om de betekenis van de tekenreeks te verduidelijken. Doorgaans helpt de interface gebruikers de betekenis van dubbelzinnige woorden te bepalen. De vertaler ziet de tekenreeks echter niet binnen de context van de gebruikersinterface. De vertaalhint verwijdert de dubbelzinnigheid. Een opmerking helpt de vertaler bijvoorbeeld te begrijpen dat het Engelse woord Request wordt gebruikt als zelfstandig naamwoord in plaats van als werkwoord.

Vertaalhints maken ook onderscheid tussen tekenreeksen die identiek zijn en verschillende betekenissen hebben. Het woord Zoeken kan bijvoorbeeld een zelfstandig naamwoord of werkwoord zijn, waarvoor twee items in het woordenboek met twee verschillende vertaaltips moeten worden gezocht. De code die om het koord verzoekt omvat ook de vertaalwenk zodat het correcte koord in UI wordt gebruikt.

**met inbegrip van Geïndexeerde Variabelen**

Neem variabelen op in de gelokaliseerde tekenreeks om contextuele betekenis in een zin op te nemen. Nadat u zich bijvoorbeeld hebt aangemeld bij een webtoepassing, wordt op de homepage het bericht &quot;Welkom terug Administrator&quot; weergegeven. U hebt 2 berichten in uw Postvak IN.&quot; De paginacontext bepaalt de gebruikersnaam en het aantal berichten.

Om variabelen in het gelokaliseerde koord te omvatten, plaats gehaakte indexen bij de plaats van de variabelen in het eerste argument van de methode get. Gebruik de lokalisatiehint om de waarden te beschrijven. De vertaler moet de betekenis van de variabelen begrijpen omdat de verschillende talen verschillende zinsstructuren gebruiken.

Merk op dat [&#x200B; de code die om het vertaalde koord &#x200B;](/help/sites-developing/i18n-dev.md#including-variables-in-localized-sentences) verzoekt waarden voor de geïndexeerde variabelen volgens de context verstrekt.

De volgende tekenreeks wordt bijvoorbeeld weergegeven wanneer een gebruiker zich aanmeldt bij een website en wordt opgenomen in het woordenboek:

`Welcome back {0}. You have {1} messages.`

In de volgende opmerking worden de variabelen beschreven:

`{0} = the user name, {1} = the number of items in the user's inbox`

**het Wijzigen van Koorden**

Engelse tekenreeksen wijzigen of verwijderen wanneer deze worden gewijzigd of verwijderd in de code. Wanneer u een tekenreeks wijzigt, blijft de oorspronkelijke tekenreeks behouden en wordt een nieuwe tekenreeks gemaakt die de wijziging weerspiegelt. Voordat u een tekenreeks verwijdert, moet u ervoor zorgen dat deze door geen enkele code wordt gebruikt.

Gebruik de volgende procedure om een tekenreeks toe te voegen.

1. Selecteer in de vervolgkeuzelijst Woordenboeken het woordenboek waaraan u een tekenreeks toevoegt. In het vervolgkeuzemenu worden woordenboeken weergegeven door hun pad in de betreffende map.
1. Klik boven de tabel Tekenreeksen en vertalingen op Toevoegen.

   ![&#x200B; chlimage_1-209 &#x200B;](assets/chlimage_1-209.png)

1. Typ de Engelse tekenreeks in het vak Tekenreeks van het dialoogvenster Tekenreeks toevoegen. Typ indien nodig een vertaaltip voor de vertaler in het vak Opmerking.
1. Klik op OK.
1. Klik op Opslaan.

   ![&#x200B; chlimage_1-210 &#x200B;](assets/chlimage_1-210.png)

Gebruik de volgende procedure om een tekenreeks in een woordenboek te wijzigen.

1. Selecteer in het vervolgkeuzemenu Woordenboeken het woordenboek dat de tekenreeks bevat die u wilt wijzigen.
1. Dubbelklik op de tekenreeks die u wilt wijzigen.
1. Selecteer Tekenreeks of Opmerking wijzigen in het dialoogvenster Tekenreeks bewerken (er wordt een kopie gemaakt).

   ![&#x200B; chlimage_1-211 &#x200B;](assets/chlimage_1-211.png)

1. Wijzig de tekenreeks of de opmerking en klik op OK.
1. Klik op Opslaan.

   ![&#x200B; chlimage_1-212 &#x200B;](assets/chlimage_1-212.png)

Gebruik de volgende procedure om een tekenreeks uit een woordenboek te verwijderen.

1. Selecteer in het vervolgkeuzemenu Woordenboeken het woordenboek waaruit u een tekenreeks verwijdert.
1. Klik verwijderen.

   ![&#x200B; chlimage_1-213 &#x200B;](assets/chlimage_1-213.png)

1. Klik op Opslaan.

   ![&#x200B; chlimage_1-214 &#x200B;](assets/chlimage_1-214.png)

### Zoeken naar tekenreeksen {#searching-for-strings}

De zoekbalk onder aan het gereedschap Vertaler bevat opties voor tekenreeksselectie:

* **Filter door tekst:** een patroon om met het Engelse koord, de commentaar, of de vertalingen aan te passen. Alleen items die overeenkomen met het patroon of een deel ervan, worden weergegeven in de tabel.
* **Veranderingen: Om het even welk, Gewijzigd, Nieuw, Geschrapt:** toon punten die zijn veranderd en niet bewaard.

   * Willekeurig: items tonen die zijn gewijzigd, toegevoegd of verwijderd.
   * Gewijzigd: items tonen die zijn gewijzigd.
   * Nieuw: items tonen die zijn toegevoegd.
   * Verwijderd: items tonen die moeten worden verwijderd.
   * Meerdere selecties: items weergeven die alle geselecteerde eigenschappen hebben.

* **heeft Commentaar**: toon punten die commentaren voor vertalers hebben.
* **Ontbrekende Vertalingen:** toon punten waar minstens één taal geen vertaling heeft.

![&#x200B; chlimage_1-215 &#x200B;](assets/chlimage_1-215.png)

1. Selecteer de filteropties op de zoekbalk.
1. Klik op Filter om met de opties te filteren.
1. Klik op Wissen om de filters te verwijderen en alle items in het woordenboek weer te geven.

### Vertaalde tekenreeksen bewerken {#editing-translated-strings}

Nadat u de Engelse tekenreeks aan een woordenboek hebt toegevoegd, kunt u vertalingen van de tekenreeks toevoegen. U kunt [&#x200B; het woordenboek &#x200B;](/help/sites-developing/i18n-translator.md#exporting-a-dictionary) ook uitvoeren om het door een derde vertaald te hebben.

1. Selecteer [&#x200B; uw project specifieke woordenboek &#x200B;](#creating-a-dictionary) aangezien het de weg in de bewaarplaats die de vertalingen houdt specificeert. Bijvoorbeeld, selecteer **Woordenboeken** als:

   `/apps/myProject/i18n`

   >[!CAUTION]
   >
   >Bewerk alleen woordenboeken die voor uw project zijn gemaakt en zich onder `/apps` bevinden.
   >
   >AEM systeemwoordenboeken zijn ook beschikbaar in dit hulpmiddel. Wijzig de AEM systeemwoordenboeken niet omdat dit problemen kan veroorzaken met de interface van de AEM. Ook, kunnen de veranderingen bij verbetering worden verloren. AEM systeemwoordenboeken bevinden zich onder `/libs` .

1. Als u de vertaalde teksten voor een van de tekenreeksen wilt bewerken, kunt u:

   * Dubbelklik op de gewenste taal voor de vereiste tekenreeks om die ene tekst te bewerken:

   ![&#x200B; chlimage_1-216 &#x200B;](assets/chlimage_1-216.png)

   * Dubbelklik het **Koord** of **3&rbrace; gebieden van de Commentaar &lbrace;voor het vereiste koord om** te openen geef koord **dialoog uit, geef de vertaling(en) zoals vereist uit, dan klik O.K.** **om de dialoog te sluiten:**

   ![&#x200B; chlimage_1-217 &#x200B;](assets/chlimage_1-217.png)

1. Klik **sparen** in de toolbar om uw veranderingen vast te leggen.

   >[!NOTE]
   >
   >Het klikken op **Terugstellen &amp; verfrissen** (in plaats van **sparen**) keert om het even welke veranderingen in de vroegere teksten terug.

## Vertalers van derden gebruiken {#using-third-party-translators}

Ter ondersteuning van het gebruik van externe vertaalservices kunt u met het gereedschap Vertaling woordenboeken exporteren en importeren.

### Woordenboek exporteren {#exporting-a-dictionary}

Exporteer een woordenboek naar een XLIFF-bestand, zodat een service van derden de woordenboektekenreeksen kan vertalen.

* Exporteer een woordenboek en neem het Engels en de vertaalde termen voor een taal op.
* Exporteer enkele of alle Engelse tekenreeksen.

Wanneer u een XLIFF-bestand exporteert en een taal opneemt, moet de knooppuntstructuur van het woordenboek in de opslagplaats die taal bevatten. Als de taal niet is opgenomen, treden fouten op. Als u bijvoorbeeld het Franse XLIFF-bestand wilt exporteren, moet de map dictionary het onderliggende knooppunt `mix:language` met de naam `fr` bevatten. (Zie [&#x200B; Creërend een Woordenboek &#x200B;](/help/sites-developing/i18n-translator.md#creating-a-dictionary).)

Gebruik de volgende procedure om een XLIFF-bestand voor een bepaalde taal te exporteren.

1. Het gereedschap Vertalen openen `http://<host>:<port>/libs/cq/i18n/translator.html`
1. Gebruik het vervolgkeuzemenu Woordenboeken om het woordenboek te selecteren dat u wilt exporteren.
1. Klik de Uitvoer > de Volledige Opties van XX *Xliff van de Uitvoer, waar* XX *de tweelettertaalcode zoals DE of FR is.*

   Het XLIFF-bestand wordt geopend in een nieuw tabblad of venster.

1. Met de opdrachten van de webbrowser slaat u de pagina op als een bestand op uw bestandssysteem, bijvoorbeeld Bestand > Pagina opslaan als.

Gebruik de volgende procedure om alle of sommige van alleen de Engelse tekenreeksen te exporteren.

1. Open het gereedschap Vertalen. `http://<host>:<port>/libs/cq/i18n/translator.html`
1. Gebruik het vervolgkeuzemenu Woordenboeken om het woordenboek te selecteren dat u wilt exporteren.
1. Als u een subset van de tekenreeksen exporteert, selecteert u de items in het woordenboek die u wilt exporteren. Als u geen items selecteert, worden alle items geëxporteerd.
1. Klik op Exporteren > Selectie exporteren als XLIFF (alleen tekenreeksen).
1. Kopieer de tekst in het dialoogvenster dat verschijnt en plak deze in een tekstbestand.

### Woordenboek importeren {#importing-a-dictionary}

Importeer een XLIFF-bestand in een woordenboek om het woordenboek te vullen. Als het woordenboek een vertaling voor een Engelse tekenreeks bevat en het XLIFF-bestand een andere vertaling voor dezelfde tekenreeks bevat, wordt de woordenboekvertaling vervangen.

1. Het gereedschap Vertalen openen `http://<host>:<port>/libs/cq/i18n/translator.html`
1. Klik op Importeren > XLIFF-vertalingen.
1. Selecteer het te importeren bestand en klik op OK.

## Ondersteunde talen beheren {#managing-supported-lanuages}

Voeg of verwijder talen toe die het hulpmiddel van de Vertaling steunt en die aan gebruikers van uw Web-pagina&#39;s worden verstrekt.

### Talen wijzigen die in de tabel met woordenboeken worden vermeld {#changing-languages-listed-in-the-dictionary-table}

Het gereedschap Vertaler bevat de volgende talen in de woordenlijst:

* de - Duits
* fr - Frans
* it - Italiaans
* es - Spaans
* ja - Japans
* pt-br - Braziliaans Portugees
* zh-cn - Vereenvoudigd Chinees
* zh-tw - Traditioneel Chinees (beperkte ondersteuning)
* ko-kr - Koreaans

Gebruik de volgende procedure om talen toe te voegen of te verwijderen.

1. Maak een knooppunt met CRXDE Lite:

   `/etc/languages`

1. Voor deze knoop, creeer een bezit:

   * **Naam**: `languages`
   * **Type**: `Multi-String`
   * **Waarde**: de lijst van talen u getoond wilt. Bijvoorbeeld:

      * fr
      * es

   >[!NOTE]
   >
   >De taalcodes moeten in kleine letters worden geschreven.

1. Klik **sparen allen** in CRXDE Lite en herlaad de vertaler. Het raster wordt bijgewerkt om de gedefinieerde talen weer te geven.

   >[!NOTE]
   >
   >De vertaler zal slechts vertalingen voor talen bewaren die eigenlijk [&#x200B; in het woordenboek &#x200B;](#creating-a-dictionary) (namelijk onder de woordenboekweg zoals `/apps/myProject/i18n`) aanwezig zijn.
   >
   >Zorg ervoor dat deze overeenkomen met de talen die worden weergegeven in het raster.

### Talen beschikbaar maken voor auteurs {#making-languages-available-to-authors}

Na het bepalen van een woordenboek voor een taal nieuw aan uw AEM instantie moet u dit voor selectie door de auteurs (bijvoorbeeld, voor gebruik in **Voorkeur**) ter beschikking stellen:

1. Om de lijst van beschikbare talen te veranderen beschikbaar in **Voorkeur** van de **console van de Veiligheid**:

   1. Maak een bedekking in de toepassingscode voor:

      ```
              /libs/cq/security/widgets/source/widgets/security/Preferences.js
       and update as required.
      ```

1. Om de taal beschikbaar te maken in **Voorkeur** van de **&#x200B;**&#x200B;console van Websites moet u de volgende veranderingen in uw toepassing aanbrengen:

   1. Maak een bedekking voor de structuur onder:

      `/libs/cq/security/content/tools/userProperties`

   1. Werk de taallijst onder in de overlay bij:

      `items/common/items /lang/options`

1. Sla alles op en laad de juiste console opnieuw.

### Taalnamen en standaardlanden wijzigen {#changing-language-names-and-default-countries}

Verschillende landen gebruiken dezelfde taal, bijvoorbeeld de Verenigde Staten, het Verenigd Koninkrijk en Australië, allemaal Engels. Dit wordt aangegeven met een code die zowel taal als land aangeeft, zoals `en_US` , `en_GB` en `en_AU` .

De standaardlanden worden gebruikt wanneer het tonen van vlaggen (bijvoorbeeld, in de dialoog van het taalexemplaar), zij worden gebruikt om het land voor een taalcode op te lossen.

>[!NOTE]
>
>Voor lokalisaties die door de bovenstaande vertaler worden beheerd, werkt alleen de exacte taal. Als de taalvoorkeursvervolgkeuzelijst `en_uk` gebruikt, moet de gegevensopslagruimte een `en_uk` -woordenboek bevatten.

De standaarddefinities wijzigen:

1. Een taallijst wordt opgeslagen onder:

   `/libs/wcm/core/resources/languages`

   Bedek dit door het te kopiëren naar:

   `/apps/wcm/core/resources/languages`

   Vervolgens wijzigt of verlengt u de lijst daar. De eigenschap `defaultCountry` op een taalknooppunt (bijvoorbeeld `ja` ) moet de volledige code bevatten, zoals `ja_jp` , die `jp` zou definiëren als het standaardland voor de taal `ja` .

1. Werk de **Manager van de Taal van CQ WCM** bij.

   * **lijst van de Taal**:

     Het pad naar de taallijst in de opslagplaats. Stel deze in op de locatie die wordt gebruikt voor bedekking:

     ```
            /apps/wcm/core/resources/languages
     ```

   U kunt dit doen gebruikend de Console van het Web OSGi:

   ```shell
   https://<hostname>:<port-number>/system/console/configMgr/com.day.cq.wcm.core.impl.LanguageManagerImpl
   ```

## Woordenboeken publiceren {#publishing-dictionaries}

Neem uw woordenboeken op in het releasebeheerproces van uw AEM toepassingen. Neem bijvoorbeeld het woordenboek op in het inhoudspakket van uw toepassing voor implementatie op de publicatieinstantie. Deze strategie biedt de volgende voordelen:

* Er zijn woordenboeken beschikbaar voor componenten in de publicatieomgeving.
* Wijzigingen in de UI-tekenreeksen van componenten worden samen met de bijgewerkte vertalingen geïmplementeerd.

Ook het testen van woordenboektekenreeksen moet worden uitgevoerd als onderdeel van de normale ontwikkelingscyclus van software.

>[!NOTE]
>
>Gebruik geen normale publicatiefunctionaliteit, of replicatie, voor woordenboeken. In plaats daarvan moeten woordenboeken op dezelfde manier worden behandeld als code en configuratie. Dit omvat het gebruiken van broncontrole om veranderingen te volgen, en het gebruiken van inhoudspakketten om veranderingen op auteur toe te passen en te publiceren.

>[!NOTE]
>
>Wanneer het gebruiken van Dispatcher, moet u [&#x200B; ongeldig maken caching pagina&#39;s &#x200B;](https://helpx.adobe.com/nl/experience-manager/dispatcher/using/page-invalidate.html) om nieuwe dicationaire koorden in teruggegeven componentenkoorden te omvatten.
