---
title: Werken met XMP hulpprogramma's
description: Gebruik de XMP Utilities Java en de Dienst APIs van het Web om XMP meta-gegevens in een document van PDF programmatically in te voeren en XMP meta-gegevens van een document van PDF terug te winnen en op te slaan.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: cff65f74-ba95-438e-88a4-5ec7d22aafba
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1380'
ht-degree: 0%

---

# Werken met XMP hulpprogramma&#39;s {#working-with-xmp-utilities}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

**Informatie over de service XMP**

PDF-documenten bevatten metagegevens. Dit zijn gegevens over het document die worden onderscheiden van de inhoud van het document, zoals tekst en afbeeldingen. Adobe Extensible Metadata Platform (XMP) is een standaard voor de verwerking van metagegevens van documenten.

Met de XMP Utilities kunt u XMP metagegevens uit PDF-documenten ophalen en opslaan, en XMP metagegevens importeren in PDF-documenten.

U kunt deze taken uitvoeren met behulp van de service XMP Hulpprogramma&#39;s:

* Metagegevens importeren in PDF-documenten. (Zie [Metagegevens importeren in PDF-documenten](xmp-utilities.md#importing-metadata-into-pdf-documents).)
* Metagegevens exporteren uit PDF-documenten. (Zie [Metagegevens exporteren uit PDF-documenten](xmp-utilities.md#exporting-metadata-from-pdf-documents).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Hulpmiddelen van de XMP, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Metagegevens importeren in PDF-documenten {#importing-metadata-into-pdf-documents}

Met de XMP Utilities Java en de webservice-API&#39;s kunt u XMP metagegevens programmatisch importeren in een PDF-document. Metagegevens bevatten informatie over een PDF-document, zoals de auteur van het document en trefwoorden die betrekking hebben op het document. Metagegevens kunnen worden weergegeven in het dialoogvenster Documenteigenschappen van het document, zoals in de volgende afbeelding wordt getoond.

![ww_ww_metadatadialog](assets/ww_ww_metadatadialog.png)

Als u metagegevens programmatisch wilt importeren in een PDF-document, kunt u een bestaand XML-document gebruiken dat de metagegevenswaarden opgeeft of een object van het type gebruiken `XMPUtilityMetadata`. (Zie [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

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
>Voor meer informatie over de dienst van de Hulpmiddelen van de XMP, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om XMP metagegevens te importeren in een PDF-document:

1. Inclusief projectbestanden.
1. Maak een XMPUtilityService-client.
1. Roep de importbewerking voor XMP metagegevens aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een XMPUtilityService-client maken**

Voordat u een XMP Utilities-bewerking programmatisch kunt uitvoeren, moet u een XMPUtilityService-client maken. Met de Java API wordt dit bereikt door een `XMPUtilityServiceClient` object. Met de webservice-API kunt u dit bereiken door een `XMPUtilityServiceService` object.

**De importbewerking voor XMP metagegevens aanroepen**

Nadat u de de dienstcliënt creeert, kunt u één van de XMP meta-gegevens aanhalen invoerverrichtingen om de XMP meta-gegevens in het gespecificeerde document van PDF in te voeren.

**Zie ook**

[Metagegevens XMP importeren met de Java API](xmp-utilities.md#import-xmp-metadata-using-the-java-api)

[XMP metagegevens importeren met de webservice-API](xmp-utilities.md#importing-xmp-metadata-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Metagegevens XMP importeren met de Java API {#import-xmp-metadata-using-the-java-api}

Importeer XMP metagegevens met de XMP Utilities-API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

   >[!NOTE]
   >
   >Het bestand adobe-pdfutility-client.jar bevat klassen waarmee u de service Hulpprogramma&#39;s voor XMP programmatisch kunt aanroepen.

1. Een XMPUtilityService-client maken

   Een `XMPUtilityServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. De importbewerking voor XMP metagegevens aanroepen

   Als u de XMP metagegevens wilt wijzigen, roept u een van de `XMPUtilityServiceClient` object `importMetadata` methode of `importXMP` methode.

   Als u het `importMetadata` , geeft u de volgende waarden door:

   * A `com.adobe.idp.Document` object dat het PDF-bestand vertegenwoordigt.
   * An `XMPUtilityMetadata` -object dat de te importeren metagegevens bevat.

   Als u het `importXMP` , geeft u de volgende waarden door:

   * A `com.adobe.idp.Document` object dat het PDF-bestand vertegenwoordigt.
   * A `com.adobe.idp.Document` object dat staat voor een XML-bestand dat de te importeren metagegevens bevat.

   In beide gevallen is de geretourneerde waarde een `com.adobe.idp.Document` object dat het PDF-bestand met de nieuw geïmporteerde metagegevens vertegenwoordigt. U kunt dit object vervolgens op schijf opslaan.

**Zie ook**

[Metagegevens importeren in PDF-documenten](xmp-utilities.md#importing-metadata-into-pdf-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XMP metagegevens importeren met de webservice-API {#importing-xmp-metadata-using-the-web-service-api}

Voer de volgende taken uit om XMP metagegevens via de API voor XMP hulpprogramma&#39;s programmatisch te importeren:

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van het XMP gebruikt. (Zie [AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verwijs naar de Microsoft .NET cliëntassemblage. (Zie [Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)

1. Een XMPUtilityService-client maken

   Een `XMPUtilityServiceService` -object door uw proxyklasseconstructor te gebruiken.

1. De importbewerking voor XMP metagegevens aanroepen

   Als u de XMP metagegevens wilt wijzigen, roept u een van de `XMPUtilityServiceService` object `importMetadata` methode of `importXMP` methode.

   Als u het `importMetadata` , geeft u de volgende waarden door:

   * A `BLOB` object dat het PDF-bestand vertegenwoordigt.
   * An `XMPUtilityMetadata` -object dat de te importeren metagegevens bevat.

   Als u het `importXMP` , geeft u de volgende waarden door:

   * A `BLOB` object dat het PDF-bestand vertegenwoordigt.
   * A `BLOB` object dat staat voor een XML-bestand dat de te importeren metagegevens bevat.

   In beide gevallen is de geretourneerde waarde een `BLOB` object dat het PDF-bestand met de nieuw geïmporteerde metagegevens vertegenwoordigt. U kunt dit object vervolgens op schijf opslaan.

**Zie ook**

[Metagegevens importeren in PDF-documenten](xmp-utilities.md#importing-metadata-into-pdf-documents)

<!--REVIEW: [Quick Start (Base64): Importing XMP metadata using the web service API](unresolvedlink-lc-qs-xmp-utilities-xu.xml#ws624e3cba99b79e12e69a9941333732bac8-7be8.2)-->

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Metagegevens exporteren uit PDF-documenten {#exporting-metadata-from-pdf-documents}

Met de XMP Utilities Java en de webservice-API&#39;s kunt u XMP metagegevens uit een PDF-document programmatisch ophalen en opslaan.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Hulpmiddelen van de XMP, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om XMP metagegevens uit een PDF-document te exporteren:

1. Inclusief projectbestanden.
1. Maak een XMPUtilityService-client.
1. Roep de exportbewerking XMP metagegevens aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een XMPUtilityService-client maken**

Voordat u een XMP Utilities-bewerking programmatisch kunt uitvoeren, moet u een XMPUtilityService-client maken. Met Java AP, wordt dit verwezenlijkt door het creëren van `XMPUtilityServiceClient` object. Met de webservice-API wordt dit bereikt met een `XMPUtilityServiceService` object.

**De exportbewerking XMP metagegevens aanroepen**

Nadat u de de dienstcliënt creeert, kunt u één van de XMP meta-gegevens uitvoerverrichtingen aanhalen, die kunnen worden gebruikt om de XMP meta-gegevens te inspecteren of het op schijf te bewaren.

**Zie ook**

[Metagegevens XMP importeren met de Java API](xmp-utilities.md#import-xmp-metadata-using-the-java-api)

[XMP metagegevens importeren met de webservice-API](xmp-utilities.md#importing-xmp-metadata-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Metagegevens XMP exporteren met de Java API {#export-xmp-metadata-using-the-java-api}

Exporteer XMP metagegevens met behulp van de XMP Utilities-API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

   >[!NOTE]
   >
   >Het bestand adobe-pdfutility-client.jar bevat klassen waarmee u de service XMP Utility programmatisch kunt aanroepen.

1. Een XMPUtilityService-client maken

   Een `XMPUtilityServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. De importbewerking voor XMP metagegevens aanroepen

   Als u de XMP-metagegevens wilt inspecteren, roept u de `XMPUtilityServiceClient` object `exportMetadata` methode en geeft een `com.adobe.idp.Document` object dat het PDF-bestand vertegenwoordigt. De methode retourneert een `XMPUtilityMetadata` object dat de opgehaalde metagegevens bevat.

   Als u de XMP metagegevens wilt ophalen en opslaan, roept u de `XMPUtilityServiceClient` object `exportXMP` methode en geeft een `com.adobe.idp.Document` object dat het PDF-bestand vertegenwoordigt. De methode retourneert een `com.adobe.idp.Document` -object dat de opgehaalde metagegevens bevat. U kunt dit vervolgens als XML-bestand op schijf opslaan.

**Zie ook**

[Metagegevens exporteren uit PDF-documenten](xmp-utilities.md#exporting-metadata-from-pdf-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Metagegevens XMP exporteren met de webservice-API {#export-xmp-metadata-using-the-web-service-api}

Exporteer XMP metagegevens met behulp van de XMP Utilities API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van het XMP gebruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. Een XMPUtilityService-client maken

   Een `XMPUtilityServiceService` -object door uw proxyklasseconstructor te gebruiken.

1. De importbewerking voor XMP metagegevens aanroepen

   Als u de XMP-metagegevens wilt inspecteren, roept u de `XMPUtilityServiceClient` object `exportMetadata` methode en geeft een `BLOB` object dat het PDF-bestand vertegenwoordigt. De methode retourneert een `XMPUtilityMetadata` object dat de opgehaalde metagegevens bevat.

   Als u de XMP metagegevens wilt ophalen en opslaan, roept u de `XMPUtilityServiceClient` object `exportXMP` methode en geeft een `BLOB` object dat het PDF-bestand vertegenwoordigt. De methode retourneert een `BLOB` -object dat de opgehaalde metagegevens bevat. U kunt dit vervolgens als XML-bestand op schijf opslaan.

**Zie ook**

[Metagegevens exporteren uit PDF-documenten](xmp-utilities.md#exporting-metadata-from-pdf-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
