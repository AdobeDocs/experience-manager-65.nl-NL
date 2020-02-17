---
title: Starten promoten
seo-title: Starten promoten
description: U moet opstartiepagina's promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen. Wanneer een startpagina wordt bevorderd, wordt de bijbehorende pagina van de bronpagina's vervangen door de inhoud van de gepromoveerde pagina.
seo-description: U moet opstartiepagina's promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen. Wanneer een startpagina wordt bevorderd, wordt de bijbehorende pagina van de bronpagina's vervangen door de inhoud van de gepromoveerde pagina.
uuid: 91f1c6ac-8c4e-4459-aaab-feaa32befc45
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 8d38c6f7-8fea-4d27-992d-03b604b9541f
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4

---


# Starten promoten{#promoting-launches}

U moet opstartiepagina&#39;s promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen. Wanneer een startpagina wordt bevorderd, wordt de bijbehorende pagina van de bronpagina&#39;s vervangen door de inhoud van de gepromoveerde pagina. De volgende opties zijn beschikbaar bij het promoten van een startpagina:

* Of alleen de huidige pagina of de volledige lancering wordt bevorderd.
* Of de onderliggende pagina&#39;s van de huidige pagina worden bevorderd.
* Of de volledige lancering of slechts pagina&#39;s wordt bevorderd die zijn veranderd.

## Startpagina&#39;s promoten {#promoting-launch-pages}

Als u pagina&#39;s wilt promoten, voert u de volgende stappen uit tijdens het bewerken van de startpagina die u wilt promoten:

1. Klik op het tabblad **Pagina** in Sidetrap op **Starten** bevorderen.
1. Geef de pagina&#39;s op die u wilt promoten:

   * (Standaard) Als u alleen de huidige pagina wilt promoten, selecteert u Paginawijzigingen **bevorderen in productieversie**.
   * Selecteer **Inclusief subpagina&#39;s** om ook de onderliggende pagina&#39;s van de huidige pagina te bevorderen.
   * Als u alle pagina&#39;s wilt promoten tijdens het starten, selecteert u Volledige **Starten naar productieversie** bevorderen.

1. Als u de productiepagina&#39;s aan een workflowpakket wilt toevoegen, selecteert u **Toevoegen aan workflowpakket** en selecteert u vervolgens het workflowpakket.
1. Klik op **Opwaarderen**.

## Promotiepagina&#39;s verwerken met AEM-workflow {#processing-promoted-pages-using-aem-workflow}

Gebruik workflowmodellen voor bulkverwerking van geconverteerde startpagina&#39;s:

1. Maak een workflowpakket.
1. Wanneer auteurs startpagina&#39;s promoten, slaan ze deze op in het workflowpakket.
1. Start een workflowmodel met het pakket als de payload.

Als u een workflow automatisch wilt starten wanneer pagina&#39;s worden geconverteerd, [configureert u een werkstroomstartprogramma](/help/sites-administering/workflows-starting.md#workflows-launchers) voor het pakketknooppunt.

U kunt bijvoorbeeld automatisch aanvragen voor paginanactivering genereren wanneer auteurs pagina&#39;s starten promoten. Configureer een werkstroomstartprogramma om de workflow voor activering van aanvragen te starten wanneer het pakketknooppunt wordt gewijzigd.

![chlimage_1-136](assets/chlimage_1-136.png)

