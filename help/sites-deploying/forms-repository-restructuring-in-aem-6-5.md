---
title: Forms Repositoregeling Herstructurering in AEM 6.5
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe repository structuur in AEM 6.5 voor Forms.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
feature: Upgrading
exl-id: d555422e-dc97-4d45-9525-4299d22315e2
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# Forms Repositoregeling Herstructurering in AEM 6.5{#forms-repository-restructuring-in-aem}

Zoals beschreven op het bovenliggende element [Herstructurering van de depositaris in AEM 6.5](/help/sites-deploying/repository-restructuring.md) op de pagina, moeten klanten die een upgrade uitvoeren naar AEM 6.5 deze pagina gebruiken om de werkinspanning te beoordelen die gepaard gaat met wijzigingen in de opslagplaats die gevolgen hebben voor de AEM Forms-oplossing. Sommige veranderingen vereisen het werk inspanning tijdens het AEM 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

**Met 6,5-upgrade**

* [Dic](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#misc)

**Voor toekomstige upgrade**

* [Configuratie EchoSign-Cloud Service](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#echosign-cloud-service-configuration)
* [Configuraties van Recaptcha-Cloud Servicen](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#recaptcha-cloud-service-configurations)
* [Configuraties van Typekit-Cloud Servicen](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#typekit-cloud-service-configurations)
* [Dic](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#misc)

## Met 6,5-upgrade {#with-upgrade}

### Dic {#misc}

| **Vorige locatie** | `/etc/clientlibs/fd/fp` |
|---|---|
| **Nieuwe locatie** | `/libs/fd/fp/components` |
| **Herstructureringsrichtsnoeren** | Om het even welke expliciete verwijzingen in douanecode aan de plaats van de Oudheid moeten aan de Nieuwe plaats worden bijgewerkt. |
| **Notities** | Deze clientbibliotheken mogen niet worden bewerkt of uitgebreid. |

| **Vorige locatie** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Nieuwe locatie** | `/libs/fd/rte` |
| **Herstructureringsrichtsnoeren** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Notities** | NVT |

| **Vorige locatie** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nieuwe locatie** | `/libs/fd/af/authoring/clientlibs` |
| **Herstructureringsrichtsnoeren** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Notities** | NVT |

| **Vorige locatie** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Nieuwe locatie** | `/libs/fd/xfaforms/clientlibs/` |
| **Herstructureringsrichtsnoeren** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Notities** | NVT |

| **Vorige locatie** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nieuwe locatie** | `/libs/fd/af/runtime/clientlibs` |
| **Herstructureringsrichtsnoeren** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Notities** | NVT |

| **Vorige locatie** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nieuwe locatie** | `/libs/fd/af/runtime/clientlibs` |
| **Herstructureringsrichtsnoeren** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Notities** | NVT |

| **Vorige locatie** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Nieuwe locatie** | `/libs/fd/expeditor/clientlibs` |
| **Herstructureringsrichtsnoeren** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Notities** | NVT |

| **Vorige locatie** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Nieuwe locatie** | `/libs/fd/fmaddon` |
| **Herstructureringsrichtsnoeren** | Het wijzigen van deze clientlibs is nooit aanbevolen of ondersteund. Als deze clientlibs zijn gewijzigd, moeten ze worden teruggedraaid om de AEM code te gebruiken. |
| **Notities** | NVT |

| **Vorige locatie** | `/etc/aep` |
|---|---|
| **Nieuwe locatie** | `/var/fd/content/annotations` |
| **Herstructureringsrichtsnoeren** | Het wijzigen van deze clientlibs is nooit aanbevolen of ondersteund. Als deze clientlibs zijn gewijzigd, moeten ze worden teruggedraaid om de AEM code te gebruiken. |
| **Notities** | NVT |

## Voor toekomstige upgrade {#prior-to-upgrade}

### Configuratie EchoSign-Cloud Service {#echosign-cloud-service-configuration}

| **Vorige locatie** | `/etc/cloudservices/echosign` |
|---|---|
| **Nieuwe locatie** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **Herstructureringsrichtsnoeren** | De [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) te activeren hulpprogramma vanuit de gebruikersinterface van Forms Migration. |
| **Notities** | NVT |

### Configuraties van Recaptcha-Cloud Servicen {#recaptcha-cloud-service-configurations}

| **Vorige locatie** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Nieuwe locatie** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **Herstructureringsrichtsnoeren** | De [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) te activeren hulpprogramma vanuit de gebruikersinterface van Forms Migration. |
| **Notities** | NVT |

### Configuraties van Typekit-Cloud Servicen {#typekit-cloud-service-configurations}

| **Vorige locatie** | `/etc/cloudservices/typekit` |
|---|---|
| **Nieuwe locatie** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **Herstructureringsrichtsnoeren** | De [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) te activeren hulpprogramma vanuit de gebruikersinterface van Forms Migration. |
| **Notities** | NVT |

### Dic {#misc-1}

| **Vorige locatie** | `/etc/cloudservices/fdm` |
|---|---|
| **Nieuwe locatie** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **Herstructureringsrichtsnoeren** | De [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) te activeren hulpprogramma vanuit de gebruikersinterface van Forms Migration. |
| **Notities** | NVT |

| **Vorige locatie** | `/etc/designs/fd/fp` |
|---|---|
| **Nieuwe locatie** | `/libs/fd/fp` |
| **Herstructureringsrichtsnoeren** | Verwijzingen naar de sjablonen /etc bijwerken om naar de sjablonen te verwijzen `/libs` tegenhangers. |
| **Notities** | NVT |
