---
title: Starten gebruiken om inhoud voor een toekomstige release te ontwikkelen
description: Met Launches kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release. Met deze pagina's kunt u wijzigingen klaar maken voor toekomstige publicatie, terwijl uw huidige pagina's behouden blijven.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
exl-id: b25d3f8e-5687-49ab-95e1-19ec75c87f6e
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 6%

---

# Lanceringen{#launches}

Met behulp van opstartprogramma&#39;s kunt u op efficiënte wijze inhoud ontwikkelen voor een toekomstige release.

Er wordt een lancering gecreeerd zodat u veranderingen klaar voor toekomstige publicatie (terwijl het handhaven van uw huidige pagina&#39;s) kunt maken. Nadat u de startpagina&#39;s hebt bewerkt en bijgewerkt, publiceert u deze weer naar de bron en activeert u vervolgens de bronpagina&#39;s (hoofdniveau). Als u de opstartinhoud verhoogt, wordt deze teruggezet naar de bronpagina&#39;s en kan dit handmatig of automatisch gebeuren (afhankelijk van de velden die zijn ingesteld bij het maken en bewerken van de opstart).

De seizoensgebonden productpagina&#39;s van uw online winkel worden bijvoorbeeld elk kwartaal bijgewerkt, zodat de aanbevolen producten op één lijn komen met het huidige seizoen. Als u de volgende driemaandelijkse update wilt voorbereiden, kunt u de juiste webpagina&#39;s starten. In het hele kwartaal worden de volgende wijzigingen in de opstartafbeelding opgebouwd:

* Wijzigingen in de bronpagina&#39;s die optreden als gevolg van normale onderhoudstaken. Deze wijzigingen worden automatisch gedupliceerd op de startpagina&#39;s.
* Bewerkingen die rechtstreeks worden uitgevoerd op de startpagina&#39;s ter voorbereiding op het volgende kwartaal.

Wanneer het volgende kwartaal verschijnt, promoot u de startpagina&#39;s zodat u de bronpagina&#39;s kunt publiceren (met de bijgewerkte inhoud). U kunt alle pagina&#39;s of alleen de pagina&#39;s die u hebt gewijzigd, opwaarderen.

Launches kunnen ook:

* Gemaakt voor meerdere hoofdvertakkingen. Hoewel u de lancering voor de volledige plaats (en de veranderingen daar) kon tot stand brengen kan dit onpraktisch zijn aangezien de volledige plaats moet worden gekopieerd. Wanneer er honderden of zelfs duizenden pagina&#39;s bij betrokken zijn, worden de systeemvereisten en de prestaties beïnvloed door zowel de kopieeractie als later de vergelijkingen die vereist zijn voor de promotietaken.
* Genest (een lancering binnen een lancering) om u de capaciteit te geven om een lancering van een bestaande lancering tot stand te brengen zodat de auteurs van reeds aangebrachte veranderingen kunnen voordeel halen, eerder dan het moeten de zelfde veranderingen veelvoudige tijden voor elke lancering aanbrengen.

In deze sectie wordt beschreven hoe u (en indien nodig) [delete](/help/sites-authoring/launches-creating.md#deleting-a-launch)) pagina&#39;s starten vanuit de Sites-console of [de Startconsole](#the-launches-console):

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

  ![Overzicht van lanceeracties](assets/chlimage_1-111.png)

* De startconfiguratie bewerken:

   * Pagina&#39;s en/of vertakkingen toevoegen aan of verwijderen uit het opstarten.
   * Bewerk starteigenschappen, zoals markeringen voor **Titel**, **Startdatum**, **Geschikt voor productie**.

* U kunt de inhoud handmatig of automatisch publiceren:

   * Handmatig:

      * Bevestig uw opstartafhoud terug naar de **Doel** (bronpagina&#39;s) wanneer deze gereed is voor publicatie.
      * Publiceer de inhoud van de bronpagina&#39;s (na het promoten van de achterpagina&#39;s).
      * Alle pagina&#39;s of alleen gewijzigde pagina&#39;s promoten.

   * Automatisch - dit omvat het volgende:

      * De **Starten**(**Live**) **date** veld: deze kan worden ingesteld wanneer u een opstart maakt of bewerkt.

      * De **Gereed voor productie** markering: deze kan alleen worden ingesteld tijdens het bewerken van een opstart.
      * Als de **Gereed voor productie** markering is ingesteld, wordt de lancering automatisch bevorderd tot de productiepagina&#39;s op de opgegeven **Starten**(**Live**) **date**. Na de promotie worden de productiepagina’s automatisch gepubliceerd.\
        Als er geen datum is ingesteld, heeft de markering geen effect.

* Werk de bron- en startpagina&#39;s parallel bij:

   * Wijzigingen in de bronpagina&#39;s worden automatisch geïmplementeerd in de opstartafbeelding (als deze worden ingesteld op basis van overerving, dat wil zeggen als een live kopie).
   * U kunt wijzigingen aanbrengen in de opstartafbeelding zonder deze automatische updates of de bronpagina&#39;s te onderbreken.

  ![Overzicht van updates](assets/chlimage_1-112.png)

* [Een geneste start maken](/help/sites-authoring/launches-creating.md#creating-a-nested-launch) - een lancering binnen een lancering:

   * De bron is een bestaande opstart.
   * U kunt [een geneste introductie promoten](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch) naar elk doel; dit kan een bovenliggende opstart of de bronpagina&#39;s op het hoogste niveau (Productie) zijn.

  ![Overzicht van geneste lancering](assets/chlimage_1-113.png)

  >[!CAUTION]
  >
  >Als u een opstart verwijdert, wordt de opstart zelf en alle afstammende geneste opstarties verwijderd.

>[!NOTE]
>
>Voor het maken en bewerken van startpagina&#39;s zijn toegangsrechten vereist voor `/content/launches` - zoals bij de standaardgroep `content-authors`.
>
>Neem contact op met de systeembeheerder als u problemen ondervindt.

>[!CAUTION]
>
>Het opnieuw ordenen van componenten op een startpagina wordt niet ondersteund.
>
>Wanneer de pagina wordt bevorderd, zullen om het even welke inhoudveranderingen worden weerspiegeld, maar de componentenposities zullen niet veranderen.


### De opstartconsole {#the-launches-console}

De console van Lanceringen verstrekt een overzicht van uw lanceringen en laat u acties op die vermelde ondernemen. De console is toegankelijk via:

* De **Gereedschappen** Console: **Gereedschappen**, **Sites**, **Starten**.

* of rechtstreeks met [https://localhost:4502/libs/launches/content/launches.html](https://localhost:4502/libs/launches/content/launches.html)

## Starten in verwijzingen (siteconsole) {#launches-in-references-sites-console}

1. In de **Sites** naar de bron van de opstart(en).
1. Open de **Verwijzingen** rails en selecteer de bronpagina.
1. Selecteren **Starten** worden de bestaande lanceringen vermeld:

   ![Referentie, tabblad - Starten](assets/screen-shot_2019-03-05at121901-1.png)

1. Tik/klik op de gewenste opstart. De lijst met mogelijke acties wordt weergegeven:

   ![Selecteer Starten om mogelijke acties weer te geven](assets/screen-shot_2019-03-05at121952-1.png)
