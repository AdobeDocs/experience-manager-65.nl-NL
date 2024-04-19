---
title: Integratieframework eCommerce
description: AEM eCommerce helpt marketers merkboodschap, persoonlijke boodschappen op internet, mobiel en sociaal gebied te leveren.
topic-tags: e-commerce
content-type: reference
docset: aem65
exl-id: d995f0d6-9e48-4228-ac82-f33a0b25b9d3
solution: Experience Manager,Commerce
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# eCommerce{#ecommerce}

* [Concepten](/help/commerce/cif-classic/administering/concepts.md)
* [Beheer (algemeen)](/help/commerce/cif-classic/administering/generic.md)

Adobe biedt twee versies van het Commerce integration framework:

<table>
 <tbody>
  <tr>
   <th><p> </p> </th>
   <th><p>CIF op prem</p> </th>
   <th><p>CIF Cloud</p> </th>
  </tr>
  <tr>
   <td><p>Ondersteunde AEM</p> </td>
   <td><p>AEM on-prem of AMS 6.x</p> </td>
   <td>AEM AMS 6.4 en 6.5</td>
  </tr>
  <tr>
   <td><p>Terug</p> </td>
   <td>
    <ul>
     <li>AEM, Java</li>
     <li>Monolithische integratie, vooraf samengestelde toewijzing (sjabloon)</li>
     <li>JCR-opslagplaats</li>
    </ul> </td>
   <td>
    <ul>
     <li>Adobe Commerce</li>
     <li>Java en JavaScript</li>
     <li>Geen handelsgegevens opgeslagen in JCR-gegevensopslagruimte</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Voorkant</p> </td>
   <td><p>Gerenderde pagina's AEM op de server</p> </td>
   <td>Toepassing gemengde pagina (hybride rendering)</td>
  </tr>
  <tr>
   <td><p>Productcatalogus</p> </td>
   <td>
    <ul>
     <li>Producimporteur, editor, caching in AEM</li>
     <li>Gewone catalogi met AEM- of proxypagina's</li>
    </ul> </td>
   <td>
    <ul>
     <li>Geen producten importeren</li>
     <li>Algemene sjablonen</li>
     <li>Gegevens op aanvraag via aansluiting</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Schaalbaarheid</p> </td>
   <td>
    <ul>
     <li>Kan maximaal een paar miljoen producten ondersteunen (afhankelijk van het gebruiksgeval)</li>
     <li>Caching op Dispatcher</li>
    </ul> </td>
   <td>
    <ul>
     <li>Geen volumebeperking</li>
     <li>Caching op Dispatcher of CDN</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Gestandaardiseerd gegevensmodel</td>
   <td>Nee</td>
   <td>Ja, Adobe Commerce GraphQL-schema</td>
  </tr>
  <tr>
   <td>Beschikbaarheid</td>
   <td><p>Ja. SAP-Commerce Cloud (extensie die wordt bijgewerkt ter ondersteuning van AEM 6.4 en Hybris 5 (standaard) en de compatibiliteit met Hybris 4 behoudt</p> <p>Salesforce-Commerce Cloud (connector open-sourced voor ondersteuning van AEM 6.4)</p> </td>
   <td>Ja via open bron via GitHub. Adobe Commerce (ondersteunt 2.3.2 (standaard) en compatibel met 2.3.1).</td>
  </tr>
  <tr>
   <td>Wanneer gebruiken</td>
   <td>Beperkte gebruiksgevallen: bijvoorbeeld scenario's waarin kleine, statische catalogi mogelijk moeten worden geïmporteerd</td>
   <td>Voorkeursoplossing in de meeste gebruikscategorieën</td>
  </tr>
 </tbody>
</table>

eCommerce handelt samen met Product Information Management (PIM) de activiteiten van een website die gericht is op het verkopen van producten via een onlinewinkel:

* Maken, levensduur en veroudering van een product
* Prijsbeheer
* Transactiebeheer
* Beheer van volledige catalogi
* Live en gecentraliseerde opslagrecords
* Webinterfaces

AEM eCommerce helpt marketers merkboodschap, persoonlijke boodschappen op internet, mobiel en sociaal gebied te leveren. In de AEM ontwerpomgeving kunt u pagina&#39;s en componenten aanpassen op basis van de context van de doelbezoeker en de marketingstrategieën, bijvoorbeeld:

* Productpagina&#39;s
* Winkelwagentjes
* Onderdelen uitchecken

De implementatie maakt realtime toegang tot productinformatie mogelijk. Dit kan worden gebruikt om af te dwingen:

* Integriteit van productinformatie
* Prijsstelling
* Voorraadinventaris
* Variaties in de toestand van een winkelwagentje

>[!NOTE]
>
>Als u het integratieframework wilt gebruiken met externe eCommerce-providers, moet u eerst de vereiste pakketten installeren. Zie voor meer informatie [eCommerce implementeren](/help/commerce/cif-classic/deploying/ecommerce.md).
>
>Voor informatie over het uitbreiden van eCommerce-mogelijkheden raadpleegt u [Ontwikkeling van eCommerce](/help/commerce/cif-classic/developing/ecommerce.md).

## Belangrijkste functies {#main-features}

AEM eCommerce biedt:

* Een aantal **out-of-the-box AEM componenten** om te illustreren wat u kunt bereiken voor uw project:

   * Productweergave
   * Winkelwagentje
   * Uitchecken
   * Onlangs bekeken producten
   * Vouchers
   * en andere

  ![voorbeeld geometrixx-componenten](/help/sites-administering/assets/chlimage_1-130.png)

  >[!NOTE]
  >
  >Met het integratieframework dat AEM biedt, kunt u ook extra AEM maken voor handelsmogelijkheden, onafhankelijk van uw specifieke eCommerce-engine.

* **Zoeken** - met gebruikmaking van:

   * de AEM
   * het zoeken van het eCommerce-systeem
   * een zoekopdracht van derden
   * of een combinatie daarvan.

  ![zoekvoorbeeld](/help/sites-administering/assets/chlimage_1-131.png)

* Gebruikt de AEM **presenteer uw inhoud op meerdere kanalen**, of dit nu het volledige browservenster of het mobiele apparaat is. Hierdoor wordt uw inhoud geleverd in de indeling die uw bezoekers nodig hebben.

  ![voorbeeld van mobiele weergave](/help/sites-administering/assets/chlimage_1-132.png)

* De mogelijkheid om **uw eigen integratieimplementatie ontwikkelen op basis van de [AEM eCommerce-kader](#the-framework)**.

  De twee momenteel beschikbare implementaties zijn beide op dezelfde basis gebaseerd - bovenop de algemene API (het framework). Het implementeren van een nieuwe integratie houdt alleen in dat u de functies implementeert die uw integratie nodig heeft. De front-end componenten kunnen door om het even welke nieuwe implementatie worden gebruikt aangezien zij interfaces (zo onafhankelijk van de implementatie zijn) gebruiken.

* De mogelijkheid om **ervaringsgestuurde handel op basis van verkoopgegevens en activiteiten**. Dit laat u vele scenario&#39;s realiseren:

   * Een voorbeeld hiervan kan zijn het verlagen van de verzendkosten wanneer de totale bestelling een bepaald bedrag overschrijdt.
   * U kunt ook seizoensgebonden aanbiedingen doen die profielgegevens gebruiken (bijvoorbeeld locatie). Deze kunnen vervolgens worden gemarkeerd, ook als dat nodig is, afhankelijk van andere factoren.

  In het onderstaande voorbeeld ziet u een gummetje omdat de inhoud van het karretje minder dan $75 bedraagt:

  ![winkelwagentje met clientcontext](/help/sites-administering/assets/chlimage_1-133.png)

  Dit kan worden gewijzigd wanneer de inhoud van het winkelwagentje meer dan $75 bedraagt:

  ![winkelwagentje met clientcontext na wijziging](/help/sites-administering/assets/chlimage_1-134.png)

* en andere functies, zoals:

   * De inhoud van het winkelwagentje blijft behouden tijdens sessies
   * Historie van volledige volgorde
   * Catalogusupdate uitvoeren

## Het kader {#the-framework}

De [Concepten](/help/commerce/cif-classic/administering/concepts.md) In dit hoofdstuk wordt het kader nader beschreven, maar wordt het kader op hoog niveau en met hoge snelheid bekeken:

### Wat? {#what}

* Het integratieframework biedt de API, een reeks componenten om functionaliteit te illustreren en diverse extensies om voorbeelden van verbindingsmethoden te bieden.
* Het kader biedt de basisstructuur die nodig is voor de uitvoering van een project.
* Het kader is uitbreidbaar.
* Het framework biedt geen kant-en-klare site. Er is altijd een zekere hoeveelheid ontwikkelingswerk nodig om het kader aan uw specificaties aan te passen.

### Waarom? {#why}

* Om de basismechanismen te verstrekken nodig om een aangepaste plaats van de Handel snel te realiseren.
* Tp biedt de flexibiliteit die nodig is voor de ontwikkeling van een echte eCommerce-site.
* Beste werkwijzen illustreren.
