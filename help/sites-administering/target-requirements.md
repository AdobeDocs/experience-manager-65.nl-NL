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
feature: Integration
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Vereisten voor integratie met Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Als deel van de [ integratie van AEM en Adobe Target ](/help/sites-administering/target.md), moet u met Adobe Target registreren, de replicatieagent, en veilige activiteitenmontages op publiceren knoop vormen.

## Registreren bij Adobe Target {#registering-with-adobe-target}

Als u AEM wilt integreren met Adobe Target, hebt u een geldig Adobe Target-account nodig. Deze rekening moet **het niveautoestemmingen van de goedkeuraar** op een minimum hebben. Wanneer u zich bij Adobe Target registreert, ontvangt u een clientcode. U hebt de clientcode en uw Adobe Target-aanmeldingsnaam en -wachtwoord nodig om verbinding te maken AEM met Adobe Target.

De clientcode identificeert de Adobe Target-klantenaccount wanneer de Adobe Target-server wordt aangeroepen.

>[!NOTE]
>
>Uw account moet ook zijn ingeschakeld door het Target-team om de integratie te kunnen gebruiken.
>
>Als het niet het geval is, contacteer [&#128279;](https://experienceleague.adobe.com/docs/target/using/cmp-resources-and-contact-information.html) de Zorg van de Klant van de Adobe 0&rbrace;.

## De agent voor doelreplicatie inschakelen {#enabling-the-target-replication-agent}

De Test en van het Doel [ replicatieagent ](/help/sites-deploying/replication.md) moet op de auteursinstantie worden toegelaten. Merk op dat deze replicatieagent niet door gebrek wordt toegelaten als u de [ nosamplcontent ](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) looppaswijze gebruikte om AEM te installeren. Voor meer informatie over het beveiligen van uw productiemilieu, zie [ Controlelijst van de Veiligheid ](/help/sites-administering/security-checklist.md).

1. Op de AEM homepage, klik **Hulpmiddelen** > **Plaatsing** > **Replicatie**.
1. Klik **Agenten op Auteur**.
1. Klik de **Test en Doel (test en doel)** replicatieagent, en klik dan **uitgeven**.
1. Selecteer de Toegelaten optie, dan klik O.K. **&#x200B;**.

   >[!NOTE]
   >
   >Wanneer u de Test en de replicatieagent van het Doel vormt, in het **Vervoer** lusje, wordt URI geplaatst door gebrek aan **tnt:///**. Vervang dit URI niet met **https://admin.testandtarget.omniture.com**.
   >
   >Als u probeert om de verbinding met **tnt:///** te testen, werpt het een fout. Dit wordt verwacht gedrag aangezien dit URI voor intern gebruik slechts is; gebruik niet met **Verbinding van de Test**.

## Het knooppunt Activiteitsinstellingen beveiligen {#securing-the-activity-settings-node}

Beveilig de knoop van activiteitenmontages **cq:ActivitySettings** op publiceer instantie zodat het voor normale gebruikers ontoegankelijk is. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.

**cq:ActivitySettings** knoop is beschikbaar in CRXDE lijst onder `/content/campaigns/*nameofbrand*` * *onder de activiteiten jcr:content knoop;* *bijvoorbeeld, `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Dit knooppunt wordt alleen gemaakt nadat u een component als doel hebt ingesteld.

**cq:ActivitySettings** knoop onder jcr van de activiteit:inhoud wordt beschermd door volgende ACLs:

* Alles weigeren voor iedereen
* jcr:read,rep:write toestaan voor &#39;target-activity-authors&#39; (de auteur is lid van deze groep uit de doos)
* jcr:read,rep:write voor &quot;targetService&quot; toestaan

Met deze instellingen zorgt u ervoor dat normale gebruikers geen toegang hebben tot de knoopeigenschappen. Gebruik zelfde ACLs op auteur en bij publiceren. Zie [ Beleid van de Gebruiker en Veiligheid ](/help/sites-administering/security.md) voor meer informatie.

## Het vormen van de AEM Verbinding Externalzer {#configuring-the-aem-link-externalizer}

Wanneer het uitgeven van een activiteit in Adobe Target, richt URL aan **localhost** tenzij u URL op de AEM auteursknoop verandert. U kunt AEM Verbinding Externalzer vormen als u de uitgevoerde inhoud aan specifiek *wilt richten publiceert* domein.

>[!NOTE]
>
>Zie ook [ de Configuratie van de Wolk ](/help/sites-administering/experience-fragments-target.md#add-the-cloud-configuration) toevoegen.

Om de AEM externalizer te vormen:

>[!NOTE]
>
>Voor meer details zie [ het Extern stellen URLs ](/help/sites-developing/externalizer.md).

1. Navigeer aan de OSGi Webconsole in **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Vind **de Verbinding van CQ van de Dag uiterlijk** en ga het domein voor de auteursknoop in.

   ![ CQ van de Dag Verbinding Externalzer ](assets/aem-externalizer-01.png)
