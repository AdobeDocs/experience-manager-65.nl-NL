---
title: Herstructurering van de opslagplaats voor elektronische handel in AEM 6.5
seo-title: Herstructurering van de opslagplaats voor elektronische handel in AEM 6.5
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe dataopslagstructuur in AEM 6.5 voor e-commerce.
seo-description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe dataopslagstructuur in AEM 6.5 voor e-commerce.
uuid: 1fff1a4b-c8d0-4016-92fb-e2ea26e3a302
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 28c92e7d-2106-4333-afa6-c5528a00d7b4
translation-type: tm+mt
source-git-commit: d20ddba254c965e1b0c0fc84a482b7e89d4df5cb

---


# Herstructurering van de opslagplaats voor elektronische handel in AEM 6.5{#e-commerce-repository-restructuring-in-aem}

Zoals beschreven op de pagina &quot;parent [Repository Herstructurering&quot; in AEM 6.5](/help/sites-deploying/repository-restructuring.md) , zouden klanten die upgraden naar AEM 6.5 deze pagina moeten gebruiken om de werkinspanning te beoordelen die gepaard gaat met veranderingen in de opslagplaats die van invloed zijn op de AEM E-Commerce Solution. Sommige veranderingen vereisen werk inspanning tijdens het AEM 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

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
   <td><p>U kunt een <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">Uitgestelde taak van de Migratie</a> gebruiken om e-Commerce gegevens te migreren.</p> <p>De volgende stappen worden uitgevoerd:</p>
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
   <td><strong>Opmerkingen</strong></td>
   <td>N/A<br /> </td>
  </tr>
 </tbody>
</table>

