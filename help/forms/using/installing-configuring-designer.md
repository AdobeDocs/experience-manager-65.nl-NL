---
title: Designer installeren en configureren
description: Designer is beschikbaar als zelfstandig installatieprogramma en is ook gebundeld met Workbench. Leer hoe u zelfstandige Designer installeert.
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: designer
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin, User, Developer
feature: Forms Designer
exl-id: 90503d29-e079-43f4-a5dc-ce90ed7844c6
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '595'
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
> De 64-bits versie van de ontwerper werd geïntroduceerd met AEM 6.5 Forms Service Pack 19 (6.5.19.0).



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