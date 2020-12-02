---
title: Lanceringen
seo-title: Lanceringen
description: Met behulp van opstartprogramma's kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release. Met deze sjablonen kunt u wijzigingen klaar maken voor toekomstige publicatie, terwijl uw huidige pagina's behouden blijven
seo-description: Met behulp van opstartprogramma's kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release. Met deze sjablonen kunt u wijzigingen klaar maken voor toekomstige publicatie, terwijl uw huidige pagina's behouden blijven
uuid: 4bbd9865-735d-4232-b69c-b64193ac5d83
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: e145afd8-7391-47aa-b389-16fb303749d0
docset: aem65
translation-type: tm+mt
source-git-commit: 2d7492cdee9f7f730dfa6ad2ffae396b3a737b15
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 6%

---


# Lanceringen{#launches}

Met behulp van opstartprogramma&#39;s kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release.

Er wordt een lancering gecreeerd zodat u veranderingen klaar voor toekomstige publicatie kunt maken (terwijl het handhaven van uw huidige pagina&#39;s). Nadat u de startpagina&#39;s hebt bewerkt en bijgewerkt, publiceert u deze weer naar de bron en activeert u vervolgens de bronpagina&#39;s (hoofdniveau). Als u de opstartinhoud verhoogt, wordt deze teruggezet naar de bronpagina&#39;s en kan dit handmatig of automatisch gebeuren (afhankelijk van de velden die zijn ingesteld bij het maken en bewerken van de opstart).

De seizoensgebonden productpagina&#39;s van uw online winkel worden bijvoorbeeld elk kwartaal bijgewerkt, zodat de aanbevolen producten op één lijn komen met het huidige seizoen. Als u de volgende driemaandelijkse update wilt voorbereiden, kunt u de juiste webpagina&#39;s starten. In het hele kwartaal worden de volgende wijzigingen in de opstartafbeelding opgebouwd:

* Wijzigingen in de bronpagina&#39;s die optreden als gevolg van normale onderhoudstaken. Deze wijzigingen worden automatisch gedupliceerd op de startpagina&#39;s.
* Bewerkingen die rechtstreeks worden uitgevoerd op de startpagina&#39;s ter voorbereiding op het volgende kwartaal.

Wanneer het volgende kwartaal verschijnt, promoot u de startpagina&#39;s zodat u de bronpagina&#39;s kunt publiceren (met de bijgewerkte inhoud). U kunt alle pagina&#39;s of alleen de pagina&#39;s die u hebt gewijzigd, opwaarderen.

Launches kunnen ook:

* Gemaakt voor meerdere hoofdvertakkingen. Hoewel u de lancering voor de volledige plaats (en de veranderingen daar) kon tot stand brengen kan dit onpraktisch zijn aangezien de volledige plaats moet worden gekopieerd. Wanneer er honderden of zelfs duizenden pagina&#39;s bij betrokken zijn, worden de systeemvereisten en de prestaties beïnvloed door zowel de kopieeractie als later de vergelijkingen die vereist zijn voor de promotietaken.
* Genest (een lancering binnen een lancering) om u de capaciteit te geven om een lancering van een bestaande lancering tot stand te brengen zodat de auteurs van reeds aangebrachte veranderingen kunnen voordeel halen, eerder dan het moeten de zelfde veranderingen veelvoudige tijden voor elke lancering aanbrengen.

In deze sectie wordt beschreven hoe u startpagina&#39;s kunt maken, bewerken en promoten (en zo nodig [delete](/help/sites-authoring/launches-creating.md#deleting-a-launch)) vanuit de Sites-console of [de Launches-console](#the-launches-console):

* [Lanceringen maken](/help/sites-authoring/launches-creating.md)
* [Lanceringen bewerken](/help/sites-authoring/launches-editing.md)
* [Lanceringen promoten](/help/sites-authoring/launches-promoting.md)

## Starten - de volgorde van gebeurtenissen {#launches-the-order-of-events}

Met behulp van opstartprogramma&#39;s kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release van een of meer geactiveerde webpagina&#39;s.

Met Launches kunt u:

* Een kopie van de bronpagina&#39;s maken:

   * De kopie is uw lancering.
   * De bronpagina&#39;s op het hoogste niveau worden **Productie** genoemd.

      * De bronpagina&#39;s kunnen uit meerdere (afzonderlijke) vertakkingen worden genomen.

   ![chlimage_1-111](assets/chlimage_1-111.png)

* De startconfiguratie bewerken:

   * Pagina&#39;s en/of vertakkingen toevoegen aan of verwijderen uit het opstarten.
   * Bewerk starteigenschappen, zoals markeringen voor **Titel**, **Startdatum**, **Geschikt voor productie**.

* U kunt de inhoud handmatig of automatisch publiceren:

   * Handmatig:

      * Bevestig uw lanceringsinhoud terug naar **Doel** (bronpagina&#39;s) wanneer het klaar is om te worden gepubliceerd.
      * Publiceer de inhoud van de bronpagina&#39;s (na het promoten van de achterpagina&#39;s).
      * Alle pagina&#39;s of alleen gewijzigde pagina&#39;s promoten.
   * Automatisch - dit omvat het volgende:

      * Het **Launch**(**Live**) **date** veld: dit kan worden ingesteld wanneer u een opstart maakt of bewerkt.

      * De markering **Production Ready**: dit kan alleen worden ingesteld wanneer u een opstart bewerkt.
      * Als de markering **Production Ready** is ingesteld, wordt de lancering automatisch bevorderd tot de productiepagina&#39;s op de opgegeven **Launch**(**Live**) **date**. Na de promotie worden de productiepagina’s automatisch gepubliceerd.\
         Als er geen datum is ingesteld, heeft de markering geen effect.


* Werk de bron- en startpagina&#39;s parallel bij:

   * Wijzigingen in de bronpagina&#39;s worden automatisch geïmplementeerd in de opstartafbeelding (als deze zijn ingesteld op basis van overerving); d.w.z. als een live kopie).
   * U kunt wijzigingen aanbrengen in de opstartafbeelding zonder deze automatische updates of de bronpagina&#39;s te onderbreken.

   ![chlimage_1-112](assets/chlimage_1-112.png)

* [Een geneste opstart](/help/sites-authoring/launches-creating.md#creating-a-nested-launch)  maken - een opstart binnen een opstart:

   * De bron is een bestaande opstart.
   * U kunt een geneste opstart [promoten](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch) naar elk doel; Dit kan een bovenliggende opstart of de bronpagina&#39;s op het hoogste niveau (Productie) zijn.

   ![chlimage_1-113](assets/chlimage_1-113.png)

   >[!CAUTION]
   >
   >Als u een opstart verwijdert, wordt de opstart zelf en alle afstammende geneste opstarties verwijderd.

>[!NOTE]
>
>Voor het maken en bewerken van startpagina&#39;s zijn toegangsrechten vereist voor `/content/launches` - zoals bij de standaardgroep `content-authors`.
>
>Neem contact op met de systeembeheerder als u problemen ondervindt.

### De opstartconsole {#the-launches-console}

De console van Lanceringen verstrekt een overzicht van uw lanceringen en staat u toe om acties op die vermelde te voeren. De console is toegankelijk via:

* De console **Tools**: **Gereedschappen**, **Sites**, **Launches**.

* Of rechtstreeks met [https://localhost:4502/libs/launches/content/launches.html](https://localhost:4502/libs/launches/content/launches.html)

## Start in References (Sites Console) {#launches-in-references-sites-console}

1. Navigeer in de **Sites**-console naar de bron van de opstart(en).
1. Open **References** rail en selecteer de bronpagina.
1. Selecteer **Launches**, de bestaande lancering(en) zullen worden vermeld:

   ![screen-shot_2019-03-05at121901-1](assets/screen-shot_2019-03-05at121901-1.png)

1. Tik/klik op de gewenste opstart. De lijst met mogelijke acties wordt weergegeven:

   ![screen-shot_2019-03-05at121952-1](assets/screen-shot_2019-03-05at121952-1.png)
