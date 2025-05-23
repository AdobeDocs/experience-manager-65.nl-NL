---
title: Aangepast watermerk in PDF-voorvertoning letter
description: Leer hoe u een aangepast watermerk kunt maken in de PDF-voorvertoning.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: 7d90fade-1ca4-41d8-bbf9-45490465784a
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Aangepast watermerk in PDF-voorvertoning letter{#custom-watermark-in-letter-pdf-preview}

## Overzicht {#overview}

In de interface Correspondentie maken geven gebruikers van agents een voorvertoning weer van de correspondentie in de uiteindelijke vorm waarin deze wordt verzonden naar de naverwerking, bijvoorbeeld voor e-mailen of afdrukken.

Om ongeoorloofd gebruik van deze gegevens te voorkomen, kunnen organisaties een watermerk aan voorproef PDF opleggen. Het standaardwatermerk is &quot;VOORVERTONING&quot;, dat wordt weergegeven over de PDF.

Om het watermerk in voorproef PDF toe te laten, selecteer **[!UICONTROL Apply Watermark]** tijdens de optie van de Voorproef in **[!UICONTROL Correspondence Management Configurations]** bij https://&#39; [ server ]:[ haven ]&#39;/system/console/configMgr.

![ gebrek-watermerk ](assets/default-watermark.png)

U kunt de volgende stappen gebruiken om de tekst en de vormgeving van het watermerk aan te passen:

## Het watermerk aanpassen in de voorvertoning PDF in de gebruikersinterface voor het maken van correspondentie {#customizewatermark-}

1. Ga naar `https://'[server]:[port]'/[ContextPath]/crx/de` en meld u aan als beheerder.
1. Maak in de map apps een map met de naam **[!UICONTROL previewwatermark]** met een pad/structuur die lijkt op de map met het voorvertoningswatermerk in de map libs:

   1. Klik met de rechtermuisknop op de **previewwatermark** omslag bij de volgende weg en selecteer **Knoop van de Bedekking**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Zorg ervoor dat het dialoogvenster Overlay-knooppunt de volgende waarden heeft:

      **Weg:** /libs/fd/cm/configFiles/previewwatermark

      **Plaats van de Bedekking:** /apps/

      **de Types van Knoop van de Gelijke:** Gecontroleerd

      >[!NOTE]
      >
      >Breng geen veranderingen in de /libs tak aan. Alle wijzigingen die u aanbrengt, kunnen verloren gaan, omdat deze vertakking mogelijk wordt gewijzigd wanneer u:
      >
      >    
      >    
      >    * Upgrade op uw exemplaar
      >    * Een hotfix toepassen
      >    * Een functiepakket installeren
      >    
      >

   1. Klik **O.K.** en klik dan **sparen allen**. De map **[!UICONTROL previewwatermark]** wordt gemaakt in het opgegeven pad.

1. Kopieer en plak het ddx-bestand vanuit de map &quot;/libs/fd/cm/configFiles/previewwatermark&quot; naar de map &quot;/apps/fd/cm/configFiles/previewwatermark&quot; en klik op **[!UICONTROL Save All]** .
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

   Voor informatie bij het aanpassen van de watermerkverschijning, de tekst, en de groepering, zie het Toevoegen van en het verwijderen van watermerken en achtergronden in de [ Dienst van de Assembler en het 1&rbrace; document van de Verwijzing DDX.](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf)

   >[!NOTE]
   >
   >In het ddx-bestand moeten de verwijzingen naar het resultaat en de bron ongewijzigd blijven ten opzichte van output.pdf en input.pdf. De naam van de bestands-ddx mag ook niet worden gewijzigd.

1. Klik **sparen allen**.
