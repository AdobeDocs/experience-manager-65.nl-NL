---
title: Contentfragmenten - Overwegingen verwijderen
seo-title: Contentfragmenten - Overwegingen verwijderen
description: Contentfragmenten - Overwegingen verwijderen
seo-description: Contentfragmenten - Overwegingen verwijderen
uuid: e7ac1809-159f-4d02-ad30-dc6c246e8a04
contentOwner: aheimoz
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: ec21237f-9186-49b4-8039-99df4db7c14a
docset: aem65
translation-type: tm+mt
source-git-commit: a430c4de89bde3b907d342106465d3b5a7c75cc8
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 12%

---


# Contentfragmenten - Overwegingen verwijderen{#content-fragments-delete-considerations}

## Machtigingen - {#permissions-delete-or-not-delete} verwijderen of niet verwijderen

De capaciteit om inhoud te schrappen is krachtig, maar potentieel gevoelig, met vele industrieën die moeten beperken en controleren hoe deze voorrechten worden verdeeld.

Met betrekking tot het schrappen van toestemmingen, moeten de Fragmenten van de Inhoud op twee niveaus worden overwogen:

1. **Het inhoudsfragment als één entiteit.**

   * **Hoofdlettergebruik**: Een gebruiker die een inhoudsfragment moet bewerken/bijwerken -  **en een volledig fragment** moet verwijderen.
   * **Machtigingen**: De  [](/help/sites-administering/security.md#actions) machtiging Verwijderen kan worden  [toegewezen via Gebruiker en/of Groepsbeheer](/help/sites-administering/security.md#managing-permissions).

1. **De meerdere subentiteiten waaruit een inhoudsfragment bestaat; bijvoorbeeld variaties, subknooppunten.**

   De basiswerking van de inhoudfragment-editor vereist dat dergelijke tijdelijke subelementen kunnen worden verwijderd. Bijvoorbeeld bij het manipuleren van variaties; ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

   * **Hoofdlettergebruik**: Een gebruiker die een inhoudsfragment moet bewerken/bijwerken -  **zonder dat het is toegestaan een volledig fragment** te verwijderen.
   * **Machtigingen**: Zie  [Machtigingen vereist voor alleen](/help/assets/content-fragments/content-fragments-delete.md#permissions-required-for-editor-functionality-only) bewerkingsfunctionaliteit.

>[!NOTE]
>
>Wanneer een gebruiker geen [Delete](/help/sites-administering/security.md#actions) toestemmingen heeft, werkt de redacteur van het Fragment van de Inhoud op *read-only* wijze.

>[!NOTE]
>
>Zie ook [Gebruikersbeheerbewerkingen in AEM](/help/sites-administering/audit-user-management-operations.md) controleren.

## Machtigingen alleen vereist voor bewerkingsfunctionaliteit {#permissions-required-for-editor-functionality-only}

Voor gebruikers die een contentfragment moeten bewerken of bijwerken, **zonder hun toe te staan om een volledig fragment te verwijderen**, moeten specifieke machtigingen worden toegewezen, aangezien de basisbewerking van de contentfragmenteditor vereist dat tijdelijke subelementen kunnen worden verwijderd.

Bijvoorbeeld bij het manipuleren van variaties; ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

>[!NOTE]
>
>De verwijdermachtigingen, die vereist zijn om een inhoudsfragment te bewerken/bij te werken, worden opgenomen in de machtiging [Verwijderen die is toegewezen via Gebruiker en/of Groepsbeheer](/help/sites-administering/security.md#managing-permissions).

De machtigingen die nodig zijn om een fragment te bewerken/bij te werken, moeten worden toegepast op het knooppunt met het inhoudsfragment of op een geschikt bovenliggend knooppunt (op elk niveau onder `/content/dam`). Wanneer toegewezen aan een dergelijk bovenliggend knooppunt, worden de machtigingen toegepast op alle knooppunten in die vertakking.

Bijvoorbeeld een map die alle inhoudsfragmenten bevat, zoals:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Het is ook mogelijk de machtigingen voor `/content/dam` in te stellen, aangezien alle inhoudsfragmenten hier worden opgeslagen.
>
>Met deze handeling worden echter dezelfde verwijdermachtigingen ook toegepast op andere elementtypen *all*.

U kunt een inhoudsfragment alleen bewerken/bijwerken als een specifieke gebruiker en/of groep de volgende machtigingen heeft:

>[!NOTE]
>
>In deze lijst worden alle vereiste rechten weergegeven, niet alleen de verwijderingsrechten.

* Voor de knooppunten of mappen van het inhoudsfragment:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Voor het `jcr:content`knooppunt van alle inhoudsfragmenten:

   * `jcr:addChildNodes`,  `jcr:modifyProperties` en  `jcr:removeChildNodes`

* Voor alle knooppunten onder `jcr:content` van alle inhoudsfragmenten:

   * `jcr:addChildNodes`,  `jcr:modifyProperties` en  `jcr:removeChildNodes`,  `jcr:removeNode`

Deze `remove` voorrechten moeten [worden beheerd gebruikend de Lijsten van het Toegangsbeheer, binnen CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management).

De `add` en `modify` voorrechten kunnen ook in CRXDE Lite worden beheerd, of het gebruiken van de console van het Beheer van de Gebruiker.

Bijvoorbeeld, de definitie van `remove` voorrechten voor een groep `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)

