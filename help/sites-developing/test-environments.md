---
title: Welke testomgevingen zijn nodig?
seo-title: Welke testomgevingen zijn nodig?
description: Verschillende omgevingen moeten worden beschouwd als onderdeel van tests
seo-description: Verschillende omgevingen moeten worden beschouwd als onderdeel van tests
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Welke testomgevingen zijn nodig?{#which-test-environments-will-be-needed}

Als u wilt definiëren welke configuraties voor tests moeten worden gebruikt, moet u het volgende in overweging nemen:

**Ontwikkeling** - voor Eenheid, en bepaalde tests van de Integratie.

**Testen** - Voor het grootste deel van de tests.

**Live** - Voor de eindprestaties en stresstests. Ook voor goedkeuringstests met de klant.

U moet ook bepalen welke instanties u nodig hebt (meestal ten minste één voor alle testniveaus):

**Auteur** - Met deze instantie kunnen auteurs inhoud invoeren en publiceren.

**Publiceren** - Deze instantie presenteert de website in de gepubliceerde vorm voor toegang van bezoekers.

Moet worden getest in combinatie met de Dispatcher.

Ten slotte moet de werkelijke hardware in overweging worden genomen: eventuele prestatietests moeten worden uitgevoerd op een systeem dat zo dicht mogelijk bij de uiteindelijke live omgeving ligt. Daarom wordt ook aanbevolen het project te starten in een:

**Zachte lancering** - verminderde beschikbaarheid; die tijd voor prestatietests, afstelling en optimalisering in realistische omstandigheden op de productieomgeving mogelijk maakt.

**Harde start** - volledige beschikbaarheid.
