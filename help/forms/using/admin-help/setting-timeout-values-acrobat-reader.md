---
title: Afbreekwaarden instellen voor gebruik met Acrobat Reader DC Extensions
description: Leer hoe u time-outwaarden instelt voor gebruik met Acrobat Reader DC Extensions.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0a55aab3-14a3-41ad-8533-dc2cd116a848
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Afbreekwaarden instellen voor gebruik met Acrobat Reader DC Extensions  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

Wanneer u werkt aan veel PDF-bestanden in Acrobat Reader DC Extensions, moet u ervoor zorgen dat de volgende time-outwaarden op de juiste wijze zijn ingesteld om te voorkomen dat taken op het juiste moment worden uitgevoerd en mislukken:

**Tijdslimiet voor verwijdering van document**

Deze waarde kan in de beleidsconsole worden geplaatst. Klik op Instellingen > Core System Settings > Configurations en geef een waarde op voor Default Document Disposal Timeout.

**Tijdslimiet voor AEM van gebruikersbeheer:** Deze waarde kan worden ingesteld door het bestand config.xml te bewerken. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden importeren en exporteren en klik vervolgens op Exporteren. Open het geëxporteerde bestand config.xml en bewerk de volgende regels:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Sla het bestand config.xml op en importeer het vervolgens weer in de beheerconsole.

**Time-out sessie toepassingsserver:** Deze waarde kan op de toepassingsserver worden ingesteld. Raadpleeg de documentatie bij de toepassingsserver voor meer informatie.
