---
title: Designer installeren en configureren
seo-title: Installing and configuring Designer
description: Designer is beschikbaar als zelfstandig installatieprogramma en is ook gebundeld met Workbench. Leer hoe u zelfstandige Designer installeert.
seo-description: Designer is available as a stand-alone installer and is also bundled with Workbench. Learn how to install stand-alone Designer.
uuid: c5b779d1-cb6a-48f4-87d6-48464753e516
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: designer
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: f3a5b5ce-2262-4d5d-a8ae-d59a3a4229e7
docset: aem65
role: Admin
exl-id: 90503d29-e079-43f4-a5dc-ce90ed7844c6
source-git-commit: 85189a4c35d1409690cbb93946369244e8848340
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 25%

---

# Designer installeren en configureren{#installing-and-configuring-designer}

## Voorwaarden {#pre-requisites}

* 32-bits versie van  [Visuele C++ 2019 Redistributable (x86)](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Zorg ervoor dat de eerder vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start.
* Een gebruiker met beheerdersrechten om Designer te installeren of verwijderen.

## Designer installeren {#install-designer}

Designer is beschikbaar als zelfstandig installatieprogramma en is ook gebundeld met WorkBench. Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor Designer gebruikt:

1. Verwijder de vorige versie van AEM Forms Designer als deze al is geïnstalleerd.
1. Designer downloaden van [Adobe-website voor licentieverlening](https://licensing.adobe.com/).

   >[!NOTE]
   >
   > * Adobe Experience Manager 6.5 Forms Service Pack 15 (6.5.15.0) vanaf de versie van Forms Designer bevat ook de versie Service Pack. Voor Service Pack 15 is het versienummer bijvoorbeeld 6.5.15.20221112.1.0. In dit voorbeeld, is 6.5.15 de versie van het de dienstpak.


1. Start het Designer-installatieprogramma door te dubbelklikken op setup.exe.
1. Ga verder en geef uw details en het serienummer op het scherm Personaliseren op.
1. Als u de licentieovereenkomst wilt accepteren, klikt u op Volgende om door te gaan.
1. (Optioneel) Wijzig het standaardinstallatiepad als u Designer op een andere locatie wilt installeren. Klik op Next.
1. Klik op Vorige als u voorkeuren wilt wijzigen. Klik op Installeren om Designer te installeren.
1. Klik na de installatie op Voltooien.

U kunt de Designer ook via de opdrachtregel installeren in de passieve of stille modus.

* Passieve opdrachtregelinstallatie: In het installatieprogramma wordt een voortgangsbalk weergegeven die aangeeft dat de installatie wordt uitgevoerd, maar er worden geen aanwijzingen of foutberichten weergegeven. Nadat de installatie is gestart, kunt u de installatie niet annuleren.

```shell
msiexec /i "<absolute path>\Designer.msi" /passive SERIALNUMBER=****-****-****-****-****-****
```

* Stille opdrachtregelinstallatie: Het installatieprogramma voert de installatie uit zonder een gebruikersinterface weer te geven. Er worden geen aanwijzingen, berichten of dialoogvensters weergegeven. Nadat de installatie is gestart, kunt u de installatie niet annuleren.

```shell
msiexec /i "<absolute path>\Designer.msi" /quiet SERIALNUMBER=****-****-****-****-****-****
```
