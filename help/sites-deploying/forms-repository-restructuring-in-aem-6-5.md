---
title: Forms Repositoregeling Herstructurering in AEM 6.5
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe repository structuur in AEM 6.5 voor Forms.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
feature: Upgrading
exl-id: d555422e-dc97-4d45-9525-4299d22315e2
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# Forms Repositoregeling Herstructurering in AEM 6.5{#forms-repository-restructuring-in-aem}

Zoals die op de ouder [ Herstructurering van de Bewaarplaats in AEM 6.5 ](/help/sites-deploying/repository-restructuring.md) pagina wordt beschreven, zouden de klanten die aan AEM 6.5 worden bevorderd deze pagina moeten gebruiken om de het werkinspanning te beoordelen verbonden aan bewaarplaatsveranderingen die de Oplossing van AEM Forms beïnvloeden. Sommige veranderingen vereisen het werk inspanning tijdens het AEM 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

**met 6.5 Verbetering**

* [Dic](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#misc)

**vóór Toekomstige Verbetering**

* [Configuratie EchoSign-Cloud Service](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#echosign-cloud-service-configuration)
* [Configuraties van Recaptcha-Cloud Servicen](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#recaptcha-cloud-service-configurations)
* [Configuraties van Typekit-Cloud Servicen](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#typekit-cloud-service-configurations)
* [Dic](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md#misc)

## Met 6,5-upgrade {#with-upgrade}

### Dic {#misc}

| **Vorige plaats** | `/etc/clientlibs/fd/fp` |
|---|---|
| **Nieuwe plaats** | `/libs/fd/fp/components` |
| **begeleiding van de Herstructurering** | Om het even welke expliciete verwijzingen in douanecode aan de plaats van de Oudheid moeten aan de Nieuwe plaats worden bijgewerkt. |
| **Nota&#39;s** | Deze clientbibliotheken mogen niet worden bewerkt of uitgebreid. |

| **Vorige plaats** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Nieuwe plaats** | `/libs/fd/rte` |
| **begeleiding van de Herstructurering** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Nota&#39;s** | NVT |

| **Vorige plaats** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nieuwe plaats** | `/libs/fd/af/authoring/clientlibs` |
| **begeleiding van de Herstructurering** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Nota&#39;s** | NVT |

| **Vorige plaats** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Nieuwe plaats** | `/libs/fd/xfaforms/clientlibs/` |
| **begeleiding van de Herstructurering** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Nota&#39;s** | NVT |

| **Vorige plaats** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nieuwe plaats** | `/libs/fd/af/runtime/clientlibs` |
| **begeleiding van de Herstructurering** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Nota&#39;s** | NVT |

| **Vorige plaats** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nieuwe plaats** | `/libs/fd/af/runtime/clientlibs` |
| **begeleiding van de Herstructurering** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Nota&#39;s** | NVT |

| **Vorige plaats** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Nieuwe plaats** | `/libs/fd/expeditor/clientlibs` |
| **begeleiding van de Herstructurering** | Voor de middelen in de cliëntbibliotheken die door absolute wegen kunnen worden bedoeld, moet u nieuwere wegen in verse activa gebruiken. |
| **Nota&#39;s** | NVT |

| **Vorige plaats** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Nieuwe plaats** | `/libs/fd/fmaddon` |
| **begeleiding van de Herstructurering** | Het wijzigen van deze clientlibs is nooit aanbevolen of ondersteund. Als deze clientlibs zijn gewijzigd, moeten ze worden teruggedraaid om de AEM code te gebruiken. |
| **Nota&#39;s** | NVT |

| **Vorige plaats** | `/etc/aep` |
|---|---|
| **Nieuwe plaats** | `/var/fd/content/annotations` |
| **begeleiding van de Herstructurering** | Het wijzigen van deze clientlibs is nooit aanbevolen of ondersteund. Als deze clientlibs zijn gewijzigd, moeten ze worden teruggedraaid om de AEM code te gebruiken. |
| **Nota&#39;s** | NVT |

## Voor toekomstige upgrade {#prior-to-upgrade}

### Configuratie EchoSign-Cloud Service {#echosign-cloud-service-configuration}

| **Vorige plaats** | `/etc/cloudservices/echosign` |
|---|---|
| **Nieuwe plaats** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **begeleiding van de Herstructurering** | Het [ Uitgestelde nut van de Migratie van de Inhoud ](/help/sites-deploying/lazy-content-migration.md) dat van de Migratie UI van Forms moet worden teweeggebracht. |
| **Nota&#39;s** | NVT |

### Configuraties van Recaptcha-Cloud Servicen {#recaptcha-cloud-service-configurations}

| **Vorige plaats** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Nieuwe plaats** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **begeleiding van de Herstructurering** | Het [ Uitgestelde nut van de Migratie van de Inhoud ](/help/sites-deploying/lazy-content-migration.md) dat van de Migratie UI van Forms moet worden teweeggebracht. |
| **Nota&#39;s** | NVT |

### Configuraties van Typekit-Cloud Servicen {#typekit-cloud-service-configurations}

| **Vorige plaats** | `/etc/cloudservices/typekit` |
|---|---|
| **Nieuwe plaats** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **begeleiding van de Herstructurering** | Het [ Uitgestelde nut van de Migratie van de Inhoud ](/help/sites-deploying/lazy-content-migration.md) dat van de Migratie UI van Forms moet worden teweeggebracht. |
| **Nota&#39;s** | NVT |

### Dic {#misc-1}

| **Vorige plaats** | `/etc/cloudservices/fdm` |
|---|---|
| **Nieuwe plaats** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **begeleiding van de Herstructurering** | Het [ Uitgestelde nut van de Migratie van de Inhoud ](/help/sites-deploying/lazy-content-migration.md) dat van de Migratie UI van Forms moet worden teweeggebracht. |
| **Nota&#39;s** | NVT |

| **Vorige plaats** | `/etc/designs/fd/fp` |
|---|---|
| **Nieuwe plaats** | `/libs/fd/fp` |
| **begeleiding van de Herstructurering** | Werk alle verwijzingen naar de sjablonen /etc bij, zodat deze verwijzen naar hun `/libs` -tegenhangers. |
| **Nota&#39;s** | NVT |
