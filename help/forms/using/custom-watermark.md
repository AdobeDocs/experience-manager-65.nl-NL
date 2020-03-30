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
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Aangepast watermerk in PDF-voorbeeld met letter{#custom-watermark-in-letter-pdf-preview}

## Overzicht {#overview}

In de interface Correspondentie maken geven gebruikers van agents een voorvertoning weer van de correspondentie in de uiteindelijke vorm waarin deze wordt verzonden naar de naverwerking, bijvoorbeeld voor e-mailen of afdrukken.

Om ongeoorloofd gebruik van deze gegevens te voorkomen, kunnen organisaties een watermerk op de voorvertoning-PDF plaatsen. Het standaardwatermerk is &quot;VOORVERTONING&quot;, dat in de PDF wordt weergegeven.

Als u het watermerk wilt inschakelen in de voorbeeld-PDF, selecteert u de optie Watermerk **[!UICONTROL toepassen tijdens voorvertoning in]** Correspondence Management Configurations **[!UICONTROL op https://&#39;]** server[:]port[]&#39;/system/console/configMgr.

![default-watermark](assets/default-watermark.png)

U kunt de volgende stappen gebruiken om de tekst en de vormgeving van het watermerk aan te passen:

## Het watermerk aanpassen in de PDF-voorvertoning in de gebruikersinterface Correspondentie maken {#customizewatermark-}

1. Ga naar Beheerder `https://'[server]:[port]'/[ContextPath]/crx/de` en meld u aan.
1. Maak in de map apps een map met de naam **[!UICONTROL previewwatermark]** met een pad/structuur die lijkt op de map met het voorvertoningswatermerk in de map libs:

   1. Klik met de rechtermuisknop op het **voorvertoningswatermerk** in het volgende pad en selecteer **Overlayknooppunt**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Zorg ervoor dat het dialoogvenster Overlay-knooppunt de volgende waarden heeft:

      **Pad:** /libs/fd/cm/configFiles/previewwatermark

      **Locatie bedekking:** /apps/

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


   1. Klik op **OK** en vervolgens op Alles **** opslaan. De **[!UICONTROL map met het voorvertoningswatermerk]** wordt gemaakt in het opgegeven pad.



1. Kopieer en plak het ddx-bestand vanuit de map &quot;/libs/fd/cm/configFiles/previewwatermark&quot; naar de map &quot;/apps/fd/cm/configFiles/previewwatermark&quot; en klik op Alles **** opslaan.
1. Breng de gewenste wijzigingen aan in het ddx-bestand onder /apps/fd/cm/configFiles/previewwatermark/.

   ```
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

   Voor informatie over het aanpassen van de verschijning van het watermerk, de tekst, en de groepering, zie het Toevoegen van en het verwijderen van watermerken en achtergronden in de Dienst van de [Assembler en het document van de Verwijzing](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf) DDX.

   >[!NOTE]
   >
   >In het ddx-bestand moeten de verwijzingen naar het resultaat en de bron ongewijzigd blijven ten opzichte van output.pdf en input.pdf. De naam van de bestands-ddx mag ook niet worden gewijzigd.

1. Klik op Alles **opslaan**.

