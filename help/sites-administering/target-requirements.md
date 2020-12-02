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
source-git-commit: 70b18dbe351901abb333d491dd06a6c1c1c569d6
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---


# Vereisten voor integratie met Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Als deel van [integratie van AEM en Adobe Target](/help/sites-administering/target.md), moet u bij Adobe Target registreren, de replicatieagent, en veilige activiteitenmontages op publiceren knoop vormen.

## Registreren bij Adobe Target {#registering-with-adobe-target}

Als u AEM wilt integreren met Adobe Target, hebt u een geldig Adobe Target-account nodig. Voor dit account moeten minimaal **fiatteurs**-machtigingen zijn ingesteld. Wanneer u zich bij Adobe Target registreert, ontvangt u een clientcode. U hebt de clientcode en uw Adobe Target-aanmeldingsnaam en -wachtwoord nodig om verbinding te maken AEM met Adobe Target.

De clientcode identificeert de Adobe Target-klantenaccount wanneer de Adobe Target-server wordt aangeroepen.

>[!NOTE]
>
>Uw account moet ook door het Target-team zijn ingeschakeld om de integratie te kunnen gebruiken.
>
>Als dit niet het geval is, gelieve [Adobe klantenZorg ](https://docs.adobe.com/content/help/en/target/using/cmp-resources-and-contact-information.html) te contacteren.

## Het toelaten van de Agent van de Replicatie van het Doel {#enabling-the-target-replication-agent}

De test en het Doel [replicatieagent](/help/sites-deploying/replication.md) moet op de auteursinstantie worden toegelaten. Merk op dat deze replicatieagent niet door gebrek wordt toegelaten als u [nosamplcontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) uitvoeringswijze voor het installeren van AEM gebruikte. Voor meer informatie over het beveiligen van uw productiemilieu, zie [Controlelijst van de Veiligheid](/help/sites-administering/security-checklist.md).

1. Klik of tik op **Tools** > **Implementatie** > **Replication** op de AEM startpagina.
1. Klik of tik **Agenten op Auteur**.
1. Klik of tik **Test en Doel (test en doel)** replicatieagent, en klik of tik dan **Edit**.
1. Selecteer de optie Ingeschakeld en klik of tik op **OK**.

   >[!NOTE]
   >
   >Wanneer u de de replicatieagent van de Test en van het Doel vormt, op **Vervoer** lusje, wordt URI geplaatst door gebrek aan **tnt:///**. Vervang deze URI niet door **https://admin.testandtarget.omniture.com**.
   >
   >Houd er rekening mee dat als u de verbinding probeert te testen met **tnt:///**, er een fout optreedt. Dit wordt verwacht gedrag aangezien dit URI voor intern gebruik slechts is en niet met **Verbinding van de Test** zou moeten worden gebruikt.

## Het knooppunt Activiteitsinstellingen {#securing-the-activity-settings-node} beveiligen

U moet het knooppunt activity settings **cq:ActivitySettings** op de publicatie-instantie beveiligen zodat dit niet toegankelijk is voor normale gebruikers. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.

Het **cq:ActivitySettings**-knooppunt is beschikbaar in de CRXDE-lijst onder `/content/campaigns/*nameofbrand*`* *onder de activity jcr:content node;* *bijvoorbeeld `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Dit knooppunt wordt alleen gemaakt nadat u een component als doel hebt ingesteld.

De **cq:ActivitySettings** knoop onder jcr van de activiteit:inhoud wordt beschermd door volgende ACLs:

* Alles weigeren voor iedereen
* jcr:read,rep:write toestaan voor &#39;target-activity-authors&#39; (de auteur is lid van deze groep uit de doos)
* jcr:read,rep:write voor &quot;targetService&quot; toestaan

Met deze instellingen zorgt u ervoor dat normale gebruikers geen toegang hebben tot de knoopeigenschappen. Gebruik zelfde ACLs op auteur en bij publiceren. Zie [Gebruikersbeheer en beveiliging](/help/sites-administering/security.md) voor meer informatie.

## Het vormen van de AEM Verbinding Externalzer {#configuring-the-aem-link-externalizer}

Wanneer u een activiteit bewerkt in Adobe Target, verwijst de URL naar **localhost**, tenzij u de URL wijzigt op het AEM auteurknooppunt. U kunt AEM Verbinding Externalzer vormen als u de uitgevoerde inhoud aan specifiek *publish* domein wilt richten.

>[!NOTE]
>
>Zie ook [Cloud Configuration toevoegen](/help/sites-administering/experience-fragments-target.md#add-the-cloud-configuration).

De AEM-externalizer configureren:

>[!NOTE]
>
>Zie [URL&#39;s extern maken](/help/sites-developing/externalizer.md) voor meer informatie.

1. Navigeer naar de OSGi-webconsole op **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Zoek **Day CQ Link Externalzer** en voer het domein voor het auteurknooppunt in.

   ![chlimage_1-120](assets/aem-externalizer-01.png)

