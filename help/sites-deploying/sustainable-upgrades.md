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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 0%

---

# Duurzame verbeteringen{#sustainable-upgrades}

## Customization Framework {#customization-framework}

### Architectuur (functioneel / infrastructuur / inhoud / toepassing)  {#architecture-functional-infrastructure-content-application}

De functie van het Kader van de Aanpassing wordt ontworpen helpen de schendingen in niet verlengbare gebieden van de code (zoals APIS) of inhoud (zoals overlays) verminderen die niet verbeteringsvriendelijk zijn.

Er zijn twee componenten van het aanpassingskader: het **API-oppervlak** en de **Inhoudsclassificatie**.

#### API-oppervlak {#api-surface}

In eerdere versies van Adobe Experience Manager (AEM) werden veel API&#39;s via Uber Jar weergegeven. Sommige van deze API&#39;s waren niet bedoeld voor gebruik door klanten, maar werden blootgesteld aan ondersteuning voor AEM functionaliteit in verschillende bundels. De Java™ API&#39;s zijn in de toekomst gemarkeerd als Public of Private om aan klanten aan te geven welke API&#39;s veilig kunnen worden gebruikt in de context van upgrades. Andere bijzonderheden zijn:

* Java™ API&#39;s gemarkeerd als `Public` kan worden gebruikt en van verwijzingen voorzien door de bundels van de douaneimplementatie.

* De openbare API&#39;s zijn achterwaarts compatibel met de installatie van een compatibiliteitspakket.
* Het compatibiliteitspakket bevat een Uber JAR-compatibiliteitspakket om achterwaartse compatibiliteit te garanderen
* Java™ API&#39;s gemarkeerd als `Private` zijn alleen bedoeld voor gebruik door AEM interne bundels, niet door aangepaste bundels.

>[!NOTE]
>
>Het begrip `Private` en `Public` in deze context niet verward te worden met Java™-noties van openbare en particuliere klassen.

![image2018-2-12_23-52-48](assets/image2018-2-12_23-52-48.png)

#### Inhoudsclassificaties {#content-classifications}

AEM gebruikt al lang de principal of overlays en Sling Resource Merger om klanten toe te staan AEM functionaliteit uit te breiden en aan te passen. De vooraf bepaalde functionaliteit die de AEM consoles en UI van kracht maakt wordt opgeslagen in **/libs**. Klanten mogen niets wijzigen **/libs** maar kan hieronder extra inhoud toevoegen **/apps** om de in **/libs** (Zie Ontwikkelen met overlays voor meer informatie.) Dit heeft nog steeds veel problemen veroorzaakt bij het upgraden van AEM als de inhoud in **/libs** kan veranderen waardoor de overlayfunctionaliteit op onverwachte manieren wordt verbroken. Klanten kunnen ook AEM componenten uitbreiden via overerving `sling:resourceSuperType`of gewoon verwijzen naar een component in **/libs** rechtstreeks via sling:resourceType. Vergelijkbare upgradeproblemen kunnen optreden met verwijzing en gebruikstoepassingen negeren.

Om het voor klanten veiliger en gemakkelijker te maken om te begrijpen welke gebieden **/libs** zijn veilig te gebruiken en de inhoud te bedekken in **/libs** is ingedeeld met de volgende mengsels:

* **Public (granite:PublicArea)** - Definieert een knooppunt als &#39;public&#39;, zodat het kan worden bedekt, overgeërfd ( `sling:resourceSuperType`) of rechtstreeks gebruikt ( `sling:resourceType`). De knopen onder /libs duidelijk als Openbaar zijn veilig om met de toevoeging van een Pakket van de Verenigbaarheid te bevorderen. In het algemeen, zouden de klanten slechts knopen moeten gebruiken die als Openbaar worden gemerkt.

* **Abstract (graniet:AbstractArea)** - Definieert een knooppunt als abstract. Knooppunten kunnen worden bedekt of overgeërfd ( `sling:resourceSupertype`) maar niet rechtstreeks gebruikt ( `sling:resourceType`).

* **Final (graniet:FinalArea)** - Definieert een knooppunt als definitief. Als definitief geclassificeerde knooppunten mogen idealiter niet worden bedekt of overgeërfd. Uiteindelijke knooppunten kunnen rechtstreeks worden gebruikt via `sling:resourceType`. Subknooppunten onder het laatste knooppunt worden standaard als intern beschouwd.

* ***Internal (granite:InternalArea)*** *- *Definieert een knooppunt als internal. Knooppunten die idealiter als interne knooppunten zijn geclassificeerd, mogen niet worden bedekt, overgeërfd of rechtstreeks worden gebruikt. Deze knooppunten zijn alleen bedoeld voor de interne functionaliteit van AEM

* **Geen aantekening** - Knooppunten nemen classificatie over op basis van de boomhiërarchie. De /-hoofdmap is standaard Openbaar. **Knooppunten met een als intern of definitief ingedeelde ouder moeten ook als intern worden behandeld.**

>[!NOTE]
>
>Dit beleid wordt slechts afgedwongen tegen het Verdelen van zoekpad-gebaseerde mechanismen. Andere gebieden van **/libs** zoals een clientbibliotheek kan worden gemarkeerd als `Internal`, maar kan nog steeds worden gebruikt met standaard clientlib inclusie. Het is belangrijk dat een klant in deze gevallen de interne classificatie blijft respecteren.

#### Type-indicatoren voor CRXDE Lite-inhoud {#crxde-lite-content-type-indicators}

In CRXDE Lite toegepaste mengsels tonen inhoudsknooppunten en bomen die als `INTERNAL` als gedimd (grijs weergegeven). Voor `FINAL`, alleen het pictogram wordt grijs weergegeven. De onderliggende knooppunten van deze knooppunten worden ook gedimd weergegeven. In beide gevallen is de functie Overlay Node uitgeschakeld.

**Openbaar**

![image2018-2-8_23-34-5](assets/image2018-2-8_23-34-5.png)

**Definitief**

![image2018-2-8_23-34-56](assets/image2018-2-8_23-34-56.png)

**Intern**

![image2018-2-8_23-38-23](assets/image2018-2-8_23-38-23.png)

**Controle van inhoudsstatus**

>[!NOTE]
>
>Vanaf AEM 6.5 raadt Adobe u aan de patroondetector te gebruiken om schendingen van de toegang tot inhoud te detecteren. Patroondetectorrapporten zijn gedetailleerder, detecteren meer problemen en verminderen de kans op valse positieven.
>
>Zie voor meer informatie [De complexiteit van upgrades beoordelen met de patroondetector](/help/sites-deploying/pattern-detector.md).

AEM 6.5 wordt geleverd met een health check om klanten te waarschuwen als overlay- of referentieinhoud wordt gebruikt op een manier die niet in overeenstemming is met de inhoudclassificatie.

De *** Controle op de toegang tot inhoud via verkoop/graniet** is een nieuwe health check die de opslagplaats controleert om te zien of de code van de klant de beveiligde knooppunten in AEM op onjuiste wijze benadert.

Dit scant **/apps** en duurt meestal enkele seconden.

Ga als volgt te werk om deze nieuwe health check te openen:

1. Navigeer in het AEM Startscherm naar **Gereedschappen > Bewerkingen > Gezondheidsrapporten**
1. Klikken **Toegangscontrole voor verkoop/graniet**.

   ![screen_shot_2017-12-14at55648pm](assets/screen_shot_2017-12-14at55648pm.png)

Nadat de scan is voltooid, wordt een lijst met waarschuwingen weergegeven waarmee een eindgebruiker op de hoogte wordt gebracht van het beveiligde knooppunt waarnaar niet correct wordt verwezen:

![screenshot-2018-2-5health reports](assets/screenshot-2018-2-5healthreports.png)

Na het herstellen van de schendingen keert het terug naar groene staat:

![screenshot-2018-2-5health reports-violi](assets/screenshot-2018-2-5healthreports-violations.png)

De gezondheidscontrole toont informatie die door de achtergronddienst wordt verzameld die asynchroon controleert wanneer een bekleding of middeltype over alle Verschuivende onderzoekspaden wordt gebruikt. Als de inhoudmix onjuist wordt gebruikt, wordt een schending gemeld.
