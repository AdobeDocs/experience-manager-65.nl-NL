---
title: Starten gebruiken om inhoud voor een toekomstige release te ontwikkelen
description: Met Launches kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release. Met deze pagina's kunt u wijzigingen klaar maken voor toekomstige publicatie, terwijl uw huidige pagina's behouden blijven.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
exl-id: b25d3f8e-5687-49ab-95e1-19ec75c87f6e
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Launches
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 4%

---

# Lanceringen{#launches}

Met behulp van opstartprogramma&#39;s kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release.

A *Lancering* wordt gecreeerd om u toe te staan om veranderingen in voorbereiding op toekomstige publicatie aan te brengen, tezelfdertijd als het handhaven van uw huidige pagina&#39;s. Dit betekent dat u in feite twee versies tegelijk bewerkt: pagina&#39;s die momenteel worden gepubliceerd en een versie van deze pagina&#39;s die in de toekomst tegelijk worden gepubliceerd. Zodra dat tijdstip is bereikt, kunt u de originele pagina&#39;s vervangen en de nieuwe versie publiceren.

U creeert a *Lancering*, dan na het uitgeven en het bijwerken van uw *3&rbrace; pagina&#39;s van de Lancering &lbrace;u* bevordert *hen terug naar* Source *.* U kunt deze *Source* pagina&#39;s (top-level) dan activeren. Als u de opstartinhoud verhoogt, wordt deze teruggezet naar de bronpagina&#39;s en kan dit handmatig of automatisch gebeuren (afhankelijk van de velden die zijn ingesteld bij het maken en bewerken van de opstart).

De seizoensgebonden productpagina&#39;s van uw online winkel worden bijvoorbeeld elk kwartaal bijgewerkt, zodat de aanbevolen producten op één lijn komen met het huidige seizoen. Als u de volgende driemaandelijkse update wilt voorbereiden, kunt u de juiste webpagina&#39;s starten. In het hele kwartaal worden de volgende wijzigingen in de opstartafbeelding opgebouwd:

* Wijzigingen in de bronpagina&#39;s die optreden als gevolg van normale onderhoudstaken. Deze wijzigingen worden automatisch gedupliceerd op de startpagina&#39;s.
* Bewerkingen die rechtstreeks worden uitgevoerd op de startpagina&#39;s ter voorbereiding op het volgende kwartaal.

Wanneer het volgende kwartaal verschijnt, promoot u de startpagina&#39;s zodat u de bronpagina&#39;s kunt publiceren (met de bijgewerkte inhoud). U kunt alle pagina&#39;s of alleen de pagina&#39;s die u hebt gewijzigd, opwaarderen.

Launches kunnen ook:

* Gemaakt voor meerdere hoofdvertakkingen. Hoewel u de lancering voor de volledige plaats (en de veranderingen daar) kon tot stand brengen kan dit onpraktisch zijn aangezien de volledige plaats moet worden gekopieerd. Wanneer er honderden of zelfs duizenden pagina&#39;s bij betrokken zijn, worden de systeemvereisten en de prestaties beïnvloed door zowel de kopieeractie als later de vergelijkingen die vereist zijn voor de promotietaken.
* Genest (een lancering binnen een lancering) om u de capaciteit te geven om een lancering van een bestaande lancering tot stand te brengen zodat de auteurs van reeds aangebrachte veranderingen kunnen voordeel halen, eerder dan het moeten de zelfde veranderingen veelvoudige tijden voor elke lancering aanbrengen.

Deze sectie beschrijft om te creëren, uit te geven en te bevorderen (en indien nodig [&#x200B; schrapt &#x200B;](/help/sites-authoring/launches-creating.md#deleting-a-launch)) lanceringspagina&#39;s van binnen de console van Plaatsen of [&#x200B; de console van Lanceringen &#x200B;](#the-launches-console):

* [Starten maken](/help/sites-authoring/launches-creating.md)
* [Starten bewerken](/help/sites-authoring/launches-editing.md)
* [Starten promoten](/help/sites-authoring/launches-promoting.md)

## Starten - de volgorde van gebeurtenissen {#launches-the-order-of-events}

Met behulp van opstartprogramma&#39;s kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release van een of meer geactiveerde webpagina&#39;s.

Met Launches kunt u:

* Een kopie van de bronpagina&#39;s maken:

   * De kopie is uw lancering.
   * De bronpagina&#39;s op het hoogste niveau worden **Productie** genoemd.

      * De bronpagina&#39;s kunnen uit meerdere (afzonderlijke) vertakkingen worden genomen.

  ![&#x200B; Overzicht van lanceringsacties &#x200B;](assets/chlimage_1-111.png)

* De startconfiguratie bewerken:

   * Pagina&#39;s en/of vertakkingen toevoegen aan of verwijderen uit het opstarten.
   * Bewerk starteigenschappen, zoals markeringen voor **Titel**, **Startdatum**, **Geschikt voor productie**.

* U kunt de inhoud handmatig of automatisch publiceren:

   * Handmatig:

      * Bevestig uw lanceringsinhoud terug naar het **Doel** (bronpagina&#39;s) wanneer het klaar is om te worden gepubliceerd.
      * Publiceer de inhoud van de bronpagina&#39;s (na het promoten van de achterpagina&#39;s).
      * Alle pagina&#39;s of alleen gewijzigde pagina&#39;s promoten.

   * Automatisch - dit omvat het volgende:

      * Het **Lanceergebied** (**Levende**) **datum**: dit kan worden geplaatst wanneer het creëren van of het uitgeven van een lancering.

      * De **Klaar vlag van de Productie**: dit kan slechts worden geplaatst wanneer het uitgeven van een lancering.
      * Als de **Klaar van de Productie** vlag wordt geplaatst, zal de lancering automatisch aan de productiepagina&#39;s op de gespecificeerde **Lancering** worden bevorderd (**Levende**) **datum**. Na de promotie worden de productiepagina&#39;s automatisch gepubliceerd.\
        Als er geen datum is ingesteld, heeft de markering geen effect.

* Werk de bron- en startpagina&#39;s parallel bij:

   * Wijzigingen in de bronpagina&#39;s worden automatisch geïmplementeerd in de opstartafbeelding (als deze worden ingesteld op basis van overerving, dat wil zeggen als een live kopie).
   * U kunt wijzigingen aanbrengen in de opstartafbeelding zonder deze automatische updates of de bronpagina&#39;s te onderbreken.

  ![&#x200B; Overzicht van updates &#x200B;](assets/chlimage_1-112.png)

* [&#x200B; creeer een genestelde lancering &#x200B;](/help/sites-authoring/launches-creating.md#creating-a-nested-launch) - een lancering binnen een lancering:

   * De bron is een bestaande opstart.
   * U kunt [&#x200B; een genestelde lancering &#x200B;](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch) aan om het even welk doel bevorderen; dit kan een ouderlancering of de top-level bronpagina&#39;s (Productie) zijn.

  ![&#x200B; Overzicht van genestelde lancering &#x200B;](assets/chlimage_1-113.png)

  >[!CAUTION]
  >
  >Als u een opstart verwijdert, wordt de opstart zelf en alle afstammende geneste opstarties verwijderd.

>[!NOTE]
>
>Voor het maken en bewerken van startpagina&#39;s zijn toegangsrechten vereist voor `/content/launches` , net als voor de standaardgroep `content-authors` .
>
>Neem contact op met de systeembeheerder als u problemen ondervindt.

>[!CAUTION]
>
>Het opnieuw ordenen van componenten op een startpagina wordt niet ondersteund.
>
>Wanneer de pagina wordt bevorderd, zullen om het even welke inhoudveranderingen worden weerspiegeld, maar de componentenposities zullen niet veranderen.

## De opstartconsole {#the-launches-console}

De console van Lanceringen verstrekt een overzicht van uw lanceringen en laat u acties op die vermelde ondernemen. De console is toegankelijk via:

* De **Console van Hulpmiddelen**: **Hulpmiddelen**, **Plaatsen**, **Lanceringen**.

* Of direct met [&#x200B; https://localhost :4502 /libs/launches/content/launches.html &#x200B;](https://localhost:4502/libs/launches/content/launches.html)

## Starten in verwijzingen (siteconsole) {#launches-in-references-sites-console}

1. In de **console van Plaatsen**, navigeer aan de bron van lancering(en).
1. Open het **spoor van Verwijzingen** en selecteer de bronpagina.
1. Selecteer **Lanceringen**, zal de bestaande lancering(en) worden vermeld:

   ![&#x200B; lusje van de Verwijzing - Lanceringen &#x200B;](assets/screen-shot_2019-03-05at121901-1.png)

1. Klik op de juiste start en de lijst met mogelijke acties wordt weergegeven:

   ![&#x200B; Uitgezochte lancering om mogelijke acties te tonen &#x200B;](assets/screen-shot_2019-03-05at121952-1.png)
