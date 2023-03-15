---
title: Afdrukwaarden instellen voor gebruik met Acrobat Reader DC-extensies
seo-title: Setting timeout values for use with Acrobat Reader DC extensions
description: Leer hoe u time-outwaarden instelt voor gebruik met Acrobat Reader DC-extensies.
seo-description: Learn how to set timeout values for use with Acrobat Reader DC extensions.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
exl-id: 0a55aab3-14a3-41ad-8533-dc2cd116a848
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Afdrukwaarden instellen voor gebruik met Acrobat Reader DC-extensies  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

Wanneer u werkt aan veel PDF-bestanden in Acrobat Reader DC-extensies, moet u ervoor zorgen dat de volgende time-outwaarden op de juiste wijze zijn ingesteld om te voorkomen dat taken op het juiste moment worden uitgevoerd en mislukken:

**Tijdslimiet voor verwijdering van document**

Deze waarde kan in beleidsconsole worden geplaatst. Klik op Instellingen > Core System Settings > Configurations en geef een waarde op voor Default Document Disposal Timeout.

**Tijdslimiet voor AEM van gebruikersbeheer:** Deze waarde kan worden ingesteld door het bestand config.xml te bewerken. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden importeren en exporteren en klik vervolgens op Exporteren. Open het geëxporteerde bestand config.xml en bewerk de volgende regels:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Sla het bestand config.xml op en importeer het vervolgens weer in de beheerconsole.

**Time-out sessie toepassingsserver:** Deze waarde kan op de toepassingsserver worden ingesteld. Raadpleeg de documentatie bij de toepassingsserver voor meer informatie.
