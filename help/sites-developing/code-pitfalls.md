---
title: Codevalkuilen
seo-title: Codevalkuilen
description: Gemeenschappelijke coderingsvalkuilen om te vermijden bij het ontwikkelen voor AEM
seo-description: Gemeenschappelijke coderingsvalkuilen om te vermijden bij het ontwikkelen voor AEM
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Codevalkuilen{#code-pitfalls}

## Bindingen in Java-code voorkomen {#avoid-sling-bindings-in-java-code}

Het verkopen Bindingen zijn een ongepaste manier om tot de dienst in 90% van gevallen toegang te krijgen. Gebruik in plaats daarvan *@Reference* of *@Injectopties* .

## Geen thread.interrupt in Java-code {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* is gevaarlijk omdat het dossiers, met inbegrip van dossiers Lucene en blijvende geheim voorgeheugendossiers, wanneer geroepen op het verkeerde ogenblik kan sluiten.

## Gebruik geen Java-synchronisatie met ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

Dit kan tot een rassenvoorwaarde leiden waarin de code uiteindelijk zal blokkeren.
