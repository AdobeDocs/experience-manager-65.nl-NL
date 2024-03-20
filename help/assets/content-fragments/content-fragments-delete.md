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

1. **Het inhoudsfragment als één entiteit.**

   * **Hoofdletters gebruiken**: Een gebruiker die een inhoudsfragment moet bewerken/bijwerken - **en verwijder een volledig fragment**.
   * **Machtigingen**: De [Verwijderen](/help/sites-administering/security.md#actions) toestemming kan [toegewezen via gebruikers- en/of groepsbeheer](/help/sites-administering/security.md#managing-permissions).

2. **De meerdere subentiteiten waaruit een inhoudsfragment bestaat, bijvoorbeeld variaties, subknooppunten.**

   De basiswerking van de inhoudfragment-editor vereist dat dergelijke tijdelijke subelementen kunnen worden verwijderd. Bijvoorbeeld bij het manipuleren van variaties, ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

   * **Hoofdletters gebruiken**: Een gebruiker die een inhoudsfragment moet bewerken/bijwerken - **zonder dat een volledig fragment mag worden verwijderd**.
   * **Machtigingen**: Zie [Machtigingen alleen vereist voor Editor-functionaliteit](#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Wanneer een gebruiker geen [Verwijderen](/help/sites-administering/security.md#actions) machtigingen, de Content Fragment-editor werkt in *alleen-lezen* -modus.

>[!NOTE]
>
>Zie ook [Hoe te om de Verrichtingen van het Beheer van de Gebruiker in AEM te controleren](/help/sites-administering/audit-user-management-operations.md).

## Machtigingen alleen vereist voor Editor-functionaliteit {#permissions-required-for-editor-functionality-only}

Voor gebruikers die een contentfragment moeten bewerken of bijwerken, **zonder hun toe te staan om een volledig fragment te verwijderen**, moeten specifieke machtigingen worden toegewezen, aangezien de basisbewerking van de contentfragmenteditor vereist dat tijdelijke subelementen kunnen worden verwijderd.

Bijvoorbeeld bij het manipuleren van variaties, ook bij het bewerken van metagegevens of het beheren van bijbehorende inhoud.

>[!NOTE]
>
>De machtigingen voor verwijderen die vereist zijn om een inhoudsfragment te bewerken/bij te werken, worden opgenomen in de machtiging Verwijderen. [toegewezen via gebruikers- en/of groepsbeheer](/help/sites-administering/security.md#managing-permissions).

De machtigingen die nodig zijn om een fragment te bewerken/bij te werken, moeten worden toegepast op het knooppunt met het inhoudsfragment of op een geschikt bovenliggend knooppunt (op elk niveau onder `/content/dam`). Wanneer toegewezen aan een dergelijk bovenliggend knooppunt, worden de machtigingen toegepast op alle knooppunten in die vertakking.

Bijvoorbeeld een map die alle inhoudsfragmenten bevat, zoals:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Machtigingen instellen op `/content/dam` is ook mogelijk, omdat alle inhoudsfragmenten hier worden opgeslagen.
>
>Deze handeling past echter dezelfde verwijdermachtigingen toe op *alles* ook andere soorten activa.

U kunt een inhoudsfragment alleen bewerken/bijwerken als een specifieke gebruiker en/of groep de volgende machtigingen heeft:

>[!NOTE]
>
>In deze lijst worden alle vereiste rechten weergegeven, niet alleen de verwijderingsrechten.

* Voor knooppunten of mappen van inhoudsfragment:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Voor de `jcr:content`knooppunt van alle inhoudsfragmenten:

   * `jcr:addChildNodes`, `jcr:modifyProperties` en `jcr:removeChildNodes`

* Voor alle onderstaande knooppunten `jcr:content` van alle inhoudsfragmenten:

   * `jcr:addChildNodes`, `jcr:modifyProperties` en `jcr:removeChildNodes`, `jcr:removeNode`

Deze `remove` rechten moeten [beheerd met behulp van Access Control Lists, binnen CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management).

De `add` en `modify` U kunt ook rechten beheren in CRXDE Lite of via de gebruikersbeheerconsole.

De definitie van bijvoorbeeld `remove` rechten voor een groep `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)
