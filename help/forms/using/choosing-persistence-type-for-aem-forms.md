---
title: Een persistentietype kiezen voor een installatie van AEM Forms
seo-title: Een persistentietype kiezen voor een installatie van AEM Forms
description: Kies verstandig een persistentietype. Hiermee kunt u een efficiënte en schaalbare AEM Forms-omgeving maken.
seo-description: Kies verstandig een persistentietype. Hiermee kunt u een efficiënte en schaalbare AEM Forms-omgeving maken.
uuid: 1c692502-5039-4757-9358-1772772b3904
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: a972fb35-38a7-4b83-99bd-6a6dddf8043b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Een persistentietype kiezen voor een installatie van AEM Forms {#choosing-a-persistence-type-for-an-aem-forms-installation}

Kies verstandig een persistentietype. Hiermee kunt u een efficiënte en schaalbare AEM Forms-omgeving maken.

Persistentie is de methode om inhoud op de fysieke opslag op te slaan. Het bepaalt de daadwerkelijke gegevensstructuur en opslagmechanisme voor de gegevens. MicroKernels fungeren als persistentiemanagers in AEM Forms. AEM Forms ondersteunt persistentie (MicroKernals) van het type TarMK, MongoMK en RDBMK. U kunt een persistentietype voor Vormen AEM afhankelijk van het doel en plaatsingstype (enige-Server, Farm, of Cluster) van een instantie van Vormen AEM kiezen.

>[!NOTE]
>
>LiveCycle ES4 SP1 gebruikt TarPM-persistentie om inhoud op te slaan.

De volgende tabel bevat een lijst met alle ondersteunde typen persistentie en diverse parameters waarmee u een persistentietype voor uw omgeving kunt kiezen:

<table>
 <tbody>
  <tr>
   <th><strong>Type installatie/kosten</strong></th>
   <th><strong>TarMK</strong></th>
   <th><strong>MongoMk</strong></th>
   <th><strong>RDBMK</strong></th>
  </tr>
  <tr>
   <th><strong>Standalone-instelling</strong></th>
   <td>Ondersteund<br /> </td>
   <td>Ondersteund</td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <th><strong>Clusterinstelling</strong></th>
   <td>Niet ondersteund</td>
   <td>Ondersteund</td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <th><strong>Licentiekosten</strong></th>
   <td>Opgenomen met AEM </td>
   <td>Afzonderlijke vergunning vereist</td>
   <td>Afzonderlijke vergunning vereist</td>
  </tr>
 </tbody>
</table>

TarMK is ontworpen voor prestaties, terwijl MongoMK en RDBMK zijn ontworpen voor schaalbaarheid. Adobe raadt TarMK ten zeerste aan als de standaardpersistentietechnologie voor alle implementatiescenario&#39;s van AEM Forms, voor zowel auteur- als publicatieinstanties, behalve in de gebruiksgevallen die worden beschreven in de sectie Mongo [kiezen of een relationele database-microkernel via TarMK](#p-choosing-mongo-or-a-relational-database-microkernel-over-tarmk-p).

Voor de lijst van gesteunde Microkernels, zie de Vormen van [AEM op de Technische Vereisten](/help/sites-deploying/technical-requirements.md) van OSGi of de Vormen van [AEM op JEE gesteunde platformcombinaties](/help/forms/using/aem-forms-jee-supported-platforms.md) artikelen.

## Mongo of een relationele database-microkernel kiezen boven TarMK {#choosing-mongo-or-a-relational-database-microkernel-over-tarmk}

Een scalable (gegroepeerde) milieu van Vormen AEM is een reeks van twee of meer horizontaal gevormde actieve auteursinstanties. U kunt ervoor kiezen om meer dan één auteurinstantie uit te voeren als één enkele server, die alle gelijktijdige auteursactiviteiten steunt, niet meer duurzaam is.

Alleen het persistentietype MongoMK en RDBMK wordt ondersteund voor een schaalbare (geclusterde) AEM-formulieren in een JEE-omgeving. Het aantal servers of de grootte van scalable milieu varieert voor elke installatie. Voor een lijst van overwegingen en voorbeelden, zie de [Geadviseerde Inzet](/help/sites-deploying/recommended-deploys.md) en of de [Architectuur en plaatsingstopologieën voor het artikel van Vormen](/help/forms/using/aem-forms-architecture-deployment.md) AEM. U kunt ook contact opnemen met de ondersteuning van AEM Forms voor gedetailleerde informatie over capaciteitsplanning voor AEM Forms met RDBMK en TarMK.
