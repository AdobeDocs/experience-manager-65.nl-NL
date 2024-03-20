---
title: Codevalkuilen
description: Gemeenschappelijke coderingsvalkuilen die worden vermeden bij het ontwikkelen voor AEM
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: c448c5d5-def8-4c1a-8db4-41eb49d0cd20
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Codevalkuilen{#code-pitfalls}

## Bindingen in Java-code voorkomen {#avoid-sling-bindings-in-java-code}

Het verkopen Bindingen zijn een ongepaste manier om tot de dienst in 90% van gevallen toegang te krijgen. Gebruik in plaats daarvan *@Reference* of *@Injecteren* annotaties.

## Geen thread.interrupt in Java-code {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* is gevaarlijk omdat het dossiers, met inbegrip van Lucene- dossiers en blijvende geheim voorgeheugendossiers, wanneer geroepen op het verkeerde ogenblik kan sluiten.

## Gebruik geen Java-synchronisatie met ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

Dit kan tot een rassenvoorwaarde leiden waarin de code uiteindelijk zal blokkeren.
