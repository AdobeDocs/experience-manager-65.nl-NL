---
title: Duurzame verbeteringen
seo-title: Duurzame verbeteringen
description: Meer informatie over duurzame upgrades in AEM 6.4.
seo-description: Meer informatie over duurzame upgrades in AEM 6.4.
uuid: 80673076-624b-4308-8233-129cb4422bd5
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: e35c9352-f0d5-4db5-b88f-0720af8f6883
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Duurzame verbeteringen{#sustainable-upgrades}

## Customization Framework {#customization-framework}

### Architectuur (functioneel / infrastructuur / inhoud / toepassing) {#architecture-functional-infrastructure-content-application}

De functie van het Kader van de Aanpassing wordt ontworpen om de schendingen in niet verlengbare gebieden van de code (zoals APIS) of inhoud (zoals overlays) te helpen verminderen die niet verbeteringsvriendelijk zijn.

Er zijn twee componenten van het aanpassingskader: het **API-oppervlak** en de **inhoudsclassificatie**.

#### API-oppervlak {#api-surface}

In eerdere versies van AEM werden veel API&#39;s via de Uber Jar weergegeven. Sommige van deze API&#39;s waren niet bedoeld voor gebruik door klanten, maar werden beschikbaar gesteld voor ondersteuning van AEM-functionaliteit in verschillende bundels. In de toekomst worden de Java API&#39;s gemarkeerd als Public of Private om aan klanten aan te geven welke API&#39;s veilig kunnen worden gebruikt in de context van upgrades. Andere bijzonderheden zijn:

* Java API&#39;s die zijn gemarkeerd als `Public` kunnen worden gebruikt en waarnaar wordt verwezen door aangepaste implementatiebundels.

* De openbare API&#39;s zijn achterwaarts compatibel met de installatie van een compatibiliteitspakket.
* Het compatibiliteitspakket bevat een compatibiliteitspakket van Uber JAR om achterwaartse compatibiliteit te garanderen
* Java API&#39;s die zijn gemarkeerd als `Private` zijn alleen bedoeld voor gebruik door interne AEM-bundels en mogen niet worden gebruikt door aangepaste bundels.

>[!NOTE]
>
>Het concept `Private` en `Public` in deze context mag niet worden verward met Java-noties van publieke en private klassen.

![image2018-2-12_23-52-48](assets/image2018-2-12_23-52-48.png)

#### Inhoudsclassificaties {#content-classifications}

AEM heeft al lang de principal of overlays en Sling Resource Merger gebruikt om klanten in staat te stellen de AEM-functionaliteit uit te breiden en aan te passen. Vooraf gedefinieerde functionaliteit die de AEM-consoles en UI kracht geeft, worden opgeslagen in **/libs**. Klanten mogen niets wijzigen onder **/libs** , maar kunnen aanvullende inhoud onder **/apps** toevoegen om de in **/libs** gedefinieerde functionaliteit te bedekken en uit te breiden (zie Ontwikkelen met overlays voor meer informatie). Dit heeft nog steeds veel problemen veroorzaakt bij het upgraden van AEM omdat de inhoud in **/bibliotheken** kan veranderen, waardoor de overlayfunctionaliteit op onverwachte manieren wordt onderbroken. Klanten kunnen AEM-componenten ook uitbreiden via overerving via `sling:resourceSuperType`of gewoon rechtstreeks via sling:resourceType verwijzen naar een component in **/libs** . Vergelijkbare upgradeproblemen kunnen optreden met verwijzing en gebruikstoepassingen negeren.

Om het voor klanten veiliger en gemakkelijker te maken om te begrijpen welke gebieden van **/libs** veilig kunnen worden gebruikt en om de inhoud in **/libs** te bedekken, is de inhoud ingedeeld met de volgende mengsels:

* **Public (granite:PublicArea)** - Hiermee wordt een knooppunt gedefinieerd als public zodat het kan worden bedekt, overgeërfd ( `sling:resourceSuperType`) of rechtstreeks ( `sling:resourceType`) gebruikt. De knopen onder /libs duidelijk als Openbaar zullen veilig zijn om met de toevoeging van een Pakket van de Verenigbaarheid te bevorderen. In het algemeen moeten klanten alleen knooppunten gebruiken die zijn gemarkeerd als Public.

* **Abstract (granite:AbstractArea)** - Definieert een knooppunt als abstract. Knooppunten kunnen worden bedekt of overgeërfd ( `sling:resourceSupertype`) maar mogen niet rechtstreeks worden gebruikt ( `sling:resourceType`).

* **Final (granite:FinalArea)** - Definieert een knooppunt als definitief. Als definitief geclassificeerde knooppunten mogen idealiter niet worden bedekt of overgeërfd. Uiteindelijke knooppunten kunnen rechtstreeks via `sling:resourceType`de verbinding worden gebruikt. Subknooppunten onder het laatste knooppunt worden standaard als intern beschouwd.

* ***Internal (granite:InternalArea)*** *- *Definieert een knooppunt als internal. Knooppunten die idealiter als interne knooppunten zijn geclassificeerd, mogen niet worden bedekt, overgeërfd of rechtstreeks worden gebruikt. Deze knooppunten zijn alleen bedoeld voor de interne functionaliteit van AEM

* **Geen annotatie** - knooppunten nemen de classificatie over op basis van de boomhiërarchie. De /-hoofdmap is standaard Openbaar. **Knooppunten met een als intern of definitief ingedeelde ouder moeten ook als intern worden behandeld.**

>[!NOTE]
>
>Dit beleid wordt slechts afgedwongen tegen het Verdelen van onderzoekspad gebaseerde mechanismen. Andere gebieden van **/bibliotheken** zoals een cliënt-zijbibliotheek kunnen als worden gemerkt `Internal`, maar nog kunnen met standaardcliëntlib opneming worden gebruikt. Het is belangrijk dat een klant in deze gevallen de interne classificatie blijft respecteren.

#### CRXDE Lite inhoudstype-indicatoren {#crxde-lite-content-type-indicators}

De mengsels die in CRXDE Lite worden toegepast zullen inhoudsknooppunten en bomen tonen die als `INTERNAL` uit worden gemerkt. Alleen voor het pictogram wordt grijs weergegeven. `FINAL` De onderliggende knooppunten van deze knooppunten worden ook grijs weergegeven. In beide gevallen is de functie Overlayknooppunt uitgeschakeld.

**Openbaar**

![image2018-2-8_23-34-5](assets/image2018-2-8_23-34-5.png)

**Definitief**

![image2018-2-8_23-34-56](assets/image2018-2-8_23-34-56.png)

**Intern**

![image2018-2-8_23-38-23](assets/image2018-2-8_23-38-23.png)

**Controle van inhoudsstatus**

>[!NOTE]
>
>Vanaf AEM 6.5 raadt Adobe aan de patroondetector te gebruiken om schendingen van de toegang tot inhoud te detecteren. Patroondetectorrapporten zijn gedetailleerder, detecteren meer problemen en verminderen de kans op valse positieven.
>
>Zie De [complexiteit upgraden met de patroondetector](/help/sites-deploying/pattern-detector.md)beoordelen voor meer informatie.

AEM 6.5 wordt verzonden met een health check om klanten te waarschuwen als overlay of inhoud waarnaar wordt verwezen, wordt gebruikt op een manier die inconsistent is met de inhoudclassificatie.

De *** Controle op de toegang tot inhoud via verkoop/graniet** is een nieuwe health check die de opslagplaats controleert om te zien of de code van de klant de beveiligde nodes in AEM op onjuiste wijze benadert.

Dit gaat scannen **/toepassingen** en duurt meestal enkele seconden.

Voor toegang tot deze nieuwe health check moet u het volgende doen:

1. Navigeer in het startscherm van AEM naar **Gereedschappen > Bewerkingen > Gezondheidsrapporten**
1. Klik op de **Controle** van de Toegang van de Inhoud van de Verkoop/van de Graniet zoals hieronder getoond:

   ![screen_shot_2017-12-14at55648pm](assets/screen_shot_2017-12-14at55648pm.png)

Nadat het aftasten volledig is, zal een lijst van waarschuwingen aan een eind - gebruiker op de hoogte brengen van de beschermde knoop die verkeerd referenced is:

![screenshot-2018-2-5health reports](assets/screenshot-2018-2-5healthreports.png)

Na het herstellen van de overtredingen keert het terug naar de groene staat:

![screenshot-2018-2-5health reports-violi](assets/screenshot-2018-2-5healthreports-violations.png)

De gezondheidscontrole toont informatie die door de achtergronddienst wordt verzameld die asynchroon controleert wanneer een bekleding of middeltype over alle Verschuivende onderzoekspaden wordt gebruikt. Als inhoudmix onjuist wordt gebruikt, wordt een schending gerapporteerd.
