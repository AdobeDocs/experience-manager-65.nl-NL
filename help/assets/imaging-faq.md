---
title: Slimme beeldverwerking
description: Slimme beeldverwerking past de unieke weergavekenmerken van elke gebruiker toe, zodat deze automatisch de juiste afbeeldingen levert die zijn geoptimaliseerd voor zijn of haar ervaring, wat resulteert in betere prestaties en betrokkenheid.
uuid: c11e52ba-8d64-4dc5-b30a-fc10c2b704e5
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: bf8c6bbd-847d-43d7-9ff4-7231bfd8d107
feature: Beheer van bedrijfsmiddelen
role: Bedrijfs Praktijk, Beheerder
translation-type: tm+mt
source-git-commit: 2e734041bdad7332c35ab41215069ee696f786f4
workflow-type: tm+mt
source-wordcount: '1830'
ht-degree: 0%

---


# Smart Imaging {#smart-imaging}

## Wat is &quot;Smart Imaging&quot;? {#what-is-smart-imaging}

Slimme beeldverwerking past Adobe Sensei AI-mogelijkheden toe en werkt met bestaande &quot;voorinstellingen voor afbeeldingen&quot; om de prestaties van de beeldlevering te verbeteren door de afbeeldingsindeling, -grootte en -kwaliteit automatisch te optimaliseren op basis van de mogelijkheden van de clientbrowser.

>[!NOTE]
>
>Voor deze functie is het vereist dat u de CDN uit de doos gebruikt die bij Adobe Experience Manager Dynamic Media is gebundeld. Een andere aangepaste CDN wordt niet ondersteund met deze functie.

De slimme Beeldvorming profiteert ook van de extra prestatiesverhoging van volledig geïntegreerd zijn met de best-in-klasse de dienst van CDN van de Adobe. Deze dienst vindt de optimale Internet route tussen servers, netwerken, en peering punten. Het vindt een route die de laagste latentie en het laagste tarief van het pakketverlies in plaats van het gebruiken van de standaardroute op Internet heeft.

De volgende voorbeelden van afbeeldingselementen geven de toegevoegde optimalisatie van Smart Imaging aan:

| Afbeelding<br>(URL) | Miniatuur | Grootte<br> (JPEG) | Grootte (WebP)<br> (met Smart Imaging) | % reductie |
|---|---|---|---|---|
| [Afbeelding 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![beeld1](/help/assets/assets-dm/picture1.png) | 73,75 kB | 45,92 kB | 38% |
| [Afbeelding 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture2](/help/assets/assets-dm/picture2.png) | 191 kB | 70,66 kB | 63% |
| [Afbeelding 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture3](/help/assets/assets-dm/picture3.png) | 96,64 kB | 39,44 kB | 59% |
| [Afbeelding 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture4](/help/assets/assets-dm/picture4.png) | 315,80 kB | 178,19 kB | 44% |
|  |  |  |  | Gemiddelde = 51% |

Net als hierboven heeft Adobe ook een test uitgevoerd met 7009 URL&#39;s van live klantsites. Dankzij de mogelijkheden van Smart Imaging konden ze gemiddeld 38% meer optimalisatie voor de bestandsgrootte van JPEG bereiken en 31% meer optimalisatie voor de bestandsgrootte van PNG met WebP-indeling.

## Wat zijn de belangrijkste voordelen van de nieuwste Smart Imaging? {#what-are-the-key-benefits-of-smart-imaging}

Omdat de beelden het grootste deel van de ladingstijd van een pagina vormen, kan de prestatiesverbetering een diepgaande invloed op een Zaken zoals hogere omzetting, tijd die aan plaats wordt doorgebracht, en lagere plaats het stuiteren tarief hebben.

Verbeteringen in de nieuwste versie van Smart Imaging:

* Hiermee wordt geoptimaliseerde inhoud direct (tijdens runtime) weergegeven.
* Gebruikt Adobe Sensei-technologie voor conversie op basis van de kwaliteit (qlt) die is opgegeven in de afbeeldingsaanvraag.
* Smart Imaging kan worden uitgeschakeld met de URL-parameter &quot;bfc&quot;.
* onafhankelijk van TTL (Time to Live). Eerder was een minimale TTL van 12 uur verplicht voor Smart Imaging.
* Eerder waren zowel de oorspronkelijke als de afgeleide afbeeldingen in het cachegeheugen opgeslagen. Het was een proces van twee stappen om de cache ongeldig te maken. Bij de nieuwste Smart Imaging worden alleen de derivaten in het cachegeheugen opgeslagen, zodat een cachevalidatieproces in één stap mogelijk is.
* Klanten die aangepaste kopteksten in hun regels gebruiken. Bijvoorbeeld &quot;Timing Allow Origin&quot;, &quot;X-Robot&quot; zoals voorgesteld in [Een aangepaste koptekstwaarde toevoegen aan afbeeldingsreacties|Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html)). Ze kunnen profiteren van de nieuwste functie voor slimme afbeeldingen, omdat deze headers, in tegenstelling tot de vorige versie van Smart Imaging, niet worden geblokkeerd.

## Zijn er licentiekosten verbonden aan intelligente beeldverwerking? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Nee. Smart Imaging is inbegrepen bij uw bestaande licentie van Dynamic Media Classic of Adobe Experience Manager - Dynamic Media (On-prem, AMS en AEM als Cloud Service).

>[!NOTE]
>
>Smart Imaging is niet beschikbaar voor Dynamic Media - Hybride klanten.


## Hoe werkt intelligente beeldverwerking? {#how-does-smart-imaging-work}

Wanneer een consument om een afbeelding vraagt, controleert Smart Imaging de gebruikerskenmerken en wordt deze op basis van de gebruikte browser omgezet in de juiste afbeeldingsindeling. Deze formaatomzettingen worden gedaan op een manier die geen visuele getrouwheid degradeert. Met Slimme afbeeldingen worden afbeeldingen op de volgende manier automatisch omgezet in verschillende indelingen op basis van browsermogelijkheden.

* Automatisch converteren naar WebP voor de volgende browsers:
   * Chroom
   * Firefox
   * Microsoft Edge
   * Safari 14.0 +
      * Alleen Safari 14 met iOS 14.0 en hoger en macOS BigSur en hoger
   * Android
   * Opera
* Ondersteuning voor oudere browsers:

   | Browser | Versie browser/besturingssysteem | Format |
   | --- | --- | --- |
   | Safari | iOS 14.0 of eerder | JPEG2000 |
   | Rand | 18 of lager | JPEGXR |
   | Internet Explorer | 9+ | JPEGXR |
* Voor browsers die deze indelingen niet ondersteunen, wordt de oorspronkelijk aangevraagde afbeeldingsindeling weergegeven.

Als de oorspronkelijke afbeelding kleiner is dan het resultaat van Smart Imaging, wordt de oorspronkelijke afbeelding weergegeven.

## Welke afbeeldingsindelingen worden ondersteund? {#what-image-formats-are-supported}

De volgende afbeeldingsindelingen worden ondersteund voor Smart Imaging:
* JPEG
* PNG

<!-- For any other format mentioned in a URL, you should explicity turn off Smart Imaging.  Append modifier `bfc=off` to the URL for file formats other than JPEG and PNG. You can accomplish this by using either one of the following methods:

* Use a ruleset if the `fmt` modifier is mentioned in the URL. 
* Append in URL modifiers field of the presets concerned.

Adobe is working on a permanent fix that does not require you to append `bfc=off` for `fmt !=JPEG` or `fmt !=PNG`. This topic will be updated after the fix is delivered. -->

## Hoe werkt Smart Imaging met mijn bestaande voorinstellingen voor afbeeldingen die al in gebruik zijn? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

Slimme afbeeldingen werken met uw bestaande &quot;voorinstellingen voor afbeeldingen&quot; en nemen alle afbeeldingsinstellingen in acht, behalve de instellingen voor kwaliteit (qlt) en indeling (fmt) als de gewenste bestandsindeling JPEG of PNG is. Voor conversie van indelingen behoudt Smart Imaging volledige visuele getrouwheid zoals gedefinieerd door de vooraf ingestelde instellingen van de afbeelding, maar met een kleinere bestandsgrootte. Als de oorspronkelijke afbeelding kleiner is dan het resultaat van Smart Imaging, wordt de oorspronkelijke afbeelding weergegeven.

<!-- In addition, if your image presets are used to return `fmt !=JPEG` or `fmt !=PNG`, be sure append `bfc=off` in the preset modifier field to return the requested file format. -->

## Moet ik URL&#39;s, afbeeldingsvoorinstellingen wijzigen of nieuwe code op mijn site implementeren voor Smart Imaging? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Smart Imaging werkt naadloos met uw bestaande afbeeldings-URL&#39;s en voorinstellingen voor afbeeldingen als u Smart Imaging configureert op uw bestaande aangepaste domein. Bovendien hoeft u bij Slimme afbeeldingen geen code aan uw website toe te voegen om de browser van een gebruiker te detecteren. Deze wordt allemaal automatisch afgehandeld.

Als u een nieuw aangepast domein moet configureren voor het gebruik van Smart Imaging, moeten de URL&#39;s worden bijgewerkt om dit aangepaste domein te weerspiegelen.

Zie [Ben ik geschikt voor het gebruik van Smart Imaging?](#am-i-eligible-to-use-smart-imaging) voor meer informatie over de vereisten voor Smart Imaging.

<!-- No. Smart Imaging works seamlessly with your existing image URLs and image presets. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. All of this is handled automatically. -->

<!-- As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. -->

## Werkt Smart Imaging met HTTPS? Hoe zit het met HTTP/2? {#does-smart-imaging-working-with-https-how-about-http}

Slimme afbeeldingen werken met afbeeldingen die via HTTP of HTTPS worden geleverd. Bovendien werkt het ook via HTTP/2.

## Mag ik slimme beeldverwerking gebruiken? {#am-i-eligible-to-use-smart-imaging}

Als u Smart Imaging wilt gebruiken, moet Dynamic Media Classic of Dynamic Media van uw bedrijf voor AEM account aan de volgende vereisten voldoen:

* Gebruik Adobe-Gebundelde CDN (het Netwerk van de Levering van de Inhoud) als deel van uw vergunning.
* Gebruik een specifiek domein (bijvoorbeeld `images.company.com` of `mycompany.scene7.com`), niet een algemeen domein (bijvoorbeeld `s7d1.scene7.com`, `s7d2.scene7.com` of `s7d13.scene7.com`).

Als u uw domeinen wilt zoeken, opent u [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) en meldt u zich aan bij uw bedrijfsaccount of -accounts.

Tik **[!UICONTROL Setup > Application Setup > General Settings.]** Zoek het veld met het label **[!UICONTROL Published Server Name.]** Als u momenteel een algemeen domein gebruikt, kunt u vragen dat u als onderdeel van deze overgang naar uw eigen aangepast domein gaat wanneer u een technisch ondersteuningsticket verzendt.

Voor je eerste aangepaste domein zijn er geen extra kosten verbonden met een Dynamic Media-licentie.

## Wat is het proces voor het inschakelen van Smart Imaging voor mijn account? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

U start het verzoek om intelligente beeldverwerking te gebruiken; deze wordt niet automatisch ingeschakeld.

1. [Gebruik de Admin Console om een draagtas te maken.](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
1. Geef de volgende informatie op in uw ondersteuningsgeval:

   1. Primaire contactpersoon, e-mail, telefoon.
   1. Alle domeinen die voor slimme beeldverwerking (namelijk `images.company.com` of `mycompany.scene7.com`) moeten worden toegelaten.

      Als u uw domeinen wilt zoeken, opent u [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) en meldt u zich aan bij uw bedrijfsaccount of -accounts.

      Klik op **[!UICONTROL Setup > Application Setup > General Settings.]**

      Zoeken naar het veld met het label **[!UICONTROL Published Server Name.]**
   1. Verifieer dat u CDN door Adobe gebruikt en niet met een directe verhouding wordt beheerd.
   1. Verifieer u een specifiek domein zoals `images.company.com` of `mycompany.scene7.com`, en niet een generisch domein, zoals `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com` gebruikt.

      Als u uw domeinen wilt zoeken, opent u [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) en meldt u zich aan bij uw bedrijfsaccount of -accounts.

      Klik op **[!UICONTROL Setup > Application Setup > General Settings.]**

      Zoek het veld met het label **[!UICONTROL Published Server Name.]** Als u momenteel een algemeen Dynamic Media Classic-domein gebruikt, kunt u vragen dat u als onderdeel van deze overgang naar uw eigen aangepaste domein gaat.
   1. Geef aan of deze via HTTP/2 moet werken.

1. De Zorg van de Klant van Adobe voegt u aan de Slimme Lijst van de Wacht van het Beeld toe de klant gebaseerd op de orde waarin de verzoeken werden voorgelegd.
1. Wanneer Adobe bereid is om uw verzoek te behandelen, steuncontacten u om een doeldatum te coördineren en te plaatsen.
1. **Optioneel**: U kunt optioneel de functie voor het maken van slimme afbeeldingen in Staging testen voordat Adobe de nieuwe functie in productie neemt.
1. U wordt op de hoogte gesteld na voltooiing door ondersteuning.
1. Om de prestatieverbeteringen van Smart Imaging te maximaliseren, raadt Adobe aan om de Time To Live (TTL) in te stellen op 24 uur of langer. De TTL bepaalt hoe lang de activa door CDN in het voorgeheugen worden opgeslagen. Deze instelling wijzigen:

   1. Als u Dynamic Media Classic gebruikt, klikt u op **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server.]** Stel de waarde **[!UICONTROL Default Client Cache Time To Live]** in op 24 of hoger.
   1. Als u Dynamic Media gebruikt, volgt u [deze instructies](config-dynamic.md). Stel de waarde **[!UICONTROL Expiration]** 24 uur of langer in.

## Wanneer kan ik verwachten dat mijn account is ingeschakeld met Smart Imaging? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

De verzoeken worden verwerkt in de orde waarin zij door de Zorg van de Klant, volgens de Wachtlijst worden ontvangen.

>[!NOTE]
Er kan een lange aanlooptijd zijn, omdat het inschakelen van Smart Imaging Adobe het wissen van de cache met zich meebrengt. Daarom kunnen slechts een paar klantenovergangen op elk bepaald ogenblik worden behandeld.

## Wat zijn de risico&#39;s wanneer u overschakelt op het gebruik van Smart Imaging? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

Er is geen risico voor een klantenwebpagina. Bij de overgang naar Smart Imaging wordt de cache bij de CDN echter gewist, omdat er bij de Experience Manager naar een nieuwe configuratie van Dynamic Media Classic of Dynamic Media moet worden overgeschakeld.

Tijdens de eerste overgang raakten de afbeeldingen in de cache rechtstreeks op servers die niet in de Adobe zijn opgeslagen, totdat het cachegeheugen opnieuw wordt opgebouwd. Dientengevolge, is Adobe van plan om een paar klantenovergangen in een tijd te behandelen zodat de aanvaardbare prestaties worden gehandhaafd wanneer het trekken van verzoeken van de oorsprong. Voor de meeste klanten wordt de cache binnen ~1 - 2 dagen volledig opnieuw opgebouwd bij de CDN.

## Hoe kan ik controleren of slimme beeldverwerking werkt zoals verwacht?{#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Wanneer uw account is geconfigureerd met smart imaging, laadt u een Dynamic Media Classic- of Adobe Experience Manager - Dynamic Media-afbeeldings-URL in de browser.
1. Open het deelvenster Chrome-ontwikkelaar door in de browser op **[!UICONTROL View > Developer > Developer Tools]** te klikken. Of kies een ander browserontwikkelaarsgereedschap van uw keuze.

1. Zorg ervoor dat de cache is uitgeschakeld wanneer de ontwikkelprogramma&#39;s zijn geopend.

   * In Windows navigeert u naar de instellingen in het venster voor het gereedschap Ontwikkelaar en schakelt u **[!UICONTROL Disable cache (while devtools is open)]** in.
   * Mac: selecteer **[!UICONTROL disable cache]** onder het tabblad **[!UICONTROL Network]** in het venster Ontwikkelaar.

1. Waarnemen dat het inhoudstype wordt omgezet in de juiste indeling. In de volgende schermafbeelding ziet u een PNG-afbeelding die dynamisch wordt omgezet in WebP op Chrome.
1. Herhaal deze test voor verschillende browsers en gebruikersomstandigheden.

>[!NOTE]
Niet alle afbeeldingen worden geconverteerd. Smart Imaging bepaalt of de conversie de prestaties kan verbeteren. Soms wordt de afbeelding niet geconverteerd als er geen verwachte prestatieverbetering is of de indeling geen JPEG- of PNG-indeling is.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

## Kan Smart Imaging voor een aanvraag worden uitgeschakeld? {#turning-off-smart-imaging}

Ja. U kunt Smart Imaging uitschakelen door de optie `bfc=off` aan de URL toe te voegen.

## Wat is &quot;tuning&quot; beschikbaar? Zijn er instellingen of gedragingen die kunnen worden gedefinieerd? (#tuning-settings)

Op dit moment kunt u Smart Imaging optioneel in- of uitschakelen. Er is geen andere tuning beschikbaar.

## Als u de kwaliteitsinstellingen beheert met Smart Imaging, zijn er dan minimum- en maximumwaarden die ik kan instellen? Is het bijvoorbeeld mogelijk om &quot;niet lager dan 60&quot; en &quot;niet groter dan 80&quot; in te stellen? (#minimum-maximum)

De huidige slimme beeldverwerking biedt geen dergelijke provisioningmogelijkheden.

## Soms wordt een JPEG-afbeelding geretourneerd naar Chrome in plaats van een WebP-afbeelding. Waarom? (#jpeg-webp)

Slimme afbeeldingen bepalen of de conversie nuttig is of niet. De nieuwe afbeelding wordt alleen geretourneerd als de conversie resulteert in een kleinere bestandsgrootte met vergelijkbare kwaliteit.
