---
title: Inhoud vertalen voor meertalige sites
seo-title: Inhoud vertalen voor meertalige sites
description: Leer hoe u inhoud voor meertalige sites vertaalt.
seo-description: Leer hoe u inhoud voor meertalige sites vertaalt.
uuid: 69b3e3a9-6773-4759-8178-aaa612e4c170
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 1e0a68c5-1583-4103-9dbb-7a53faa03c06
docset: aem65
legacypath: /content/docs/en/aem/6-0/administer/integration/third-party-services/machine-translation
translation-type: tm+mt
source-git-commit: 8b53e79e3a88f58423e99477db930a4912a1ba09
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Inhoud vertalen voor meerdere sites {#translating-content-for-multilingual-sites}

Automatiseer de vertaling van pagina-inhoud, elementen en door de gebruiker gegenereerde inhoud om meertalige websites te maken en te onderhouden. Om vertaalworkflows te automatiseren, integreert u de leveranciers van vertaaldiensten met AEM en creeert projecten voor het vertalen van inhoud in veelvoudige talen. AEM ondersteunt workflows voor het vertalen van mensen en machines.

* Menselijke vertaling: Inhoud wordt naar uw vertaalbureau verzonden en door professionele vertalers vertaald. Wanneer de vertaalde inhoud is voltooid, wordt deze geretourneerd en in AEM geïmporteerd. Wanneer uw vertaalbureau is geïntegreerd met AEM, wordt de inhoud automatisch verzonden tussen AEM en de vertaalprovider.
* Machinevertaling: De vertaalservice van de computer zet uw inhoud onmiddellijk om.

Voor het vertalen van inhoud worden de volgende stappen uitgevoerd:

1. [Sluit AEM aan bij uw ](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider) leverancier van vertaalservices en  [maak configuraties](/help/sites-administering/tc-tic.md) van vertaalintegratieframework.
1. [Koppel de pagina&#39;s van uw taalbeheersing ](/help/sites-administering/tc-tic.md#configuring-pages-for-translation) aan de vertaalservice en frameworkconfiguraties.
1. [Identificeer het type ](/help/sites-administering/tc-rules.md) inhoud dat u wilt vertalen.
1. [Bereid de inhoud voor voor ](/help/sites-administering/tc-prep.md) vertaling door de master taal te ontwerpen en de basispagina&#39;s van taalkopieën te maken.
1. [Maak vertaalprojecten ](/help/sites-administering/tc-manage.md) om de te vertalen inhoud te verzamelen en het vertaalproces voor te bereiden.
1. Gebruik de vertaalprojecten om het vertaalproces [te beheren van de inhoud](/help/sites-administering/tc-manage.md).

Als uw vertaalservicebureau geen aansluiting voor integratie met AEM biedt, ondersteunt AEM het handmatig extraheren en opnieuw invoegen van vertaalinhoud in XML-indeling.

>[!NOTE]
>
>Uw gebruiker moet een lid van de project-beheerders groep zijn om de eigenschappen van het Exemplaar van de Taal te gebruiken.

## Best practices voor {#best-practices}

De pagina [Aanbevolen procedures voor vertaling](/help/sites-administering/tc-bp.md) bevat belangrijke informatie over uw implementatie.
