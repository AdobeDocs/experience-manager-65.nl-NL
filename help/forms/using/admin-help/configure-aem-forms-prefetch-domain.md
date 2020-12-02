---
title: Formulieren configureren AEM Prefetchdomain-informatie
seo-title: Formulieren configureren AEM Prefetchdomain-informatie
description: Vorm AEM vormen om domeininformatie vooraf in te stellen als u een langzamere reactietijd wegens diep genestelde groepen ervaart of als u een lid van vele groepen bent.
seo-description: Vorm AEM vormen om domeininformatie vooraf in te stellen als u een langzamere reactietijd wegens diep genestelde groepen ervaart of als u een lid van vele groepen bent.
uuid: 53c8995e-3f9d-42e8-9f75-cee7debe6ce1
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f9a3f897-90c6-4942-8a86-aae510298f2a
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---


# Formulieren configureren AEM Prefetchdomeingegevens {#configure-aem-forms-to-prefetchdomain-information}

De gebruikers kunnen een langzamere reactietijd ervaren als zij tot vele groepen (bijvoorbeeld, 500 of meer) behoren of als de groepen diep worden genesteld (bijvoorbeeld, 30 niveaus). Als dit probleem optreedt, kunt u AEM formulieren zo configureren dat de gegevens in bepaalde domeinen vooraf worden opgehaald.

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Configuration > Import And Export Configuration Files]**.
1. Als u de huidige configuratie-instelling naar een bestand wilt exporteren, klikt u op **[!UICONTROL Export]** en slaat u het configuratiebestand op een andere locatie op.
1. Voeg het volgende knooppunt toe (vet gemarkeerd):

   ```xml
    <node name="UM">
    <map/>
    <node name="PrincipalCache">
        <map>
            <entry key="principalCacheSize" value="1000"/>
            <entry key="principalCacheBatchFetchSize" value="10"/>
            <entry key="rebuildCacheAfterSync" value="true />
            <entry key="enableFullPrefetch" value="false"/>
            <entry key="principalCacheDomains" value="Domain_Name1/Domain_Name2/Domain_Name3"/>
        <map>
    </node>
    <node name="APSAuditService">
   ```

   In dit voorbeeld worden meerdere domeinen geconfigureerd voor prefetch. De domeinnamen worden gescheiden door een &quot;/&quot;. Dit wordt getoond in het voorbeeld hierboven met *Domain_Name1*, *Domain_Name2*, en *Domain_Name3*.

1. Klik in Gebruikersbeheer op **[!UICONTROL Configuration > Import And Export Configuration Files]** om het bijgewerkte bestand te importeren.
1. Klik **[!UICONTROL Browse]** om het dossier te vinden, de Invoer te klikken, en dan **[!UICONTROL OK]** te klikken.

