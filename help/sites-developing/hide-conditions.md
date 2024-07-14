---
title: Voorwaarden verbergen gebruiken
description: De voorwaarden van de huid kunnen worden gebruikt om te bepalen als een componentenmiddel wordt teruggegeven of niet.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
exl-id: 65f5d5e1-ac11-4a3c-8a51-ce06a741c264
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Voorwaarden verbergen gebruiken {#using-hide-conditions}

De voorwaarden van de huid kunnen worden gebruikt om te bepalen als een componentenmiddel wordt teruggegeven of niet. Een voorbeeld van dit zou zijn wanneer een malplaatjeauteur de de lijstcomponent van de Component van de Kern [ ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html) in de [ malplaatjedacteur ](/help/sites-authoring/templates.md) vormt en besluit om de opties onbruikbaar te maken om de lijst te bouwen die op kindpagina&#39;s wordt gebaseerd. Als u deze optie in het dialoogvenster Ontwerp uitschakelt, wordt een eigenschap zo ingesteld dat wanneer de component List wordt gerenderd, de voorwaarde hide wordt geëvalueerd en de optie om onderliggende pagina&#39;s weer te geven niet wordt weergegeven.

## Overzicht {#overview}

Dialoogvensters kunnen complex worden met talrijke opties voor de gebruiker, die slechts een fractie van de opties kan gebruiken die tot zijn beschikking staan. Dit kan leiden tot een overweldigende ervaring voor de gebruikersinterface.

Door huidenvoorwaarden te gebruiken, hebben de beheerders, de ontwikkelaars, en de super gebruikers een manier om middelen te verbergen die op een reeks regels worden gebaseerd. Met deze functie kunnen ze bepalen welke bronnen moeten worden weergegeven wanneer een auteur inhoud bewerkt.

>[!NOTE]
>
>Het verbergen van een middel dat op een uitdrukking wordt gebaseerd vervangt ACL geen toestemmingen. De inhoud blijft bewerkbaar, maar wordt niet weergegeven.

## Implementatie- en gebruiksgegevens {#implementation-and-usage-details}

`com.adobe.granite.ui.components.FilteringResourceWrapper` is verantwoordelijk voor het filteren van de bronnen op basis van het bestaan en de waarde van de eigenschap `granite:hide` , die zich in het te filteren veld bevindt. De implementatie van `/libs/cq/gui/components/authoring/dialog/dialog.jsp` bevat een instantie van `FilteringResourceWrapper.`

De implementatie maakt gebruik van graniet [ ELResolver API ](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/docs/server/el.html) en voegt een `cqDesign` douanevariabele via ExpressionCustomizer toe.

Hier volgen enkele voorbeelden van verbergingsvoorwaarden voor een ontwerpknooppunt onder `etc/design` of als een inhoudsbeleid.

```
${cqDesign.myProperty}
${!cqDesign.myProperty}
${cqDesign.myProperty == 'someText'}
${cqDesign.myProperty != 'someText'}
${cqDesign.myProperty == true}
${cqDesign.myProperty == true}
${cqDesign.property1 == 'someText' && cqDesign.property2 || cqDesign.property3 != 1 || header.myHeader}
```

Houd rekening met het volgende wanneer u de expressie hide definieert:

* Om geldig te zijn, moet het bereik waarin de eigenschap wordt gevonden, worden uitgedrukt (bijvoorbeeld `cqDesign.myProperty` ).
* Waarden zijn alleen-lezen.
* De functies (indien nodig) moeten beperkt blijven tot een bepaalde reeks die door de dienst wordt geleverd.

## Voorbeeld {#example}

De voorbeelden van verborgen voorwaarden kunnen door AEM en de [ kerncomponenten ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in het bijzonder worden gevonden. Bijvoorbeeld, overweeg de [ component van de lijstkern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html).

[ Gebruikend de malplaatjeredacteur ](/help/sites-authoring/templates.md), kan de malplaatjeauteur in de ontwerpdialoog bepalen welke opties van de lijstcomponent die aan de paginaauteur beschikbaar zijn. U kunt bijvoorbeeld instellen of de lijst een statische lijst moet zijn, of een lijst met onderliggende pagina&#39;s, een lijst met gecodeerde pagina&#39;s enzovoort, moet worden in- of uitgeschakeld.

Als een sjabloonauteur ervoor kiest de optie voor onderliggende pagina&#39;s uit te schakelen, wordt een ontwerpeigenschap ingesteld en wordt een voorwaarde voor verbergen aan de hand hiervan geëvalueerd. Hierdoor wordt de optie niet gerenderd voor de auteur van de pagina.

1. Door gebrek, kan de paginaauteur de component van de lijstkern gebruiken om een lijst te bouwen gebruikend kindpagina&#39;s door de optie **Pagina&#39;s van het Kind te kiezen**.

   ![ chlimage_1-218 ](assets/chlimage_1-218.png)

1. In de ontwerpdialoog van de component van de lijstkern, kan de malplaatjeauteur de optie **kiezen maakt Kinderen** onbruikbaar om de optie te verhinderen om een lijst te produceren die op kindpagina&#39;s wordt gebaseerd aan de paginaauteur worden getoond.

   ![ chlimage_1-219 ](assets/chlimage_1-219.png)

1. Een beleidsknooppunt wordt gemaakt onder `/conf/we-retail/settings/wcm/policies/weretail/components/content/list` met een eigenschap `disableChildren` ingesteld op `true` .
1. De voorwaarde hide wordt gedefinieerd als de waarde van een eigenschap `granite:hide` in het knooppunt met dialoogeigenschappen `/conf/we-retail/settings/wcm/policies/weretail/components/content/list`

   ![ chlimage_1-220 ](assets/chlimage_1-220.png)

1. De waarde van `disableChildren` wordt uit de ontwerpconfiguratie gehaald en de expressie `${cqDesign.disableChildren}` evalueert naar `false` , wat betekent dat de optie niet wordt gerenderd als onderdeel van de component.

   U kunt de huidenuitdrukking als waarde van het `granite:hide` bezit [ in GitHub hier ](https://github.com/adobe/aem-core-wcm-components/blob/main/content/src/content/jcr_root/apps/core/wcm/components/list/v1/list/_cq_dialog/.content.xml#L40) bekijken.

1. De optie **Pagina&#39;s van het Kind** wordt niet meer teruggegeven voor de paginaauteur wanneer het gebruiken van de lijstcomponent.

   ![ chlimage_1-221 ](assets/chlimage_1-221.png)
