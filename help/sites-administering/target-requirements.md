---
title: Vereisten voor integratie met Adobe Target
seo-title: Vereisten voor integratie met Adobe Target
description: Lees meer over de voorwaarden voor integratie met Adobe Target.
seo-description: Lees meer over de voorwaarden voor integratie met Adobe Target.
uuid: 55d87a96-5fe7-4f7e-93c1-fdf7fbb7c971
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: ae4a6e97-c0d7-472d-a25f-b89b1abf4df3
docset: aem65
translation-type: tm+mt
source-git-commit: 4b965d8f7814816126601f6366c1ba313e404538

---


# Vereisten voor integratie met Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Als onderdeel van de [integratie van AEM en Adobe Target](/help/sites-administering/target.md)moet u zich registreren bij Adobe Target, de replicatieagent configureren en activiteiteninstellingen op het publicatieknooppunt beveiligen.

## Registreren bij Adobe Target {#registering-with-adobe-target}

U moet een geldig Adobe Target-account hebben om AEM te kunnen integreren met Adobe Target. Deze account moet minimaal **toegangsrechten op het niveau van de fiatteur** hebben. Wanneer u zich bij Adobe Target registreert, ontvangt u een clientcode. U hebt de clientcode en uw Adobe Target-aanmeldnaam en -wachtwoord nodig om verbinding te maken met AEM voor Adobe Target.

De clientcode identificeert de Adobe Target-klantaccount wanneer de Adobe Target-server wordt aangeroepen.

>[!NOTE]
>
>Uw account moet ook door het Target-team zijn ingeschakeld om de integratie te kunnen gebruiken.
>
>
>Neem contact op met de klantenservice [van](https://marketing.adobe.com/resources/help/en_US/target/target/r_problem.html)Adobe Target als dit niet het geval is.

## Toelatend de Agent van de Replicatie van het Doel {#enabling-the-target-replication-agent}

De test en de [replicatieagent](/help/sites-deploying/replication.md) van het Doel moet op de auteursinstantie worden toegelaten. Merk op dat deze replicatieagent niet door gebrek wordt toegelaten als u de [nosamplcontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) looppas wijze voor het installeren van AEM gebruikte. Raadpleeg de lijst [Beveiligingscontrole](/help/sites-administering/security-checklist.md)voor meer informatie over het beveiligen van uw productieomgeving.

1. Klik of tik op **Extra** > **Implementatie** > **Replicatie** op de AEM-startpagina.
1. Klik of tik **Agenten op Auteur**.
1. Klik of tik de **Test en (test en doel)** replicatieagent van het Doel, en klik of tik dan **uitgeven**.
1. Selecteer de optie Ingeschakeld en klik of tik op **OK**.

   >[!NOTE]
   >
   >Wanneer u de de replicatieagent van de Test en van het Doel vormt, op het lusje van het **Vervoer** , wordt URI geplaatst door gebrek aan **tnt:///**. Vervang deze URI niet door **https://admin.testandtarget.omniture.com**.
   >
   >Houd er rekening mee dat als u de verbinding probeert te testen met **tnt:///**, dit een fout veroorzaakt. Dit wordt verwacht aangezien dit URI voor intern gebruik slechts is en niet met de Verbinding **van de** Test zou moeten worden gebruikt.

## Het knooppunt Activiteitsinstellingen beveiligen {#securing-the-activity-settings-node}

U moet het knooppunt activity settings (activity settings) **cq:ActivitySettings** op de publicatie-instantie beveiligen, zodat dit niet toegankelijk is voor normale gebruikers. Het knooppunt met activiteiteninstellingen mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt naar Adobe Target.

**Het knooppunt** cq:ActivitySettings`/content/campaigns/*nameofbrand*` is beschikbaar in de CRXDE-lijst onder *** onder het knooppunt activities jcr:content. *bijvoorbeeld `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Dit knooppunt wordt alleen gemaakt nadat u een component als doel hebt ingesteld.

De **cq:ActivitySettings** knoop onder jcr van de activiteit:inhoud wordt beschermd door volgende ACLs:

* Alles weigeren voor iedereen
* jcr:read,rep:write toestaan voor &#39;target-activity-authors&#39; (de auteur is lid van deze groep uit de doos)
* jcr:read,rep:write voor &quot;targetService&quot; toestaan

Met deze instellingen zorgt u ervoor dat normale gebruikers geen toegang hebben tot de knoopeigenschappen. Gebruik zelfde ACLs op auteur en bij publiceren. Zie [Gebruikersbeheer en Beveiliging](/help/sites-administering/security.md) voor meer informatie.

## De AEM Link Externalzer configureren {#configuring-the-aem-link-externalizer}

Wanneer u een activiteit bewerkt in Adobe Target, verwijst de URL naar de **localhost** , tenzij u de URL wijzigt in het auteurknooppunt van AEM. U kunt de AEM-koppelingsextern instellen als u wilt dat de geëxporteerde inhoud naar een specifiek *publicatiedomein* verwijst.

>[!NOTE]
>
>Zie ook Cloud Configuration [toevoegen](/help/sites-administering/experience-fragments-target.md#add-the-cloud-configuration).

De AEM-externalizer configureren:

>[!NOTE]
>
>Zie URL&#39;s [extern maken voor meer informatie](/help/sites-developing/externalizer.md).

1. Navigeer naar de OSGi-webconsole op **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Zoek **de Verbinding Externalzer** van CQ van de Dag en ga het domein voor de auteursknoop in.

   ![chlimage_1-120](assets/aem-externalizer-01.png)

