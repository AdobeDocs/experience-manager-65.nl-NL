---
title: Designer installeren en configureren
description: Designer is beschikbaar als zelfstandig installatieprogramma en is ook gebundeld met Workbench. Leer hoe u zelfstandige Designer installeert.
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: designer
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin, User, Developer
feature: Forms Designer,Designer
exl-id: 90503d29-e079-43f4-a5dc-ce90ed7844c6
solution: Experience Manager, Experience Manager Forms
source-git-commit: 8f14518117b3aff1cdb2e033fbfe40d0a903d53f
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 0%

---

# Designer installeren en configureren{#installing-and-configuring-designer}

## Voorwaarden {#pre-requisites}

+++ Voor 64-bits AEM Forms Designer (aanbevolen)

* Installeer versie met 64 bits van [&#x200B; Visuele C++ 2019 Redistributable (x64) &#x200B;](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Zorg ervoor dat de eerder vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start.
* Een gebruiker met beheerdersrechten om AEM Forms Designer te installeren of verwijderen.
* Op het systeem waarop 64-bits AEM Forms Designer wordt uitgevoerd, moet OpenSSL3 zijn geïnstalleerd, met name de gedeelde bibliotheek `libcrypto-3-x64.dll` .\
  Deze bibliotheek wordt vereist voor AEM Designer om correct te functioneren en **SHAHash** te berekenen.

+++

+++ Voor 32-bits AEM Forms Designer

* Installeer versie met 32 bits van [&#x200B; Visuele C++ 2019 Redistributable (x64) &#x200B;](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Zorg ervoor dat de eerder vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start.
* Een gebruiker met beheerdersrechten om AEM Forms Designer te installeren of verwijderen.

+++

>[!NOTE]
>
>* De versie met 64 bits van de ontwerper werd geïntroduceerd met AEM 6.5 Forms Service Pack 19 (6.5.19.0).
>* De versie met 32 bits van de ontwerper wordt afgekeurd sinds de versie van [&#x200B; AEM Forms Service Pack 21 (6.5.21.0) &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).
> * De ondersteunde platformen voor Forms Designer worden uitgelijnd met de door AEM Forms ondersteunde platforms. Om over de gesteunde platforms voor Forms Designer te leren, [&#x200B; klik hier &#x200B;](/help/forms/using/aem-forms-jee-supported-platforms.md).

Voor meer informatie betreffende installatie van Forms Designer, bezoek [&#x200B; vaak gestelde vragen &#x200B;](#fandq).

## AEM Forms Designer installeren {#install-designer}

Designer is beschikbaar als zelfstandig installatieprogramma en is ook gebundeld met WorkBench. Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor AEM Forms Designer gebruikt:

1. Verwijder de vorige versie van AEM Forms Designer als deze al is geïnstalleerd.
1. Download op basis van uw vereisten de 64-bits AEM Forms Designer (aanbevolen) of de 32-bits AEM Forms Designer.

   >[!NOTE]
   > 
   >* 32-bits Forms Designer zal volgens de planning worden vervangen door de AEM 6.5 Forms Service Packs 20 (6.5.20.0)-release. Adobe raadt u aan een upgrade uit te voeren naar de 64-bits Forms-ontwerper.
   >* 64-bits Forms Designer is alleen beschikbaar voor AEM 6.5 Forms Service Packs 19 (6.5.19.0) of hoger.
   >* Adobe Experience Manager 6.5 Forms Service Pack 15 (6.5.15.0) vanaf Forms Designer versie omvat ook de versie Service Pack. Voor Service Pack 15 is het versienummer bijvoorbeeld 6.5.15.20221112.1.0. In dit voorbeeld, is 6.5.15 de versie van het de dienstpak.

1. Start het installatieprogramma van AEM Forms Designer door te dubbelklikken op setup.exe.
1. Ga verder en geef uw gegevens en het serienummer op het Personalization-scherm op.

   >[!NOTE]
   >
   >* Verkrijg uw Forms Designer vergunningssleutel van [&#x200B; Adobe Vergunnend Website &#x200B;](https://licensing.adobe.com/).

1. Als u de licentieovereenkomst accepteert, klikt u op Volgende om door te gaan.
1. (Optioneel) Wijzig het standaardinstallatiepad als u Designer op een door u gekozen locatie wilt installeren. Klik op Volgende.
1. Klik op Vorige om voorkeuren te wijzigen. Klik op Installeren om Designer te installeren.
1. Klik op Voltooien als de installatie is voltooid.

U kunt de AEM Forms Designer ook via de opdrachtregel installeren in de passieve of stille modus.

* Passieve opdrachtregelinstallatie: in het installatieprogramma wordt een voortgangsbalk weergegeven die aangeeft dat de installatie wordt uitgevoerd, maar dat er geen aanwijzingen of foutberichten worden weergegeven. Nadat de installatie is gestart, kunt u de installatie niet annuleren.

```shell
msiexec /i "<absolute path>\Designer.msi" /passive SERIALNUMBER=****-****-****-****-****-****
```

* Stille opdrachtregelinstallatie: het installatieprogramma voert de installatie uit zonder een gebruikersinterface weer te geven. Er worden geen aanwijzingen, berichten of dialoogvensters weergegeven. Nadat de installatie is gestart, kunt u de installatie niet annuleren.

```shell
msiexec /i "<absolute path>\Designer.msi" /quiet SERIALNUMBER=****-****-****-****-****-****
```

## AEM Forms Designer bijwerken {#update-forms-designer}

Er zijn twee gevallen bij het bijwerken van de nieuwste versie van AEM Forms Designer 6.5.16.0 :

* **Geval 1**: Wanneer de gebruiker de versie van AEM Forms Designer vroeger dan 6.5.15.0 heeft.
* **Geval 2**: Wanneer de gebruiker 6.5.15.0 versie van AEM Forms Designer heeft.

+++**wanneer de gebruiker de versie van AEM Forms Designer vroeger dan 6.5.15.0 heeft.**

Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor AEM Forms Designer gebruikt:

1. Alvorens **AEM Forms Designer6.5.16.0** te installeren, moeten de gebruikers om het even welke vorige versies verwijderen.
1. De download en installeert [&#x200B; AEM Forms Designer 6.5.15.0 &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=nl-NL) van de Pagina van de Versies van de Vorm van AEM.
1. Na succesvolle installatie van **AEM Forms Designer6.5.15.0**, download en installeer [&#x200B; AEM Forms Designer 6.5.16.0 &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=nl-NL) door op het gedownloade installatiedossier tweemaal te klikken.

+++

+++**wanneer de gebruiker 6.5.15.0 versie van AEM Forms Designer** heeft

Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor AEM Forms Designer gebruikt:
1. De recentste versie van AEM Forms Designer van de download [&#x200B; portal van de softwaredistributie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=nl-NL).
1. Installeer de nieuwste versie van AEM Forms Designer door te dubbelklikken op het gedownloade installatiebestand.

+++

## Veelgestelde vragen {#fandq}

* **kan een gebruiker een ontwerper met 64 bits direct bevorderen of installeren?**
   * Ja, gebruikers kunnen de ontwerper met 64 bits direct bevorderen of installeren. Om te bevorderen, installeer [&#x200B; SP19 &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/Designer-Patch/sp19_x64/aemforms_designer_6_5_0_wwe_win.zip) ontwerper volledig installatieprogramma en pas verdere designerflardversie over dat toe.

     >[!NOTE]
     > Voordat u een upgrade uitvoert naar de 64-bits ontwerper, moet u eerst de 32-bits ontwerper verwijderen als deze bestaat.

* **kunnen de gebruikers zowel met 32 bits als met 64 bits geïnstalleerd op hun systeem houden?**
   * Nee, 32-bits en 64-bits installatie werkt niet op dezelfde computer. De gebruiker kan of een ontwerper met 32 bits of een ontwerper met 64 bits hebben.

* **hoe controleert u als een gebruiker op ontwerper met 64 bits of ontwerper met 32 bits is?**
   * Er zijn twee manieren om de Forms Designer-versie te controleren:

      1. Open Designer, ga Hulp, klik over ontwerper en u ziet de informatie van de ontwerpversie samen met de beetjeinformatie, bijvoorbeeld, wordt 64 beetje geschreven aan het eind van de versie zoals hier getoond:

         `6.5.21.20240522.1.161 | 64 bit`
      1. Open Designer. Linksboven ziet u dat een brandpictogram 64-bits informatie met de productnaam bevat.

