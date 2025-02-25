---
title: Een persistentietype kiezen voor een AEM Forms-installatie
description: Kies verstandig een persistentietype. Het helpt u een efficiënte en schaalbare AEM Forms-omgeving op te bouwen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
role: Admin
exl-id: 621fe107-f4ac-42b1-8c7b-8abbcaac7380
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 1%

---

# Een persistentietype kiezen voor een AEM Forms-installatie {#choosing-a-persistence-type-for-an-aem-forms-installation}

Kies verstandig een persistentietype. Het helpt u een efficiënte en schaalbare AEM Forms-omgeving op te bouwen.

Persistentie is de methode om inhoud op de fysieke opslag op te slaan. Het bepaalt de daadwerkelijke gegevensstructuur en opslagmechanisme voor de gegevens. MicroKernels fungeert als persistentiemanagers in AEM Forms. AEM Forms ondersteunt persistentie (MicroKernals) van het type TarMK, MongoMK en RDBMK. U kunt een persistentietype voor AEM Forms kiezen, afhankelijk van het doel en het implementatietype (Single-Server, Farm of Cluster) van een AEM Forms-instantie.

>[!NOTE]
>
>LiveCycle ES4 SP1 gebruikt persistentie TarPM om inhoud op te slaan.

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
   <td>Ondersteund <br /> </td>
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

TarMK is ontworpen voor prestaties, terwijl MongoMK en RDBMK zijn ontworpen voor schaalbaarheid. De Adobe adviseert hoogst TarMK als standaardpersistentietechnologie voor alle de plaatsingsscenario&#39;s van AEM Forms, voor zowel Auteur als de instanties van Publish, behalve in de gebruiksgevallen die in sectie [ worden geschetst die Mongo of een Relationele Microkernel van het Gegevensbestand over TarMK ](#p-choosing-mongo-or-a-relational-database-microkernel-over-tarmk-p) kiezen.

Voor de lijst van gesteunde Microkernels, zie [ AEM Forms op Technische Vereisten OSGi ](/help/sites-deploying/technical-requirements.md) of [ AEM Forms op JEE gesteunde platformcombinaties ](/help/forms/using/aem-forms-jee-supported-platforms.md) artikelen.

## Mongo of een relationele database-microkernel kiezen boven TarMK {#choosing-mongo-or-a-relational-database-microkernel-over-tarmk}

Een scalable (gegroepeerde) milieu van AEM Forms is een reeks van twee of meer horizontaal gevormde actieve auteursinstanties. U kunt ervoor kiezen om meer dan één auteurinstantie uit te voeren als één enkele server, die alle gelijktijdige auteursactiviteiten steunt, niet meer duurzaam is.

Alleen het persistentietype MongoMK en RDBMK wordt ondersteund voor een schaalbare (geclusterde) AEM Forms op JEE-omgeving. Het aantal servers of de grootte van scalable milieu varieert voor elke installatie. Voor een lijst van overwegingen en voorbeelden, zie [ Geadviseerde Inzet ](/help/sites-deploying/recommended-deploys.md) en of [ Architectuur en plaatsingstopologieën voor AEM Forms ](/help/forms/using/aem-forms-architecture-deployment.md) artikel. U kunt ook contact opnemen met AEM Forms-ondersteuning voor gedetailleerde informatie over capaciteitsplanning voor AEM Forms met RDBMK en TarMK.
