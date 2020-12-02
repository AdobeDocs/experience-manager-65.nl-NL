---
title: Een taalbasis maken met de klassieke gebruikersinterface
seo-title: Een taalbasis maken met de klassieke gebruikersinterface
description: Leer hoe u een taalhoofdmap maakt met de klassieke gebruikersinterface.
seo-description: Leer hoe u een taalhoofdmap maakt met de klassieke gebruikersinterface.
uuid: 62e40d39-2868-4d3d-9af7-c60a1a658be0
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: b88edad4-2a2e-429b-86a2-cc68ba69697e
docset: aem65
translation-type: tm+mt
source-git-commit: 8b53e79e3a88f58423e99477db930a4912a1ba09
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# Een taalbasis maken met de klassieke UI{#creating-a-language-root-using-the-classic-ui}

De volgende procedure gebruikt klassieke UI om een taalwortel van een plaats tot stand te brengen. Zie [Taalhoofdmap maken](/help/sites-administering/tc-prep.md#creating-a-language-root) voor meer informatie.

1. Selecteer in de websiteconsole in de boomstructuur Websites de hoofdpagina van de site. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Voeg een nieuwe kindpagina toe die de taalversie van de plaats vertegenwoordigt:

   1. Klik op Nieuw > Nieuwe pagina.
   1. Geef in het dialoogvenster de titel en de naam op. De naam moet de notatie `<language-code>` of `<language-code>_<country-code>` hebben, bijvoorbeeld en, en_US, en_us, en_GB, en_gb.

      * De ondersteunde taalcode is tweeletterige code in kleine letters, zoals gedefinieerd door ISO-639-1
      * De ondersteunde landcode is tweeletterige, kleine letters of hoofdletters volgens ISO 3166
   1. Selecteer de sjabloon en klik op Maken.

   ![newpagefr](assets/newpagefr.png)

1. Selecteer in de websiteconsole in de boomstructuur Websites de hoofdpagina van de site.
1. Selecteer Taalkopie in het menu Gereedschappen.

   ![toolslangucopy](assets/toolslanguagecopy.png)

   In het dialoogvenster Taalkopie wordt een matrix weergegeven met beschikbare taalversies en webpagina&#39;s. Een x in een taalkolom betekent dat de pagina in die taal beschikbaar is.

   ![taalcopydialog](assets/languagecopydialog.png)

1. Als u een bestaande pagina of paginastructuur naar een taalversie wilt kopiëren, selecteert u de cel voor die pagina in de taalkolom. Klik op de pijl en selecteer het type kopie dat u wilt maken.

   In het volgende voorbeeld wordt de pagina voor apparatuur/zonnebril/irian gekopieerd naar de Franse taalversie.

   ![languageCopydilogdropdown](assets/languagecopydilogdropdown.png)

   | Type taalkopie | Beschrijving |
   |---|---|
   | auto | Gebruikt het gedrag van bovenliggende pagina&#39;s |
   | ignore | Er wordt geen kopie van deze pagina en de onderliggende elementen gemaakt |
   | `<language>+` (bijvoorbeeld Frans+) | Kopieert de pagina en alle onderliggende items van die taal |
   | `<language>` (bijvoorbeeld Frans) | Hiermee wordt alleen de pagina uit die taal gekopieerd |

1. Klik op OK om het dialoogvenster te sluiten.
1. Klik in het volgende dialoogvenster op Ja om de kopie te bevestigen.

