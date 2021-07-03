---
title: Slimme beeldverwerking
description: Slimme beeldverwerking past de unieke weergavekenmerken van elke gebruiker toe, zodat deze automatisch de juiste afbeeldingen levert die zijn geoptimaliseerd voor zijn of haar ervaring, wat resulteert in betere prestaties en betrokkenheid.
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: bf8c6bbd-847d-43d7-9ff4-7231bfd8d107
feature: Middelenbeheer, uitvoeringen
role: User, Admin
exl-id: e427d4ee-d5c8-421b-9739-f3cf2de36e41
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '2575'
ht-degree: 1%

---


# Slimme afbeeldingen {#smart-imaging}

## Wat is &quot;Smart Imaging&quot;? {#what-is-smart-imaging}

Slimme beeldverwerking past Adobe Sensei AI-mogelijkheden toe en werkt met bestaande &quot;voorinstellingen voor afbeeldingen&quot; om de prestaties van de beeldlevering te verbeteren door de afbeeldingsindeling, -grootte en -kwaliteit automatisch te optimaliseren op basis van de mogelijkheden van de clientbrowser.

>[!NOTE]
>
>Deze functie vereist dat u de CDN (Content Delivery Network) gebruikt die buiten de box valt en die is meegeleverd bij Adobe Experience Manager Dynamic Media. Een andere aangepaste CDN wordt niet ondersteund met deze functie.

De slimme Beeldvorming profiteert ook van de extra prestatiesverhoging van volledig geïntegreerd zijn met de best-in-klasse de dienst van CDN van de Adobe. Deze dienst vindt de optimale Internet route tussen servers, netwerken, en peering punten. Het vindt een route die de laagste latentie en het laagste tarief van het pakketverlies in plaats van het gebruiken van de standaardroute op Internet heeft.

De volgende voorbeelden van afbeeldingselementen geven de toegevoegde optimalisatie van Smart Imaging aan:

| Afbeelding<br>(URL) | Miniatuur | Grootte<br> (JPEG) | Grootte (WebP)<br> (met Smart Imaging) | % reductie |
|---|---|---|---|---|
| [Afbeelding 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![beeld1](/help/assets/assets-dm/picture1.png) | 73,75 kB | 45,92 kB | 38% |
| [Afbeelding 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture2](/help/assets/assets-dm/picture2.png) | 191 kB | 70,66 kB | 63% |
| [Afbeelding 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture3](/help/assets/assets-dm/picture3.png) | 96,64 kB | 39,44 kB | 59% |
| [Afbeelding 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture4](/help/assets/assets-dm/picture4.png) | 315,80 kB | 178,19 kB | 44% |
|  |  |  |  | Gemiddelde = 51% |

Net als hierboven heeft Adobe ook een test uitgevoerd met 7009 URL&#39;s van live klantsites. Ze konden gemiddeld 38% meer optimalisatie voor de bestandsgrootte voor JPEG bereiken. Voor PNG met WebP-indeling konden deze bestanden gemiddeld nog 31% optimaliseren. Dit soort optimalisatie is mogelijk vanwege de mogelijkheid van Smart Imaging.

Op het mobiele web worden de uitdagingen nog verergerd door twee factoren:

* Grote verscheidenheid aan apparaten met verschillende vormfactoren en high-resolution vertoningen.
* Beperkte netwerkbandbreedte.

Wat afbeeldingen betreft, is het de bedoeling om afbeeldingen van de beste kwaliteit zo efficiënt mogelijk te bedienen.

### Optimalisatie van apparaatpixelverhoudingen {#dpr}

De apparaatpixelverhouding (DPR) - ook wel CSS-pixelverhouding genoemd - is de relatie tussen de fysieke pixels van een apparaat en logische pixels. Vooral met de komst van Retina-schermen groeit de pixelresolutie van moderne mobiele apparaten snel.

Als u de pixelverhouding van het apparaat inschakelt, wordt de afbeelding weergegeven met de native resolutie van het scherm, waardoor deze er scherp uitziet.

Als u de DPR-configuratie voor Smart Imaging inschakelt, wordt de gevraagde afbeelding automatisch aangepast op basis van de pixeldichtheid van de weergave waarvan de aanvraag wordt verzonden. Momenteel is de pixeldichtheid van het beeldscherm afkomstig van Akamai CDN-headerwaarden.

| Toegestane waarden in de URL van een afbeelding | Beschrijving |
|---|---|
| `dpr=off` | Schakel DPR-optimalisatie op individueel afbeeldings-URL-niveau uit. |
| `dpr=on,dprValue` | Overschrijf de DPR-waarde die door Smart Imaging wordt gedetecteerd, met een aangepaste waarde (zoals wordt gedetecteerd door elke logica aan de clientzijde of andere methode). Toegestane waarde voor `dprValue` is een getal groter dan 0. Opgegeven waarden van 1,5, 2 of 3 zijn standaard. |

>[!NOTE]
>
>* U kunt `dpr=on,dprValue` zelfs gebruiken als het bedrijfniveau DPR plaatsen als weg.
>* Als de resulterende afbeelding door DPR-optimalisatie groter is dan de Dynamic Media-instelling MaxPix, wordt de breedte van MaxPix altijd herkend door de hoogte-breedteverhouding van de afbeelding te behouden.


| Grootte aangevraagde afbeelding | DPR-waarde | Afgeleverde afbeeldingsgrootte |
|---|---|---|
| 816x500 | 1 | 816x500 |
| 816x500 | 2 | 1632x1000 |

Zie ook [Bij het werken met afbeeldingen](/help/assets/adding-dynamic-media-assets-to-pages.md#when-working-with-images) en [Bij het werken met Smart Crop](/help/assets/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

### Informatie over netwerkbandbreedteoptimalisatie {#network-bandwidth-optimization}

Als u Netwerkbandbreedte inschakelt, wordt automatisch de beeldkwaliteit aangepast die wordt aangeboden op basis van de werkelijke netwerkbandbreedte. Voor slechte netwerkbandbreedte, wordt de optimalisering DPR automatisch uitgezet, zelfs als het reeds aanstaat.

Uw bedrijf kan desgewenst de optimalisatie van de netwerkbandbreedte op het niveau van de individuele afbeelding uitschakelen door `network=off` aan de URL van de afbeelding toe te voegen.

| Toegestane waarde in de URL van een afbeelding | Beschrijving |
|---|---|
| `network=off` | Hiermee schakelt u netwerkoptimalisatie op individueel afbeeldings-URL-niveau uit. |

>[!NOTE]
>
>DPR en de waarden van de netwerkbandbreedte zijn gebaseerd op de ontdekte cliënt-zijwaarden van gebundelde CDN. Deze waarden zijn soms onjuist. iPhone5 met DPR=2 en iPhone12 met DPR=3 tonen beide DPR=2. Voor apparaten met hoge resolutie is het beter DPR=2 te verzenden dan DPR=1 te verzenden. Binnenkort beschikbaar: Adobe werkt aan code aan de clientzijde om de DPR van een eindgebruiker nauwkeurig te bepalen.

## Wat zijn de belangrijkste voordelen van de nieuwste Smart Imaging? {#what-are-the-key-benefits-of-smart-imaging}

Omdat de beelden het grootste deel van de ladingstijd van een pagina vormen, kan de prestatiesverbetering een diepgaande invloed op een Zaken zoals hogere omzetting, tijd die aan plaats wordt doorgebracht, en lagere plaats het stuiteren tarief hebben.

Verbeteringen in de nieuwste versie van Smart Imaging:

* Verbeterde Google SEO-classificatie voor webpagina&#39;s die gebruikmaken van de nieuwste Smart Imaging.
* Hiermee wordt geoptimaliseerde inhoud direct (tijdens runtime) weergegeven.
* Gebruikt Adobe Sensei-technologie voor conversie op basis van de kwaliteit (qlt) die is opgegeven in de afbeeldingsaanvraag.
* Smart Imaging kan worden uitgeschakeld met de URL-parameter &quot;bfc&quot;.
* onafhankelijk van TTL (Time to Live). Eerder was een minimale TTL van 12 uur verplicht voor Smart Imaging.
* Eerder waren zowel de oorspronkelijke als de afgeleide afbeeldingen in het cachegeheugen opgeslagen. Het was een proces van twee stappen om de cache ongeldig te maken. Bij de nieuwste Smart Imaging worden alleen de derivaten in het cachegeheugen opgeslagen, zodat een cachevalidatieproces in één stap mogelijk is.
* Klanten die aangepaste koppen in hun linialen gebruiken, profiteren van de nieuwste functie voor Smart Imaging, omdat deze koppen, in tegenstelling tot de vorige versie van Smart Imaging, niet worden geblokkeerd. Bijvoorbeeld &quot;Timing Allow Origin&quot;, &quot;X-Robot&quot; zoals voorgesteld in [Een aangepaste koptekstwaarde toevoegen aan afbeeldingsreacties|Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html).

## Zijn er licentiekosten verbonden aan intelligente beeldverwerking? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Nee. Smart Imaging is inbegrepen bij uw bestaande licentie van Dynamic Media Classic of Adobe Experience Manager - Dynamic Media (On-prem, AMS en Adobe Experience Manager als Cloud Service).

>[!NOTE]
>
>Smart Imaging is niet beschikbaar voor Dynamic Media - Hybride klanten.

## Hoe werkt intelligente beeldverwerking? {#how-does-smart-imaging-work}

Wanneer een consument om een afbeelding vraagt, controleert Smart Imaging de gebruikerskenmerken en wordt deze op basis van de gebruikte browser omgezet in de juiste afbeeldingsindeling. Deze formaatomzettingen worden gedaan op een manier die geen visuele getrouwheid degradeert. Met Slimme afbeeldingen worden afbeeldingen op de volgende manier automatisch omgezet in verschillende indelingen op basis van browsermogelijkheden.

<!--   * Safari 14.0 +
    * Safari 14 only with iOS 14.0 and above and macOS BigSur and above -->

* Automatisch converteren naar WebP voor de volgende browsers:
   * Chroom
   * Firefox
   * Microsoft® Edge
   * Safari (in iOS, macOS, iPadOS), biedt ondersteuning voor de browser en OS-versie WebP
   * Android™
   * Opera
* Ondersteuning voor oudere browsers:

   | Browser | Versie browser/besturingssysteem | Format |
   | --- | --- | --- |
   | Safari | Eerder dan iOS/iPad 14.0 of macOS BigSur | JPEG2000 |
   | Rand | Eerder dan 18 | JPEGXR |
   | Internet Explorer | 9+ | JPEGXR |
* Voor browsers die deze indelingen niet ondersteunen, wordt de oorspronkelijk aangevraagde afbeeldingsindeling weergegeven.

Als de oorspronkelijke afbeelding kleiner is dan het resultaat van Smart Imaging, wordt de oorspronkelijke afbeelding weergegeven.

## Welke afbeeldingsindelingen worden ondersteund? {#what-image-formats-are-supported}

De volgende afbeeldingsindelingen worden ondersteund voor Smart Imaging:

* JPEG
* PNG

<!-- CQDOC-15846 For any other format mentioned in a URL, you should explicity turn off Smart Imaging.  Append modifier `bfc=off` to the URL for file formats other than JPEG and PNG. You can accomplish this by using either one of the following methods:

* Use a ruleset if the `fmt` modifier is mentioned in the URL. 
* Append in URL modifiers field of the presets concerned.

Adobe is working on a permanent fix that does not require you to append `bfc=off` for `fmt !=JPEG` or `fmt !=PNG`. This topic will be updated after the fix is delivered. -->

## Hoe werkt Smart Imaging met mijn bestaande voorinstellingen voor afbeeldingen die al in gebruik zijn? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

Slimme afbeeldingen werken met uw bestaande voorinstellingen voor afbeeldingen en nemen alle afbeeldingsinstellingen in acht, behalve de kwaliteit (`qlt`) en de indeling (`fmt`) als de gewenste bestandsindeling JPEG of PNG is. Voor conversie van indelingen behoudt Smart Imaging volledige visuele getrouwheid zoals gedefinieerd door de vooraf ingestelde instellingen van de afbeelding, maar met een kleinere bestandsgrootte. Als de oorspronkelijke afbeelding kleiner is dan het resultaat van Smart Imaging, wordt de oorspronkelijke afbeelding weergegeven.

<!-- CQDOC-15846 In addition, if your image presets are used to return `fmt !=JPEG` or `fmt !=PNG`, be sure append `bfc=off` in the preset modifier field to return the requested file format. -->

## Moet ik URL&#39;s, afbeeldingsvoorinstellingen wijzigen of nieuwe code op mijn site implementeren voor Smart Imaging? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Smart Imaging werkt naadloos met uw bestaande afbeeldings-URL&#39;s en voorinstellingen voor afbeeldingen als u Smart Imaging configureert op uw bestaande aangepaste domein. Bovendien hoeft u bij Slimme afbeeldingen geen code aan uw website toe te voegen om de browser van een gebruiker te detecteren. Deze wordt allemaal automatisch afgehandeld.

Als u een nieuw aangepast domein moet configureren voor het gebruik van Smart Imaging, moeten de URL&#39;s worden bijgewerkt om dit aangepaste domein te weerspiegelen.

Zie [Ben ik geschikt voor het gebruik van Smart Imaging?](#am-i-eligible-to-use-smart-imaging) voor meer informatie over de vereisten voor Smart Imaging.

<!-- No. Smart Imaging works seamlessly with your existing image URLs and image presets. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. All of this is handled automatically. -->

<!-- As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. -->

## Werkt Smart Imaging met HTTPS? Hoe zit het met HTTP/2? {#does-smart-imaging-working-with-https-how-about-http}

Slimme afbeeldingen werken met afbeeldingen die via HTTP of HTTPS worden geleverd. Bovendien werkt het ook via HTTP/2.

## Mag ik slimme beeldverwerking gebruiken? {#am-i-eligible-to-use-smart-imaging}

Als u Smart Imaging wilt gebruiken, moet de Dynamic Media Classic of Dynamic Media van uw bedrijf voor een Experience Manager-account aan de volgende vereisten voldoen:

* Gebruik Adobe-Gebundelde CDN (het Netwerk van de Levering van de Inhoud) als deel van uw vergunning.
* Gebruik een specifiek domein (bijvoorbeeld `images.company.com` of `mycompany.scene7.com`), niet een algemeen domein (bijvoorbeeld `s7d1.scene7.com`, `s7d2.scene7.com` of `s7d13.scene7.com`).

Als u uw domeinen wilt zoeken, opent u [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) en meldt u zich aan bij uw bedrijfsaccount of -accounts.

Tik **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]** Zoek het veld met het label **[!UICONTROL Published Server Name]**. Als u momenteel een generisch domein gebruikt, kunt u verzoeken zich over naar uw eigen douanedomein als deel van deze overgang te bewegen wanneer u een technisch steunkaartje voorlegt.

Voor je eerste aangepaste domein zijn er geen extra kosten verbonden met een Dynamic Media-licentie.

## Wat is het proces voor het inschakelen van Smart Imaging voor mijn account? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

U start het verzoek om intelligente beeldverwerking te gebruiken; deze wordt niet automatisch ingeschakeld.

Smart Imaging DPR en netwerkoptimalisatie zijn standaard uitgeschakeld voor een Dynamic Media-bedrijfsaccount. Als u een of beide van deze verbeteringen wilt inschakelen (inschakelen), maakt u een ondersteuningscase zoals hieronder wordt beschreven.

Het releaseschema voor Smart Imaging DPR en netwerkoptimalisatie is als volgt:

| Regio | Doeldatum |
|---|---|
| Noord-Amerika | Live |
| Europa, Midden-Oosten, Afrika | 13 aug. 2021 |
| Azië-Stille Oceaan | 22 jul. 2021 |

1. [Gebruik de Admin Console om een steungeval](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) tot stand te brengen.
1. Geef de volgende informatie op in uw ondersteuningsgeval:

   1. Primaire contactpersoon, e-mail, telefoon.
   1. Alle domeinen die voor slimme beeldverwerking (namelijk `images.company.com` of `mycompany.scene7.com`) moeten worden toegelaten.

      Als u uw domeinen wilt zoeken, opent u [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) en meldt u zich aan bij uw bedrijfsaccount of -accounts.

      Klik op **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]**.

      Zoek het veld met het label **[!UICONTROL Published Server Name]**.
   1. Verifieer dat u CDN door Adobe gebruikt en niet met een directe verhouding wordt beheerd.
   1. Verifieer u een specifiek domein zoals `images.company.com` of `mycompany.scene7.com`, en niet een generisch domein, zoals `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com` gebruikt.

      Als u uw domeinen wilt zoeken, opent u [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) en meldt u zich aan bij uw bedrijfsaccount of -accounts.

      Klik op **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]**.

      Zoek het veld met het label **[!UICONTROL Published Server Name]**. Als u momenteel een algemeen Dynamic Media Classic domein gebruikt, kunt u vragen dat u in het kader van deze overgang naar uw eigen aangepaste domein overschakelt.
   1. Geef aan of u Smart Imaging ook nodig hebt om via HTTP/2 te werken.

1. De Zorg van de Klant van Adobe voegt u aan de Slimme Lijst van de Wacht van het Beeld toe de klant gebaseerd op de orde waarin de verzoeken werden voorgelegd.
1. Wanneer Adobe bereid is om uw verzoek te behandelen, steuncontacten u om een doeldatum te coördineren en te plaatsen.
1. **Optioneel**  - U kunt optioneel slimme beeldverwerking in Staging testen voordat Adobe de nieuwe functie naar productie verplaatst.
1. U wordt op de hoogte gesteld na voltooiing door de klantenservice.
1. Om de prestatieverbeteringen van Smart Imaging te maximaliseren, raadt Adobe aan om de Time To Live (TTL) in te stellen op 24 uur of langer. De TTL bepaalt hoe lang de activa door CDN in het voorgeheugen worden opgeslagen. Deze instelling wijzigen:

   1. Als u Dynamic Media Classic gebruikt, klikt u op **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server]**. Stel de waarde **[!UICONTROL Default Client Cache Time To Live]** in op 24 of langer.
   1. Als u Dynamic Media gebruikt, volgt u [deze instructies](config-dynamic.md). Stel de waarde **[!UICONTROL Expiration]** 24 uur of langer in.

## Wanneer kan ik verwachten dat mijn account is ingeschakeld met Smart Imaging? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

De verzoeken worden verwerkt in de orde waarin zij door de Zorg van de Klant, volgens de Wachtlijst worden ontvangen.

>[!NOTE]
>
>Er kan een lange aanlooptijd zijn, omdat het inschakelen van Smart Imaging Adobe het wissen van de cache met zich meebrengt. Daarom kunnen slechts een paar klantenovergangen op elk bepaald ogenblik worden behandeld.

## Wat zijn de risico&#39;s wanneer u overschakelt op het gebruik van Smart Imaging? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

Er is geen risico voor een klantenwebpagina. Bij de overgang naar Smart Imaging wordt de cache bij de CDN echter gewist, omdat er bij de Experience Manager naar een nieuwe configuratie van Dynamic Media Classic of Dynamic Media moet worden overgeschakeld.

Tijdens de eerste overgang raakten de afbeeldingen in de cache rechtstreeks op servers die niet in de Adobe zijn opgeslagen, totdat het cachegeheugen opnieuw wordt opgebouwd. Dientengevolge, is Adobe van plan om een paar klantenovergangen in een tijd te behandelen zodat de aanvaardbare prestaties worden gehandhaafd wanneer het trekken van verzoeken van de oorsprong. Voor de meeste klanten wordt de cache binnen ~1 - 2 dagen volledig opnieuw opgebouwd bij de CDN.

## Hoe kan ik controleren of slimme beeldverwerking werkt zoals verwacht?{#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Wanneer uw account is geconfigureerd met smart imaging, laadt u een Dynamic Media Classic- of Adobe Experience Manager - Dynamic Media-afbeeldings-URL in de browser.
1. Open het deelvenster Chrome-ontwikkelaar door in de browser op **[!UICONTROL View]** > **[!UICONTROL Developer]** > **[!UICONTROL Developer Tools]** te klikken. Of kies een ander browserontwikkelaarsgereedschap van uw keuze.

1. Zorg ervoor dat de cache is uitgeschakeld wanneer de ontwikkelprogramma&#39;s zijn geopend.

   * In Windows® navigeert u naar de instellingen in het venster voor het gereedschap Ontwikkelaar en schakelt u het selectievakje **[!UICONTROL Disable cache (while devtools is open)]** in.
   * Selecteer **[!UICONTROL disable cache]** onder het tabblad **[!UICONTROL Network]** in MacOS.

1. Waarnemen dat het inhoudstype wordt omgezet in de juiste indeling. In de volgende schermafbeelding ziet u een PNG-afbeelding die dynamisch wordt omgezet in WebP op Chrome.
1. Herhaal deze test voor verschillende browsers en gebruikersomstandigheden.

>[!NOTE]
>
>Niet alle afbeeldingen worden geconverteerd. Smart Imaging bepaalt of de conversie de prestaties kan verbeteren. Soms wordt de afbeelding niet geconverteerd als er geen verwachte prestatieverbetering is of de indeling geen JPEG- of PNG-indeling is.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

## Kan Smart Imaging voor een aanvraag worden uitgeschakeld? {#turning-off-smart-imaging}

Ja. U kunt Smart Imaging uitschakelen door de optie `bfc=off` aan de URL toe te voegen.

## Kan ik vragen dat DPR en netwerkoptimalisatie op bedrijfsniveau worden uitgeschakeld? {#dpr-companylevel-turnoff}

Ja. Om DPR en netwerkoptimalisering bij uw bedrijf onbruikbaar te maken, creeer een steungeval zoals vroeger in dit onderwerp wordt beschreven.

## Wat is &quot;tuning&quot; beschikbaar? Zijn er instellingen of gedragingen die kunnen worden gedefinieerd? (#tuning-settings)

Op dit moment kunt u Smart Imaging optioneel in- of uitschakelen. Er is geen andere tuning beschikbaar.

## Als u de kwaliteitsinstellingen beheert met Smart Imaging, moet u minimum- en maximumwaarden instellen? Is het bijvoorbeeld mogelijk om &quot;niet lager dan 60&quot; en &quot;niet groter dan 80&quot; in te stellen? (#minimum-maximum)

De huidige slimme beeldverwerking biedt geen dergelijke provisioningmogelijkheden.

## Soms wordt een JPEG-afbeelding geretourneerd naar Chrome in plaats van een WebP-afbeelding. Waarom gebeurt die verandering? (#jpeg-webp)

Slimme afbeeldingen bepalen of de conversie nuttig is of niet. De nieuwe afbeelding wordt alleen geretourneerd als de conversie resulteert in een kleinere bestandsgrootte met vergelijkbare kwaliteit.

## Hoe werkt Smart Imaging DPR-optimalisatie met Adobe Experience Manager Sites-componenten en Dynamic Media-viewers?

* De Componenten van de Kern van de Plaatsen van de Experience Manager worden gevormd door gebrek voor optimalisering DPR. `dpr=off` wordt altijd toegevoegd aan Dynamic Media-afbeeldingen van Experience Manager Sites Core Components om te voorkomen dat afbeeldingen te groot worden als gevolg van DPR-optimalisatie voor Smart Imaging op de server.
* Als Dynamic Media Foundation Component standaard is geconfigureerd voor DPR-optimalisatie, wordt `dpr=off` altijd toegevoegd aan Dynamic Media Foundation Component-afbeeldingen om te grote afbeeldingen te voorkomen door DPR-optimalisatie voor Smart Imaging op de server. Zelfs als de klant DPR-optimalisatie in de DM Foundation Component uitschakelt, wordt de functie Smart Imaging DPR aan de serverzijde niet ingeschakeld. Samengevat, in de Component van de Stichting DM, komt de optimalisering DPR van kracht die op het niveau van de Component van de Stichting wordt gebaseerd DM slechts het plaatsen.
* Elke DPR-optimalisatie aan de viewerzijde werkt in combinatie met DPR-optimalisatie voor Smart Imaging op de server en resulteert niet in te grote afbeeldingen. Met andere woorden, wanneer DPR door de viewer wordt afgehandeld, zoals de hoofdweergave alleen in een viewer met zoomfunctie, worden de DPR-waarden voor Smart Imaging op de server niet geactiveerd. Op dezelfde manier wordt de DPR-waarde voor Smart Imaging op de server geactiveerd wanneer viewerelementen, zoals stalen en miniaturen, geen DPR-verwerking hebben.

Zie ook [Bij het werken met afbeeldingen](/help/assets/adding-dynamic-media-assets-to-pages.md#when-working-with-images) en [Bij het werken met Smart Crop](/help/assets/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).
