---
title: Ga aan de slag met AEM-headless-vertaling
description: Lees hoe u uw inhoud zonder kop kunt ordenen en hoe de vertaalhulpmiddelen van AEM werken.
exl-id: 764f78a7-1d3d-4406-85b1-b80dffae2350
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,Language Copy
role: Admin, Developer, User, Leader
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '1472'
ht-degree: 0%

---

# Aan de slag met AEM Headless Translation {#getting-started}

Lees hoe u uw inhoud zonder kop kunt ordenen en hoe de vertaalhulpmiddelen van AEM werken.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de hoofdloze vertaalreis van AEM, [&#x200B; Leer over hoofdloze inhoud en hoe te in AEM &#x200B;](learn-about.md) te vertalen u de basistheorie van leerde wat een koploze CMS is en u zou nu moeten:

* Begrijp de basisconcepten van inhoud zonder kop levering.
* Wees vertrouwd met de manier waarop AEM ondersteuning biedt voor headless en translatie.

Dit artikel bouwt verder op deze basisbeginselen, zodat u begrijpt hoe AEM inhoud zonder kop opslaat en beheert en hoe u met de vertaalhulpmiddelen van AEM die inhoud kunt vertalen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u aan de slag kunt met het vertalen van inhoud zonder kop in AEM. Na het lezen moet u:

* Begrijp het belang van inhoudsstructuur voor vertaling.
* Begrijp hoe AEM inhoud zonder kop opslaat.
* Ben vertrouwd met de vertaalhulpmiddelen van AEM.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn verschillende vereisten waaraan u moet voldoen voordat u uw AEM-inhoud zonder koppen gaat vertalen.

### Kennis {#knowledge}

* Ervaar het vertalen van inhoud in een CMS
* Ervaar de basisfuncties van een grootschalig CMS
* Werken met AEM-basisverwerking
* Kennis van de vertaalservice die u gebruikt
* Basiskennis hebben van de inhoud die u wilt vertalen

>[!TIP]
>
>Als u niet vertrouwd met het gebruiken van een grootscale CMS zoals AEM bent, overweeg het herzien van de [&#x200B; Basis Behandelende &#x200B;](/help/sites-authoring/basic-handling.md) documentatie alvorens te werk te gaan. De documentatie van de Basisbehandeling maakt geen deel uit van de reis, zodat terugkeer aan deze pagina wanneer volledig.

### Gereedschappen {#tools}

* Sandbox-toegang voor het testen van het vertalen van uw inhoud
* Credentials om verbinding te maken met uw voorkeursvertaalservice
* Lid zijn van de `projects-administrators` -groep in AEM

## Structuur is sleutel {#content-structure}

AEM-inhoud, of het nu krantenloze of traditionele webpagina&#39;s zijn, wordt aangestuurd door de structuur ervan. AEM stelt weinig vereisten aan de inhoudsstructuur op, maar zorgvuldige overweging van uw inhoudshiërarchie als onderdeel van de projectplanning kan vertaling veel eenvoudiger maken.

>[!TIP]
>
>Plan voor vertaling bij het allereerste begin van het project zonder kop. Werk vroeg nauw samen met de projectmanager en de inhoudarchitecten.
>
>Een projectmanager voor internationalisatie kan worden verlangd als een aparte persoon die tot taak heeft te bepalen welke inhoud moet worden vertaald en wat niet, en welke vertaalde inhoud door regionale of lokale inhoudproducenten kan worden gewijzigd.

## Hoe AEM inhoud zonder kop opslaat {#headless-content-in-aem}

Voor de vertaalspecialist is het niet belangrijk om diepgaand te begrijpen hoe AEM inhoud zonder kop beheert. Het is echter handig om de basisbeginselen en -terminologie te kennen, aangezien u later vertaalhulpmiddelen voor AEM gebruikt. Het belangrijkste is dat u uw eigen inhoud begrijpt en hoe deze gestructureerd is om deze effectief te vertalen.

### Inhoudsmodellen {#content-models}

Om ervoor te zorgen dat inhoud zonder kop consistent wordt geleverd tussen kanalen, regio&#39;s en talen, moet de inhoud zeer gestructureerd zijn. AEM maakt gebruik van Content Models om deze structuur te handhaven. U kunt Content Models zien als een soort sjabloon of patroon voor het maken van inhoud zonder kop. Omdat elk project zijn eigen behoeften heeft, bepaalt elk project zijn eigen Modellen van het Fragment van de Inhoud. AEM heeft geen vaste eisen of structuur voor dergelijke modellen.

De inhoudarchitect werkt in een vroeg stadium van het project om deze structuur te definiëren. Als vertaler moet u nauw samenwerken met de inhoudarchitect om de inhoud te begrijpen en te ordenen.

>[!NOTE]
>
>Het is de verantwoordelijkheid van de inhoudarchitect om de inhoudsmodellen te definiëren. De vertaalspecialist mag alleen vertrouwd zijn met de structuur die in de volgende stappen wordt beschreven.

Omdat de inhoudsmodellen de structuur van uw inhoud bepalen, moet u weten welke gebieden van uw modellen moeten worden vertaald. In het algemeen werkt u met de inhoudarchitect om dit te definiëren. Volg onderstaande stappen om door de velden van uw inhoudsmodellen te bladeren.

1. Navigeer aan **Hulpmiddelen** > **Assets** > **Modellen van het Fragment van de Inhoud**.
1. Modellen van inhoudsfragmenten worden over het algemeen opgeslagen in een mapstructuur. Klik op de map voor uw project.
1. De modellen worden vermeld. Klik op het model om de details weer te geven.
   ![Modellen van contentfragmenten](assets/content-fragment-models.png)
1. De **ModelRedacteur van het Fragmentmodel van de Inhoud** opent.
   1. De linkerkolom bevat de velden van het model. Deze kolom interesseert ons.
   1. De rechterkolom bevat de velden die aan het model kunnen worden toegevoegd. Deze kolom kunnen wij negeren.
      ![&#x200B; de ModelRedacteur van het Fragment van de Inhoud &#x200B;](assets/content-fragment-model-editor.png)
1. Klik op een van de velden van het model. AEM markeert het en de details van dat gebied worden getoond in de juiste kolom.
   ![&#x200B; de details van de ModelRedacteur van het Fragment van de Inhoud &#x200B;](assets/content-fragment-model-editor-detail.png)

Neem nota van de naam van het gebied **Bezit** voor alle gebieden die moeten worden vertaald. U zult deze informatie later in de reis nodig hebben. Deze **Naam van het Bezit** wordt vereist om AEM mee te delen welke gebieden van uw inhoud moeten worden vertaald.

>[!TIP]
>
>Over het algemeen verstrekt de inhoudarchitect de vertaalspecialist van de **Naam van het Bezit** van alle gebieden die voor vertaling worden vereist. Deze veldnamen zijn nodig voor latere reizen. De voorafgaande stappen zijn bedoeld voor het begrijpen van de vertaalspecialist.

### Inhoudsfragmenten {#content-fragments}

Inhoudsmodellen worden door de auteurs van de inhoud gebruikt om de inhoud zonder kop te maken. Inhoudsauteurs selecteren op welk model ze hun inhoud willen baseren en maken vervolgens Inhoudsfragmenten. Inhoudsfragmenten zijn exemplaren van de modellen en vertegenwoordigen feitelijke inhoud die zonder kop moet worden geleverd.

Als Content Models de patronen voor de inhoud zijn, zijn de Content Fragments de daadwerkelijke inhoud die op die patronen wordt gebaseerd. De inhoudsfragmenten vertegenwoordigen de inhoud die moet worden vertaald.

Inhoudsfragmenten worden in AEM als elementen beheerd in het kader van DAM (Digital Asset Management). Dit is belangrijk omdat ze allemaal onder het pad `/content/dam` staan.

## Aanbevolen inhoudsstructuur {#recommended-structure}

Zoals eerder geadviseerd, werk met uw inhoudarchitect om de aangewezen inhoudsstructuur voor uw eigen project te bepalen. Het volgende is echter een bewezen, eenvoudige en intuïtieve structuur die heel effectief is.

Definieer een basismap voor uw project onder `/content/dam` .

```text
/content/dam/<your-project>
```

De taal waarin uw inhoud wordt geschreven wordt genoemd de taalwortel. In ons voorbeeld is het Engels en moet het onder dit pad liggen.

```text
/content/dam/<your-project>/en
```

Alle projectinhoud die mogelijk moet worden gelokaliseerd, moet onder de hoofdmap van de taal worden geplaatst.

```text
/content/dam/<your-project>/en/<your-project-content>
```

De vertalingen zouden als sibling omslagen naast de taalwortel met hun omslagnaam moeten worden gecreeerd die ISO-2 taalcode van de taal vertegenwoordigt. Duits zou bijvoorbeeld het volgende pad hebben.

```text
/content/dam/<your-project>/de
```

>[!NOTE]
>
>Over het algemeen is de inhoudsarchitect verantwoordelijk voor het maken van deze taalmappen. Als ze niet worden gecreëerd, kan AEM later geen vertaalbanen creëren.

De uiteindelijke structuur kan er ongeveer als volgt uitzien.

```text
/content
    |- dam
        |- your-project
            |- en
                |- some
                |- exciting
                |- headless
                |- content
            |- de
            |- fr
            |- it
            |- ...
        |- another-project
        |- ...
```

Let op het specifieke pad van uw inhoud, want dit zal later nodig zijn om uw vertaling te configureren.

>[!NOTE]
>
>Het is doorgaans de verantwoordelijkheid van de inhoudarchitect om de inhoudstructuur te definiëren, maar kan samenwerken met de vertaalspecialist.
>
>Het wordt hier nader toegelicht om de volledigheid te waarborgen.

## AEM-omzettingsgereedschappen {#translation-tools}

Nu u begrijpt wat Content Fragments zijn en hoe belangrijk de inhoudsstructuur is, kunnen we bekijken hoe we deze inhoud kunnen vertalen. De vertaalhulpmiddelen in AEM zijn vrij krachtig, maar zijn eenvoudig te begrijpen op hoog niveau.

* **Schakelaar van de Vertaling** - de schakelaar is het verband tussen AEM en de vertaaldienst die u gebruikt.
* **de Regels van de Vertaling** - bepaalt welke inhoud onder bijzondere wegen zou moeten worden vertaald.
* **de Projecten van de Vertaling** - De vertaalprojecten verzamelen inhoud die als één enkele vertaalinspanning zou moeten worden gericht en de vooruitgang van de vertaling volgen, die met de schakelaar omzet om de te vertalen inhoud over te brengen en het terug van de vertaaldienst te ontvangen.

U plaatst over het algemeen slechts eens opstelling uw schakelaar voor uw instantie en regels per headless project. Vervolgens gebruikt u vertaalprojecten om uw inhoud te vertalen en de vertalingen voortdurend bij te werken.

## Volgende functies {#what-is-next}

Nu u dit deel van de reis zonder kop hebt voltooid, moet u:

* Begrijp het belang van inhoudsstructuur voor vertaling.
* Begrijp hoe AEM inhoud zonder kop opslaat.
* Ben vertrouwd met de vertaalhulpmiddelen van AEM.

Bouw op deze kennis voort en ga uw de hoofdloze vertaalreis van AEM door het document [&#x200B; opnieuw te bekijken vormen de vertaalintegratie &#x200B;](configure-connector.md) waar u zult leren hoe te om AEM met de vertaaldienst te verbinden.|

## Aanvullende bronnen {#additional-resources}

Terwijl wordt geadviseerd dat u zich op het volgende deel van de hoofdloze vertaalreis door het document [&#x200B; te herzien de vertaalschakelaar &#x200B;](configure-connector.md) beweegt is het volgende wat extra, facultatieve middelen die een diepere duik op sommige concepten doen in dit document worden vermeld, maar zij worden niet vereist om op de headless reis verder te gaan.

* [&#x200B; Basisbehandeling van AEM &#x200B;](/help/sites-authoring/basic-handling.md) - leer de grondbeginselen van AEM UI om essentiële taken gemakkelijk te kunnen navigeren en uitvoeren zoals het vinden van uw inhoud.
* [&#x200B; identificerend Inhoud om &#x200B;](/help/sites-administering/tc-rules.md) te vertalen - leer hoe de vertaalregels inhoud identificeren die moet vertalen.
* [&#x200B; Vormend het Kader van de Integratie van de Vertaling &#x200B;](/help/sites-administering/tc-tic.md) - leer hoe te om het Kader van de Integratie van de Vertaling te vormen om met de diensten van de derdevertaling te integreren.
* [&#x200B; het Leiden Vertaalprojecten &#x200B;](/help/sites-administering/tc-manage.md) - leer hoe te om zowel machine als menselijke vertaalprojecten in AEM tot stand te brengen en te leiden.
* Een [&#x200B; Inleiding aan AEM als Headless CMS &#x200B;](/help/sites-developing/headless/introduction.md)
* Het [&#x200B; Portaal van de Ontwikkelaar van AEM &#x200B;](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [&#x200B; Leerprogramma&#39;s voor Zwaartepunt in AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)
