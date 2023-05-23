---
title: Herstructurering van de opslagplaats voor elektronische handel in AEM 6.5
seo-title: E-Commerce Repository Restructuring in AEM 6.5
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe dataopslagstructuur in AEM 6.5 voor e-commerce.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.5 for E-Commerce.
uuid: 1fff1a4b-c8d0-4016-92fb-e2ea26e3a302
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 28c92e7d-2106-4333-afa6-c5528a00d7b4
feature: Upgrading
exl-id: 78b7c497-c474-4308-bfab-8f424b5f7268
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Herstructurering van de opslagplaats voor elektronische handel in AEM 6.5{#e-commerce-repository-restructuring-in-aem}

Zoals beschreven op het bovenliggende element [Herstructurering van de depositaris in AEM 6.5](/help/sites-deploying/repository-restructuring.md) pagina, zouden de klanten die aan AEM 6.5 bevorderen deze pagina moeten gebruiken om de het werkinspanning te beoordelen verbonden aan bewaarplaatsveranderingen die de AEM E-Commerce Oplossing beïnvloeden. Sommige veranderingen vereisen het werk inspanning tijdens het AEM 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

## Met 6,5-upgrade {#with-upgrade}

### Gegevens over producten, bestellingen, verzamelingen, classificaties, verzendmethoden en betalingsmethoden {#product-order-collections-classifications-shipping-methods-and-payment-methods-data}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><p><code>/etc/commerce/products</code></p> <p><code>/etc/commerce/orders</code></p> <p><code>/etc/commerce/collections</code></p> <p><code>/etc/commerce/classifications</code></p> <p><code>/etc/commerce/shipping-methods</code></p> <p><code>/etc/commerce/payment-methods</code></p> </td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/var/commerce/products</code></p> <p><code>/var/commerce/orders</code></p> <p><code>/var/commerce/collections</code></p> <p><code>/var/commerce/classifications</code></p> <p><code>/var/commerce/shipping-methods</code></p> <p><code>/var/commerce/payment-methods</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>U kunt een <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">Lazy Migration</a> taak om gegevens over e-handel te migreren.</p> <p>De volgende stappen worden uitgevoerd:</p>
    <ul>
     <li>Hiermee wijzigt u verwijzingen naar oude locatie zodat deze naar een nieuwe locatie verwijzen</li>
     <li>Hiermee wordt inhoud van de oude locatie naar de nieuwe locatie verplaatst</li>
     <li>verwijdert oude locatie om uiteindelijk het gebruik van een nieuwe locatie in het hele systeem te activeren</li>
    </ul> <p>De locaties waarop de taak betrekking heeft, zijn:</p>
    <ul>
     <li>/etc/commerce/products</li>
     <li>/etc/commerce/collections<br /> </li>
     <li>/etc/commerce/orders<br /> </li>
     <li>/etc/commerce/payment-methods<br /> </li>
     <li>/etc/commerce/Shipping-methods<br /> </li>
    </ul> <p>Voor grotere catalogi wordt aanbevolen de handelsmigratietaak afzonderlijk uit te voeren door de volgende Java-systeemeigenschap aan AEM door te geven:</p> <p><code>propertyname: com.adobe.upgrade.forcemigration</code></p> <p><code>property value: com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></p> <p>Na de migratie moet AEM opnieuw worden opgestart.</p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>
