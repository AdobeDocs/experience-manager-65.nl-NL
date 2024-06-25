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
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 0%

---

# Designer installeren en configureren{#installing-and-configuring-designer}

## Voorwaarden {#pre-requisites}

+++ Voor 64-bits AEM Forms Designer (aanbevolen)

* 64-bits versie van  [Visuele C++ 2019 Redistributable (x64)](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Zorg ervoor dat de eerder vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start.
* Een gebruiker met beheerdersrechten om AEM Forms Designer te installeren of verwijderen.

+++

+++ Voor 32-bits AEM Forms Designer

* 32-bits versie van  [Visuele C++ 2019 Redistributable (x64)](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Zorg ervoor dat de eerder vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start.
* Een gebruiker met beheerdersrechten om AEM Forms Designer te installeren of verwijderen.

+++

>[!NOTE]
>
>* De 64-bits versie van de ontwerper werd geïntroduceerd met AEM 6.5 Forms Service Pack 19 (6.5.19.0).
>* De versie met 32 bits van de ontwerper wordt afgekeurd sinds de versie van [AEM Forms Service Pack 21 (6.5.21.0)](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).

Ga voor meer informatie over de installatie van Forms Designer naar [Veelgestelde vragen](#fandq).

## AEM Forms Designer installeren {#install-designer}

Designer is beschikbaar als zelfstandig installatieprogramma en is ook gebundeld met WorkBench. Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor AEM Forms Designer gebruikt:

1. Verwijder de vorige versie van AEM Forms Designer als deze al is geïnstalleerd.
1. Download op basis van uw vereisten 64-bits AEM Forms Designer (aanbevolen) of 32-bits AEM Forms Designer.

   >[!NOTE]
   > 
   >* 32-bits Forms Designer wordt vervangen door AEM 6.5 Forms Service Packs 20 (6.5.20.0). Adobe raadt u aan een upgrade uit te voeren naar de 64-bits Forms-ontwerper.
   >* 64-bits Forms Designer is alleen beschikbaar voor AEM 6.5 Forms Service Packs 19 (6.5.19.0) of hoger.
   >* Adobe Experience Manager 6.5 Forms Service Pack 15 (6.5.15.0) vanaf de versie van Forms Designer bevat ook de versie Service Pack. Voor Service Pack 15 is het versienummer bijvoorbeeld 6.5.15.20221112.1.0. In dit voorbeeld, is 6.5.15 de versie van het de dienstpak.

1. Start het installatieprogramma van AEM Forms Designer door te dubbelklikken op setup.exe.
1. Ga verder en geef uw gegevens en het serienummer op het scherm Personaliseren op.

   >[!NOTE]
   >
   >* Verkrijg je Forms Designer-licentiecode van [Licentiewebsite voor Adobe](https://licensing.adobe.com/).

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

Er zijn twee gevallen bij het bijwerken van de nieuwste versie van AEM Forms Designer 6.5.16.0:

* **Geval 1**: Als de gebruiker een AEM Forms Designer-versie heeft die ouder is dan 6.5.15.0.
* **Zaak 2**: Als de gebruiker de versie 6.5.15.0 van AEM Forms Designer heeft.

+++**Wanneer de gebruiker een AEM Forms Designer-versie heeft die ouder is dan 6.5.15.0.**

Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor AEM Forms Designer gebruikt:

1. Voordat u gaat installeren **AEM Forms Designer 6.5.16.0**, moeten gebruikers eerdere versies verwijderen.
1. Downloaden en installeren [AEM Forms Designer 6.5.15.0](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) op de pagina AEM formulierreleases.
1. Nadat de installatie van **AEM Forms Designer 6.5.15.0**, downloaden en installeren [AEM Forms Designer 6.5.16.0](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) door te dubbelklikken op het gedownloade installatiebestand.

+++

+++**Wanneer de gebruiker 6.5.15.0 AEM Forms Designer-versie heeft**

Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor AEM Forms Designer gebruikt:
1. Download de nieuwste versie van AEM Forms Designer van de [Software-distributieportal](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).
1. Installeer de nieuwste versie van AEM Forms Designer door te dubbelklikken op het gedownloade installatiebestand.

+++

## Veelgestelde vragen {#fandq}

* **Kan een gebruiker een 64-bits ontwerper rechtstreeks upgraden of installeren?**
   * Ja, gebruikers kunnen de ontwerper met 64 bits direct bevorderen of installeren. Installeer de [SP19](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/Designer-Patch/sp19_x64/aemforms_designer_6_5_0_wwe_win.zip) de ontwerper volledig installatieprogramma en pas verdere designer flardversie over dat toe.

     >[!NOTE]
     > Voordat u een upgrade uitvoert naar de 64-bits ontwerper, moet u eerst de 32-bits ontwerper verwijderen als deze bestaat.

* **Kunnen gebruikers zowel 32-bits als 64-bits op hun systeem installeren?**
   * Nee, 32-bits en 64-bits installatie werkt niet op dezelfde computer. De gebruiker kan of een ontwerper met 32 bits of een ontwerper met 64 bits hebben.

* **Hoe controleert u of is een gebruiker op ontwerper met 64 bits of ontwerper met 32 bits?**
   * Er zijn twee manieren om de Forms Designer-versie te controleren:

      1. Open Designer, ga naar Help, klik op Informatie over ontwerper en u ziet de informatie over de ontwerpversie samen met de bits-informatie. U ziet bijvoorbeeld dat 64-bits aan het einde van de versie is geschreven, zoals u hier ziet:
         `6.5.21.20240522.1.161 | 64 bit`
      1. Open Designer en linksboven ziet u een brandpictogram dat 64-bits informatie met de productnaam bevat.