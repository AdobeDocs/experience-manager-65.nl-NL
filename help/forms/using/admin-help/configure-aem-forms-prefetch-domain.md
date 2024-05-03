---
title: Formulieren configureren AEM Prefetchdomain-informatie
description: Vorm AEM vormen om domeininformatie vooraf in te stellen als u een langzamere reactietijd wegens diep genestelde groepen ervaart of als u een lid van vele groepen bent.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: cf5283a5-dbfb-460d-a8bd-11cd15ab8640
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Formulieren configureren AEM Prefetchdomain-informatie {#configure-aem-forms-to-prefetchdomain-information}

De gebruikers kunnen een langzamere reactietijd ervaren als zij tot vele groepen (bijvoorbeeld, 500 of meer) behoren of als de groepen diep worden genesteld (bijvoorbeeld, 30 niveaus). Als dit probleem optreedt, kunt u AEM formulieren zo configureren dat de gegevens in bepaalde domeinen vooraf worden opgehaald.

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Configuration > Import And Export Configuration Files]**.
1. Klik op **[!UICONTROL Export]** en sla het configuratiebestand op een andere locatie op.
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
