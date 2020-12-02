---
title: SocialUtils Refactoring
seo-title: SocialUtils Refactoring
description: Het pakket com.adobe.cq.social.ugcbase.SocialUtils is vervangen in AEM 6.1
seo-description: Het pakket com.adobe.cq.social.ugcbase.SocialUtils is vervangen in AEM 6.1
uuid: 54a0d98e-5ead-4c12-850f-8252ea9b3263
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4ade0d6b-041e-4a2f-98f8-3b8fcae0fb29
translation-type: tm+mt
source-git-commit: 1429a099288f038510cb0a194fb55632297ef371
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# Refactoring voor sociale hulpmiddelen {#socialutils-refactoring}

## Pakket met sociale hulpmiddelen Vervangen {#socialutils-package-deprecated}

Het pakket `com.adobe.cq.social.ugcbase.SocialUtils` is afgekeurd in AEM 6.1.

In de volgende tabellen worden de methoden weergegeven die moeten worden gebruikt in plaats van de methoden `SocialUtils`.

## Pakket met socialeResourceUtilities {#socialresourceutilities-package}

| Methoden in com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities |
|---|
| Boolean checkPermission(ResourceResolver resolver, String path, String action) |  |
| SocialResourceProvider getSocialResourceProvider(resource) |  |
| SocialResourceConfiguration getStorageConfig (resource) |  |
| Resource getUGCResource(Resource userResource) |  |
| Resource getUGCResource(Resource userResource, ResourceResolverFactory rf) | new |
| Resource getUGCResource(Resource userResource, ResourceResolverFactory rf, String resourceTypeHint) | new |
| Resource getUGCResource(Resource userResource, String resourceTypeHint) |  |
| boolean hasModeratePermissions(Resource resource) |  |
| String resourceToACLPath(Resource resource) |  |
| String resourceToUGCStoragePath(Resource resource) | vervangt String resourceToUGCPath(Resource resource) |
| String UGCToResourcePath(Resource resource) |  |
| String UGCToResourcePath(String ugcPath) | methodehandtekening gewijzigd |
| String UGCToResourcePath(String ugcPath, ResourceResolver resolver) | new |

| Methoden in `com.adobe.cq.social.`utilities.resource.api.SocialResourceUtilities |
|---|
| SocialResourceProvider getSocialResourceProvider(resource) | vervangt SocialResourceProvider getConfiguredProvider(resource) |

## SCFUtilities Package {#scfutilities-package}

| Methoden in `com.adobe.cq.social.`utilities.scf.api.SCFUtilites |
|---|
| String getAvatar(UserProperties userProperties) |
| String getAvatar(UserProperties userProperties, int size) |
| String getAvatar(UserProperties userProperties, String absoluteDefaultAvatar) |
| String getAvatar(UserProperties userProperties, String absoluteDefaultAvatar, SocialUtils.AVATAR_SIZE size) |
| Page getConcontainingPage(resource) |
| String getSocialProfileURL(String-gebruikersnaam, ResourceResolver-oplosser, pagina) |
| UserProperties getUserProperties(ResourceResolver resolver, String userId) |

## Alleen voor intern gebruik {#for-internal-use-only}

| boolean canAddNode(Sessie, tekenreekspad) |
|---|
| String createUniqueNameHint(String message) |
| String createUniqueNameHint(String message, int numRandomChars) |
| String generateRandomString(int length) |
| SocialResourceConfiguration getDefaultStorageConfig() |
| Page getPage (String path, ResourceResolver resolver) |
| String getPagePath(Resource resource) |
| String getPagePath(String path) |
| String getResourceTypeForIncludedResource(Resource component, String defaultResourceType, String designPropertyName) |
| String getResourceTypeFromDesign(Resource resource, String styleProperty, String defaultValue) |
| boolean isResourceOwner(Resource resource) |
| String mapUGCPath(Resource resource) |
| String mapUGCPath(String ugcPath, ResourceResolver resolver) |
| boolean mayPost(ResourceResolver resolver, Resource resource) |
| String prepareUserGeneratedContent(ResourceResolver resolver, String path) |

## Methoden niet meer beschikbaar {#methods-no-longer-available}

| Node createNode(ResourceResolver resolver, String path, String nodeType) |
|---|
| Resource getResourceAtPath(ResourceResolver resolver, String path) |
| Resource getResourceAtPath(ResourceResolver resolver, String path, String resourceType) |
| Configuration getStorageCloudServiceConfig(Resource resource) |
| TranslationManager getTranslationManager() |
| TranslationSaveQueue getTranslationSaveQueue() |
| boolean mayAccessUGC(ResourceResolver resolver) |

