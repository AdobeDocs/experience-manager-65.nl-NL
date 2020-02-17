---
title: Analyse aanvragen
seo-title: Analyse aanvragen
description: Het manuscript van de verzoekanalyse wordt gemaakt om de analyse van de access.log dossiers te verlichten die een leesbaar rapport voor recentere verwerking produceren
seo-description: Het manuscript van de verzoekanalyse wordt gemaakt om de analyse van de access.log dossiers te verlichten die een leesbaar rapport voor recentere verwerking produceren
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Analyse aanvragen{#request-analysis-script}

## Downloaden {#download}

Dit script is gemaakt om de analyse te vereenvoudigen van de `access.log` bestanden die een leesbaar rapport voor latere verwerking produceren.

[Bestand ophalen](assets/analyse-access.sh)

## Beschrijving {#description}

Dit script is gemaakt om de analyse te vereenvoudigen van de `access.log` bestanden die een leesbaar rapport voor latere verwerking produceren.

Het produceert het algemene verzoekaantal, GET versus POST, Verzoek distributie in tijd en meer.

De uitvoer wordt uitgevoerd in de syntaxis Markdown. Het is daarom gemakkelijker om de uitvoer te converteren naar PDF met gereedschappen zoals een pandoc-bestand of de uitvoer weer te geven in een browser met plug-ins zoals een Markeringen-viewer.

Een aangepast pad op de opdrachtregel kan worden geanalyseerd.

Maak kennis met de opmerking in het bestand die u vertelt hoe u de opmerking moet uitvoeren:

Analyseer CQ `access.log` -extrapolatie van verschillende informatie en produceer een Markering-uitvoer op `stdout`.

## Usage {#usage}

`./analyse-access.sh access.log.2013-&ast;`

u kunt aanvullende aangepaste paden opgeven die u wilt analyseren op de opdrachtregel

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

u kunt de output bewaren door eenvoudige pijpleiding

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
