---
title: Werken met XMP-hulpprogramma's
seo-title: Werken met XMP-hulpprogramma's
description: 'null'
seo-description: 'null'
uuid: 90ce6cef-efe1-456a-8e0c-5ba90249dda0
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 01d5677f-5c87-4a6e-987b-8eda9acc0b27
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1369'
ht-degree: 0%

---


# Werken met XMP-hulpprogramma&#39;s {#working-with-xmp-utilities}

**Informatie over de XMP Utilities Service**

PDF-documenten bevatten metagegevens. Dit zijn gegevens over het document die worden onderscheiden van de inhoud van het document, zoals tekst en afbeeldingen. Adobe XMP (Extensible Metadata Platform) is een standaard voor de verwerking van metagegevens van documenten.

Met de XMP-hulpprogramma&#39;s kunt u XMP-metagegevens uit PDF-documenten ophalen en opslaan, en XMP-metagegevens importeren in PDF-documenten.

U kunt deze taken uitvoeren met behulp van de XMP Utilities-service:

* Metagegevens importeren in PDF-documenten. (Zie Metagegevens [importeren in PDF-documenten](xmp-utilities.md#importing-metadata-into-pdf-documents).)
* Metagegevens uit PDF-documenten exporteren. (Zie Metagegevens [exporteren uit PDF-documenten](xmp-utilities.md#exporting-metadata-from-pdf-documents).)

>[!NOTE]
>
>Voor meer informatie over de dienst van Hulpmiddelen XMP, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Metagegevens importeren in PDF-documenten {#importing-metadata-into-pdf-documents}

U kunt de Java- en webservice-API&#39;s voor XMP-hulpprogramma&#39;s gebruiken om XMP-metagegevens programmatisch te importeren in een PDF-document. Metagegevens bevatten informatie over een PDF-document, zoals de auteur van het document en trefwoorden die betrekking hebben op het document. Metagegevens kunnen worden gevonden in het dialoogvenster Documenteigenschappen van het document, zoals in de volgende afbeelding wordt getoond.

![ww_ww_metadatadialog](assets/ww_ww_metadatadialog.png)

Als u metagegevens programmatisch wilt importeren in een PDF-document, kunt u een bestaand XML-document gebruiken dat de metagegevenswaarden opgeeft of een object van het type gebruiken `XMPUtilityMetadata`. (Zie [API-naslaggids](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)voor AEM Forms.)

>[!NOTE]
>
>In deze sectie wordt beschreven hoe u een XML-document kunt gebruiken om metagegevens te importeren in een PDF-document.

De volgende XML-code bevat metagegevenswaarden die overeenkomen met de vorige illustratie. Let bijvoorbeeld op de vette items die trefwoorden opgeven.

```xml
 <?xpacket begin="?" id="W5M0MpCehiHzreSzNTczkc9d"?>
 <x:xmpmeta xmlns:x="adobe:ns:meta/" x:xmptk="Adobe XMP Core 4.2-jc015 52.349034, 2008 Jun 20 00:30:39-PDT (debug)">
       <rdf:RDF xmlns:rdf="https://www.w3.org/1999/02/22-rdf-syntax-ns#">
          <rdf:Description rdf:about=""
                xmlns:xmp="https://ns.adobe.com/xap/1.0/">
             <xmp:MetadataDate>2008-10-22T10:52:21-04:00</xmp:MetadataDate>
             <xmp:CreatorTool>AEM Forms</xmp:CreatorTool>
             <xmp:ModifyDate>2008-10-22T10:52:21-04:00</xmp:ModifyDate>
             <xmp:CreateDate>2008-02-13T11:00:18-05:00</xmp:CreateDate>
          </rdf:Description>
          <rdf:Description rdf:about=""
                xmlns:pdf="https://ns.adobe.com/pdf/1.3/">
             <pdf:Producer>AEM Forms</pdf:Producer>
             <pdf:Keywords>keyword1, keyword2, keyword3,keyword4</pdf:Keywords>
          </rdf:Description>
          <rdf:Description rdf:about=""
                xmlns:xmpMM="https://ns.adobe.com/xap/1.0/mm/">
             <xmpMM:DocumentID>uuid:1cce1f84-331e-4d8d-8538-15441c271dd7</xmpMM:DocumentID>
             <xmpMM:InstanceID>uuid:cdda0ca6-7c91-4771-9dc9-796c8fe59350</xmpMM:InstanceID>
          </rdf:Description>
          <rdf:Description rdf:about=""
                >
             <dc:format>application/pdf</dc:format>
             <dc:description>
                <rdf:Alt>
                   <rdf:li xml:lang="x-default">Adobe Designer Sample</rdf:li>
                </rdf:Alt>
             </dc:description>
             <dc:title>
                <rdf:Alt>
                   <rdf:li xml:lang="x-default">Grant Application</rdf:li>
                </rdf:Alt>
             </dc:title>
             <dc:creator>
                <rdf:Seq>
                   <rdf:li>Tony Blue</rdf:li>
                </rdf:Seq>
             </dc:creator>
             <dc:subject>
                <rdf:Bag>
                   <rdf:li>keyword1</rdf:li>
                   <rdf:li>keyword2</rdf:li>
                   <rdf:li>keyword3</rdf:li>
                   <rdf:li>keyword4</rdf:li>
                </rdf:Bag>
             </dc:subject>
          </rdf:Description>
          <rdf:Description rdf:about=""
                xmlns:desc="https://ns.adobe.com/xfa/promoted-desc/">
             <desc:version rdf:parseType="Resource">
                <rdf:value>1.0</rdf:value>
                <desc:ref>/template/subform[1]</desc:ref>
             </desc:version>
             <desc:contact rdf:parseType="Resource">
                <rdf:value>Adobe Systems Incorporated</rdf:value>
                <desc:ref>/template/subform[1]</desc:ref>
             </desc:contact>
          </rdf:Description>
       </rdf:RDF>
 </x:xmpmeta>
```

>[!NOTE]
>
>Voor meer informatie over de dienst van Hulpmiddelen XMP, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om XMP-metagegevens te importeren in een PDF-document:

1. Inclusief projectbestanden.
1. Maak een XMPUtilityService-client.
1. Roep de importbewerking voor XMP-metagegevens aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een XMPUtilityService-client maken**

Voordat u een XMP-hulpprogramma-bewerking programmatisch kunt uitvoeren, moet u een XMPUtilityService-client maken. Met de Java API wordt dit bereikt door een `XMPUtilityServiceClient` object te maken. Met de webservice-API gebeurt dit met behulp van een `XMPUtilityServiceService` object.

**De importbewerking voor XMP-metagegevens aanroepen**

Nadat u de serviceclient hebt gemaakt, kunt u een van de bewerkingen voor het importeren van XMP-metagegevens uitvoeren om de XMP-metagegevens in het opgegeven PDF-document te importeren.

**Zie ook**

[XMP-metagegevens importeren met de Java API](xmp-utilities.md#import-xmp-metadata-using-the-java-api)

[XMP-metagegevens importeren met de webservice-API](xmp-utilities.md#importing-xmp-metadata-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XMP-metagegevens importeren met de Java API {#import-xmp-metadata-using-the-java-api}

XMP-metagegevens importeren met de XMP Utilities API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

   >[!NOTE]
   >
   >Het bestand adobe-pdfutility-client.jar bevat klassen waarmee u de service XMP Utilities programmatisch kunt activeren.

1. Een XMPUtilityService-client maken

   Maak een `XMPUtilityServiceClient` object met behulp van de constructor en geef een `ServiceClientFactory` object door dat verbindingseigenschappen bevat.

1. De importbewerking voor XMP-metagegevens aanroepen

   Als u de XMP-metagegevens wilt wijzigen, roept u de `XMPUtilityServiceClient` methode van het object of de `importMetadata` `importXMP` methode van het object aan.

   Geef de volgende waarden door wanneer u de `importMetadata` methode gebruikt:

   * Een `com.adobe.idp.Document` object dat het PDF-bestand vertegenwoordigt.
   * Een `XMPUtilityMetadata` object dat de te importeren metagegevens bevat.

   Geef de volgende waarden door wanneer u de `importXMP` methode gebruikt:

   * Een `com.adobe.idp.Document` object dat het PDF-bestand vertegenwoordigt.
   * Een `com.adobe.idp.Document` object dat een XML-bestand vertegenwoordigt dat de te importeren metagegevens bevat.

   In beide gevallen is de geretourneerde waarde een `com.adobe.idp.Document` object dat staat voor het PDF-bestand met de nieuw geïmporteerde metagegevens. U kunt dit object vervolgens op schijf opslaan.

**Zie ook**

[Metagegevens importeren in PDF-documenten](xmp-utilities.md#importing-metadata-into-pdf-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XMP-metagegevens importeren met de webservice-API {#importing-xmp-metadata-using-the-web-service-api}

Voer de volgende taken uit om XMP-metagegevens via programmacode te importeren met de XMP Utilities-webservice-API:

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van XMP gebruikt. (Zie AEM Forms [aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verwijs naar de cliëntassemblage van Microsoft .NET. (Zie het [Creëren van een .NET cliëntassemblage die Base64 het coderen](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding). gebruikt)

1. Een XMPUtilityService-client maken

   Maak een `XMPUtilityServiceService` object met de constructor van de proxyklasse.

1. De importbewerking voor XMP-metagegevens aanroepen

   Als u de XMP-metagegevens wilt wijzigen, roept u de `XMPUtilityServiceService` methode van het object of de `importMetadata` `importXMP` methode van het object aan.

   Geef de volgende waarden door wanneer u de `importMetadata` methode gebruikt:

   * Een `BLOB` object dat het PDF-bestand vertegenwoordigt.
   * Een `XMPUtilityMetadata` object dat de te importeren metagegevens bevat.

   Geef de volgende waarden door wanneer u de `importXMP` methode gebruikt:

   * Een `BLOB` object dat het PDF-bestand vertegenwoordigt.
   * Een `BLOB` object dat een XML-bestand vertegenwoordigt dat de te importeren metagegevens bevat.

   In beide gevallen is de geretourneerde waarde een `BLOB` object dat staat voor het PDF-bestand met de nieuw geïmporteerde metagegevens. U kunt dit object vervolgens op schijf opslaan.

**Zie ook**

[Metagegevens importeren in PDF-documenten](xmp-utilities.md#importing-metadata-into-pdf-documents)

<!--REVIEW: [Quick Start (Base64): Importing XMP metadata using the web service API](unresolvedlink-lc-qs-xmp-utilities-xu.xml#ws624e3cba99b79e12e69a9941333732bac8-7be8.2)-->

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Metagegevens exporteren uit PDF-documenten {#exporting-metadata-from-pdf-documents}

U kunt de Java- en webservice-API&#39;s voor XMP-hulpprogramma&#39;s gebruiken om XMP-metagegevens uit een PDF-document op te halen en op te slaan.

>[!NOTE]
>
>Voor meer informatie over de dienst van Hulpmiddelen XMP, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om XMP-metagegevens uit een PDF-document te exporteren:

1. Inclusief projectbestanden.
1. Maak een XMPUtilityService-client.
1. Roep de XMP-exportbewerking voor metagegevens aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een XMPUtilityService-client maken**

Voordat u een XMP-hulpprogramma-bewerking programmatisch kunt uitvoeren, moet u een XMPUtilityService-client maken. Met Java AP, wordt dit verwezenlijkt door een `XMPUtilityServiceClient` voorwerp te creëren. Met de webservice-API wordt dit gedaan met behulp van een `XMPUtilityServiceService` object.

**De exportbewerking voor XMP-metagegevens aanroepen**

Nadat u de serviceclient hebt gemaakt, kunt u een van de XMP-exportbewerkingen voor metagegevens activeren. Deze bewerkingen kunnen worden gebruikt om de XMP-metagegevens te inspecteren of op schijf op te slaan.

**Zie ook**

[XMP-metagegevens importeren met de Java API](xmp-utilities.md#import-xmp-metadata-using-the-java-api)

[XMP-metagegevens importeren met de webservice-API](xmp-utilities.md#importing-xmp-metadata-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XMP-metagegevens exporteren met de Java API {#export-xmp-metadata-using-the-java-api}

XMP-metagegevens exporteren met de XMP Utilities API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

   >[!NOTE]
   >
   >Het bestand adobe-pdfutility-client.jar bevat klassen waarmee u de service XMP-hulpprogramma programmatisch kunt activeren.

1. Een XMPUtilityService-client maken

   Maak een `XMPUtilityServiceClient` object met behulp van de constructor en geef een `ServiceClientFactory` object door dat verbindingseigenschappen bevat.

1. De importbewerking voor XMP-metagegevens aanroepen

   Als u de XMP-metagegevens wilt inspecteren, roept u de `XMPUtilityServiceClient` methode van het object aan en geeft u een `exportMetadata` `com.adobe.idp.Document` object door dat het PDF-bestand vertegenwoordigt. De methode retourneert een `XMPUtilityMetadata` object dat de opgehaalde metagegevens bevat.

   Als u de XMP-metagegevens wilt ophalen en opslaan, roept u de `XMPUtilityServiceClient` methode van het object aan en geeft u een `exportXMP` `com.adobe.idp.Document` object door dat het PDF-bestand vertegenwoordigt. De methode retourneert een `com.adobe.idp.Document` object dat de opgehaalde metagegevens bevat. U kunt deze vervolgens als XML-bestand op schijf opslaan.

**Zie ook**

[Metagegevens exporteren uit PDF-documenten](xmp-utilities.md#exporting-metadata-from-pdf-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XMP-metagegevens exporteren met de webservice-API {#export-xmp-metadata-using-the-web-service-api}

XMP-metagegevens exporteren met de XMP Utilities API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van XMP gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een XMPUtilityService-client maken

   Maak een `XMPUtilityServiceService` object met de constructor van de proxyklasse.

1. De importbewerking voor XMP-metagegevens aanroepen

   Als u de XMP-metagegevens wilt inspecteren, roept u de `XMPUtilityServiceClient` methode van het object aan en geeft u een `exportMetadata` `BLOB` object door dat het PDF-bestand vertegenwoordigt. De methode retourneert een `XMPUtilityMetadata` object dat de opgehaalde metagegevens bevat.

   Als u de XMP-metagegevens wilt ophalen en opslaan, roept u de `XMPUtilityServiceClient` methode van het object aan en geeft u een `exportXMP` `BLOB` object door dat het PDF-bestand vertegenwoordigt. De methode retourneert een `BLOB` object dat de opgehaalde metagegevens bevat. U kunt deze vervolgens als XML-bestand op schijf opslaan.

**Zie ook**

[Metagegevens exporteren uit PDF-documenten](xmp-utilities.md#exporting-metadata-from-pdf-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
