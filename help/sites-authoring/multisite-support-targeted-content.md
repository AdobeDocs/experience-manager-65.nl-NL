---
title: Werken met getargete content in meerdere sites
seo-title: Werken met getargete content in meerdere sites
description: Als u gerichte inhoud, zoals activiteiten, ervaringen, en aanbiedingen tussen uw plaatsen moet beheren, kunt u uit AEM ingebouwde multisite steun voor gerichte inhoud voordeel halen
seo-description: Als u gerichte inhoud, zoals activiteiten, ervaringen, en aanbiedingen tussen uw plaatsen moet beheren, kunt u uit AEM ingebouwde multisite steun voor gerichte inhoud voordeel halen
uuid: acb2ffe1-d846-4580-bb69-d5af860796db
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 4dda6a03-d3ad-4e65-8b37-cee030fa4f7f
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '2906'
ht-degree: 5%

---


# Werken met getargete content in meerdere sites{#working-with-targeted-content-in-multisites}

Als u gerichte inhoud, zoals activiteiten, ervaringen, en aanbiedingen tussen uw plaatsen moet beheren, kunt u uit AEM ingebouwde multisite steun voor gerichte inhoud voordeel halen.

>[!NOTE]
>
>Het werken met ondersteuning voor meerdere sites voor doelgerichte inhoud is een geavanceerde functie. Als u deze functie wilt gebruiken, moet u bekend zijn met [Multi Site Manager](/help/sites-administering/msm.md) en de [Adobe Target-integratie](/help/sites-administering/target.md) met AEM.

In dit document wordt het volgende beschreven:

* Verstrekt een kort overzicht van AEM multisite steun voor gerichte inhoud.
* Beschrijft sommige mogelijke gebruiksscenario&#39;s op hoe u plaatsen (in één merk) kunt verbinden.
* Verstrekt een voorbeeldanalyse van hoe de marketers deze eigenschap zouden gebruiken.
* Gedetailleerde instructies voor het implementeren van ondersteuning voor meerdere sites voor gerichte inhoud.

Als u wilt instellen hoe uw sites gepersonaliseerde inhoud delen, moet u de volgende stappen uitvoeren:

1. [Maak een nieuw ](#creating-new-areas) gebied of  [maak een nieuw gebied als livekopie](#creating-new-areas). Een gebied omvat alle activiteiten die voor *gebied* van de pagina beschikbaar zijn; Dit is de locatie op de pagina waarop de component is aangewezen. Als u een nieuw gebied maakt, wordt een leeg gebied gemaakt, terwijl u door een nieuw gebied te maken als een live kopie inhoud kunt overnemen in de sitestructuren.

1. [Koppel uw site of ](#linking-sites-to-an-area) pagina aan een gebied.

U kunt de overerving op elk gewenst moment opschorten of herstellen. Als u de overerving niet wilt onderbreken, kunt u bovendien lokale ervaringen creëren. Standaard gebruiken alle pagina&#39;s het Master gebied, tenzij u anders opgeeft.

## Inleiding tot ondersteuning voor meerdere sites voor doelinhoud {#introduction-to-multisite-support-for-targeted-content}

De multisite steun voor gerichte inhoud is beschikbaar uit de doos en laat u gerichte inhoud van de master pagina duwen die u door MSM aan een lokale levende kopie beheert of laat u globale en lokale wijzigingen van dergelijke inhoud beheren.

U beheert dit in een **Gebied**. Gebieden scheiden gerichte inhoud (activiteiten, ervaringen en aanbiedingen) die in verschillende plaatsen wordt gebruikt en verstrekken een op MSM-Gebaseerd mechanisme om de overerving van gerichte inhoud samen met plaatsovererving tot stand te brengen en te beheren. Zo voorkomt u dat u doelgerichte inhoud in overgeërfde sites opnieuw moet maken, zoals was vereist vóór AEM 6.2.

In een gebied worden alleen activiteiten die met dat gebied verband houden, naar levende exemplaren geduwd. Standaard is het Master gebied geselecteerd. Nadat u aanvullende gebieden hebt gemaakt, kunt u deze koppelen aan uw sites of pagina&#39;s om aan te geven welke doelinhoud wordt geduwd.

Een site of live kopie is gekoppeld aan een gebied met de activiteiten die beschikbaar moeten zijn op die site of live kopie. De site of de live kopie maakt standaard koppelingen naar het master gebied, maar u kunt ook andere gebieden koppelen naast de master gebieden.

>[!NOTE]
>
>Houd rekening met het volgende wanneer u ondersteuning voor meerdere sites gebruikt voor specifieke inhoud:
>
>* Als u rollouts of live kopieën gebruikt, is een MSM-licentie vereist.
>* Wanneer u synchronisatie naar Adobe Target gebruikt, is een Adobe Target-licentie vereist.

>



## Gebruik gevallen {#use-cases}

U kunt ondersteuning voor meerdere sites instellen voor doelinhoud op verschillende manieren, afhankelijk van uw gebruiksscenario. In deze sectie wordt beschreven hoe dit theoretisch zou werken met één merk. Daarnaast wordt in [Voorbeeld: Als u inhoud aanwijst op basis van Geogrpahy](#example-targeting-content-based-on-geography), kunt u een echte toepassing zien voor het aanwijzen van inhoud op meerdere sites.

Gerichte inhoud wordt verpakt in zogenaamde gebieden, die het bereik voor sites of pagina&#39;s bepalen. Deze gebieden worden op merkniveau gedefinieerd. Eén merk kan meerdere gebieden bevatten. Gebieden kunnen verschillend zijn tussen merken. Hoewel één merk slechts het master gebied kan bevatten en daarom over alle merken wordt gedeeld, kan een ander merk meerdere merken bevatten (bijvoorbeeld per regio). Merkens hoeven dus niet de reeks gebieden ertussen te weerspiegelen.

Met multisite ondersteuning voor gerichte inhoud kunt u bijvoorbeeld twee (of meer) sites hebben met het merk **one** die een van de volgende kenmerken hebben:

* Een geheel *verschillende* reeks van gerichte inhoud - het uitgeven van gerichte inhoud in één beïnvloedt niet andere. Plaatsen die met verschillende gebieden verbinden lezen en schrijven aan hun eigen gevormde gebied. Bijvoorbeeld:

   * Site A verwijst naar gebied X
   * Site B-koppelingen naar gebied Y

* Een *gedeelde* set met doelinhoud - Het bewerken in één set heeft een directe invloed op beide sites. u kunt dit instellen door twee sites naar hetzelfde gebied te laten verwijzen. Sites die aan hetzelfde gebied zijn gekoppeld, delen de doelinhoud binnen dit gebied. Bijvoorbeeld:

   * Site A verwijst naar gebied X
   * Site B-koppelingen naar gebied X

* Een duidelijke reeks gerichte inhoud *geërft* van een andere plaats via MSM - de Inhoud kan unidirectioneel van master aan levende exemplaar worden uitgerold. Bijvoorbeeld:

   * Site A verwijst naar gebied X
   * Site B koppelt aan Gebied Y (dat een live kopie is van Gebied X)

U zou **veelvoudige** merken ook kunnen hebben die in één plaats worden gebruikt, die complexer zou kunnen zijn dan dit voorbeeld.

![chlimage_1-270](assets/chlimage_1-270.png)

>[!NOTE]
>
>Voor een meer technische blik bij deze eigenschap, zie [Hoe Multisite Beheer voor Gerichte Inhoud wordt gestructureerd](/help/sites-authoring/technical-multisite-targeted.md).

## Voorbeeld: Inhoud als doel instellen op basis van geografie {#example-targeting-content-based-on-geography}

Met multisite functionaliteit voor doelinhoud kunt u inhoud delen, implementeren of isoleren. Om beter te illustreren hoe deze eigenschap wordt gebruikt, overweeg een scenario waar u wilt controleren hoe de gerichte inhoud uit gebaseerd op geografie zoals in het volgende scenario wordt opgesteld:

Er zijn vier versies van dezelfde site op basis van geografie:

* De site **United States** bevindt zich in de linkerbovenhoek en is de master site. In dit voorbeeld is deze geopend in de modus Doel.
* De drie andere versies van deze site zijn **Canada**, **Groot-Brittannië** en **Australië**, die allemaal live kopieën zijn. Deze sites zijn geopend in de modus Voorbeeld.

![chlimage_1-271](assets/chlimage_1-271.png)

Elke site deelt gepersonaliseerde inhoud in geografische regio&#39;s:

* Canada deelt het master gebied met de Verenigde Staten.
* De grote Brit is verbonden met de Europese ruimte en erft van de master regio.
* Australië heeft zijn eigen gepersonaliseerde inhoud, omdat het zich op het zuidelijk halfrond bevindt en seizoensgebonden producten niet van toepassing zouden zijn.

![chlimage_1-272](assets/chlimage_1-272.png)

Voor het noordelijk halfrond hebben we een winteractiviteit gecreëerd, maar in het mannelijke publiek zou de marktmaker in Noord-Amerika een ander beeld voor de winter willen, dus hij of zij verandert het op de site van de Verenigde Staten.

![chlimage_1-273](assets/chlimage_1-273.png)

Nadat u het tabblad hebt vernieuwd, verandert de Canadese site in de nieuwe afbeelding zonder actie van onze kant. Dat gebeurt omdat het de master regio deelt met de Verenigde Staten. In de sites van Groot-Brittannië en Australië verandert het beeld niet.

![chlimage_1-274](assets/chlimage_1-274.png)

De markator wil deze wijzigingen in de Europese regio doorvoeren en [rolt de live kopie](/help/sites-administering/msm-livecopy.md) door te tikken of te klikken op **Uitrolpagina**. Na het vernieuwen van de tab heeft de site van Groot-Brittannië het nieuwe beeld dat het Europese gebied erft van het master gebied (na de uitrol).

![chlimage_1-275](assets/chlimage_1-275.png)

De afbeelding op de Australische site blijft ongewijzigd, wat het gewenste gedrag is, omdat het in de zomer in Australië is en de markeerteken die inhoud niet wil wijzigen. De site van Australië verandert niet omdat het een gebied niet deelt met een andere regio en het ook geen live kopie van een andere regio is. De marketeter hoeft zich nooit zorgen te maken dat de doelinhoud van de Australische site wordt overschreven.

Bovendien kunt u voor Groot-Brittannië, dat een live kopie van het master gebied is, de overervingsstatus zien door de groene indicator naast de naam van de activiteit. Als een activiteit wordt geërft, kunt u het niet wijzigen tenzij u onderbreekt of de levende kopie loskoppelt.

U kunt de overerving op elk gewenst moment opschorten of de overerving volledig loskoppelen. U kunt ook altijd lokale ervaringen toevoegen die alleen beschikbaar zijn voor die ervaring zonder de overerving op te schorten.

>[!NOTE]
>
>Voor een meer technische blik bij deze eigenschap, zie [Hoe Multisite Beheer voor Gerichte Inhoud wordt gestructureerd](/help/sites-authoring/technical-multisite-targeted.md).

### Een nieuw gebied maken in plaats van een nieuw gebied te maken als een livecopie {#creating-a-new-area-versus-creating-a-new-area-as-livecopy}

In AEM kunt u een nieuw gebied maken of nieuwe gebieden maken als een livecopy. Het creëren van een nieuw gebied groepeert activiteiten en om het even wat die tot die activiteiten behoren, zoals aanbiedingen, ervaringen, etc. U maakt een nieuw gebied als u een volledig aparte set doelinhoud wilt maken of als u een set doelinhoud wilt delen.

Als, echter, u erfenisopstelling via MSM tussen de twee plaatsen hebt, dan kunt u de activiteiten willen erven. In dit geval maakt u een nieuw gebied als een live kopie, waarbij Y een live kopie van X is en dus ook alle activiteiten overneemt.

>[!NOTE]
>
>De standaarduitrol activeert volgende uitrollingen van de doelinhoud wanneer een pagina een actieve kopie is die aan een gebied wordt gekoppeld dat zelf een actieve kopie is van het gebied dat aan de paginablauwdruk is gekoppeld.

In het volgende diagram zijn er bijvoorbeeld vier sites waar twee het master gebied delen (en alle activiteiten die deel uitmaken van dat gebied), één site die een gebied heeft dat een live kopie van een gebied is, zodat het de activiteiten deelt bij de uitrol, en één kant die volledig gescheiden is (en dus een gebied voor zijn activiteiten vereist).

![chlimage_1-276](assets/chlimage_1-276.png)

Om dit in AEM te bereiken, zou u het volgende doen:

* Site A is gekoppeld aan het Master gebied - er hoeft geen gebied te worden gemaakt. Master gebied is standaard in AEM geselecteerd. Site A en B delen activiteiten, enzovoort.
* Site B is gekoppeld aan het Master gebied - er hoeft geen gebied te worden gemaakt. Master gebied is standaard in AEM geselecteerd. Site A en B delen activiteiten, enzovoort.
* Site C koppelt aan Overgenomen gebied. Dit is een live kopie van het Master gebied - Gebied maken als actieve kopie waar u een live kopie maakt op basis van het Master gebied. Het overerfde Gebied erft activiteiten van het Master Gebied bij rollout.
* Site D maakt koppelingen naar een eigen geïsoleerd gebied - Maak een gebied waar u een geheel nieuw gebied maakt zonder activiteiten die nog niet zijn gedefinieerd. Het geïsoleerde gebied zal geen activiteiten met een andere plaats delen.

## Nieuwe gebieden maken {#creating-new-areas}

Gebieden kunnen activiteiten en aanbiedingen omvatten. Nadat u een gebied in één van beide (bijvoorbeeld, activiteiten) hebt gecreeerd, hebt u ook het gebied beschikbaar in andere (bijvoorbeeld, aanbiedingen).

>[!NOTE]
>
>Het standaardgebied genaamd Mastergebied wordt standaard samengevouwen wanneer u op de naam van een merk tikt of klikt **totdat** u een ander gebied maakt. Wanneer u vervolgens een merk selecteert in de console **Activiteit** of **Aanbiedingen**, ziet u de console **Gebied**.

Een nieuw gebied maken:

1. Ga naar **Personalisatie** > **Activiteiten** of **Aanbiedingen** en ga vervolgens naar uw merk.
1. Tik of klik op **Gebied maken**.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klik op het pictogram **Gebied** en klik op **Volgende**.
1. Voer in het veld **Titel** een naam in voor het nieuwe gebied. Selecteer optioneel tags.
1. Tik of klik op **Maken**.

   AEM wordt omgeleid naar het merkvenster, waar de gemaakte gebieden worden vermeld. Als er een ander gebied buiten het Master Gebied is, dan kunt u gebieden direct in de console van het Merk tot stand brengen.

   ![chlimage_1-278](assets/chlimage_1-278.png)

## Gebieden maken als actieve kopieën {#creating-areas-as-live-copies}

U maakt een gebied als een live kopie om de doelinhoud over te nemen in de sitestructuren.

Een gebied maken als een livecopy:

1. Ga naar **Personalisatie** > **Activiteiten** of **Aanbiedingen** en ga vervolgens naar uw merk.
1. Tik of klik op **Gebied maken als actieve kopie**.

   ![chlimage_1-279](assets/chlimage_1-279.png)

1. Selecteer het gebied waarvan u een live kopie wilt maken en klik op **Volgende**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Voer in het veld **Naam** een naam in voor de livekopie. Standaard worden subpagina&#39;s opgenomen. Sluit ze uit door het selectievakje **Subpagina&#39;s uitsluiten** in te schakelen.

   ![chlimage_1-281](assets/chlimage_1-281.png)

1. Selecteer de juiste configuratie in het vervolgkeuzemenu **Rollout Configs**.

   Zie [Geïnstalleerde Configuraties van de Uitvoer](/help/sites-administering/msm-sync.md#installed-rollout-configurations) voor beschrijvingen van elke optie.

   Zie [Actieve kopieën maken en synchroniseren](/help/sites-administering/msm-livecopy.md) voor meer informatie over actieve kopieën.

   >[!NOTE]
   >
   >Wanneer een pagina aan Levend Exemplaar wordt opgesteld en het gebied dat voor de pagina van de Vervaging wordt gevormd ook de Vervaging voor het gebied is dat voor Levende Exemplaar van Pagina&#39;s wordt gevormd, leidt LiveAction **personalizationContentRollout** tot een synchrone subRollout, die deel van **Standaard rollout config** uitmaakt.

1. Tik of klik op **Maken**.

   AEM wordt omgeleid naar het merkvenster, waar de gemaakte gebieden worden vermeld. Als er naast het Master gebied nog een gebied is, kunt u gebieden rechtstreeks vanuit het merkvenster maken.

   ![chlimage_1-282](assets/chlimage_1-282.png)

## Sites koppelen aan een gebied {#linking-sites-to-an-area}

U kunt gebieden koppelen aan pagina&#39;s of aan een site. Gebieden worden door alle subpagina&#39;s overgeërfd, tenzij deze pagina&#39;s worden overschreven door een toewijzing op een subpagina. Over het algemeen geldt echter dat u een koppeling tot stand brengt op het niveau van de site.

Als u een koppeling maakt, zijn alleen die activiteiten, ervaringen en aanbiedingen uit het geselecteerde gebied beschikbaar. Hiermee voorkomt u dat inhoud die onafhankelijk wordt beheerd, per ongeluk wordt gemengd. Als geen ander gebied wordt gevormd, wordt het master gebied van elk merk gebruikt.

>[!NOTE]
>
>Pagina&#39;s of sites die naar hetzelfde gebied verwijzen, gebruiken de *same* gedeelde set activiteiten, ervaringen en aanbiedingen. Het bewerken van een activiteit, ervaring of aanbieding die door meerdere sites wordt gedeeld, heeft invloed op alle sites.

Een site koppelen aan een gebied:

1. Navigeer naar de site (of pagina) die u wilt koppelen aan een gebied.
1. Selecteer de site of pagina en tik of klik op **Eigenschappen weergeven**.
1. Tik of klik op het tabblad **Personalisatie**.
1. Selecteer in het menu **Merk** het merk waaraan u het gebied wilt koppelen. Nadat u het merk hebt geselecteerd, zijn de beschikbare gebieden beschikbaar in het menu **Referentie gebied**.

   ![chlimage_1-283](assets/chlimage_1-283.png)

1. Selecteer het gebied in de vervolgkeuzelijst **Referentiegebied** en tik op **Opslaan** of klik op &lt;a2/>Opslaan.

   ![chlimage_1-284](assets/chlimage_1-284.png)

## Live kopie losmaken of overerving van doelinhoud {#detaching-live-copy-or-suspending-inheritance-of-targeted-content} opschorten

Mogelijk wilt u de overerving van de doelinhoud opschorten of loskoppelen. Het onderbreken of losmaken van de live kopie gebeurt per activiteit. Bijvoorbeeld, kunt u ervaringen in uw activiteit willen wijzigen, maar als die activiteit nog aan geërfte exemplaar verbonden is, kunt u niet de ervaring of om het even welke eigenschappen van de activiteit wijzigen.

Als u de live kopie tijdelijk opheft, wordt de overerving tijdelijk verbroken, maar in de toekomst kunt u de overerving herstellen. Als u de live kopie loskoppelt, wordt de overerving permanent verbroken.

U kunt de overerving van de doelinhoud onderbreken of loskoppelen door deze in een activiteit te herstellen. Als een pagina of site een koppeling bevat naar een gebied dat een live kopie is, kunt u de overervingsstatus van een activiteit weergeven.

Een activiteit die overerft van een andere site wordt groen gemarkeerd naast de naam van de activiteit. Een onderbroken overerving wordt rood gemarkeerd en een lokaal gemaakte activiteit heeft geen pictogram.

>[!NOTE]
>
>* U kunt actieve kopieën in een activiteit alleen opschorten of loskoppelen.
>* U hoeft live kopieën niet op te schorten of los te koppelen om een overgeërfde activiteit uit te breiden. U kunt **nieuwe** lokale ervaringen en aanbiedingen voor die activiteit altijd tot stand brengen. Als u een bestaande activiteit wilt wijzigen, dan moet u overerving opschorten.

>



### Opschorting van overerving {#suspending-inheritance}

Om erfenis van gerichte inhoud in een activiteit op te schorten of los te maken:

1. Navigeer naar de pagina waar u overerving los wilt maken of wilt onderbreken en tik of klik op **Doel** in het vervolgkeuzemenu van de modus.
1. Als de pagina is gekoppeld aan een gebied dat een live kopie is, ziet u de overervingsstatus. Tik of klik op **Doel starten**.
1. Voer een van de volgende handelingen uit om een activiteit op te schorten:

   1. Selecteer een element van de activiteit, zoals het publiek. AEM geeft automatisch een bevestigingsvenster voor Live kopie onderbreken weer. (U kunt livekopieën opschorten door tijdens het doelproces op een element te tikken of te klikken.)
   1. Selecteer **Live kopie onderbreken** in het keuzemenu op de werkbalk.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Tik of klik op **Onderbreken** om de activiteit op te schorten. Uitgestelde activiteiten worden rood gemarkeerd.

   ![chlimage_1-286](assets/chlimage_1-286.png)

### Overerving {#breaking-inheritance} breken

Overerving van doelinhoud in een activiteit onderbreken:

1. Navigeer naar de pagina waar u de live kopie van het master bestand wilt loskoppelen en tik of klik op **Doel** in het vervolgkeuzemenu Modus.
1. Als de pagina is gekoppeld aan een gebied dat een live kopie is, ziet u de overervingsstatus. Tik of klik op **Doel starten**.
1. Selecteer **Livekopie loskoppelen** in het vervolgkeuzemenu op de werkbalk. AEM bevestigt dat u de livekopie wilt loskoppelen.
1. Tik of klik op **Loskoppelen** om de actieve kopie los te koppelen van de activiteit. Nadat deze is losgekoppeld, wordt het vervolgkeuzemenu met betrekking tot overerving niet meer weergegeven. De activiteit is nu een lokale activiteit.

   ![chlimage_1-287](assets/chlimage_1-287.png)

## Overerving van doelinhoud {#restoring-inheritance-of-targeted-content} herstellen

Als u de overerving van de doelinhoud van een activiteit hebt opgeschort, kunt u deze op elk gewenst moment herstellen. Als u de live kopie echter hebt losgekoppeld, kunt u de overerving niet herstellen.

Om erfenis van gerichte inhoud in een activiteit te herstellen:

1. Navigeer naar de pagina waar u overerving wilt herstellen en tik of klik op **Doel** in het vervolgkeuzemenu van de modus.
1. Tik of klik op **Doel starten**.
1. Selecteer **Livekopie hervatten** in het vervolgkeuzemenu op de werkbalk.

   ![chlimage_1-288](assets/chlimage_1-288.png)

1. Tik of klik op **Hervatten** om te bevestigen dat u overerving van live kopiëren wilt hervatten. Eventuele wijzigingen aan de huidige activiteit gaan verloren als u de overerving hervat.

## Gebieden {#deleting-areas} verwijderen

Wanneer u een gebied verwijdert, verwijdert u alle activiteiten in dat gebied. AEM waarschuwt u alvorens u een gebied kunt schrappen. Als u een gebied verwijdert waaraan een site is gekoppeld, wordt de toewijzing voor dit merk automatisch opnieuw toegewezen aan het master gebied.

Een gebied verwijderen:

1. Navigeer naar **Personalisatie** > **Activiteiten** of **Aanbiedingen** en vervolgens naar uw merk.
1. Tik of klik op het pictogram naast het gebied dat u wilt verwijderen.
1. Tik of klik op **Verwijderen** en bevestig dat u het gebied wilt verwijderen.

