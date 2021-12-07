---
title: Designer installeren en configureren
seo-title: Installing and configuring Designer
description: 'Designer is beschikbaar als zelfstandig installatieprogramma en is ook gebundeld met Workbench. Leer hoe u zelfstandige Designer installeert.  '
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
source-git-commit: a3cf926bde4a4b3a0810058e84ac01012a4a3a57
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 26%

---

# Designer installeren en configureren{#installing-and-configuring-designer}

## Voorwaarden {#pre-requisites}

Voor het installatieprogramma van AEM Forms Designer is de 32-bits versie van [Visuele C++ redistributable runtime package 2012](https://support.microsoft.com/en-us/topic/the-latest-supported-visual-c-downloads-2647da03-1eea-4433-9aff-95f26a218cc0) en [Visuele C++ redistributable runtime package 2013](https://support.microsoft.com/en-in/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package). Zorg ervoor dat de eerder vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start.

U hebt beheerdersrechten nodig om Designer te installeren of verwijderen.

## Designer installeren {#install-designer}

Designer is beschikbaar als zelfstandig installatieprogramma en is ook gebundeld met WorkBench. Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor Designer gebruikt:

1. Designer downloaden van Adobe [Licentiewebsite](https://licensing.adobe.com/).

   >[!NOTE]
   >
   >Als u een vorige versie van Designer hebt geïnstalleerd, verwijdert u de vorige versie voordat u verdergaat.

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


