---
title: Welke testomgevingen zijn nodig?
seo-title: Which Test Environments are needed?
description: Verschillende omgevingen moeten worden beschouwd als onderdeel van tests
seo-description: Several environments should be considered as part of testing
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
exl-id: 05f7a513-5ee7-4870-a691-4a0602e0cbb2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Welke testomgevingen zijn nodig?{#which-test-environments-will-be-needed}

Als u wilt definiëren welke configuraties voor tests moeten worden gebruikt, moet u het volgende in overweging nemen:

**Ontwikkeling** - voor eenheid en bepaalde integratietests.

**Testen** - Voor het grootste deel van de tests.

**Live** - voor de eindprestaties en stresstests. Ook voor goedkeuringstests met de klant.

U moet ook bepalen welke instanties u nodig hebt (meestal ten minste één voor alle testniveaus):

**Auteur** - Met dit exemplaar kunnen auteurs inhoud invoeren en publiceren.

**Publiceren** - Dit exemplaar presenteert de website in zijn gepubliceerde formulier voor toegang van bezoekers.

Moet worden getest in combinatie met de Dispatcher.

Ten slotte moet de werkelijke hardware in overweging worden genomen: eventuele prestatietests moeten worden uitgevoerd op een systeem dat zo dicht mogelijk bij de uiteindelijke live omgeving ligt. Daarom wordt ook aanbevolen het project te starten in een:

**Zacht starten** - verminderde beschikbaarheid; die tijd voor prestatietests, afstelling en optimalisering in realistische omstandigheden op de productieomgeving mogelijk maakt.

**Hard starten** - Volledige beschikbaarheid.
