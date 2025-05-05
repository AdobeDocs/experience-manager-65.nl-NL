---
title: De vertaalintegratie configureren
description: Leer hoe u verbinding AEM maken met een vertaalservice.
exl-id: a1a4b1ca-d353-46e2-a992-f38be6be338e
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,Language Copy
role: Admin, Architect,Data Architect,Developer,User,Leader
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# De vertaalintegratie configureren {#configure-integration}

Leer hoe u verbinding AEM maken met een vertaalservice.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM hoofdloze vertaalreis, [ wordt begonnen met AEM hoofdloze vertaling ](learn-about.md) u leerde hoe te om uw inhoud zonder kop te organiseren en hoe AEM vertaalhulpmiddelen werken en u zou nu moeten:

* Begrijp het belang van inhoudsstructuur voor vertaling.
* Begrijp hoe AEM inhoud zonder kop opslaat.
* Wees vertrouwd met AEM vertaalhulpmiddelen.

Dit artikel bouwt op die grondbeginselen voort zodat kunt u de eerste configuratiestap nemen en de vertaaldienst opzetten, die u later in de reis zult gebruiken om uw inhoud te vertalen.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u een AEM integratie aan uw gekozen vertaaldienst plaatst. Na het lezen moet u:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

## Het vertaalintegratieframework {#tif}

AEM TIF (Translation Integration Framework) integreert met vertaalservices van derden om de vertaling van AEM inhoud te ordenen. Het gaat om drie basisstappen.

1. Maak verbinding met uw vertaalserviceprovider.
1. Creeer een configuratie van het Kader van de Integratie van de Vertaling.
1. Koppel de configuratie aan uw inhoud.

In de volgende secties worden deze stappen nader beschreven.

## Verbinding maken met een vertaalserviceprovider {#connect-translation-provider}

De eerste stap bestaat uit het kiezen van de vertaalservice die u wilt gebruiken. Er zijn vele keuzen voor mensen en machine vertaaldiensten beschikbaar aan AEM. De meeste providers bieden een vertaalpakket aan dat moet worden geïnstalleerd. Zie de [ Extra sectie van Middelen ](#additional-resources) voor een selectie van beschikbare opties.

>[!NOTE]
>
>De vertaalspecialist is over het algemeen verantwoordelijk voor het kiezen van welke vertaaldienst aan gebruik, maar de beheerder is typisch verantwoordelijk voor het installeren van het vereiste pakket van de vertaalschakelaar.

Voor deze reis gebruiken we de Microsoft-vertaler die een proeflicentie AEM aanbieden. Zie de [ Extra sectie van Middelen ](#additional-resources) voor meer informatie over deze leverancier.

Als u een andere leverancier kiest, moet uw beheerder het aansluitingspakket installeren volgens de instructies van de vertaalservice.

>[!NOTE]
>
>Het gebruik van de uit-van-de-doos Microsoft Vertaler in AEM vereist geen extra opstelling en werkt zoals-is zonder extra schakelaarconfiguratie.
>
>Als u verkiest om de Vertaalschakelaar van Microsoft voor het testen doeleinden te gebruiken, te hoeven u niet om de stappen in de volgende twee secties uit te voeren: [ Creërend een Configuratie van de Integratie van de Vertaling ](#create-config) en [ associeer de Configuratie met Uw Inhoud.](#associate) Nochtans wordt u geadviseerd om hen te lezen zodat u met de stappen vertrouwd bent voor wanneer u uw aangewezen schakelaar moet vormen.
>
>De proefvergunning van de Vertaalschakelaar van Microsoft is niet voorgenomen voor productiedoeleinden en als u besluit om het vergunning te geven, moet de systeembeheerder de stappen volgen die in de [ Extra sectie van Middelen ](#additional-resources) aan het eind van dit document worden gedetailleerd om die vergunning te vormen.

## Een configuratie voor vertaalintegratie maken {#create-config}

Nadat het schakelaarpakket voor uw aangewezen vertaaldienst wordt geïnstalleerd, moet u een configuratie van het Kader van de Integratie van de Vertaling voor die dienst tot stand brengen. De configuratie bevat de volgende informatie:

* Welke vertaalserviceprovider moet worden gebruikt?
* Of het vertalen van mensen of machines moet worden uitgevoerd
* Of andere inhoud die aan het inhoudsfragment is gekoppeld, zoals tags, moet worden vertaald

Een vertaalconfiguratie maken:

1. In het globale navigatiemenu, klik **Hulpmiddelen** > **Cloud Servicen** > **Cloud Servicen van de Vertaling**.
1. Navigeer naar de plaats waar u de configuratie in uw inhoudsstructuur wilt maken. Dit is vaak gebaseerd op een bepaald project of kan globaal zijn.
   * In dit geval zou een configuratie globaal kunnen worden gemaakt om op alle inhoud, of enkel voor het WKND project van toepassing te zijn.

   {de configuratielocatie van 0} Vertaling ![&#128279;](assets/translation-configuration-location.png)

1. Verstrek de volgende informatie op de gebieden en klik dan **creëren**.
   1. Selecteer **Type van Configuratie** in drop-down. Selecteer **Integratie van de Vertaling** van de lijst.
   1. Ga a **Titel** voor uw configuratie in. De **Titel** identificeert de configuratie in de **Cloud Servicen** console en in pagina bezit drop-down lijsten.
   1. Naar keuze, typ a **Naam** om voor de opslagplaats knoop te gebruiken die de configuratie opslaat.

   ![ creeer vertaalconfiguratie ](assets/create-translation-configuration.png)

1. Klik **creeer** en **geef het venster van de Configuratie** uit verschijnt waar u de configuratieeigenschappen kunt vormen.

1. Inhoudsfragmenten worden opgeslagen als elementen in AEM. Klik het **Assets** lusje.

![ de configuratieeigenschappen van de Vertaling ](assets/translation-configuration.png)

1. Geef de volgende informatie op.

   1. **Vertaalmethode** - selecteer **Vertaling van de Machine** of **Menselijke Vertaling** afhankelijk van uw vertaalleverancier. In het kader van deze reis gaan we uit van machinevertaling.
   1. **Vertaalleveranciers** - selecteer de schakelaar u voor uw vertaaldienst van de lijst installeerde.
   1. **Categorie van de Inhoud** - selecteer de meest aangewezen categorie om de vertaling (slechts voor machinevertaling) beter te richten.
   1. **vertaal het Fragment van de Inhoud Assets** - controleer dit om activa verbonden aan de Fragmenten van de Inhoud te vertalen.
   1. **vertaal Assets** - controleer dit om de activa te vertalen.
   1. **vertaal Meta-gegevens** - controleer dit om activa meta-gegevens te vertalen.
   1. **Vertaal Markeringen** - controleer dit om markeringen te vertalen die met de activa worden geassocieerd.
   1. **Auto-Uitvoer Vertaling** - controleer dit bezit als u vertalingen automatisch naar uw vertaaldienst wilt worden verzonden.

1. Klik **sparen &amp; Sluiten**.

U hebt nu de schakelaar aan uw vertaaldienst gevormd.

## De configuratie koppelen aan uw inhoud {#associate}

AEM is een flexibel en krachtig hulpmiddel en steunt veelvoudige, gelijktijdige vertaaldiensten via veelvoudige schakelaars en veelvoudige configuraties. Het opzetten van een dergelijke configuratie valt buiten het bereik van deze reis. Nochtans betekent deze flexibiliteit dat u moet specificeren welke schakelaars en configuratie zouden moeten worden gebruikt om uw inhoud te vertalen door deze configuratie met uw inhoud te associëren.

Navigeer hiertoe naar de hoofdtaalmap van de inhoud. Voor ons voorbeelddoel is dit

```text
/content/dam/<your-project>/en
```

1. Ga naar de globale navigatie en ga naar **Navigatie** > **Assets** > **Dossiers**.
1. In de activa console, selecteer de taalwortel om **Eigenschappen** te vormen en te klikken.
1. Klik de **Cloud Servicen** tabel.
1. Onder **Configuraties van de Cloud Service** in **voeg configuratie** dropdown toe, selecteer uw schakelaar. Het zou in dropdown moeten verschijnen wanneer u zijn pakket zoals [ eerder beschreven hebt geïnstalleerd.](#connect-translation-provider)
1. Onder **Configuraties van de Cloud Service** in **voeg configuratie** dropdown toe, selecteer ook uw configuratie.
1. Klik **sparen &amp; Sluiten**.

![ Uitgezochte configuraties van de wolkendienst ](assets/select-cloud-service-configurations.png)

## Volgende functies {#what-is-next}

Nu u dit deel van de reis zonder kop hebt voltooid, moet u:

* Begrijp de belangrijke parameters van het Kader van de Integratie van de Vertaling in AEM.
* Uw eigen verbinding met uw vertaalservice instellen.

Bouw op deze kennis voort en zet uw AEM hoofdloze vertaalreis door het document [ te herzien vorm vertaalregels, ](translation-rules.md) waar u zult leren hoe te om te bepalen welke inhoud te vertalen.

## Aanvullende bronnen {#additional-resources}

Terwijl wordt geadviseerd dat u zich op het volgende deel van de hoofdloze vertaalreis door het document [ te herzien vormt vertaalregels ](translation-rules.md) beweegt is het volgende wat extra, facultatieve middelen die een diepere duik op sommige concepten doen in dit document worden vermeld, maar zij worden niet vereist om op de hoofdloze reis verder te gaan.

* [ Vormend het Kader van de Integratie van de Vertaling ](/help/sites-administering/tc-tic.md) - herzie een lijst van geselecteerde vertaalschakelaars en leer hoe te om het Kader van de Integratie van de Vertaling te vormen om met derdevertaaldiensten te integreren.
* [ Verbonden met de Vertaler van Microsoft ](/help/sites-administering/tc-msconf.md) - AEM verstrekt een proefrekening van de Vertaling van Microsoft voor het testen doeleinden.
