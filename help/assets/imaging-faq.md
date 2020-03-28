---
title: Slimme beeldverwerking
description: Slimme beeldverwerking maakt gebruik van de unieke weergavekenmerken van elke gebruiker, zodat deze automatisch de juiste afbeeldingen levert die zijn geoptimaliseerd voor zijn of haar ervaring, wat resulteert in betere prestaties en betrokkenheid.
uuid: c11e52ba-8d64-4dc5-b30a-fc10c2b704e5
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: bf8c6bbd-847d-43d7-9ff4-7231bfd8d107
translation-type: tm+mt
source-git-commit: 3e37ee6da263bb12eb0efea85213987e8286bc60

---


# Smart Imaging {#smart-imaging}

## Wat is &quot;Smart Imaging&quot;? {#what-is-smart-imaging}

Smart Imaging-technologie maakt gebruik van Adobe Sensei AI-mogelijkheden en werkt met bestaande &quot;voorinstellingen voor afbeeldingen&quot; om de prestaties van de beeldlevering te verbeteren door de afbeeldingsindeling, -grootte en -kwaliteit automatisch te optimaliseren op basis van de mogelijkheden van de clientbrowser.

Smart Imaging biedt ook voordelen van de extra prestatieverhoging door volledig te zijn geïntegreerd met de hoogwaardige CDN-service van Adobe. Deze dienst vindt de optimale Internet route tussen servers, netwerken, en peerpunten die de laagste latentie, en/of pakketverliestarief dan de standaardroute op Internet hebben.

De volgende voorbeelden van afbeeldingselementen geven de toegevoegde optimalisatie van Smart Imaging aan:

| Afbeelding<br>(URL) | Miniatuur | Grootte<br> (JPEG) | Grootte (WebP)<br> (met slimme beeldverwerking) | % reductie |
|---|---|---|---|---|
| [Afbeelding 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&fmt=jpg&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![picture1](/help/assets/assets-dm/picture1.png) | 73,75 kB | 45,92 kB | 38% |
| [Afbeelding 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&fmt=jpg&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![picture2](/help/assets/assets-dm/picture2.png) | 191 kB | 70,66 kB | 63% |
| [Afbeelding 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&fmt=jpg&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![picture3](/help/assets/assets-dm/picture3.png) | 96,64 kB | 39,44 kB | 59% |
| [Afbeelding 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&qlt=85&resmode=bisharp&op_usm=5,0.125,5,0) | ![picture4](/help/assets/assets-dm/picture4.png) | 315,80 kB | 178,19 kB | 44% |
|  |  |  |  | Gemiddelde = 51% |

Net als het bovenstaande heeft Adobe ook een test uitgevoerd met 7009 URL&#39;s van live klantsites en kon het bestand gemiddeld 38% verder worden geoptimaliseerd voor JPEG en 31% verder worden geoptimaliseerd voor PNG met WebP-indeling, vanwege de mogelijkheid van Smart Imaging.

## Wat zijn de belangrijkste voordelen van de nieuwste Smart Imaging? {#what-are-the-key-benefits-of-smart-imaging}

Omdat de beelden een meerderheid van de ladingstijd van een pagina vormen, kan de prestatiesverbetering een diepgaande invloed op zaken KPIs zoals hogere omzetting, tijd die aan plaats wordt doorgebracht, en lagere plaats hebben stuitend tarief.

Verbeteringen in de nieuwste versie van Smart Imaging:

* Hiermee wordt geoptimaliseerde inhoud direct (tijdens runtime) weergegeven.
* Gebruikt Adobe Sensei-technologie voor conversie op basis van de kwaliteit (qlt) die is opgegeven in de afbeeldingsaanvraag.
* Smart Imaging kan worden uitgeschakeld met de URL-parameter &quot;bfc&quot;.
* onafhankelijk van TTL (Time to Live). Eerder was een minimale TTL van 12 uur verplicht voor Smart Imaging.
* Eerder waren zowel de oorspronkelijke als de afgeleide afbeeldingen in het cachegeheugen opgeslagen. Het was een proces van twee stappen om de cache ongeldig te maken. In de nieuwste Smart Imaging worden alleen de derivaten in het cachegeheugen opgeslagen, zodat een procedure voor het invalideren van het cachegeheugen in één stap mogelijk is.
* Klanten die in hun regels aangepaste kopteksten gebruiken (bijvoorbeeld &#39;&#39;Timing Allow Origin&#39;&#39;, &#39;&#39;X-Robot&#39;&#39; zoals wordt gesuggereerd in [Een aangepaste koptekstwaarde toevoegen aan reacties op afbeeldingen|Dynamische media Klassiek](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html)) profiteren van de nieuwste functie voor Smart Imaging, omdat deze kopteksten, in tegenstelling tot de vorige versie van Smart Imaging, niet worden geblokkeerd.

## Zijn er licentiekosten verbonden aan intelligente beeldverwerking? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Nee. Smart Imaging wordt meegeleverd bij uw bestaande licentie van Dynamic Media Classic (Scene7) of AEM Dynamic Media (On Prem, AMS en AEM als Cloud Service).

>[!NOTE]
>
>Smart Imaging is niet beschikbaar voor Dynamic Media - Hybride klanten.


## Hoe werkt intelligente beeldverwerking? {#how-does-smart-imaging-work}

Voor Smart Imaging wordt Adobe Sensei gebruikt om afbeeldingen automatisch om te zetten in de meest optimale indeling, grootte en kwaliteit, op basis van de browsermogelijkheden:

* Automatisch converteren naar WebP voor browsers zoals Chrome, Firefox, Microsoft Edge, Android en Opera.
* Automatisch omzetten in JPEG2000 voor browsers zoals Safari.
* Automatisch omzetten in JPEG voor browsers zoals Internet Explorer 9+.
* Voor browsers die deze indelingen niet ondersteunen, wordt de oorspronkelijk aangevraagde afbeeldingsindeling weergegeven.

Als de oorspronkelijke afbeelding kleiner is dan het resultaat van Smart Imaging, wordt de oorspronkelijke afbeelding weergegeven.

## Welke afbeeldingsindelingen worden ondersteund? {#what-image-formats-are-supported}

De volgende afbeeldingsindelingen worden ondersteund voor Smart Imaging:
* JPEG
* PNG

Voor elke andere indeling die in een URL wordt vermeld, moet u Slim beeld expliciet uitschakelen.  Voeg een optie `bfc=off` aan de URL toe voor andere bestandsindelingen dan JPEG en PNG. U kunt dit bereiken door één van beide volgende methodes te gebruiken:

* Gebruik een liniaal als de `fmt` modifier wordt vermeld in de URL.
* Toevoegen in het veld URL-wijzigingstoetsen van de betreffende voorinstellingen.

Adobe werkt aan een permanente oplossing waarvoor u geen toevoeging `bfc=off` voor `fmt !=JPEG` of `fmt !=PNG`. Dit onderwerp zal worden bijgewerkt nadat de moeilijke situatie wordt geleverd.


## Hoe werkt Smart Imaging met onze bestaande voorinstellingen voor afbeeldingen die al in gebruik zijn? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

Slimme afbeeldingen werken met uw bestaande &quot;voorinstellingen voor afbeeldingen&quot; en nemen alle afbeeldingsinstellingen in acht, met uitzondering van kwaliteit (qlt) en indeling (fmt) als de gewenste bestandsindeling JPEG of PNG is. Voor het omzetten van de bestandsindeling blijven de volledige visuele getrouwheid behouden, zoals wordt gedefinieerd door de instellingen van de voorinstelling voor de afbeelding, maar is het bestand kleiner. Als de oorspronkelijke afbeelding kleiner is dan het resultaat van Smart Imaging, wordt de oorspronkelijke afbeelding weergegeven.

Als de afbeeldingsvoorinstellingen worden gebruikt om terug te keren `fmt !=JPEG` of `fmt !=PNG`, moet u bovendien toevoegen `bfc=off` in het veld Voorinstelling wijzigen om de gewenste bestandsindeling te retourneren.

## Moet ik URL&#39;s, voorinstellingen voor afbeeldingen wijzigen of nieuwe code op mijn site implementeren voor Smart Imaging? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Nee. Slimme afbeeldingen werken naadloos met bestaande URL&#39;s voor afbeeldingen en voorinstellingen voor afbeeldingen. Bovendien hoeft u bij Slimme afbeeldingen geen code aan uw website toe te voegen om de browser van een gebruiker te detecteren. Dit alles wordt automatisch afgehandeld.

Zoals eerder vermeld, ondersteunt Smart Imaging alleen JPEG- en PNG-afbeeldingsindelingen. Voor andere indelingen moet u de `bfc=off` bepaling aan URL toevoegen zoals eerder beschreven.

Zie ook [Ben ik verkiesbaar om Slimme Beelden te gebruiken?](#am-i-eligible-to-use-smart-imaging) om inzicht te krijgen in de vereisten voor slimme beeldverwerking.

## Werkt Smart Mmaging met HTTPS? Hoe zit het met HTTP/2? {#does-smart-imaging-working-with-https-how-about-http}

Slimme afbeeldingen werken met afbeeldingen die via HTTP of HTTPS worden geleverd. Bovendien werkt het ook via HTTP/2.

## Mag ik slimme beeldverwerking gebruiken? {#am-i-eligible-to-use-smart-imaging}

Als u Smart Imaging wilt gebruiken, moet de Dynamic Media Classic of Dynamic Media van uw bedrijf op een AEM-account aan de volgende vereisten voldoen:

* Gebruik de door Adobe gebundelde CDN (Content Delivery Network) als onderdeel van uw licentie.
* Gebruik een specifiek domein (bijvoorbeeld, `images.company.com` of `mycompany.scene7.com`) en geen algemeen domein (bijvoorbeeld, `s7d1.scene7.com`, `s7d2.scene7.com`, of `s7d13.scene7.com`).

Meld u aan bij uw bedrijfsaccount of accounts om uw domeinen te zoeken.

Tik op **[!UICONTROL Instellingen > Toepassingsinstellingen > Algemene instellingen]**. Zoek het veld **[!UICONTROL Gepubliceerde servernaam]**. Als u momenteel een generisch domein gebruikt, kunt u verzoeken zich over naar uw eigen douanedomein als deel van deze overgang te bewegen wanneer u een technisch steunkaartje voorlegt.

Uw eerste aangepaste domein kost geen extra geld met een Dynamic Media-licentie.

## Wat is het proces voor het inschakelen van Smart Imaging voor mijn account? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

U moet het verzoek starten om intelligente beeldverwerking te gebruiken. deze wordt niet automatisch ingeschakeld.

1. Een aanvraag voor technische ondersteuning starten (e-mail: `s7support@adobe.com`).
1. Geef de volgende informatie op in uw supportverzoek:

   1. Primaire contactpersoon, e-mail, telefoon.
   1. Alle domeinen die moeten worden ingeschakeld voor slimme beeldverwerking (dat wil zeggen `images.company.com` of `mycompany.scene7.com`).

      Meld u aan bij uw bedrijfsaccount of accounts om uw domeinen te zoeken.

      Klik op **[!UICONTROL Setup > Application Setup > General Settings]**.

      Zoek het veld **[!UICONTROL Gepubliceerde servernaam]**.
   1. Controleer of u de CDN gebruikt via Adobe en niet met een directe relatie.
   1. Verifieer u een specifiek domein zoals `images.company.com` of `mycompany.scene7.com`, en niet een generisch domein, zoals, `s7d1.scene7.com`, `s7d2.scene7.com``s7d13.scene7.com`gebruikt.

      Meld u aan bij uw bedrijfsaccount of accounts om uw domeinen te zoeken.

      Klik op **[!UICONTROL Setup > Application Setup > General Settings]**.

      Zoek het veld **[!UICONTROL Gepubliceerde servernaam]**. Als u momenteel een generisch Dynamisch Dynamisch Klassiek domein van Media gebruikt, kunt u verzoeken zich over naar uw eigen douanedomein als deel van deze overgang te bewegen.
   1. Geef aan of u dit ook nodig hebt om via HTTP/2 te werken.

1. De technische Steun zal u aan de Slimme Lijst van de Wacht van het Beeld toevoegen die op de orde wordt gebaseerd waarin de verzoeken werden voorgelegd.
1. Wanneer Adobe klaar is om uw verzoek te verwerken, neemt de ondersteuning contact met u op om een doeldatum te coördineren en in te stellen.
1. **Optioneel**: U kunt slimme beeldverwerking in Staging testen voordat de nieuwe functie door Adobe wordt omgezet in productie.
1. U wordt op de hoogte gesteld na voltooiing door ondersteuning.
1. Adobe raadt u aan om de prestaties van Smart Imaging te verbeteren door de tijd voor live (TTL) in te stellen op 24 uur of langer. De TTL bepaalt hoe lang de activa door CDN in het voorgeheugen worden opgeslagen. Deze instelling wijzigen:

   1. Als u Dynamic Media Classic gebruikt, klikt u op **[!UICONTROL Instellingen > Toepassingsinstellingen > Publicatie-instellingen > Afbeeldingsserver]**. Stel de **[!UICONTROL standaardtijd voor clientcache in op Live]** -waarde op 24 of hoger.
   1. Als u Dynamic Media gebruikt, volgt u [deze instructies](config-dynamic.md). Stel de waarde voor **[!UICONTROL Verlopen]** 24 uur of langer in.

## Wanneer kan ik verwachten dat mijn account is ingeschakeld met Smart Imaging? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

De verzoeken worden verwerkt in de orde waarin zij door Technische Steun, volgens de Wachtlijst worden ontvangen.

>[!NOTE]
Er kan een lange gebruiksduur zijn, omdat het inschakelen van Smart Imaging inhoudt dat Adobe de cache wist. Daarom kunnen slechts een paar klantenovergangen op elk bepaald ogenblik worden behandeld.

## Wat zijn de risico&#39;s wanneer u overschakelt naar het gebruik van Smart Imaging? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

Er is geen risico voor een klantenwebpagina. Nochtans, zou u zich ervan bewust moeten zijn dat de overgang aan Slimme Beelden uw geheime voorgeheugen bij CDN ontruimt omdat het het bewegen aan een nieuwe configuratie van Dynamische Media Klassieke of Dynamische Media op AEM impliceert.

Tijdens de eerste overgang raken de niet-in de cache opgeslagen afbeeldingen de oorspronkelijke servers van Adobe rechtstreeks aan totdat het cachegeheugen opnieuw wordt opgebouwd. Daarom is Adobe van plan enkele klantovergangen tegelijk af te handelen, zodat acceptabele prestaties behouden blijven wanneer verzoeken van onze oorsprong worden opgehaald. Voor de meeste klanten wordt het cachegeheugen binnen ~1 tot 2 dagen volledig opgebouwd bij de CDN.

## Hoe kan ik controleren of slimme beeldverwerking werkt zoals verwacht?  {#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Wanneer uw account is geconfigureerd met slimme beeldverwerking, laadt u een URL voor de afbeelding Dynamic Media Classic (Scene7)/Dynamic Media in de browser.
1. Open het deelvenster Chrome-ontwikkelaar door in de browser op **[!UICONTROL Weergave > Ontwikkelaar > Gereedschappen]** voor ontwikkelaars te klikken. Of kies een ander browserontwikkelaarsgereedschap van uw keuze.

1. Zorg ervoor dat de cache is uitgeschakeld wanneer de ontwikkelprogramma&#39;s zijn geopend.

   * In Windows: navigeer naar de instellingen in het venster voor het gereedschap Ontwikkelaar en schakel vervolgens het selectievakje Cache **[!UICONTROL uitschakelen (terwijl de apparaten geopend zijn)]** in.
   * On Mac – in the developer pane, under the **[!UICONTROL Network]** tab, select **[!UICONTROL disable cache]** .

1. Waarnemen dat het inhoudstype wordt omgezet in de juiste indeling. In de volgende schermafbeelding ziet u een PNG-afbeelding die dynamisch wordt omgezet in WebP op Chrome.
1. Herhaal deze test voor verschillende browsers en gebruikersomstandigheden.

>[!NOTE]
Niet alle afbeeldingen worden geconverteerd. Smart Imaging bepaalt of de conversie nodig is om de prestaties te verbeteren. In sommige gevallen waarin er geen verwachte prestatieverhoging is of de indeling geen JPEG of PNG is, wordt de afbeelding niet geconverteerd.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

## Kan Smart Imaging voor een aanvraag worden uitgeschakeld? {#turning-off-smart-imaging}

Ja. U kunt Smart Imaging uitschakelen door de optie aan de URL toe `bfc=off` te voegen.

## Wat is &quot;tuning&quot; beschikbaar? Zijn er instellingen of gedragingen die kunnen worden gedefinieerd? (#tuning-settings)

Op dit moment kunt u Smart Imaging optioneel in- of uitschakelen. Er is geen andere tuning beschikbaar.

## Als Smart Imaging de kwaliteitsinstellingen beheert, zijn er dan minimum- en maximumwaarden die we kunnen instellen? Is het bijvoorbeeld mogelijk om &quot;niet lager dan 60&quot; en &quot;niet groter dan 80&quot; in te stellen? (#minimum-maximum)

De huidige slimme beeldverwerking biedt geen dergelijke provisioningmogelijkheden.

## In sommige gevallen wordt een JPEG-afbeelding geretourneerd naar Chrome in plaats van een WebP-afbeelding. Waarom gebeurt dat? (#jpeg-webp)

Slimme afbeeldingen bepalen of de conversie nuttig is of niet. De nieuwe afbeelding wordt alleen geretourneerd als de conversie resulteert in een kleinere bestandsgrootte met vergelijkbare kwaliteit.
