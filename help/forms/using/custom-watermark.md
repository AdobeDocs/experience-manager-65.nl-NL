---
title: Aangepast watermerk in PDF-voorbeeld met letter
seo-title: Aangepast watermerk in PDF-voorbeeld met letter
description: Leer hoe u een aangepast watermerk kunt maken in de PDF-voorvertoning met letters.
seo-description: Leer hoe u een aangepast watermerk kunt maken in de PDF-voorvertoning met letters.
uuid: 5adfede3-9b38-4a12-bf14-6d80cfb0a05a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: adc7ec13-0675-4071-9c4c-e238202d9d85
docset: aem65
feature: Correspondence Management
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Aangepast watermerk in PDF-voorbeeld met letter{#custom-watermark-in-letter-pdf-preview}

## Overzicht {#overview}

In de interface Correspondentie maken geven gebruikers van agents een voorvertoning weer van de correspondentie in de uiteindelijke vorm waarin deze wordt verzonden naar de naverwerking, bijvoorbeeld voor e-mailen of afdrukken.

Om ongeoorloofd gebruik van deze gegevens te voorkomen, kunnen organisaties een watermerk aan de voorproefPDF opleggen. Het standaardwatermerk is &quot;VOORVERTONING&quot;, dat in de PDF wordt weergegeven.

Als u het watermerk wilt inschakelen in voorvertoning-PDF, selecteert u de optie **[!UICONTROL Apply Watermark]** Tijdens voorvertoning in **[!UICONTROL Correspondence Management Configurations]** op https://&#39;[server]:[poort]&#39;/system/console/configMgr.

![default-watermark](assets/default-watermark.png)

U kunt de volgende stappen gebruiken om de tekst en de vormgeving van het watermerk aan te passen:

## Het watermerk aanpassen in de PDF-voorvertoning in de gebruikersinterface Correspondentie maken {#customizewatermark-}

1. Ga naar `https://'[server]:[port]'/[ContextPath]/crx/de` en login als Beheerder.
1. Maak in de map apps een map met de naam **[!UICONTROL previewwatermark]** met een pad/structuur die vergelijkbaar is met de map met het voorvertoningswatermerk in de map libs:

   1. Klik met de rechtermuisknop op de map **previewwatermark** op het volgende pad en selecteer **Overlay Node**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Zorg ervoor dat het dialoogvenster Overlay-knooppunt de volgende waarden heeft:

      **Pad:** /libs/fd/cm/configFiles/previewwatermark

      **Overlay-locatie:** /apps/

      **Identieke knooppunttypen:** Ingeschakeld

      >[!NOTE]
      >
      >Breng geen veranderingen in de /libs tak aan. Alle wijzigingen die u aanbrengt, kunnen verloren gaan, omdat deze vertakking mogelijk wordt gewijzigd wanneer u:
      >
      >    
      >    
      >    * Upgrade op uw exemplaar
      >    * Een hotfix toepassen
      >    * Een functiepakket installeren


   1. Klik **OK** en klik vervolgens op **Alles opslaan**. De map **[!UICONTROL previewwatermark]** wordt gemaakt in het opgegeven pad.



1. Kopieer en plak het ddx-bestand vanuit de map &quot;/libs/fd/cm/configFiles/previewwatermark&quot; naar de map &quot;/apps/fd/cm/configFiles/previewwatermark&quot; en klik op **[!UICONTROL Save All]**.
1. Breng de gewenste wijzigingen aan in het ddx-bestand onder /apps/fd/cm/configFiles/previewwatermark/.

   ```xml
   <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
    <PDF result="output.pdf">
     <PDF source="input.pdf"/>
           <Watermark opacity="15%" rotation="45">
            <StyledText>
                     <p font-family="Georgia" font-size="70pt" color="black" font-weight="bold">
                         PREVIEW
                    </p>
            </StyledText>
           </Watermark>
    </PDF>
   </DDX>
   ```

   Zie Watermerken en achtergronden toevoegen en verwijderen in het document [Assembler Service en DDX Reference](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf) voor informatie over het aanpassen van de vormgeving, tekst en uitlijning van watermerken.

   >[!NOTE]
   >
   >In het ddx-bestand moeten de verwijzingen naar het resultaat en de bron ongewijzigd blijven ten opzichte van output.pdf en input.pdf. De naam van de bestands-ddx mag ook niet worden gewijzigd.

1. Klik **Alles opslaan**.

