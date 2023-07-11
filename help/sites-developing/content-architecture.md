---
title: Inhoudsarchitectuur
description: 'Tips voor het ontwerpen van uw inhoud (tip: alles is inhoud)'
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: bcebbdb4-20b9-4c2d-8a87-013549d686c1
source-git-commit: 1ef5593495b4bf22d2635492a360168bccc1725d
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Inhoudsarchitectuur{#content-architecture}

## Volg David&#39;s model {#follow-david-s-model}

David&#39;s Model werd jaren geleden geschreven door David Nuescheler, maar de ideeën gelden vandaag. De belangrijkste uitgangspunten van David&#39;s Model zijn:

* Gegevens komen als eerste, structuur later. Misschien.
* Geef de inhoudshiërarchie de drijfveer, laat het niet gebeuren.
* Werkruimten zijn bedoeld voor `clone()`, `merge()`, en `update()`.
* Let op dat u dezelfde naam hebt als op hetzelfde vel.
* Verwijzingen worden als schadelijk beschouwd.
* Bestanden zijn bestanden.
* Id&#39;s zijn slecht.

Het model van David is te vinden op de Jackrabbit wiki op [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### Alles is inhoud {#everything-is-content}

Alles moet in de gegevensopslagruimte worden opgeslagen in plaats van te vertrouwen op afzonderlijke gegevensbronnen van derden, zoals databases. Dit geldt voor geschreven inhoud, binaire gegevens zoals afbeeldingen, code en configuraties. Hierdoor kunnen we één set API&#39;s gebruiken om alle inhoud te beheren en de promotie van deze inhoud via replicatie te beheren. U krijgt ook één bron van steun, registreren, etc.

### Het ontwerpbeginsel &quot;inhoudsmodel eerst&quot; gebruiken {#use-the-content-model-first-design-principle}

Wanneer u een nieuwe functie maakt, begint u altijd eerst met het ontwerpen van de JCR-inhoudsstructuur. Daarna leest u de inhoud en schrijft u deze in de standaardservlets. Dit laat u ervoor zorgen dat uw implementatie goed met uit de doos controlemechanismen van de toegangscontrole werkt en staat u toe om het produceren van onnodige CRUD-Stijl servlets te vermijden.

### Wees RESTful {#be-restful}

De servers zouden op resourceTypes in plaats van wegen moeten worden bepaald. Dit maakt het mogelijk om de toegangscontroles van het JCR te gebruiken, aan de principes van het REST te houden, en de middel en middeloplosser te gebruiken die aan ons in het verzoek worden verstrekt. Hierdoor kunnen we ook de scripts wijzigen die URL&#39;s renderen aan de serverzijde zonder dat we URL&#39;s hoeven te wijzigen aan de clientzijde, terwijl implementatiedetails aan de serverzijde voor extra beveiliging worden verborgen.

### Nieuwe knooppunttypen niet definiëren {#avoid-defining-new-node-types}

De types van knoop werken op een laag niveau in de infrastructuurlaag en de meeste vereisten kunnen worden voldaan door een sling te gebruiken:resourceType dat aan een nt:unStructured, eik:UnStructured, sling:Omslag of cq:het knooppunttype van de Pagina wordt toegewezen. De types van knoop komen aan schema in de bewaarplaats overeen en het veranderen van knooptypes kan in de weg duur zijn.

### Naleving van naamgevingsconventies in het JCR {#adhere-to-naming-conventions-in-the-jcr}

Het naleven van noemende overeenkomsten voegt consistentie aan uw codebasis toe, verlaagt het veelvoud van onvolkomenheden en verhoogt de snelheid van ontwikkelaars die in het systeem werken. Adobe gebruikt de volgende conventies bij het ontwikkelen van AEM:

* Node-namen

   * Alles kleine letters
   * Woordscheiding met afbreekstreepjes

* Namen van eigenschappen

   * Camelhoofdletter, beginnend met een kleine letter

* Componenten (JSP/HTML)

   * Alles kleine letters
   * Woordscheiding met afbreekstreepjes
