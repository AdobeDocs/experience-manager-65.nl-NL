---
title: Vertaalregels configureren
description: Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren.
index: true
hide: false
hidefromtoc: false
source-git-commit: 7cf68868e0963930bde9fcda647822a03914b61d
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 0%

---

# Vertaalregels configureren {#configure-translation-rules}

Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM zonder kop [Vertaalaansluiting configureren](configure-connector.md) u leerde hoe te om uw vertaalschakelaar te installeren en te vormen en zou nu moeten:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

Nu uw schakelaar opstelling is, neemt dit artikel u door de volgende stap van het identificeren van welke inhoud u moet vertalen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u AEM vertaalregels kunt gebruiken om uw vertaalinhoud te identificeren. Nadat u dit document hebt gelezen, moet u:

* Begrijp wat de vertaalregels doen.
* U kunt uw eigen vertaalregels definiëren.

## Vertaalregels {#translation-rules}

Inhoudsfragmenten, die uw inhoud zonder kop vertegenwoordigen, kunnen veel informatie bevatten die is ingedeeld in gestructureerde velden. Afhankelijk van uw projectbehoeften is het waarschijnlijk dat niet alle velden in een inhoudsfragment moeten worden vertaald.

In de vertaalregels wordt aangegeven welke inhoud is opgenomen in of uitgesloten van vertaalprojecten. Wanneer de inhoud wordt vertaald, AEM de inhoud uitpakt of oogst die op deze regels wordt gebaseerd. Op die manier wordt alleen inhoud die moet worden vertaald naar de vertaaldienst verzonden.

De vertaalregels bevatten de volgende informatie:

* Het pad van de inhoud waarop de regel van toepassing is
   * De regel is ook van toepassing op de onderliggende elementen van de inhoud
* De namen van de eigenschappen die de te vertalen inhoud bevatten
   * Het bezit kan voor een specifiek middeltype of voor alle middeltypes specifiek zijn

Omdat de Modellen van het Fragment van de Inhoud, die de structuur van uw Inhoudsfragmenten bepalen, aan uw eigen project uniek zijn, is het essentieel aan opstellingsvertaalregels zodat AEM weet welke elementen van uw inhoudsmodellen om moeten vertalen.

>[!TIP]
>
>Over het algemeen biedt de architect van de inhoud de vertaler **Eigenschapnaam** s van alle velden die nodig zijn voor vertaling. Deze namen zijn nodig om vertaalregels te configureren. Als vertaler [kan deze vinden **Eigenschapnaam** zoals uzelf](getting-started.md#content-models) zoals eerder beschreven in deze reis.

## Vertaalregels maken {#creating-rules}

Er kunnen meerdere regels worden gemaakt ter ondersteuning van complexe vertaalvereisten. Het ene project waaraan u werkt, vereist bijvoorbeeld dat alle velden van het model worden vertaald, maar dat andere alleen beschrijvingsvelden worden vertaald terwijl titels niet worden vertaald.

De vertaalregels worden ontworpen om dergelijke scenario&#39;s te behandelen. Nochtans in dit voorbeeld illustreren wij hoe te om regels tot stand te brengen door zich op een eenvoudige, enige configuratie te concentreren.

Er is een **Configuratie vertaling** console beschikbaar voor het vormen van vertaalregels. Toegang tot dit bestand:

1. Navigeren naar **Gereedschappen** -> **Algemeen**.
1. Tik of klik op **Configuratie vertaling**.

In de **Configuratie vertaling** UI, zijn er een aantal opties beschikbaar voor uw vertaalregels. Hier benadrukken wij de meest noodzakelijke en typische stappen die voor een basisconfiguratie zonder kop worden vereist.

1. Tik of klik op **Context toevoegen**, waarmee u een pad kunt toevoegen. Dit is het pad van de inhoud waarop de regel van toepassing is.
   ![Context toevoegen](assets/add-translation-context.png)
1. Gebruik de padbrowser om het vereiste pad te selecteren en tik of klik op de knop **Bevestigen** op te slaan. Onthoud dat Content Fragments, die inhoud zonder kop bevatten, zich doorgaans onder `/content/dam/<your-project>`.
   ![Het pad selecteren](assets/select-context.png)
1. AEM slaat de configuratie op.
1. Selecteer de context die u zojuist hebt gemaakt en tik of klik op **Bewerken**. Hierdoor wordt het **Editor voor omzettingsregels** om de eigenschappen te configureren.
   ![Editor voor vertaalregels](assets/translation-rules-editor.png)
1. Standaard worden alle configuraties overgeërfd van het bovenliggende pad, in dit geval `/content/dam`. Schakel de optie uit **Overnemen van`/content/dam`** om extra gebieden aan de configuratie toe te voegen.
1. Als deze optie is uitgeschakeld, onder de knop **Algemeen** in de lijst, voegt u de eigenschapnamen toe van de Content Fragment Model(s) die u [eerder geïdentificeerd als velden voor vertaling.](getting-started.md#content-models)
   1. Voer de naam van de eigenschap in het dialoogvenster **Nieuwe eigenschap** veld.
   1. De opties **Vertalen** en **Overnemen** worden automatisch ingeschakeld.
   1. Tik of klik op **Toevoegen**.
   1. Herhaal deze stappen voor alle velden die u moet vertalen.
   1. Tik of klik op **Opslaan**.
      ![Eigenschap toevoegen](assets/add-property.png)

U hebt nu uw vertaalregels geconfigureerd.

## Geavanceerd gebruik {#advanced-usage}

Er zijn een aantal extra eigenschappen die als deel van uw vertaalregels kunnen worden gevormd. Bovendien kunt u uw regels handmatig als XML opgeven, waardoor meer specificiteit en flexibiliteit mogelijk zijn.

Dergelijke functies zijn meestal niet nodig om uw inhoud zonder kop te lokaliseren, maar u kunt er meer over lezen in het dialoogvenster [Aanvullende bronnen](#additional-resources) als u geïnteresseerd bent.

## Volgende functies {#what-is-next}

Nu u dit deel van de reis zonder kop hebt voltooid, moet u:

* Begrijp wat de vertaalregels doen.
* U kunt uw eigen vertaalregels definiëren.

Gebaseerd op deze kennis en doorgaan met uw AEM doorlopende vertaaltocht door het document opnieuw te bekijken [Inhoud vertalen](translate-content.md) waar u zult leren hoe uw schakelaar en regels samenwerken om hoofdloze inhoud te vertalen.

## Aanvullende bronnen {#additional-resources}

U kunt het beste naar het volgende gedeelte van de reis zonder kop gaan door het document te bekijken [Inhoud vertalen](translate-content.md)Hieronder volgt een aantal aanvullende, optionele bronnen die een diepgaander inzicht geven in bepaalde concepten die in dit document worden genoemd, maar die niet nodig zijn om verder te gaan op de weg zonder kop.

* [Te vertalen inhoud identificeren](/help/sites-administering/tc-rules.md) - Leer hoe vertaalregels inhoud identificeren die moet worden vertaald.
