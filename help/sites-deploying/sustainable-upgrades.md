---
title: Duurzame verbeteringen
description: Meer informatie over duurzame upgrades in Adobe Experience Manager 6.4.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
exl-id: b777fdca-e7a5-427a-9e86-688dd7cac636
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 0%

---

# Duurzame verbeteringen{#sustainable-upgrades}

## Customization Framework {#customization-framework}

### Architectuur (functioneel / infrastructuur / inhoud / toepassing)  {#architecture-functional-infrastructure-content-application}

De functie van het Kader van de Aanpassing wordt ontworpen helpen de schendingen in niet verlengbare gebieden van de code (zoals APIS) of inhoud (zoals overlays) verminderen die niet verbeteringsvriendelijk zijn.

Er zijn twee componenten van het aanpassingskader: het **API Oppervlak** en de **Inhoudsclassificatie**.

#### API-oppervlak {#api-surface}

In eerdere versies van Adobe Experience Manager (AEM) werden veel API&#39;s via Uber Jar weergegeven. Sommige van deze API&#39;s waren niet bedoeld voor gebruik door klanten, maar werden blootgesteld aan ondersteuning voor AEM functionaliteit in verschillende bundels. De Java™ API&#39;s zijn in de toekomst gemarkeerd als Public of Private om aan klanten aan te geven welke API&#39;s veilig kunnen worden gebruikt in de context van upgrades. Andere bijzonderheden zijn:

* Java™ API&#39;s die als `Public` zijn gemarkeerd, kunnen worden gebruikt en waarnaar wordt verwezen door aangepaste implementatiebundels.

* De openbare API&#39;s zijn achterwaarts compatibel met de installatie van een compatibiliteitspakket.
* Het compatibiliteitspakket bevat een Uber JAR-compatibiliteitspakket om achterwaartse compatibiliteit te garanderen
* Java™ API&#39;s die als `Private` zijn gemarkeerd, mogen alleen worden gebruikt door AEM interne bundels, niet door aangepaste bundels.

>[!NOTE]
>
>Het concept `Private` en `Public` in deze context mag niet worden verward met Java™-noties van openbare en particuliere klassen.

![&#x200B; image2018-2-12_23-52-48 &#x200B;](assets/image2018-2-12_23-52-48.png)

#### Inhoudsclassificaties {#content-classifications}

AEM gebruikt al lang de principal of overlays en Sling Resource Merger om klanten toe te staan AEM functionaliteit uit te breiden en aan te passen. De vooraf bepaalde functionaliteit die de AEM consoles en UI van kracht maakt wordt opgeslagen in **/libs**. Klanten mogen niets wijzigen onder **/libs** maar kunnen onder **/apps** extra inhoud toevoegen om de functionaliteit te bedekken en uit te breiden die in **wordt bepaald/libs** (Zie Ontwikkelen met Bedekkingen voor meer informatie). Dit veroorzaakte nog talrijke kwesties wanneer het bevorderen van AEM aangezien de inhoud in **/libs** zou kunnen veranderen veroorzakend de bedekkingsfunctionaliteit om op onverwachte manieren te breken. De klanten konden AEM componenten door overerving door middel van `sling:resourceSuperType` ook uitbreiden, of eenvoudig een component in **/libs** direct door middel van sling:resourceType van verwijzingen voorzien. Vergelijkbare upgradeproblemen kunnen optreden met verwijzing en gebruikstoepassingen negeren.

Om het voor klanten veiliger en gemakkelijker te maken om te begrijpen welke gebieden van **/libs** veilig zijn om te gebruiken en bedekken de inhoud in **/libs** is geclassificeerd met de volgende mengelingen:

* **Openbaar (granite:PublicArea)** - bepaalt een knoop als openbaar zodat het kan worden bedekt, worden geërft ( `sling:resourceSuperType`) of direct ( `sling:resourceType`) worden gebruikt. De knopen onder /libs duidelijk als Openbaar zijn veilig om met de toevoeging van een Pakket van de Verenigbaarheid te bevorderen. In het algemeen, zouden de klanten slechts knopen moeten gebruiken die als Openbaar worden gemerkt.

* **Abstract (graniet:AbstractArea)** - bepaalt een knoop als abstract. Knooppunten kunnen worden bedekt of overgeërfd ( `sling:resourceSupertype` ), maar niet rechtstreeks ( `sling:resourceType` ) worden gebruikt.

* **Definitief (granite:FinalArea)** - bepaalt een knoop als definitief. Als definitief geclassificeerde knooppunten mogen idealiter niet worden bedekt of overgeërfd. Uiteindelijke knooppunten kunnen rechtstreeks via `sling:resourceType` worden gebruikt. Subknooppunten onder het laatste knooppunt worden standaard als intern beschouwd.

* ***Intern (graniet:InternalArea)*** * - *Definieert een knoop als intern. Knooppunten die idealiter als interne knooppunten zijn geclassificeerd, mogen niet worden bedekt, overgeërfd of rechtstreeks worden gebruikt. Deze knooppunten zijn alleen bedoeld voor de interne functionaliteit van AEM

* **Geen Annotatie** - de knopen erven classificatie die op de boomhiërarchie wordt gebaseerd. De /-hoofdmap is standaard Openbaar. **Knooppunten met een ouder die als Intern of Definitief wordt geclassificeerd moeten ook als Intern worden behandeld.**

>[!NOTE]
>
>Dit beleid wordt slechts afgedwongen tegen het Verdelen van zoekpad-gebaseerde mechanismen. Andere gebieden van **/libs** als een cliënt-zijbibliotheek kunnen als `Internal` worden gemerkt, maar konden nog met standaardcliëntlib opneming worden gebruikt. Het is belangrijk dat een klant in deze gevallen de interne classificatie blijft respecteren.

#### Type-indicatoren voor CRXDE Lite-inhoud {#crxde-lite-content-type-indicators}

In CRXDE Lite toegepaste mixen tonen inhoudsknooppunten en bomen die zijn gemarkeerd als `INTERNAL` als zijnde gedimd (grijs weergegeven). Voor `FINAL` wordt alleen het pictogram grijs weergegeven. De onderliggende knooppunten van deze knooppunten worden ook gedimd weergegeven. In beide gevallen is de functie Overlay Node uitgeschakeld.

**Openbaar**

![&#x200B; image2018-2-8_23-34-5 &#x200B;](assets/image2018-2-8_23-34-5.png)

**Definitief**

![&#x200B; image2018-2-8_23-34-56 &#x200B;](assets/image2018-2-8_23-34-56.png)

**Intern**

![&#x200B; image2018-2-8_23-38-23 &#x200B;](assets/image2018-2-8_23-38-23.png)

**Controle van de Gezondheid van de Inhoud**

>[!NOTE]
>
>Vanaf AEM 6.5 raadt Adobe u aan de patroondetector te gebruiken om schendingen van de toegang tot inhoud te detecteren. Patroondetectorrapporten zijn gedetailleerder, detecteren meer problemen en verminderen de kans op valse positieven.
>
>Voor meer informatie, zie [&#x200B; die de Complexiteit van de Verbetering met de Detector van het Patroon &#x200B;](/help/sites-deploying/pattern-detector.md) beoordelen.

AEM 6.5 wordt geleverd met een health check om klanten te waarschuwen als overlay- of referentieinhoud wordt gebruikt op een manier die niet in overeenstemming is met de inhoudclassificatie.

De *** Controle op de toegang tot inhoud via verkoop/graniet** is een nieuwe health check die de opslagplaats controleert om te zien of de code van de klant de beveiligde knooppunten in AEM op onjuiste wijze benadert.

Dit scant **/apps** en neemt typisch verscheidene seconden aan voltooiing.

Ga als volgt te werk om deze nieuwe health check te openen:

1. Van het AEM Scherm van het Huis, navigeer aan **Hulpmiddelen > Verrichtingen > de Rapporten van de Gezondheid**
1. Klik **Sling/de Controle van de Toegang van de Inhoud van Granite**.

   ![&#x200B; screen_shot_2017-12-14at55648pm &#x200B;](assets/screen_shot_2017-12-14at55648pm.png)

Nadat de scan is voltooid, wordt een lijst met waarschuwingen weergegeven waarmee een eindgebruiker op de hoogte wordt gebracht van het beveiligde knooppunt waarnaar niet correct wordt verwezen:

![&#x200B; screenshot-2018-2-5health rapporten &#x200B;](assets/screenshot-2018-2-5healthreports.png)

Na het herstellen van de schendingen keert het terug naar groene staat:

![&#x200B; screenshot-2018-2-5health reports-violi &#x200B;](assets/screenshot-2018-2-5healthreports-violations.png)

De gezondheidscontrole toont informatie die door de achtergronddienst wordt verzameld die asynchroon controleert wanneer een bekleding of middeltype over alle Verschuivende onderzoekspaden wordt gebruikt. Als de inhoudmix onjuist wordt gebruikt, wordt een schending gemeld.
