---
title: Aanbevolen procedures voor e-mailsjablonen
seo-title: Best Practices for Email Templates
description: Vind beste praktijken bij het creëren van e-mailmalplaatjes in AEM.
seo-description: Find best practices on creating email templates in AEM.
uuid: 07417a63-7ca6-484c-b55d-57b319428329
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration, best-practices
content-type: reference
discoiquuid: 2418777e-4eb2-4d82-aa9e-8d1b0bf740f3
docset: aem65
exl-id: 6666eddc-dc17-4bd4-9d55-e6522f40a680
source-git-commit: 70be796a50a93267b965d00db1b359d9a809ec08
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 0%

---

# Aanbevolen procedures voor e-mailsjablonen {#best-practices-for-email-templates}

>[!CAUTION]
>
>Dit artikel is op de afgekeurde Componenten van de Stichting van toepassing die AEM e-mailcomponenten worden gebaseerd.
>
>Gebruikers worden aangemoedigd gebruik te maken van de moderne [E-mailcomponenten van kerncomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/email/introduction.html)

In dit document worden enkele van de aanbevolen procedures beschreven voor het ontwerpen van e-mailberichten. Dit resulteert in een goed ontwikkelde sjabloon voor e-mailcampagnes.

De demo-campagne in AEM volgt al deze beste praktijken. Hoe de beste praktijken in de demo campagne worden uitgevoerd wordt beschreven voor elke beste praktijken.

Gebruik deze aanbevolen procedures bij het maken van uw eigen nieuwsbrief.

>[!NOTE]
>
>Alle inhoud van de campagne moet worden gemaakt onder een `master` tekstpagina `cq/personalization/components/ambitpage`.
>
>Bijvoorbeeld als uw geplande campagnestructuur ongeveer als volgt is
>
>`/content/campaigns/teasers/en/campaign-promotion-global`
>
>Zorg ervoor dat het onder een `master` page
>
>`/content/campaigns/teasers/master/en/campaign-promotion-global`

>[!NOTE]
>
>Wanneer u een e-mailsjabloon voor Adobe Campaign maakt, moet u de eigenschap **acMapping** met de waarde **mapRecipient** in de **jcr:inhoud** van de sjabloon, of u kunt de Adobe Campaign-sjabloon niet selecteren in **Pagina-eigenschappen** AEM (veld is uitgeschakeld).

## Sjabloon/pagina-component {#template-page-component}

***/libs/mcm/campagne/components/campagne_newsletterpage***

<table>
 <tbody>
  <tr>
   <td><strong>Beste praktijken</strong></td>
   <td><strong>Implementatie</strong></td>
  </tr>
  <tr>
   <td><p>Geef het documenttype op om consistente rendering te garanderen.</p> <p>DOCTYPE toevoegen aan het begin (HTML of XHTML)</p> </td>
   <td><p>Is configureerbaar door ontwerp veranderend <i>cq:doctype</i> eigenschap in<i>"/etc/designs/default/jcr:content/campagne_newsletterpage"</i></p> <p>De standaardwaarde is "XHTML":</p> <p>&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;</p> <p>Kan worden gewijzigd in "HTML_5":</p> <p>&lt;!DOCTYPE HTML&gt;</p> </td>
  </tr>
  <tr>
   <td><p>Geef een tekendefinitie op om ervoor te zorgen dat speciale tekens correct worden weergegeven.</p> <p>CHARSET-declaratie toevoegen (bijvoorbeeld iso-8859-15, UTF-8) aan &lt;head&gt;</p> </td>
   <td><p>Is ingesteld op UTF-8.</p> <p>&lt;meta http-equiv="content-type" content="text/html; charset=UTF-8"&gt;</p> </td>
  </tr>
  <tr>
   <td><p>Alle structuur coderen met behulp van de &lt;table&gt;element. Voor complexere lay-outs moet u tabellen nesten om complexe structuren te maken.</p> <p>E-mail moet er goed uitzien, zelfs zonder css.</p> </td>
   <td><p>Tabellen worden in de gehele sjabloon gebruikt voor het structureren van inhoud. Momenteel met maximaal vier geneste tabellen (1 basislabel + max.) 3 nestniveaus)</p> <p>&lt;div&gt; -tags worden alleen gebruikt in de ontwerpmodus voor een juiste componentbewerking.</p> </td>
  </tr>
  <tr>
   <td>Gebruik elementkenmerken (zoals celopvulling, valsing en breedte) om tabelafmetingen in te stellen. Dit dwingt een box-model structuur.</td>
   <td><p>Alle tabellen bevatten noodzakelijke kenmerken, zoals <i>border</i>, <i>celopvulling</i>, <i>celafstand</i> en <i>width</i>.</p> <p>Om de plaatsing van elementen in tabellen te harmoniseren, hebben alle tabelcellen het kenmerk <i>valign="top"</i> wordt ingesteld.</p> </td>
  </tr>
  <tr>
   <td><p>Indien mogelijk rekening houden met de vriendelijkheid van mobiele apparaten. Gebruik mediaquery's om de tekstgrootte op kleine schermen te verhogen en selecteer aanraakgebieden met de grootte van het blokje voor koppelingen.</p> <p>Maak een e-mail ontvankelijk als het ontwerp het toestaat.</p> </td>
   <td>Voor zover CSS-stijlen worden gebruikt om demonstratieontwerp te illustreren, worden mediaquery's gebruikt om een mobiele versie aan te bieden.</td>
  </tr>
  <tr>
   <td>Inline CSS is beter dan het plaatsen van alle CSS aan het begin.</td>
   <td><p>Om de onderliggende HTML-structuur beter aan te tonen en de mogelijkheid om de nieuwsbrief-structuur aan te passen te vereenvoudigen, zijn slechts enkele CSS-definities gealigneerd.</p> <p>Basisstijlen en sjabloonvariaties zijn geëxtraheerd naar een stijlblok in het dialoogvenster &lt;head&gt; van de pagina. Bij de definitieve indiening van de nieuwsbrief moeten deze CSS-definities in de HTML worden opgenomen. Een automatisch inlineringsmechanisme is gepland, maar is momenteel niet beschikbaar.</p> </td>
  </tr>
  <tr>
   <td>Houd uw CSS eenvoudig. Vermijd samengestelde stijldeclaraties, korte code, CSS-lay-outeigenschappen, complexe kiezers en pseudo-elementen.</td>
   <td>Voor zover CSS-stijlen worden gebruikt om demonstratieontwerp te illustreren, worden de CSS-aanbevelingen gevolgd.</td>
  </tr>
  <tr>
   <td>E-mails moeten een maximale breedte van 600-800 pixels hebben. Hierdoor kunnen ze zich beter gedragen binnen de grootte van het voorvertoningsvenster die door veel clients wordt geboden.</td>
   <td>De <i>width</i> van inhoudsopgave is beperkt tot 600 px in demo-ontwerp.</td>
  </tr>
 </tbody>
</table>

### Afbeeldingen {#images}

/libs/mcm/campagne/componenten/image

| **Beste praktijken** | **Implementatie** |
|---|---|
| Toevoegen *alt* kenmerken voor afbeeldingen | De *alt* -kenmerk is gedefinieerd als verplicht voor de afbeeldingscomponent. |
| Gebruiken *jpg* in plaats van *png* bestandsindeling voor afbeeldingen | Afbeeldingen worden altijd door de afbeeldingscomponent als JPG weergegeven. |
| Gebruiken `<img>` in plaats van achtergrondafbeeldingen in een tabel. | Er worden geen achtergrondafbeeldingsgegevens gebruikt in de sjablonen. |
| Kenmerkstijl=&quot;weergaveblok&quot; toevoegen aan afbeeldingen. Staat toe om goed op Gmail te tonen. | Alle afbeeldingen bevatten standaard de *style=&quot;display block&quot;* kenmerk. |

### Tekst en koppelingen {#text-and-links}

/libs/mcm/campagne/components/heading, /libs/mcm/campagne/components/textiel

<table>
 <tbody>
  <tr>
   <td><strong>Beste praktijken</strong></td>
   <td><strong>Implementatie</strong></td>
  </tr>
  <tr>
   <td>HTML gebruiken in plaats van stijl in CSS (font-family)</td>
   <td>De RichTextEditor (bijvoorbeeld in de component van de textielafbeelding) ondersteunt nu het kiezen en toepassen van lettertypefamilies en tekengrootten op geselecteerde teksten. Ze worden weergegeven als tags.</td>
  </tr>
  <tr>
   <td>Gebruik standaard, platformonafhankelijke lettertypen, zoals <i>Arial, Verdana, Georgia</i> en <i>Times New Roman</i>.</td>
   <td><p>Afhankelijk van het ontwerp van de nieuwsbrief.</p> <p>Voor het demo-ontwerp wordt het lettertype "Helvetica" gebruikt, maar het wordt teruggezet naar het algemene sans-serif-lettertype, indien dit niet aanwezig is.</p> </td>
  </tr>
 </tbody>
</table>

### Algemeen {#generic}

| **Beste praktijken** | **Implementatie** |
|---|---|
| Gebruik W3C-validatie om de HTML-code te corrigeren. Zorg ervoor dat alle open labels goed zijn gesloten. | Code is gevalideerd. Voor XHTML-overgangsdocument alleen het ontbrekende xmlns-kenmerk voor de `<html>` element ontbreekt. |
| Let niet op met JavaScript of Flash - deze technologieën worden grotendeels niet ondersteund door e-mailclients. | JavaScript en Flash worden niet gebruikt in de sjabloon voor nieuwsbrieven. |
| Voeg een gewone tekstversie toe voor het verzenden van meerdere onderdelen. | Er is een nieuwe widget toegevoegd aan de pagina-eigenschappen om eenvoudig een plaintekstversie uit de pagina-inhoud te extraheren. Dit kan als uitgangspunt voor de definitieve plaintext versie worden gebruikt. |

## Sjablonen en voorbeelden voor nieuwsbrieven voor campagnes {#campaign-newsletter-templates-and-examples}

AEM wordt geleverd met verschillende sjablonen en componenten uit de doos die u kunt gebruiken om campagnebulletins te maken. U kunt deze sjablonen en componenten gebruiken om uw aangepaste nieuwsbrieven te maken.

### Sjablonen {#templates}

Er zijn drie enigszins verschillende sjabloontypen beschikbaar uit het vak om een solide basis aan te bieden en de verscheidenheid aan mogelijkheden voor inhoudsstroom uit te breiden. U kunt deze eenvoudig gebruiken om een aangepaste nieuwsbrief te maken.

Alle hebben een **header**, **voettekst** en **lichaam** sectie. Onder de hoofdsectie verschilt elke sjabloon in **kolomontwerp** (1, 2 of 3 kolommen).

![](assets/chlimage_1-69.png)

### Onderdelen {#components}

Er zijn momenteel [zeven componenten beschikbaar voor gebruik binnen campagnemalplaatjes](/help/sites-authoring/adobe-campaign-components.md). Deze componenten zijn allemaal gebaseerd op de opmaaktaal Adobe **HTL**.

| **Componentnaam** | **Componentpad** |
|---|---|
| Kop | /libs/mcm/campagne/componenten/kop |
| Afbeelding | /libs/mcm/campagne/componenten/image |
| Tekst&amp;personalisatie | /libs/mcm/campagne/componenten/personalisatie |
| Textimage | /libs/mcm/campagne/onderdelen/textielafbeelding |
| Koppeling | /libs/mcm/campagne/componenten/reference |
| Dynamic Media Classic (voorheen Scene7)-afbeeldingssjabloon | /libs/mcm/campagne/s7image |
| Gerichte referentie | /libs/mcm/campagne/componenten/reference |

>[!NOTE]
>
>Deze componenten zijn geoptimaliseerd voor e-mailinhoud. dat wil zeggen dat zij zich houden aan de beste praktijken die in dit document worden beschreven. Het gebruiken van andere uit-van-de-doos componenten zal gewoonlijk deze regels overtreden.

Deze componenten worden in detail beschreven [Adobe Campaign-componenten](/help/sites-authoring/adobe-campaign-components.md).
