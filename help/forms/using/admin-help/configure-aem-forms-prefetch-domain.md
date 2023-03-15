---
title: Formulieren configureren AEM Prefetchdomain-informatie
seo-title: Configure AEM forms to prefetchdomain information
description: Vorm AEM vormen om domeininformatie vooraf in te stellen als u een langzamere reactietijd wegens diep genestelde groepen ervaart of als u een lid van vele groepen bent.
seo-description: Configure AEM forms to prefetch domain information if you experience a slower response time due to deeply nested groups or if you are a member of many groups.
uuid: 53c8995e-3f9d-42e8-9f75-cee7debe6ce1
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f9a3f897-90c6-4942-8a86-aae510298f2a
exl-id: cf5283a5-dbfb-460d-a8bd-11cd15ab8640
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Formulieren configureren AEM Prefetchdomain-informatie {#configure-aem-forms-to-prefetchdomain-information}

De gebruikers kunnen een langzamere reactietijd ervaren als zij tot vele groepen (bijvoorbeeld, 500 of meer) behoren of als de groepen diep worden genesteld (bijvoorbeeld, 30 niveaus). Als dit probleem optreedt, kunt u AEM formulieren zo configureren dat de gegevens in bepaalde domeinen vooraf worden opgehaald.

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Configuration > Import And Export Configuration Files]**.
1. Als u de huidige configuratie-instelling wilt exporteren naar een bestand, klikt u op **[!UICONTROL Export]** en sla het configuratiebestand op een andere locatie op.
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

   In dit voorbeeld worden meerdere domeinen geconfigureerd voor prefetch. De domeinnamen worden gescheiden door een &quot;/&quot;. Dit wordt in het bovenstaande voorbeeld getoond met *Domain_Name1*, *Domain_Name2*, en *Domain_Name3*.

1. Als u het bijgewerkte bestand wilt importeren, klikt u in Gebruikersbeheer op **[!UICONTROL Configuration > Import And Export Configuration Files]**.
1. Klikken **[!UICONTROL Browse]** om het bestand te zoeken, klikt u op Importeren en vervolgens op **[!UICONTROL OK]**.
