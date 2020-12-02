---
title: eCommerce
seo-title: eCommerce
description: AEM eCommerce helpt marketers merkboodschap, persoonlijke boodschappen op internet, mobiel en sociaal gebied te leveren.
seo-description: AEM eCommerce helpt marketers merkboodschap, persoonlijke boodschappen op internet, mobiel en sociaal gebied te leveren.
uuid: 75818c60-1cf1-4a91-94ce-d722563b661c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: e972ee05-f0cb-40ca-9ae2-34395791c709
docset: aem65
translation-type: tm+mt
source-git-commit: 46610888fd61900c52b197e73a8a5850dc9c4c35
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---


# eCommerce{#ecommerce}

* [Concepten](/help/sites-administering/concepts.md)
* [Beheer (algemeen)](/help/sites-administering/generic.md)

Adobe verstrekt twee versies van het Kader van de Integratie van de Handel:

<table>
 <tbody>
  <tr>
   <th><p> </p> </th>
   <th><p>CIF on prem</p> </th>
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
     <li>Magento</li>
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
   <td>Ja, Magento GraphQL-schema</td>
  </tr>
  <tr>
   <td>Beschikbaarheid</td>
   <td><p>Ja. SAP Commerce Cloud (Extensie bijgewerkt ter ondersteuning van AEM 6.4 en Hybris 5 (standaard) en handhaaft compatibiliteit met Hybris 4</p> <p>Salesforce Commerce Cloud (connector open-sourced voor ondersteuning van AEM 6.4)</p> </td>
   <td>Ja via open bron via GitHub. Magento Commerce (Ondersteunt Magento 2.3.2 (standaard) en compatibel met Magento 2.3.1).</td>
  </tr>
  <tr>
   <td>Wanneer gebruiken</td>
   <td>Beperkte gebruiksgevallen: Bijvoorbeeld scenario's waarin kleine, statische catalogi mogelijk moeten worden geïmporteerd</td>
   <td>Voorkeursoplossing in de meeste gebruikscategorieën</td>
  </tr>
 </tbody>
</table>

eCommerce handelt samen met Product Information Management (PIM) de activiteiten van een website die gericht is op het verkopen van producten via een online-winkel:

* Maken, levensduur en veroudering van een product
* Prijsbeheer
* Transactiebeheer
* Beheer van volledige catalogi
* Live en gecentraliseerde opslagrecords
* Webinterfaces

AEM eCommerce helpt marketers merkboodschap, persoonlijke boodschappen op internet, mobiel en sociaal gebied te leveren. In de AEM ontwerpomgeving kunt u pagina&#39;s en componenten aanpassen op basis van de context en de marketingstrategieën van de doelbezoeker. bijvoorbeeld:

* Productpagina&#39;s
* Winkelwagentjes
* Onderdelen uitchecken

De implementatie maakt realtime toegang tot productinformatie mogelijk. Dit kan worden gebruikt om af te dwingen:

* Integriteit van productinformatie
* Prijzen
* Voorraadinventaris
* Variaties in de toestand van een winkelwagentje

>[!NOTE]
>
>Als u het integratieframework wilt gebruiken met externe eCommerce-providers, moet u eerst de vereiste pakketten installeren. Voor meer informatie, zie [Het Opstellen van eCommerce](/help/sites-deploying/ecommerce.md).
>
>Voor informatie over het uitbreiden van de mogelijkheden van de eCommerce, zie [Developing eCommerce](/help/sites-developing/ecommerce.md).

## Belangrijkste kenmerken {#main-features}

AEM eCommerce biedt:

* Een aantal **out-of-the-box AEM componenten** om te illustreren wat voor uw project kan worden bereikt:

   * Productweergave
   * Winkelwagentje
   * Uitchecken
   * Onlangs bekeken producten
   * Vouchers
   * en andere

   ![](assets/chlimage_1-130.png)

   >[!NOTE]
   >
   >Met het integratieframework dat AEM biedt, kunt u ook extra AEM maken voor handelsmogelijkheden, onafhankelijk van uw specifieke eCommerce-engine.

* **Zoeken** :

   * de AEM
   * het zoeken van het eCommerce-systeem
   * een zoekopdracht van derden (zoals Search&amp;Promote)
   * of een combinatie daarvan.

   ![](assets/chlimage_1-131.png)

* Gebruikt de AEM mogelijkheid om uw inhoud **op meerdere kanalen te presenteren**, of dat nu het volledige browservenster of het mobiele apparaat is. Hierdoor wordt uw inhoud geleverd in de indeling die uw bezoekers nodig hebben.

   ![](assets/chlimage_1-132.png)

* De mogelijkheid om **uw eigen integratieimplementatie te ontwikkelen op basis van het [AEM eCommerce-framework](#the-framework)**.

   De twee momenteel beschikbare implementaties zijn beide op dezelfde basis gebaseerd - bovenop de algemene API (het framework). Het implementeren van een nieuwe integratie houdt alleen in dat u de functies implementeert die uw integratie nodig heeft. De front-end componenten kunnen door om het even welke nieuwe implementatie worden gebruikt aangezien zij interfaces (zo onafhankelijk van de implementatie zijn) gebruiken.

* De mogelijkheid om **ervaringsgestuurde handel te ontwikkelen op basis van verkoopgegevens en activiteit**. Dit staat u toe om vele scenario&#39;s te realiseren:

   * Een voorbeeld hiervan kan zijn het verlagen van de verzendkosten wanneer de totale bestelling een bepaald bedrag overschrijdt.
   * Een andere mogelijkheid is mogelijk om seizoensgebonden aanbiedingen te doen die profielgegevens gebruiken (bijvoorbeeld locatie). Deze kunnen vervolgens worden gemarkeerd, ook als dat nodig is, afhankelijk van andere factoren.

   In het onderstaande voorbeeld ziet u een gummetje omdat de inhoud van het karretje minder dan $75 bedraagt:

   ![](assets/chlimage_1-133.png)

   Dit kan worden gewijzigd wanneer de inhoud van het winkelwagentje meer dan $75 bedraagt:

   ![](assets/chlimage_1-134.png)

* en andere functies, zoals:

   * De inhoud van het winkelwagentje blijft behouden tijdens sessies
   * Historie van volledige volgorde
   * Catalogusupdate uitvoeren

## Het framework {#the-framework}

In de sectie [Concepts](/help/sites-administering/concepts.md) wordt het framework gedetailleerder beschreven, maar de volgende secties bieden een snelle weergave op hoog niveau van het framework:

### Wat? {#what}

* Het integratieframework biedt de API, een reeks componenten om functionaliteit te illustreren en diverse extensies om voorbeelden van verbindingsmethoden te bieden.
* Het kader biedt de basisstructuur die nodig is voor de uitvoering van een project.
* Het kader is uitbreidbaar.
* Het framework biedt geen kant-en-klare site. Er is altijd een zekere hoeveelheid ontwikkelingswerk nodig om het kader aan uw specificaties aan te passen.

### Waarom? {#why}

* Om de basismechanismen te verstrekken nodig om een aangepaste plaats van de Handel snel te realiseren.
* Tp biedt de flexibiliteit die nodig is voor de ontwikkeling van een echte eCommerce-site.
* Beste werkwijzen illustreren.