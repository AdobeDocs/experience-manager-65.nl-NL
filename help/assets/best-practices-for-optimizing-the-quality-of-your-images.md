---
title: Aanbevolen procedures voor een optimale kwaliteit van uw afbeeldingen
description: Leer beste praktijken voor het optimaliseren van beeldkwaliteit in Dynamische Media
uuid: b73f0918-c723-4a0d-a63f-4242223c2d47
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 12baf001-dfc9-410a-9821-a3bae1324392
translation-type: tm+mt
source-git-commit: 76f2df9b1d3e6c2ca7a12cc998d64423d49ebc5b
workflow-type: tm+mt
source-wordcount: '1460'
ht-degree: 5%

---


# Aanbevolen procedures voor een optimale kwaliteit van uw afbeeldingen {#best-practices-for-optimizing-the-quality-of-your-images}

Het optimaliseren van de beeldkwaliteit kan een tijdrovend proces zijn omdat veel factoren bijdragen tot het renderen van acceptabele resultaten. Het resultaat is deels subjectief omdat individuen de beeldkwaliteit anders waarnemen. Gestructureerde experimenten zijn essentieel.

AEM bevat meer dan 100 opdrachten voor het leveren van dynamische media-afbeeldingen voor het instellen en optimaliseren van afbeeldingen en het renderen van resultaten. De volgende richtlijnen kunnen u helpen het proces stroomlijnen en goede resultaten snel bereiken gebruikend sommige essentiële bevelen en beste praktijken.

## Aanbevolen werkwijzen voor afbeeldingsindeling (`&fmt=`) {#best-practices-for-image-format-fmt}

* JPG of PNG zijn de beste keuze om afbeeldingen van goede kwaliteit en met beheerbare grootte en gewicht te leveren.
* Als er geen indelingsopdracht in de URL is opgegeven, wordt bij Dynamische aflevering van mediaafbeelding standaard JPG gebruikt voor levering.
* JPG wordt met een verhouding van 10:1 gecomprimeerd en levert doorgaans kleinere afbeeldingsbestanden op. PNG wordt gecomprimeerd met een verhouding van ongeveer 2:1, behalve in sommige gevallen, bijvoorbeeld wanneer afbeeldingen een witte achtergrond bevatten. PNG-bestanden zijn doorgaans echter groter dan JPG-bestanden.
* JPG maakt gebruik van compressie met verlies. Dit betekent dat afbeeldingselementen (pixels) tijdens compressie verloren gaan. PNG gebruikt daarentegen compressie zonder verlies.
* In JPG worden foto&#39;s vaak gecomprimeerd met een hogere kwaliteit dan in synthetische afbeeldingen met scherpe randen en contrast.
* Als uw afbeeldingen transparantie bevatten, gebruikt u PNG omdat JPG geen transparantie ondersteunt.

Als beste praktijken voor beeldformaat, begin met het gemeenschappelijkste plaatsen `&fmt=JPG`.

## Aanbevolen werkwijzen voor afbeeldingsgrootte {#best-practices-for-image-size}

Het dynamisch verkleinen van de afbeeldingsgrootte is een van de meest voorkomende taken. Hierbij moet u de grootte opgeven en desgewenst ook welke downsamplingmodus wordt gebruikt om de schaal van de afbeelding te verkleinen.

* Voor het aanpassen van de afbeeldingsgrootte is de beste en meest duidelijke benadering `&wid=<value>` en `&hei=<value>,`of slechts `&hei=<value>` te gebruiken. Met deze parameters wordt de afbeeldingsbreedte automatisch ingesteld op basis van de hoogte-breedteverhouding.
* `&resMode=<value>`regelt het algoritme dat wordt gebruikt voor downsampling. Begin met `&resMode=sharp2`. Deze waarde biedt de beste afbeeldingskwaliteit. Terwijl het gebruiken van het downsampling `value =bilin` sneller is, resulteert het vaak in het aliasing van artefacten.

Gebruik `&wid=<value>&hei=<value>&resMode=sharp2` of `&hei=<value>&resMode=sharp2`

## Aanbevolen procedures voor het verscherpen van afbeeldingen {#best-practices-for-image-sharpening}

Het verscherpen van afbeeldingen is het meest complexe aspect van het beheren van afbeeldingen op uw website en er worden veel fouten gemaakt. Neem de tijd voor meer informatie over hoe verscherpen en onscherp maskeren in AEM werken door naar de volgende nuttige bronnen te verwijzen:

Whitepaper over aanbevolen procedures [Het verscherpen van afbeeldingen in Adobe Scene7 Publishing System en op Image Server](/help/assets/assets/s7_sharpening_images.pdf) is ook van toepassing op AEM.

<!-- To be reviewed and updated: Broken link.
See also [Sharpening an image with unsharp mask](https://helpx.adobe.com/photoshop/atv/cs6-tutorials/sharpening-an-image-with-unsharp-mask.html). -->

Met AEM kunt u afbeeldingen verscherpen bij inname, bij levering of beide. In de meeste gevallen moet u de afbeeldingen echter verscherpen met slechts één methode, maar niet met beide. Wanneer u afbeeldingen verscherpt bij levering, op een URL, krijgt u doorgaans de beste resultaten.

U kunt twee methoden voor het verscherpen van afbeeldingen gebruiken:

* Eenvoudig verscherpen ( `&op_sharpen`) - Vergelijkbaar met het verscherpingsfilter dat in Photoshop wordt gebruikt, wordt met eenvoudige verscherping elementaire verscherping toegepast op de uiteindelijke weergave van de afbeelding na dynamisch vergroten of verkleinen. Deze methode kan echter niet door de gebruiker worden geconfigureerd. De beste manier is om &amp;op_sharpen niet te gebruiken tenzij vereist.
* Onscherp maskeren ( `&op_USM`) - Onscherp maskeren is een industriestandaard filter voor verscherpen. U kunt afbeeldingen het beste verscherpen met onscherp maskeren volgens de onderstaande richtlijnen. Met Onscherp maskeren kunt u de volgende drie parameters instellen:

   * `&op_sharpen=`bedrag,straal,drempel

      * **[!UICONTROL amount]** (0-5, sterkte van het effect.)
      * **[!UICONTROL radius]** (0-250, breedte van de &#39;verscherpingslijnen&#39; die worden getekend rond het verscherpte object, zoals wordt gemeten in pixels.)

         Onthoud dat de parameterstraal en de hoeveelheid tegen elkaar werken. Het verminderen van straal kan door stijgende hoeveelheid worden gecompenseerd. Met Straal kunt u nauwkeuriger omgaan, aangezien een lagere waarde alleen de randpixels verscherpt, terwijl met een hogere waarde een bredere reeks pixels wordt verscherpt.

      * **[!UICONTROL threshold]** (0-255, gevoeligheid van effect.)

         Deze parameter bepaalt hoe verschillend de verscherpte pixels van het omringende gebied moeten zijn alvorens zij als randpixels worden beschouwd en het filter deze scherper maakt. Met de parameter **[!UICONTROL threshold]** voorkomt u te veel verscherpende gebieden met vergelijkbare kleuren, zoals huidskleuren. Als u bijvoorbeeld een drempelwaarde van 12 instelt, worden kleine variaties in de helderheid van de huidskleur genegeerd om &quot;ruis&quot; te voorkomen, terwijl randcontrast nog steeds wordt toegevoegd aan gebieden met hoog contrast, zoals waar de wimpers de huid raken.
      Zie de volgende bronnen voor meer informatie over de manier waarop u deze drie parameters instelt, inclusief aanbevolen procedures voor gebruik met het filter:

      AEM Help-onderwerp over het verscherpen van een afbeelding.

      Best practices white paper [Sharpening images in Adobe Scene7 Publishing System and on Image Server](/help/assets/assets/s7_sharpening_images.pdf).

   * AEM kunt u ook een vierde parameter besturen: monochroom (0,1). Deze parameter bepaalt of onscherp maskeren wordt toegepast op elke kleurcomponent afzonderlijk met de waarde 0 of op de helderheid/intensiteit van de afbeelding met de waarde 1.


Als beste praktijken, begin met de onscherpe parameter van de maskerstraal. De volgende instellingen voor Straal kunt u gebruiken:

* **[!UICONTROL Website]**: 0,2-0,3 pixels
* **[!UICONTROL Photographic printing (250-300 ppi)]**: 0,3-0,5 pixels
* **[!UICONTROL Offset printing (266-300 ppi)]**: 0,7-1,0 pixels
* **[!UICONTROL Canvas printing (150 ppi)]**: 1,5-2,0 pixels

Verhoog de waarde geleidelijk van 1,75 naar 4. Als de verscherping nog steeds niet de gewenste manier is, vergroot u de straal met een decimaalteken en voer de hoeveelheid nogmaals uit van 1,75 naar 4. Herhaal deze bewerking zo nodig.

Laat de monochrome parameter-instelling op 0 staan.

### Aanbevolen procedures voor JPEG-compressie (`&qlt=`) {#best-practices-for-jpeg-compression-qlt}

* Deze parameter bepaalt de JPG-coderingskwaliteit. Een hogere waarde betekent een afbeelding van hogere kwaliteit, maar een groot bestand. Een lagere waarde betekent ook een afbeelding van lagere kwaliteit, maar een kleiner bestand. Het bereik voor deze parameter is 0-100.
* Stel de parameterwaarde niet in op 100 om te optimaliseren voor kwaliteit. Het verschil tussen een instelling van 90 of 95 en 100 is bijna onwaarneembaar, maar met 100 wordt het afbeeldingsbestand onnodig groter. Om de kwaliteit te optimaliseren maar te voorkomen dat afbeeldingsbestanden te groot worden, stelt u `qlt= value` daarom in op 90 of 95.
* Als u wilt optimaliseren voor een kleine bestandsgrootte van de afbeelding, maar de afbeeldingskwaliteit op een acceptabel niveau wilt houden, stelt u `qlt= value` in op 80. Waarden lager dan 70 tot 75 resulteren in een aanzienlijke verslechtering van de beeldkwaliteit.
* Als beste praktijken, om in het midden te blijven, plaats `qlt= value` aan 85 om in het midden te blijven.
* De chromamarkering gebruiken in `qlt=`

   * De parameter `qlt=` heeft een tweede instelling waarmee u RGB-chromaticiteitsdownsampling kunt inschakelen met de waarde `,1` of uitschakelen met de waarde `,0`.
   * Als u het eenvoudig wilt houden, start u met het downsamplen van RGB-kleuren uitgeschakeld (`,0`). Deze instelling resulteert doorgaans in een betere beeldkwaliteit, vooral bij synthetische afbeeldingen met veel scherpe randen en contrast.

Gebruik `&qlt=85,0` als aanbevolen methode voor JPG-compressie.

## Aanbevolen procedures voor JPEG-formaat (`&jpegSize=`) {#best-practices-for-jpeg-sizing-jpegsize}

jpegSize is een nuttige parameter als u wilt waarborgen dat een beeld een bepaalde grootte voor levering aan apparaten niet overschrijdt die beperkte geheugen hebben.

* Deze parameter wordt ingesteld in kilobytes (`jpegSize=&lt;size_in_kilobytes&gt;`). Hiermee wordt de maximaal toegestane grootte voor het leveren van de afbeelding gedefinieerd.
* `&jpegSize=` communiceert met de JPG-compressieparameter  `&qlt=`. Als de JPG-reactie met de opgegeven JPG-compressieparameter (`&qlt=`) de jpegSize-waarde niet overschrijdt, wordt de afbeelding geretourneerd met `&qlt=` zoals gedefinieerd. Anders wordt `&qlt=` geleidelijk verkleind totdat de afbeelding past in de maximaal toegestane grootte, of totdat het systeem bepaalt dat de afbeelding niet past en een fout retourneert.

U kunt het beste `&jpegSize=` instellen en de parameter `&qlt=` toevoegen als u JPG-afbeeldingen levert aan apparaten met beperkt geheugen.

## Overzicht van best practices {#best-practices-summary}

U kunt het beste de volgende combinatie van parameters gebruiken om een hoge afbeeldingskwaliteit en een kleine bestandsgrootte te bereiken:

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

Deze combinatie van instellingen levert in de meeste gevallen uitstekende resultaten op.

Als de afbeelding verder moet worden geoptimaliseerd, kunt u de parameters voor verscherpen (onscherp maskeren) geleidelijk perfectioneren door te beginnen met een straal die is ingesteld op 0,2 of 0,3. Vervolgens verhoogt u geleidelijk het bedrag van 1,75 tot maximaal 4 (400% in Photoshop). Controleer of het gewenste resultaat is bereikt.

Als de verscherpingsresultaten nog steeds niet bevredigend zijn, vergroot u de straal in decimale stappen. Voor elke decimale toename start u de hoeveelheid opnieuw op bij 1,75 en verhoogt u deze geleidelijk tot 4. Herhaal dit proces totdat u het gewenste resultaat hebt bereikt. Terwijl de waarden hierboven een benadering zijn die creatieve studio&#39;s hebben bevestigd, herinner me dat u met andere waarden kunt beginnen en andere strategieën kunt volgen. Of de resultaten voor u bevredigend zijn of niet is een subjectieve kwestie, daarom is gestructureerde experimenten van essentieel belang.

Tijdens het experimenteren kunt u ook de volgende algemene suggesties gebruiken om uw workflow te optimaliseren:

* Probeer verschillende parameters in real-time uit en test ze rechtstreeks op een URL of met gebruik van de functie voor het aanpassen van afbeeldingen van het Scene7 Publishing System, die real-time voorvertoningen biedt voor aanpassingsbewerkingen.
* Houd er rekening mee dat u de opdrachten Dynamische mediabeeldverwerking in een voorinstelling kunt groeperen. Een voorinstelling voor een afbeelding bestaat in feite uit URL-opdrachtmacro&#39;s met aangepaste namen voor voorinstellingen, zoals `$thumb_low$` en `&product_high$`. De naam van de aangepaste voorinstelling in een URL-pad roept deze voorinstellingen aan. Met deze functionaliteit kunt u opdrachten en kwaliteitsinstellingen voor verschillende gebruikspatronen van afbeeldingen op uw website beheren en de totale lengte van URL&#39;s verkorten.
* AEM biedt ook geavanceerdere manieren om de afbeeldingskwaliteit af te stemmen, zoals het toepassen van verscherpende afbeeldingen bij opname. Voor geavanceerd gebruik waarbij dit een optie kan zijn om de renderingresultaten verder af te stemmen en te optimaliseren, kan [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html) u helpen met aangepaste inzichten en beste praktijken.

