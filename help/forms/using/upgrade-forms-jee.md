---
title: Upgrade naar AEM 6,5 Forms in JEE
description: U kunt een directe verbetering van AEM 6.1 Forms, AEM 6.2 Forms, en LiveCycle ES4 SP1 aan AEM 6.3 Forms uitvoeren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
role: Admin,User
exl-id: 722e75a0-bcb3-465e-bb74-ea94a3b99fd3
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# Upgrade naar AEM 6,5 Forms in JEE {#upgrade-to-aem-forms-jee}

AEM 6.5.18.0 Forms op JEE biedt twee typen installatieprogramma&#39;s: volledig installatieprogramma en Patch-installatieprogramma.

**Volledig installatieprogramma**: U kunt de opdracht [AEM 6.5.18.0 op volledig JEE-installatieprogramma](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) om nieuwe AEM Forms-instanties in te stellen of upgrades uit te voeren van AEM 6.5.x.x Forms op JEE naar AEM 6.5.18.0 Forms op JEE.

**Patchinstallatieprogramma**: [AEM 6.5.18.0 op JEE-patchinstallatieprogramma](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) is voor klanten die reeds AEM 6.5.x.x versies gebruiken. U kunt het installatieprogramma van de patch gebruiken om een upgrade uit te voeren naar de nieuwste versie van AEM Forms.

In de volgende tabel ziet u de scenario&#39;s voor het gebruik van het installatieprogramma voor volledige patches en patches.

![Installatiescenario van volledig en reparatie](assets/full-and-patch-installer.png)

Voer de volgende procedure uit om het volledige installatieprogramma te gebruiken om bestaande AEM Forms 6.5.x.x op JEE aan AEM 6.5.18.0 Forms op JEE te bevorderen:

1. Download de AEM 6.5 Forms op het JEE-installatieprogramma van de [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). U hebt een geldig onderhouds- en ondersteuningscontract nodig om het installatieprogramma te kunnen gebruiken.
1. Zie [Controlelijst voor upgrades en planning](https://www.adobe.com/go/learn_aemforms_upgrade_checklist_65) om over de controles te leren om uit te voeren om een succesvolle verbetering te verzekeren.
1. Zie [Upgrade naar AEM Forms voorbereiden](https://www.adobe.com/go/learn_aemforms_prepareupgrade_65) om de taken te leren en uit te voeren die ervoor zorgen de verbetering correct met minimale serveronderbreking loopt.
1. Afhankelijk van uw bestaande omgeving en toepassingsserver kiest u een van de volgende documenten en volgt u de instructies.

   * [Upgrade van AEM 6.3 of AEM 6.4 Forms naar AEM 6.5 Forms voor JBoss](https://www.adobe.com/go/learn_aemforms_upgradeJBoss_65)
   * [Upgrade van AEM 6.3 of AEM 6.4 Forms naar AEM 6.5 Forms for WebSphere](https://www.adobe.com/go/learn_aemforms_upgradeWebSphere_65)
   * [Upgrade van AEM 6.3 of AEM 6.4 Forms naar AEM 6.5 Forms voor JBoss Turnkey](https://www.adobe.com/go/learn_aemforms_upgradeTurnkey_65)

Directe upgrade van LiveCycle ES2, LiveCycle ES3, AEM 6.0 Forms, AEM 6.1 Forms, AEM 6.2 Forms naar AEM 6.5 is niet beschikbaar. U kunt een tussentijdse upgrade uitvoeren naar een of meer versies van LiveCycle of AEM Forms en vervolgens upgraden naar AEM 6.5 Forms. Voor de lijst van tussenliggende versies en overeenkomstige verbeteringsinstructies, zie [Een upgradepad kiezen](upgrade.md).
