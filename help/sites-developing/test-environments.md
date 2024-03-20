---
title: Welke testomgevingen zijn nodig?
description: Verschillende omgevingen moeten worden beschouwd als onderdeel van tests
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
exl-id: 05f7a513-5ee7-4870-a691-4a0602e0cbb2
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Welke testomgevingen zijn nodig?{#which-test-environments-will-be-needed}

Als u wilt definiëren welke configuraties voor tests moeten worden gebruikt, moet u het volgende in overweging nemen:

**Ontwikkeling** - voor eenheid en bepaalde integratietests.

**Testen** - Voor de meeste tests.

**Live** - voor de eindprestaties en stresstests. Ook voor goedkeuringstests met de klant.

Bepaal welke gevallen u nodig hebt en waar (gewoonlijk ten minste een van beide voor alle testniveaus):

**Auteur** - Met dit exemplaar kunnen auteurs inhoud invoeren en publiceren.

**Publiceren** - Dit exemplaar presenteert de website in zijn gepubliceerde formulier voor toegang van bezoekers.

Getest met de Dispatcher.

Ten slotte moet de werkelijke hardware in overweging worden genomen: eventuele prestatietests moeten worden uitgevoerd op een systeem dat zo dicht mogelijk bij de uiteindelijke live omgeving ligt. Daarom wordt ook aanbevolen het project te starten in een:

**Zacht starten** - Een geringere beschikbaarheid, waardoor er tijd is voor prestatieonderzoek, afstemming en optimalisatie onder realistische omstandigheden in de productieomgeving.

**Hard starten** - Volledige beschikbaarheid.
