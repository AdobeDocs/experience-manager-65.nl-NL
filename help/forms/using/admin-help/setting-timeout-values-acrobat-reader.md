---
title: Time-outwaarden instellen voor gebruik met Acrobat Reader DC-extensies
seo-title: Time-outwaarden instellen voor gebruik met Acrobat Reader DC-extensies
description: Leer hoe u time-outwaarden instelt voor gebruik met Acrobat Reader DC-extensies.
seo-description: Leer hoe u time-outwaarden instelt voor gebruik met Acrobat Reader DC-extensies.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Time-outwaarden instellen voor gebruik met Acrobat Reader DC-extensies {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

Wanneer u met veel PDF-bestanden werkt in Acrobat Reader DC-extensies, moet u ervoor zorgen dat de volgende time-outwaarden op de juiste wijze zijn ingesteld om te voorkomen dat taken time-out en failed:

**Tijdslimiet voor verwijdering van document**

Deze waarde kan in beleidsconsole worden geplaatst. Klik op Instellingen > Core System Settings > Configurations en geef een waarde op voor Default Document Disposal Timeout.

**** Time-out voor AEM-formulieren voor gebruikersbeheer: Deze waarde kan worden ingesteld door het bestand config.xml te bewerken. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden importeren en exporteren en klik vervolgens op Exporteren. Open het geëxporteerde bestand config.xml en bewerk de volgende regels:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Sla het bestand config.xml op en importeer het vervolgens weer in de beheerconsole.

**** Time-out sessie toepassingsserver: Deze waarde kan op de toepassingsserver worden ingesteld. Raadpleeg de documentatie bij de toepassingsserver voor meer informatie.
