---
title: AEM Forms over OSGi-groepen en -voorrechten
description: Wijs gebruikers aan groepen toe om Adobe Experience Manager (AEM) Forms op OSGi te beheren
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
topic-tags: Configuration
docset: aem65
role: Admin,User
exl-id: d802ac53-e3db-45ca-afcb-7e99d0bb7877
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 1%

---

# AEM Forms over OSGi-groepen en -voorrechten{#aem-forms-on-osgi-groups-and-privileges}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/forms-groups-privileges-tasks.html) |
| AEM 6,5 | Dit artikel |

U kunt [groepen maken](/help/sites-administering/user-group-ac-admin.md#group-administration) en beleid en [gebruikers](/help/sites-administering/user-group-ac-admin.md#user-administration) aan de groepen in Adobe Experience Manager (AEM). Dit beleid controleert de voorrechten van de gebruikers die deel van de groep uitmaken.

Nadat u de [AEM Forms-invoegtoepassing](../../forms/using/installing-configuring-aem-forms-osgi.md), zijn de in dit artikel vermelde groepen, zoals gebruikers van formulieren en gebruikers van formulieren, automatisch beschikbaar voor toewijzing. De volgende lijst maakt een lijst van de taken die een gebruiker voor AEM Forms op OSGi kan uitvoeren die op de groepstoewijzingen wordt gebaseerd:

<table>
 <tbody>
  <tr>
   <td>Groep</td> 
   <td>Taken</td> 
  </tr>
  <tr>
   <td>formulieren-gebruikers <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Aangepaste formulieren maken, voorvertonen, publiceren en verzenden</li> 
     <li>Interactieve communicatie en documentfragmenten maken, voorvertonen en publiceren</li> 
     <li>Elementen uploaden naar een AEM-instantie</li> 
     <li>Thema's maken</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>formulieren-grootgebruikers</td> 
   <td>
    <ul> 
     <li>Aangepaste formulieren maken, voorvertonen, publiceren en verzenden</li> 
     <li>Interactieve communicatie en documentfragmenten maken, voorvertonen en publiceren</li> 
     <li>Scripts maken voor adaptieve formulieren met behulp van een code-editor</li> 
     <li>Elementen uploaden, inclusief scripts</li> 
     <li>Thema's maken</li> 
     <li>Pakketten importeren die XDP bevatten</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>formulierverzendingsrevisoren</td> 
   <td>
    <ul> 
     <li>Herziening</li> 
     <li>Indieningen goedkeuren of afwijzen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>sjabloonauteurs <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Aangepaste formulieren of interactieve communicatiesjablonen maken en hiervan een voorbeeld bekijken</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-auteurs</p> </td> 
   <td>
    <ul> 
     <li>Een formuliergegevensmodel maken en wijzigen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>cm-agent-gebruikers</td> 
   <td>
    <ul> 
     <li>Toegang tot correspondentiebeheerbrieven of interactieve communicatie met de gebruikersinterface van de Agent</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>workfloweditors</p> </td> 
   <td>
    <ul> 
     <li>Een inbox-toepassing maken</li> 
     <li>Een workflowmodel maken</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflowgebruikers</td> 
   <td>
    <ul> 
     <li>AEM Postvak In-toepassingen gebruiken<br /> <strong>Opmerking: </strong>U moet cm-agent-gebruikers en werkschema-gebruikers groepstaken hebben om tot de Interactieve Communicatie Agent UI in AEM Inbox toegang te hebben.</li> 
     <li>Workflowinstanties beheren</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-beheerders</td> 
   <td>
    <ul> 
     <li>PDF Generator configureren</li> 
     <li>De map Gecontroleerd configureren</li> 
     <li>Workflowtoepassingen beheren</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. De gebruiker met groepsrechten voor formulieren kan geen scripts schrijven voor adaptieve formulieren.
1. De gebruiker met de groepsrechten voor sjabloonauteurs kan geen scripts voor sjablonen schrijven.
