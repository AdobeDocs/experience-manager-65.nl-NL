---
title: Vereisten voor integratie met Adobe Target
description: Leer meer over de voorwaarden voor integratie met Adobe Target.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 30813c44-51ac-4e6e-8ee6-4e8baacb1ff9
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Vereisten voor integratie met Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Als onderdeel van het [integratie van AEM en Adobe Target](/help/sites-administering/target.md), moet u bij Adobe Target registreren, de replicatieagent vormen, en activiteitenmontages op het publicatieknooppunt beveiligen.

## Registreren bij Adobe Target {#registering-with-adobe-target}

Als u AEM wilt integreren met Adobe Target, hebt u een geldig Adobe Target-account nodig. Deze account moet **fiatteur** minimaal niveau aan machtigingen. Wanneer u zich bij Adobe Target registreert, ontvangt u een clientcode. U hebt de clientcode en uw Adobe Target-aanmeldingsnaam en -wachtwoord nodig om verbinding te maken AEM met Adobe Target.

De clientcode identificeert de Adobe Target-klantenaccount wanneer de Adobe Target-server wordt aangeroepen.

>[!NOTE]
>
>Uw account moet ook zijn ingeschakeld door het Target-team om de integratie te kunnen gebruiken.
>
>Indien dit niet het geval is, neemt u contact op met [Klantenservice Adoben](https://experienceleague.adobe.com/docs/target/using/cmp-resources-and-contact-information.html).

## De agent voor doelreplicatie inschakelen {#enabling-the-target-replication-agent}

Test en doel [replicatieagent](/help/sites-deploying/replication.md) moet zijn ingeschakeld op de instantie van de auteur. Merk op dat deze replicatieagent niet door gebrek wordt toegelaten als u gebruikte [nosamplcontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) uitvoeringsmodus voor het installeren van AEM. Voor meer informatie over het beveiligen van uw productieomgeving raadpleegt u de [Beveiligingscontrolelijst](/help/sites-administering/security-checklist.md).

1. Klik op de AEM homepage op **Gereedschappen** > **Implementatie** > **Replicatie**.
1. Klikken **Medewerkers op auteur**.
1. Klik op de knop **Test en doel (test en doel)** replicatieagent, en klik dan **Bewerken**.
1. Selecteer de optie Ingeschakeld en klik op **OK**.

   >[!NOTE]
   >
   >Wanneer u de Test en de replicatieagent van het Doel vormt, in **Vervoer** tab, de URI is standaard ingesteld op **tnt:///**. Vervang deze URI niet door **https://admin.testandtarget.omniture.com**.
   >
   >Als u de verbinding probeert te testen met **tnt:///** Er treedt een fout op. Dit gedrag wordt verwacht omdat deze URI alleen voor intern gebruik is; niet gebruiken met **Verbinding testen**.

## Het knooppunt Activiteitsinstellingen beveiligen {#securing-the-activity-settings-node}

Het knooppunt met activiteiteninstellingen beveiligen **cq:ActivitySettings** op de publicatie-instantie zodat deze niet toegankelijk is voor normale gebruikers. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.

De **cq:ActivitySettings** knooppunt beschikbaar in CRXDE-lijst onder `/content/campaigns/*nameofbrand*`* *onder de activiteiten jcr:content node;* *bijvoorbeeld, `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Dit knooppunt wordt alleen gemaakt nadat u een component als doel hebt ingesteld.

De **cq:ActivitySettings** knoop onder jcr van de activiteit:inhoud wordt beschermd door volgende ACLs:

* Alles weigeren voor iedereen
* jcr:read,rep:write toestaan voor &#39;target-activity-authors&#39; (de auteur is lid van deze groep uit de doos)
* jcr:read,rep:write voor &quot;targetService&quot; toestaan

Met deze instellingen zorgt u ervoor dat normale gebruikers geen toegang hebben tot de knoopeigenschappen. Gebruik zelfde ACLs op auteur en bij publiceren. Zie [Gebruikersbeheer en beveiliging](/help/sites-administering/security.md) voor meer informatie .

## Het vormen van de AEM Verbinding Externalzer {#configuring-the-aem-link-externalizer}

Wanneer u een activiteit bewerkt in Adobe Target, verwijst de URL naar **localhost** tenzij u de URL wijzigt in het AEM auteurknooppunt. U kunt AEM Verbinding Externalzer vormen als u de uitgevoerde inhoud aan specifiek wilt richten *publish* domein.

>[!NOTE]
>
>Zie ook [Cloudconfiguratie toevoegen](/help/sites-administering/experience-fragments-target.md#add-the-cloud-configuration).

Om de AEM externalizer te vormen:

>[!NOTE]
>
>Zie voor meer informatie [URL&#39;s extern maken](/help/sites-developing/externalizer.md).

1. Navigeer naar de OSGi-webconsole op **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Zoeken **Day CQ Link ExternalAlizer** en voer het domein voor het auteurknooppunt in.

   ![Day CQ Link ExternalAlizer](assets/aem-externalizer-01.png)
