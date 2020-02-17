---
title: Codetips
seo-title: Codetips
description: Tips voor codering voor AEM
seo-description: Tips voor codering voor AEM
uuid: 1bb1cc6a-3606-4ef4-a8dd-7c08a7cf5189
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 4adce3b4-f209-4a01-b116-a5e01c4cc123
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Codetips{#coding-tips}

## Taglibs of HTML zoveel mogelijk gebruiken {#use-taglibs-or-htl-as-much-as-possible}

Het opnemen van scriptlets in JSPs maakt het moeilijk om kwesties in de code te zuiveren. Bovendien, door scriptlets in JSPs op te nemen, is het moeilijk om bedrijfslogica van de meningslaag te scheiden, die een schending van het Enige Verantwoordelijkheidsbeginsel en het ontwerppatroon MVC vormt.

### Leesbare code schrijven {#write-readable-code}

Code wordt één keer geschreven, maar vaak gelezen. Als we enige tijd op voorhand besteden aan het opschonen van de code die we schrijven, zullen we dividend uitbetalen over de weg, terwijl we en andere ontwikkelaars het later moeten lezen.

### Namen kiezen die bedoeld zijn om te onthullen {#choose-intention-revealing-names}

Idealiter hoeft een andere programmeur geen module te openen om te begrijpen wat deze doet. Ze moeten ook kunnen zien wat een methode doet zonder deze te lezen. Hoe beter we ons kunnen abonneren op deze ideeën, hoe gemakkelijker het is om onze code te lezen en hoe sneller we onze code kunnen schrijven en wijzigen.

In de basis van de AEM-code worden de volgende conventies gebruikt:


* Er wordt één implementatie van een interface genoemd, `<Interface>Impl`d.w.z. `ReaderImpl`.
* De veelvoudige implementaties van een interface worden genoemd `<Variant><Interface>`, d.w.z. `JcrReader` en `FileSystemReader`.
* Abstracte basisklassen worden benoemd `Abstract<Interface>` of `Abstract<Variant><Interface>`.
* Pakketten krijgen de naam `com.adobe.product.module`.  Elke Maven-artefact- of OSGi-bundel moet een eigen pakket hebben.
* Java-implementaties worden in een impl-pakket onder de bijbehorende API geplaatst.


Deze conventies hoeven niet noodzakelijkerwijs van toepassing te zijn op de implementaties van de klant, maar het is belangrijk dat conventies worden gedefinieerd en nageleefd, zodat de code behouden kan blijven.

In het ideale geval zouden namen hun intentie moeten onthullen. Een gemeenschappelijke codetest voor wanneer de namen niet zo duidelijk zijn aangezien zij zouden moeten zijn de aanwezigheid van commentaren die verklaren wat de variabele of de methode voor zijn:

<table>
 <tbody>
  <tr>
   <td><p><strong>Onduidelijk</strong></p> </td>
   <td><p><strong>Wissen</strong></p> </td>
  </tr>
  <tr>
   <td><p>int d; //verstreken tijd in dagen</p> </td>
   <td><p>int elapsedTimeInDays;</p> </td>
  </tr>
  <tr>
   <td><p>//get getagde afbeeldingen<br /> public List getItems() {}</p> </td>
   <td><p>public List getTaggedImages() {}</p> </td>
  </tr>
 </tbody>
</table>

### Niet herhalen {#don-t-repeat-yourself}

DRY geeft aan dat dezelfde codeset nooit mag worden gedupliceerd. Dit geldt ook voor zaken als letterlijke tekenreeksen. Codeduplicatie opent de deur voor defecten wanneer iets moet veranderen en moet worden gezocht en geëlimineerd.

### Naakte CSS-regels vermijden {#avoid-naked-css-rules}

CSS-regels moeten specifiek zijn voor uw doelelement in de context van uw toepassing. Een CSS-regel die bijvoorbeeld op *.content.center* wordt toegepast, zou te breed zijn en zou mogelijk veel inhoud op uw systeem beïnvloeden, waardoor anderen in de toekomst deze stijl moeten overschrijven. *.myapp-centertext* zou een specifiekere regel zijn aangezien het gecentreerde *tekst* in de context van uw toepassing specificeert.

### Gebruik van verouderde API&#39;s elimineren {#eliminate-usage-of-deprecated-apis}

Wanneer een API wordt afgekeurd, is het altijd beter om de nieuwe geadviseerde benadering te vinden in plaats van het vertrouwen op afgekeurde API. Hierdoor zijn upgrades in de toekomst vloeiender.

### Lokaliseerbare code schrijven {#write-localizable-code}

Tekenreeksen die niet door een auteur worden verschaft, moeten worden opgenomen in een aanroep van het i18n-woordenboek van AEM via *I18n.get()* in JSP/Java en *CQ.I18n.get()* in JavaScript. Deze implementatie retourneert de tekenreeks die eraan is doorgegeven als er geen implementatie wordt gevonden. Dit biedt dus de flexibiliteit om lokalisatie te implementeren nadat de functies in de primaire taal zijn geïmplementeerd.

### Escape-hulpbronnenpaden voor veiligheid {#escape-resource-paths-for-safety}

Paden in het JCR mogen geen spaties bevatten, maar de aanwezigheid ervan mag er niet toe leiden dat code wordt afgebroken. Jackrabbit biedt een hulpprogrammaklasse Text met *escape()* - en *escapePath()* -methoden. Voor JSPs, stelt granite UI een *granite:encodeURIPath () EL* functie bloot.

### Gebruik de XSS API en/of HTML om tegen cross-site scripting aanvallen te beschermen {#use-the-xss-api-and-or-htl-to-protect-against-cross-site-scripting-attacks}

AEM verstrekt een XSS API om parameters gemakkelijk schoon te maken en veiligheid van dwars-plaats scripting aanvallen te verzekeren. Bovendien heeft HTL deze beschermingen direct in de sjabloontaal ingebouwd. Een API-controlepagina kan worden gedownload via [Development - Guidelines and Best Practices](/help/sites-developing/dev-guidelines-bestpractices.md).

### Pas het aangewezen registreren toe {#implement-appropriate-logging}

Voor code Java, steunt AEM slf4j als standaard API voor het registreren van berichten en zou samen met de configuraties moeten worden gebruikt die door de console OSGi voor consistentie in beleid ter beschikking worden gesteld. Slf4j stelt vijf verschillende registrerenniveaus bloot. Wij adviseren gebruikend de volgende richtlijnen wanneer het kiezen welk niveau om een bericht bij te registreren:

* FOUT: Wanneer er iets in de code is verbroken en de verwerking niet kan worden voortgezet. Dit gebeurt vaak als gevolg van een onverwachte uitzondering. Het is meestal handig om stacksporen in deze scenario&#39;s op te nemen.
* WAARSCHUWING: Als iets niet goed heeft gewerkt, maar de verwerking kan doorgaan. Dit zal vaak het resultaat van een uitzondering zijn die wij, zoals een *PathNotFoundException* verwachtten.
* INFO: Informatie die nuttig zou zijn wanneer het controleren van een systeem. Onthoud dat dit de standaardinstelling is en dat de meeste klanten dit op hun plaats zullen laten in hun omgeving. Gebruik het daarom niet te veel.
* FOUTOPSPORING: Informatie op een lager niveau over verwerking. Nuttig wanneer het zuiveren van een kwestie met steun.
* TRACE: Het laagste niveau van informatie, dingen zoals het ingaan van/het verlaten van methodes. Dit zal gewoonlijk slechts door ontwikkelaars worden gebruikt.

In het geval van JavaScript, zou *console.log* slechts tijdens ontwikkeling moeten worden gebruikt en alle logboekverklaringen zouden vóór versie moeten worden verwijderd.

### Ladingencatalogus vermijden {#avoid-cargo-cult-programming}

Vermijd het kopiëren van code zonder te begrijpen wat het doet. In geval van twijfel is het altijd beter om iemand te vragen die meer ervaring heeft met de module of API waarop u niet duidelijk bent.
