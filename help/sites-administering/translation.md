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

---


# Inhoud vertalen voor meertalige sites {#translating-content-for-multilingual-sites}

Automatiseer de vertaling van pagina-inhoud, elementen en door de gebruiker gegenereerde inhoud om meertalige websites te maken en te onderhouden. Om vertaalworkflows te automatiseren, integreert u de leveranciers van vertaaldiensten met AEM en creeert projecten voor het vertalen van inhoud in veelvoudige talen. AEM ondersteunt workflows voor het vertalen van mensen en machines.

* Menselijke vertaling: Inhoud wordt naar uw vertaalbureau verzonden en door professionele vertalers vertaald. Wanneer de vertaalde inhoud is voltooid, wordt deze geretourneerd en in AEM geïmporteerd. Wanneer uw vertaalbureau is geïntegreerd met AEM, wordt inhoud automatisch verzonden tussen AEM en de vertaalprovider.
* Machinevertaling: De vertaalservice van de computer zet uw inhoud onmiddellijk om.

Voor het vertalen van inhoud worden de volgende stappen uitgevoerd:

1. [Verbind AEM met uw leverancier](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider) van de vertaaldienst en [creeer configuraties](/help/sites-administering/tc-tic.md)van het vertaalintegratieframework.
1. [Koppel de pagina&#39;s van uw taalstramien](/help/sites-administering/tc-tic.md#configuring-pages-for-translation) aan de vertaalservice en frameworkconfiguraties.
1. [Identificeer het type inhoud](/help/sites-administering/tc-rules.md) dat u wilt vertalen.
1. [Bereid de inhoud voor vertaling](/help/sites-administering/tc-prep.md) voor door het taalstramien te ontwerpen en de basispagina&#39;s van taalkopieën te maken.
1. [Maak vertaalprojecten](/help/sites-administering/tc-manage.md) om de inhoud te verzamelen die u wilt vertalen en om het vertaalproces voor te bereiden.
1. Gebruik de vertaalprojecten om het vertaalproces [van de inhoud te](/help/sites-administering/tc-manage.md)beheren.

Als uw vertaalservicebureau geen aansluiting voor integratie met AEM biedt, ondersteunt AEM het handmatig extraheren en opnieuw invoegen van vertaalinhoud in XML-indeling.

>[!NOTE]
>
>Uw gebruiker moet een lid van de project-beheerders groep zijn om de eigenschappen van het Exemplaar van de Taal te gebruiken.

## Aanbevolen werkwijzen {#best-practices}

De pagina Aanbevolen werkwijzen voor [vertaling](/help/sites-administering/tc-bp.md) bevat belangrijke informatie over uw implementatie.
