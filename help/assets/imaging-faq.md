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
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Slimme afbeeldingen {#smart-imaging}

## Wat is intelligente beeldverwerking? {#what-is-smart-imaging}

Slimme beeldverwerking maakt gebruik van de unieke weergavekenmerken van elke gebruiker, zodat deze automatisch de juiste afbeeldingen levert die zijn geoptimaliseerd voor zijn of haar ervaring, wat resulteert in betere prestaties en betrokkenheid. Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding.

De slimme beeldverwerking profiteert van de extra prestatiesverhoging van volledig geïntegreerd zijn met de best-in-klasse opslagCDN dienst. Deze dienst vindt de optimale Internet route tussen servers, netwerken, en peerpunten die de laagste latentie, en/of pakketverliestarief dan de standaardroute op Internet hebben.

## Wat zijn de belangrijkste voordelen van intelligente beeldverwerking? {#what-are-the-key-benefits-of-smart-imaging}

Slimme beeldverwerking zorgt voor betere prestaties bij het leveren van de afbeelding doordat de bestandsgrootte van de afbeelding automatisch wordt geoptimaliseerd op basis van de gebruikerskenmerken. Omdat de beelden een meerderheid van de ladingstijd van een pagina vormen, kan de prestatiesverbetering een diepgaande invloed op zaken KPIs zoals hogere omzetting, tijd die aan plaats wordt doorgebracht, lagere plaats hebben stuitend tarief, etc. Adobe heeft de prestaties van de standaardlevering van afbeeldingen vergeleken met die van slimme afbeeldingen voor verschillende bestandsindelingen, browsers en QLT-instellingen (Quality, QLT). Over het geheel genomen kunt u een prestatieverbetering van 22-47% verwachten, afhankelijk van uw bestaande voorinstellingen voor afbeeldingen en specifieke kenmerken van de eindgebruiker.

![image2017-11-14_133226](assets/image2017-11-14_133226.png)

## Zijn er licentiekosten verbonden aan intelligente beeldverwerking? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Nee. De slimme beeldvorming is inbegrepen met uw bestaande vergunning van of Dynamische Media Klassieke (Scene7) of Dynamische Media. Er zijn geen extra kosten om van deze nieuwe eigenschap te profiteren.

## Hoe werkt intelligente beeldverwerking? {#how-does-smart-imaging-work}

Wanneer een consument voor het eerst om een afbeelding vraagt, controleren we de gebruikerskenmerken en zetten we de afbeelding om in de juiste afbeeldingsindeling op basis van de browser. Bovendien creëren wij gelijktijdig alle formaatomzettingen die dan in het voorgeheugen ondergebracht bij CDN worden. Wanneer consumenten in verschillende browsers vervolgens om die afbeelding vragen, wordt de juiste afbeeldingsindeling automatisch rechtstreeks vanuit de CDN-cache geleverd. Deze omzettingen van indelingen worden zonder verlies uitgevoerd, waardoor de visuele getrouwheid niet afneemt. Met Slimme afbeeldingen worden afbeeldingen automatisch als volgt omgezet in verschillende indelingen op basis van browsermogelijkheden:

* Zet automatisch om in lossless WebP voor browsers die formaat WebP, zoals Chrome, Android, en Opera steunen.
* Automatisch converteren naar JPEGXR zonder gegevensverlies voor browsers die de JPEGXR-indeling ondersteunen, zoals Internet Explorer 9+.
* Automatisch omzetten in JPEG2000 zonder verlies voor browsers die de JPEG2000-indeling ondersteunen, zoals Safari.
* Voor browsers die deze indelingen niet ondersteunen, wordt de oorspronkelijk aangevraagde afbeeldingsindeling weergegeven.

## Welke afbeeldingsindelingen worden ondersteund? {#what-image-formats-are-supported}

De volgende afbeeldingsindelingen worden ondersteund voor slimme beeldverwerking:

* RGB JPEG
* RGB-PNG
* RGB TIFF
* CMYK JPEG
* CMYK TIFF

## Hoe werkt slimme beeldverwerking met onze bestaande voorinstellingen voor afbeeldingen die al in gebruik zijn? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

Slimme beeldbewerking werkt met uw bestaande voorinstellingen voor afbeeldingen en neemt vrijwel alle afbeeldingsinstellingen in acht, zoals grootte, kwaliteit, verscherping, enzovoort. Wat zal veranderen is het beeldformaat of, in het geval van de langzame snelheid van de netwerkverbinding, het kwaliteitsinstelling. Voor het omzetten van de bestandsindeling blijven de volledige visuele getrouwheid behouden, zoals wordt gedefinieerd door de instellingen van de voorinstelling voor de afbeelding, maar is het bestand kleiner.

Stel dat een voorinstelling voor een afbeelding is gedefinieerd met de JPEG-indeling, de grootte 500x500, de kwaliteit=85 en het onscherpe masker=0,1,1,5. Wanneer wij ontdekken dat een gebruiker browser van Chrome is, wordt het beeld omgezet in lossless formaat WebP, met grootte 500x500, kwaliteit=85, en unsharp masker=0.1,1,5.

## Moet ik URL&#39;s, voorinstellingen voor afbeeldingen wijzigen of nieuwe code op mijn site implementeren voor slimme beeldverwerking? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Nee. Slimme afbeeldingen werken naadloos met bestaande URL&#39;s voor afbeeldingen en voorinstellingen voor afbeeldingen. Bovendien hoeft u voor slimme beeldverwerking geen code aan uw website toe te voegen om verschillende gebruikerskenmerken (browser, bandbreedte, apparaat, enzovoort) te detecteren. Dit alles wordt automatisch door Adobe afgehandeld.

De enige vereiste wijziging is het bijwerken van de instelling **[!UICONTROL Tijd naar live]** (TTL). Met deze instelling wordt gedefinieerd hoe lang elementen in het cachegeheugen worden opgeslagen door de CDN. Adobe raadt u aan de TTL in te stellen op 24 uur of langer om de prestatieverbeteringen van smart imaging te maximaliseren. Deze instelling wijzigen:

* Als u Dynamic Media Classic gebruikt, tikt u op **[!UICONTROL Instellingen > Toepassingsinstellingen > Publicatie-instellingen > Afbeeldingsserver]**. Stel de **[!UICONTROL standaardtijd voor clientcache in op Live]** -waarde op 24 of hoger.

* Als u Dynamic Media gebruikt, volgt u de instructies voor het [configureren van dynamische media-afbeeldingsinstellingen](config-dynamic.md) Stel de waarde voor **[!UICONTROL Expiratie]** in op 24 uur of langer.

>[!NOTE]
>
>Als u TTL &lt;= 1 uur instelt, werkt slimme beeldvorming niet.

## Werkt slimme beeldvorming met HTTPS? Hoe zit het met HTTP/2? {#does-smart-imaging-working-with-https-how-about-http}

Slimme afbeeldingen werken met afbeeldingen die via HTTP of HTTPS worden geleverd. Bovendien werkt het ook via HTTP/2.

## Mag ik slimme beeldverwerking gebruiken? {#am-i-eligible-to-use-smart-imaging}

Als u intelligente beeldverwerking wilt gebruiken, moet de Dynamic Media Classic of Dynamic Media van uw bedrijf op een AEM-account aan de volgende vereisten voldoen:

* Gebruik de door Adobe gebundelde CDN (Content Delivery Network) als onderdeel van uw licentie.
* Gebruik een specifiek domein (dat wil zeggen, `images.company.com` of `mycompany.scene7.com`), geen algemeen domein (dat wil zeggen, `s7d1.scene7.com`, `s7d2.scene7.com`, of `s7d13.scene7.com`).

   Meld u aan bij uw bedrijfsaccount of accounts om uw domeinen te zoeken.

   Tik op **[!UICONTROL Instellingen > Toepassingsinstellingen > Algemene instellingen]**. Zoek het veld **[!UICONTROL Gepubliceerde servernaam]**. Als u momenteel een algemeen domein gebruikt, kunt u verzoeken over naar uw eigen douanedomein als deel van deze overgang te bewegen.

* CMYK JPEG-afbeeldingen niet aanvragen. Als onderdeel van de verwerking worden CMYK JPEG-afbeeldingen door slimme beeldverwerking omgezet in RGB. Als u CMYK JPEG-afbeeldingen nodig hebt, kunt u geen slimme afbeeldingen gebruiken.

## Wat is het proces voor het inschakelen van intelligente beeldverwerking voor mijn account? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

U moet het verzoek starten om intelligente beeldverwerking te gebruiken. deze wordt niet automatisch ingeschakeld.

1. Een aanvraag voor technische ondersteuning starten (e-mail: s7support@adobe.com).
1. Geef de volgende informatie op in uw supportverzoek:

   1. Primaire contactpersoon, e-mail, telefoon.
   1. Alle domeinen die voor slimme beeldverwerking (namelijk images.company.com of mycompany.scene7.com) moeten worden toegelaten.

      Meld u aan bij uw bedrijfsaccount of accounts om uw domeinen te zoeken.

      Klik op **[!UICONTROL Setup > Application Setup > General Settings]**.

      Zoek het veld **[!UICONTROL Gepubliceerde servernaam]**.
   1. Controleer of u de CDN gebruikt via Adobe en niet met een directe relatie.
   1. Verifieer u een specifiek domein zoals `images.company.com` of `mycompany.scene7.com`, en niet een generisch domein, zoals, `s7d1.scene7.com`, `s7d2.scene7.com``s7d13.scene7.com`gebruikt.

      Meld u aan bij uw bedrijfsaccount of accounts om uw domeinen te zoeken.

      Klik op **[!UICONTROL Setup > Application Setup > General Settings]**.

      Zoek het veld **[!UICONTROL Gepubliceerde servernaam]**. Als u momenteel een generisch Dynamisch Dynamisch Klassiek domein van Media gebruikt, kunt u verzoeken zich over naar uw eigen douanedomein als deel van deze overgang te bewegen.
   1. Geef aan of u dit ook nodig hebt om via HTTP/2 te werken

1. De technische Steun zal u aan de slimme beeldende klant toevoegen wacht Lijst die op de orde wordt gebaseerd waarin de verzoeken werden voorgelegd.
1. Wanneer Adobe klaar is om uw verzoek te verwerken, neemt de ondersteuning contact met u op om een doeldatum te coördineren en in te stellen.
1. Optioneel: U kunt slimme beeldverwerking in Staging testen voordat de nieuwe functie door Adobe wordt omgezet in productie.
1. U wordt op de hoogte gesteld na voltooiing door ondersteuning.
1. Adobe raadt u aan om de prestatieverbeteringen van intelligente beeldverwerking in te stellen op 24 uur of langer. De TTL bepaalt hoe lang de activa door CDN in het voorgeheugen worden opgeslagen. Deze instelling wijzigen:

   1. Als u Dynamic Media Classic gebruikt, klikt u op **[!UICONTROL Instellingen > Toepassingsinstellingen > Publicatie-instellingen > Afbeeldingsserver]**. Stel de **[!UICONTROL standaardtijd voor clientcache in op Live]** -waarde op 24 of hoger.
   1. Als u Dynamic Media gebruikt, volgt u [deze instructies](config-dynamic.md). Stel de waarde voor **[!UICONTROL Verlopen]** 24 uur of langer in.

## Wanneer kan ik verwachten dat mijn account is ingeschakeld met behulp van smart imaging? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

De verzoeken worden verwerkt in de orde waarin zij door Technische Steun, volgens de Wachtlijst worden ontvangen.

>[!NOTE]
Het kan lang duren, omdat het wissen van de cache nodig is om slimme beeldverwerking mogelijk te maken. Daarom kunnen slechts een paar klantenovergangen op elk bepaald ogenblik worden behandeld.

## Wat zijn de risico&#39;s wanneer u overschakelt naar het gebruik van intelligente beeldverwerking? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

De overgang naar slimme beeldverwerking wist uit uw geheime voorgeheugen bij CDN omdat het het bewegen aan een nieuwe configuratie van Dynamische Media Klassieke of Dynamische Media op AEM impliceert.

Tijdens de eerste overgang raken de niet-in de cache opgeslagen afbeeldingen de oorspronkelijke servers van Adobe rechtstreeks aan totdat het cachegeheugen opnieuw wordt opgebouwd. Daarom is Adobe van plan enkele klantovergangen tegelijk af te handelen, zodat acceptabele prestaties behouden blijven wanneer verzoeken van onze oorsprong worden opgehaald. Voor de meeste klanten wordt het cachegeheugen binnen ~1 tot 2 dagen volledig opgebouwd bij de CDN.

## Hoe kan ik controleren of slimme beeldverwerking werkt zoals verwacht?  {#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Wanneer uw account is geconfigureerd met slimme beeldverwerking, laadt u een URL voor de afbeelding Dynamic Media Classic(S7)/Dynamic Media in de browser.
1. Open het deelvenster Chrome-ontwikkelaar door in de browser op **[!UICONTROL Weergave > Ontwikkelaar > Gereedschappen]** voor ontwikkelaars te klikken. Of kies een ander browserontwikkelaarsgereedschap van uw keuze.

1. Zorg ervoor dat de cache is uitgeschakeld wanneer de ontwikkelprogramma&#39;s zijn geopend.

   1. In Windows navigeert u naar de instellingen in het deelvenster voor ontwikkelaars en schakelt u het selectievakje Cache **[!UICONTROL uitschakelen (terwijl de apparaten geopend zijn)]** in.
   1. Op MAC, in de ontwikkelaarsruit, onder het lusje van het **[!UICONTROL Netwerk]** , selecteert **[!UICONTROL onbruikbaar maken geheime voorgeheugen]** .

1. Op het eerste verzoek wordt de afbeelding niet geoptimaliseerd. Doorgaans duurt het ongeveer 15 minuten om de geoptimaliseerde afbeelding te retourneren als deze zich niet in de CDN-cache bevindt.
1. Waarnemen dat het inhoudstype wordt omgezet in de juiste indeling. In de volgende schermafbeelding ziet u hoe PNG-afbeelding dynamisch wordt omgezet in WebP op Chrome.
1. Herhaal deze test voor verschillende browsers en gebruikersomstandigheden.

>[!NOTE]
Niet alle afbeeldingen worden geconverteerd. Slimme beeldverwerking bepaalt of de conversie nodig is om de prestaties te verbeteren. In sommige gevallen, waar er geen verwachte prestatiesverhoging is, wordt het beeld niet omgezet.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

