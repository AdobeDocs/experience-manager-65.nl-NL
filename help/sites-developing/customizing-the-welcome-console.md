---
title: De welkomstconsole aanpassen (klassieke gebruikersinterface)
seo-title: De welkomstconsole aanpassen (klassieke gebruikersinterface)
description: De welkomstconsole biedt een lijst met koppelingen naar de verschillende consoles en functies in AEM
seo-description: De welkomstconsole biedt een lijst met koppelingen naar de verschillende consoles en functies in AEM
uuid: 4ef20cef-2d7a-417d-b36b-ed4fa56cd511
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 2e408acb-3802-4837-8619-688cfc3abfa7
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# De welkomstconsole aanpassen (klassieke gebruikersinterface){#customizing-the-welcome-console-classic-ui}

>[!CAUTION]
>
>Deze pagina gaat over de klassieke gebruikersinterface.
>
>Zie De consoles [](/help/sites-developing/customizing-consoles-touch.md) aanpassen voor meer informatie over de standaardinterface met aanraakbediening.

De welkomstconsole biedt een lijst met koppelingen naar de verschillende consoles en functies in AEM.

![cq_welcomescreen](assets/cq_welcomescreen.png)

Het is mogelijk om de verbindingen te vormen die zichtbaar zijn. Dit kan voor specifieke gebruikers en/of groepen worden bepaald. De te nemen acties zijn afhankelijk van het doeltype (dat met de sectie van de console correleert zij binnen zijn):

* [Hoofdconsoles](#links-in-main-console-left-pane) - Koppelingen in de hoofdconsole (linkerdeelvenster)
* [Bronnen, Documentatie en Referentie, Functies](#links-in-sidebar-right-pane) - Koppelingen in de zijbalk (rechterdeelvenster)

## Koppelingen in hoofdconsole (linkerdeelvenster) {#links-in-main-console-left-pane}

Dit maakt een lijst van de belangrijkste consoles van AEM.

![cq_welcomescreenmainconsole](assets/cq_welcomescreenmainconsole.png)

### Bepalen of hoofdconsolekoppelingen zichtbaar zijn {#configuring-whether-main-console-links-are-visible}

Machtigingen op knooppuntniveau bepalen of de koppeling zichtbaar is of niet. De betrokken knooppunten zijn:

* **** Websites: `/libs/wcm/core/content/siteadmin`

* **** Digitale middelen: `/libs/wcm/core/content/damadmin`

* **** Gemeenschap: `/libs/collab/core/content/admin`

* **** Campagnes: `/libs/mcm/content/admin`

* **** Postvak IN: `/libs/cq/workflow/content/inbox`

* **** Gebruikers: `/libs/cq/security/content/admin`

* **** Gereedschappen: `/libs/wcm/core/content/misc`

* **** Tags: `/libs/cq/tagging/content/tagadmin`

Bijvoorbeeld:

* Als u de toegang tot **gereedschappen** wilt beperken, verwijdert u leestoegang uit

   `/libs/wcm/core/content/misc`

Zie de sectie [](/help/sites-administering/security.md) Beveiliging voor meer informatie over het instellen van de gewenste machtigingen.

### Koppelingen in zijbalk (rechterdeelvenster) {#links-in-sidebar-right-pane}

![cq_welcomescreensidebar](assets/cq_welcomescreensidebar.png)

Deze koppelingen zijn gebaseerd op het bestaan van ** en het lezen van toegang tot knooppunten onder het volgende pad:

`/libs/cq/core/content/welcome`

Er zijn drie secties (die iets uit elkaar liggen) die standaard worden opgegeven:

<table>
 <tbody>
  <tr>
   <td><strong>Bronnen</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td> Cloud Services</td>
   <td><code>/libs/cq/core/content/welcome/resources/cloudservices</code></td>
  </tr>
  <tr>
   <td> Workflows</td>
   <td><code>/libs/cq/core/content/welcome/resources/workflows</code></td>
  </tr>
  <tr>
   <td> Taakbeheer</td>
   <td><code>/libs/cq/core/content/welcome/resources/taskmanager</code></td>
  </tr>
  <tr>
   <td> Replicatie</td>
   <td><code>/libs/cq/core/content/welcome/resources/replication</code></td>
  </tr>
  <tr>
   <td> Rapporten</td>
   <td><code>/libs/cq/core/content/welcome/resources/reports</code></td>
  </tr>
  <tr>
   <td> Publicaties</td>
   <td><code>/libs/cq/core/content/welcome/resources/publishingadmin</code></td>
  </tr>
  <tr>
   <td> Manuscripts</td>
   <td><code>/libs/cq/core/content/welcome/resources/manuscriptsadmin</code></td>
  </tr>
  <tr>
   <td><strong>Documentatie en referentie</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td> Documentatie</td>
   <td><code>/libs/cq/core/content/welcome/docs/docs</code></td>
  </tr>
  <tr>
   <td> Bronnen voor ontwikkelaars</td>
   <td><code>/libs/cq/core/content/welcome/docs/dev</code></td>
  </tr>
  <tr>
   <td><strong>Functies</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td> CRXDE Lite</td>
   <td><code>/libs/cq/core/content/welcome/features/crxde</code></td>
  </tr>
  <tr>
   <td> Pakketten</td>
   <td><code>/libs/cq/core/content/welcome/features/packages</code></td>
  </tr>
  <tr>
   <td> Pakket delen</td>
   <td><code>/libs/cq/core/content/welcome/features/share</code></td>
  </tr>
  <tr>
   <td> Clustering</td>
   <td><code>/libs/cq/core/content/welcome/features/cluster</code></td>
  </tr>
  <tr>
   <td> Back-up</td>
   <td><code>/libs/cq/core/content/welcome/features/backup</code></td>
  </tr>
  <tr>
   <td> Webconsole<br /> </td>
   <td><code>/libs/cq/core/content/welcome/features/config</code></td>
  </tr>
  <tr>
   <td> Status van webconsole<br /> </td>
   <td><code>/libs/cq/core/content/welcome/features/statusdump</code></td>
  </tr>
 </tbody>
</table>

#### Configureren of Zijbalkkoppelingen zichtbaar zijn {#configuring-whether-sidebar-links-are-visible}

Het is mogelijk om een koppeling te verbergen voor specifieke gebruikers of groepen door leestoegang te verwijderen voor de knooppunten die de koppeling vertegenwoordigen.

* Bronnen - toegang verwijderen tot:

   `/libs/cq/core/content/welcome/resources/<link-target>`

* Docs - toegang verwijderen tot:

   `/libs/cq/core/content/welcome/docs/<link-target>`

* Functies - toegang verwijderen tot:

   `/libs/cq/core/content/welcome/features/<link-target>`

Bijvoorbeeld:

* Als u de koppeling naar **rapporten** wilt verwijderen, verwijdert u de leestoegang uit

   `/libs/cq/core/content/welcome/resources/reports`

* Om de verbinding aan **Pakketten** te verwijderen, verwijder leestoegang uit

   `/libs/cq/core/content/welcome/features/packages`

Zie de sectie [](/help/sites-administering/security.md) Beveiliging voor meer informatie over het instellen van de gewenste machtigingen.

### Selectiemechanisme koppelen {#link-selection-mechanism}

In `/libs/cq/core/components/welcome/welcome.jsp` gebruik wordt gemaakt van [ConsoleUtil](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/ConsoleUtil.html), die een vraag op knopen uitvoert die het bezit hebben:

* `jcr:mixinTypes` met de waarde: `cq:Console`

>[!NOTE]
>
>Voer de volgende vraag uit om de bestaande lijst te zien:
>
>* `select * from cq:Console`
>



Wanneer een gebruiker of een groep geen leestoestemming op een knoop met de mixin heeft `cq:Console`, wordt die knoop niet teruggewonnen door het `ConsoleUtil` onderzoek, vandaar is het niet vermeld op de console.

### Een aangepast item toevoegen {#adding-a-custom-item}

Met het selectiemechanisme [voor](#link-selection-mechanism) koppelingen kunt u uw eigen aangepaste item toevoegen aan de lijst met koppelingen.

Voeg uw douanepunt aan de lijst toe door de `cq:Console` mengeling aan uw widget of middel toe te voegen. Hiervoor definieert u de eigenschap:

* `jcr:mixinTypes` met de waarde: `cq:Console`

