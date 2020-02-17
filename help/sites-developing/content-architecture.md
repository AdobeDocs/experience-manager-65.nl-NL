---
title: Inhoudsarchitectuur
seo-title: Inhoudsarchitectuur
description: 'Tips voor het ontwerpen van uw inhoud (tip: alles is inhoud)'
seo-description: Tips voor het ontwerpen van uw inhoud in Adobe Experience Manager (AEM). (hint - alles is inhoud)
uuid: fef2bf0f-70ec-4621-8479-a62b7e1fbc07
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: ca46b74c-6114-458b-98c0-2a93abffcdc3
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Inhoudsarchitectuur{#content-architecture}

## Volg David&#39;s model {#follow-david-s-model}

David&#39;s Model werd jaren geleden geschreven door David Nuescheler, maar de ideeën zijn vandaag de dag van kracht. De belangrijkste uitgangspunten van David’s Model zijn:

* Gegevens komen als eerste, structuur later. Misschien.
* Geef de hiërarchie van de inhoud aan en laat deze niet gebeuren.
* De werkruimten zijn voor `clone()`, `merge()`, en `update()`.
* Wees op dezelfde naam voorbereid.
* Verwijzingen worden als schadelijk beschouwd.
* Bestanden zijn bestanden.
* Id&#39;s zijn slecht.

Het model van David is te vinden op de Jackrabbit wiki op [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### Alles is inhoud {#everything-is-content}

Alles moet in de gegevensopslagruimte worden opgeslagen in plaats van te vertrouwen op afzonderlijke gegevensbronnen van derden, zoals databases. Dit geldt voor geschreven inhoud, binaire gegevens zoals afbeeldingen, code, configuraties, enz. Hierdoor kunnen we één set API&#39;s gebruiken om alle inhoud te beheren en de promotie van deze inhoud via replicatie te beheren. We krijgen ook één bron van back-up, registratie, enzovoort.

### Het ontwerpbeginsel &quot;inhoudsmodel eerst&quot; gebruiken {#use-the-content-model-first-design-principle}

Wanneer u een nieuwe functie maakt, begint u altijd eerst met het ontwerpen van de JCR-inhoudsstructuur. Daarna leest u de inhoud en schrijft u deze in de standaardservlets. Dit zal u toestaan om ervoor te zorgen dat uw implementatie goed met uit de doos controlemechanismen van de toegangscontrole werkt en u toestaan om het produceren van onnodige CRUD-Stijl servlets te vermijden.

### Wees RESTful {#be-restful}

De servers zouden op resourceTypes in plaats van wegen moeten worden bepaald. Dit maakt het mogelijk om de toegangscontroles van het JCR te gebruiken, aan de principes van het REST te houden, en de middel en middeloplosser te gebruiken die aan ons in het verzoek worden verstrekt. Hierdoor kunnen we ook de scripts wijzigen die URL&#39;s renderen aan de serverzijde zonder dat we URL&#39;s hoeven te wijzigen aan de clientzijde, terwijl implementatiedetails aan de serverzijde voor extra beveiliging worden verborgen.

### Nieuwe knooppunttypen niet definiëren {#avoid-defining-new-node-types}

De types van knoop werken op een laag niveau in de infrastructuurlaag en de meeste vereisten kunnen worden vervuld door een sling te gebruiken:resourceType dat aan een nt:unStructured, eik:UnStructured, sling:Omslag of cq:het knooppunttype van de Pagina wordt toegewezen. De types van knoop komen aan schema in de bewaarplaats overeen en het veranderen van knooptypes kan zeer duur onderaan de weg zijn.

### Naleving van naamgevingsconventies in het JCR {#adhere-to-naming-conventions-in-the-jcr}

Het naleven van noemende overeenkomsten zal consistentie aan uw codebasis toevoegen, verminderend het veelvoud van onvolkomenheden en verhoogt de snelheid van ontwikkelaars die in het systeem werken. De volgende conventies worden door Adobe gebruikt bij de ontwikkeling van AEM:

* Node-namen

   * Alles kleine letters
   * Woordscheiding met afbreekstreepjes

* Namen van eigenschappen

   * Camelhoofdletter, beginnend met een kleine letter

* Componenten (JSP/HTML)

   * Alles kleine letters
   * Woordscheiding met afbreekstreepjes

