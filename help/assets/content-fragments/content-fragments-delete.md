---
title: Inhoudsfragmenten - Overwegingen verwijderen
description: Herzie deze belangrijke overwegingen alvorens uw beleid van de schrapping van de Fragmenten van de Inhoud in AEM te bepalen. Inhoudsfragmenten zijn een krachtig hulpmiddel voor het afleveren van inhoud zonder kop en de implicaties van het verwijderen ervan moeten zorgvuldig worden overwogen.
feature: Content Fragments
role: User
exl-id: 6212457e-a171-4c33-8d19-54c26516e981
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 7%

---

# Inhoudsfragmenten - Overwegingen verwijderen {#content-fragments-delete-considerations}

Herzie deze belangrijke overwegingen alvorens uw beleid van de schrapping van de Fragmenten van de Inhoud in AEM te bepalen. Inhoudsfragmenten zijn een krachtig hulpmiddel voor het afleveren van inhoud zonder kop en de implicaties van het verwijderen ervan moeten zorgvuldig worden overwogen.

## Machtigingen - Verwijderen of Niet verwijderen {#permissions-delete-or-not-delete}

De capaciteit om inhoud te schrappen is krachtig, maar potentieel gevoelig, met vele industrieën die moeten beperken en controleren hoe deze voorrechten worden verdeeld.

Met betrekking tot schrappingstoestemmingen, moeten de Fragmenten van de Inhoud op twee niveaus worden overwogen:

1. **het Fragment van de Inhoud als één enkele entiteit.**

   * **geval van het Gebruik**: Een gebruiker die een inhoudsfragment - **moet uitgeven/bijwerken en een volledig fragment** schrappen.
   * **Toestemmingen**: De [ schrapping ](/help/sites-administering/security.md#actions) toestemming kan [ door Gebruiker en/of het Beheer van de Groep ](/help/sites-administering/security.md#managing-permissions) worden toegewezen.

2. **de veelvoudige sub-entiteiten die omhoog een inhoudsfragment maken; bijvoorbeeld, variaties, sub-knopen.**

   De basiswerking van de inhoudfragment-editor vereist dat dergelijke tijdelijke subelementen kunnen worden verwijderd. Bijvoorbeeld bij het manipuleren van variaties, ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

   * **geval van het Gebruik**: Een gebruiker die een inhoudsfragment moet uitgeven/bijwerken - **zonder het worden toegestaan om een volledig fragment** te schrappen.
   * **Toestemmingen**: Zie [ Toestemmingen die voor de Functionaliteit van de Redacteur slechts ](#permissions-required-for-editor-functionality-only) worden vereist.

>[!NOTE]
>
>Wanneer een gebruiker geen [&#128279;](/help/sites-administering/security.md#actions) toestemmingen van de Schrapping heeft, werkt de redacteur van het Fragment van de Inhoud op *read-only* wijze.

>[!NOTE]
>
>Zie ook [ hoe te de Verrichtingen van het Beheer van de Gebruiker in AEM ](/help/sites-administering/audit-user-management-operations.md) controleren.

## Machtigingen alleen vereist voor Editor-functionaliteit {#permissions-required-for-editor-functionality-only}

Voor gebruikers die een contentfragment moeten bewerken of bijwerken, **zonder hun toe te staan om een volledig fragment te verwijderen**, moeten specifieke machtigingen worden toegewezen, aangezien de basisbewerking van de contentfragmenteditor vereist dat tijdelijke subelementen kunnen worden verwijderd.

Bijvoorbeeld bij het manipuleren van variaties, ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

>[!NOTE]
>
>De schrappingstoestemmingen, die worden vereist om een Fragment van de Inhoud uit te geven/bij te werken, zijn inbegrepen in de toestemming van de Schrapping [ die door Gebruiker en/of het Beheer van de Groep ](/help/sites-administering/security.md#managing-permissions) wordt toegewezen.

De machtigingen die nodig zijn om een fragment te bewerken/bij te werken, moeten worden toegepast op het knooppunt met het inhoudsfragment of op een geschikt bovenliggend knooppunt (op elk niveau onder `/content/dam`). Wanneer toegewezen aan een dergelijk bovenliggend knooppunt, worden de machtigingen toegepast op alle knooppunten in die vertakking.

Bijvoorbeeld een map die alle inhoudsfragmenten bevat, zoals:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Het is ook mogelijk de machtigingen voor `/content/dam` in te stellen, aangezien alle inhoudsfragmenten hier worden opgeslagen.
>
>Nochtans past deze actie de zelfde schrappingstoestemmingen op *alle* andere activa types eveneens toe.

U kunt een inhoudsfragment alleen bewerken/bijwerken als een specifieke gebruiker en/of groep de volgende machtigingen heeft:

>[!NOTE]
>
>In deze lijst worden alle vereiste rechten weergegeven, niet alleen de verwijderingsrechten.

* Voor knooppunten of mappen van inhoudsfragment:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Voor de `jcr:content` knoop van alle Fragmenten van de Inhoud:

   * `jcr:addChildNodes` , `jcr:modifyProperties` and `jcr:removeChildNodes`

* Voor alle knooppunten onder `jcr:content` van alle inhoudsfragmenten:

   * `jcr:addChildNodes` , `jcr:modifyProperties` and `jcr:removeChildNodes` , `jcr:removeNode`

Deze `remove` voorrechten moeten [ worden beheerd gebruikend de Lijsten van het Toegangsbeheer, binnen CRXDE Lite ](/help/sites-administering/user-group-ac-admin.md#access-right-management).

De `add` - en `modify` -rechten kunnen ook worden beheerd in CRXDE Lite of via de gebruikersbeheerconsole.

De definitie van de `remove` bevoegdheden voor een groep `content-authors-no-delete` is bijvoorbeeld:

![ cf-schrapping-03 ](assets/cf-delete-03.png)
