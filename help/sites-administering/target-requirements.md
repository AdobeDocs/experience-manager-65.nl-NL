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

Als deel van de [integratie van AEM en Adobe Target](/help/sites-administering/target.md), moet u bij Adobe Target registreren, de replicatieagent vormen, en activiteitenmontages op het publicatieknooppunt beveiligen.

## Registreren bij Adobe Target {#registering-with-adobe-target}

Als u AEM wilt integreren met Adobe Target, hebt u een geldig Adobe Target-account nodig. Deze account moet minimaal **toegangsrechten op het niveau van de fiatteur** hebben. Wanneer u zich bij Adobe Target registreert, ontvangt u een clientcode. U hebt de clientcode en uw Adobe Target-aanmeldingsnaam en -wachtwoord nodig om AEM te kunnen verbinden met Adobe Target.

De clientcode identificeert de Adobe Target-klantenaccount wanneer de Adobe Target-server wordt aangeroepen.

>[!NOTE]
>
>Uw account moet ook zijn ingeschakeld door het Target-team om de integratie te kunnen gebruiken.
>
>Neem contact op met de [klantenservice](https://docs.adobe.com/content/help/en/target/using/cmp-resources-and-contact-information.html)van Adobe als dit niet het geval is.

## De Target Replication Agent inschakelen {#enabling-the-target-replication-agent}

De test en de [replicatieagent](/help/sites-deploying/replication.md) van Target moet op de auteursinstantie worden toegelaten. Merk op dat deze replicatieagent niet door gebrek wordt toegelaten als u de [nosamplcontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) looppas wijze voor het installeren van AEM gebruikte. Raadpleeg de lijst [Beveiligingscontrole](/help/sites-administering/security-checklist.md)voor meer informatie over het beveiligen van uw productieomgeving.

1. Klik of tik op **Extra** > **Implementatie** > **Replicatie** op de AEM-startpagina.
1. Klik of tik **Agenten op Auteur**.
1. Klik of tik de **Test en (test en doel)** replicatieagent van Target, en klik dan of tik **uitgeven**.
1. Selecteer de optie Ingeschakeld en klik of tik op **OK**.

   >[!NOTE]
   >
   >Wanneer u de de replicatieagent van de Test en van Target vormt, op het lusje van het **Vervoer** , wordt URI geplaatst door gebrek aan **tnt:///**. Vervang deze URI niet door **https://admin.testandtarget.omniture.com**.
   >
   >Houd er rekening mee dat als u de verbinding probeert te testen met **tnt:///**, dit een fout veroorzaakt. Dit wordt verwacht aangezien dit URI voor intern gebruik slechts is en niet met de Verbinding **van de** Test zou moeten worden gebruikt.

## Het knooppunt Activiteitsinstellingen beveiligen {#securing-the-activity-settings-node}

U moet het knooppunt activity settings (activity settings) **cq:ActivitySettings** op de publicatie-instantie beveiligen, zodat dit niet toegankelijk is voor normale gebruikers. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.

Het knooppunt **cq:ActivitySettings** is beschikbaar in de CRXDE-lijst onder `/content/campaigns/*nameofbrand*`* *onder het knooppunt activities jcr:content.* *bijvoorbeeld `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Dit knooppunt wordt alleen gemaakt nadat u een component als doel hebt ingesteld.

De **cq:ActivitySettings** knoop onder jcr van de activiteit:inhoud wordt beschermd door volgende ACLs:

* Alles weigeren voor iedereen
* jcr:read,rep:write toestaan voor &#39;target-activity-authors&#39; (de auteur is lid van deze groep uit de doos)
* jcr:read,rep:write voor &quot;targetService&quot; toestaan

Met deze instellingen zorgt u ervoor dat normale gebruikers geen toegang hebben tot de knoopeigenschappen. Gebruik zelfde ACLs op auteur en bij publiceren. Zie [Gebruikersbeheer en Beveiliging](/help/sites-administering/security.md) voor meer informatie.

## De AEM Link Externalzer configureren {#configuring-the-aem-link-externalizer}

Wanneer u een activiteit bewerkt in Adobe Target, verwijst de URL naar de **localhost** , tenzij u de URL wijzigt in het auteur-knooppunt van AEM. U kunt de AEM-koppelingsextern instellen als u wilt dat de geëxporteerde inhoud naar een specifiek *publicatiedomein* verwijst.

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

