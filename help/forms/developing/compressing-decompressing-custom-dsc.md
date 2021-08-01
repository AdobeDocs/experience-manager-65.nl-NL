---
title: Hoe te om geloofsbrieven over te gaan gebruikend WS-veiligheidskopballen?
description: Leer hoe u referenties doorgeeft met WS-beveiligingskoppen
source-git-commit: 730ae7cd6cd04eb6377b37eafe29db597e93cce3
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Bestanden comprimeren en decomprimeren met een AEM Forms op een aangepaste JEE DSC {#compressing-decompressing-files}

## Vereiste kennis {#prerequisites}

Ervaring met AEM Forms op het gebied van JEE Process Management, basisprogrammering van Java en het maken van aangepaste componenten.

**Aanvullende vereiste andere producten**

Java-editor zoals [Eclipse](https://www.eclipse.org/) of [Netbeans IDE](https://netbeans.apache.org/)

## Gebruikersniveau {#user-level}

Intermediair

Met AEM Forms on JEE kunnen ontwikkelaars aangepaste DSC (Document Service Container) maken om verrijkte functies te maken. Het maken van dergelijke componenten kan op JEE runtime-omgeving naar de AEM Forms worden geplakt en dient het beoogde doel. In dit artikel wordt uitgelegd hoe u een aangepaste ZIP-service maakt waarmee u een lijst met bestanden kunt comprimeren in een ZIP-bestand en een ZIP-bestand kunt decomprimeren naar een lijst met documenten.

## Een aangepaste DSC-component maken {#create-custom-dsc-component}

Creeer een component van douaneDSC met twee de dienstverrichtingen om lijst van documenten te comprimeren en te decomprimeren. Deze component gebruikt het pakket java.util.zip voor compressie en decompressie. Voer de volgende stappen uit om een aangepaste component te maken:

1. Voeg het bestand adobe-livecycle-client.jar toe aan de bibliotheek
1. De vereiste pictogrammen toevoegen
1. Een openbare klasse maken
1. Twee openbare methoden maken met de naam UnzipDocument &amp; ZipDocuments
1. De logica voor compressie en decompressie schrijven

De code is hier te vinden:

```java
/*
 * Custom DSC : ZIP Utility
 * Purpose: This is a LiveCycle ES2 custom component used to Compress & Decompress List of Documents
 * Author: Nithiyanandam Dharmadass
 * Organization: Ministry of Finance, Kingdom of Bahrain
 * Last modified Date: 18/Apr/2011
 */
package nith.lces2.dsc;

import java.util.zip.ZipEntry;
import java.util.zip.ZipInputStream;
import com.adobe.idp.Document;
import java.io.ByteArrayOutputStream;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.List;
import java.util.zip.ZipOutputStream;

public class ZIPService {

    static final int BUFFER = 2048; // 2MB buffer size

    public java.util.List UnzipDocument(com.adobe.idp.Document zipDocument) throws Exception {
        ZipInputStream zis = new ZipInputStream(zipDocument.getInputStream());

        ZipEntry zipFile;

        List resultList = new ArrayList();

        while ((zipFile = zis.getNextEntry()) != null) {

            ByteArrayOutputStream byteArrayOutStream = new ByteArrayOutputStream();

            int count;  // an int variable to hold the number of bytes read from input stream
            byte data[] = new byte[BUFFER];
            while ((count = zis.read(data, 0, BUFFER)) != -1) {
                byteArrayOutStream.write(data, 0, count);   // write to byte array
            }

            com.adobe.idp.Document unzippedDoc = new Document(byteArrayOutStream.toByteArray());  // create an idp document
            unzippedDoc.setAttribute("file", zipFile.getName());
            unzippedDoc.setAttribute("wsfilename", zipFile.getName());  // update the wsfilename attribute
            resultList.add(unzippedDoc);
        }
        return resultList;  // List of uncompressed documents
    }

    public com.adobe.idp.Document ZipDocuments(java.util.List listOfDocuments,java.lang.String zipFileName) throws Exception {

        if (listOfDocuments == null || listOfDocuments.size() == 0) {
            return null;
        }

        ByteArrayOutputStream byteArrayOutStream = new ByteArrayOutputStream();
        ZipOutputStream zos = new ZipOutputStream(byteArrayOutStream);  // ZIP Output Stream

        for (int i = 0; i < listOfDocuments.size(); i++) {
            Document doc = (Document) listOfDocuments.get(i);
            InputStream docInputStream = doc.getInputStream();
            ZipEntry zipEntry = new ZipEntry(doc.getAttribute("file").toString());
            zos.putNextEntry(zipEntry);
            int count;
            byte data[] = new byte[BUFFER];
            while ((count = docInputStream.read(data, 0, BUFFER)) != -1) {
                zos.write(data, 0, count);  // Read document content and add to zip entry
            }
            zos.closeEntry();
        }
        zos.flush();
        zos.close();

        Document zippedDoc = new Document(byteArrayOutStream.toByteArray());
        if(zipFileName==null || zipFileName.equals(""))
        {
            zipFileName = "CompressedList.zip";
        }
        zippedDoc.setAttribute("file", zipFileName);
        return zippedDoc;
    }
}
```

## Een bestand Component.XML maken {#create-component-xml-file}

Een component.xml- dossier moet binnen de wortelomslag van het pakket worden gecreeerd dat de de dienstverrichtingen en hun parameters bepaalde.

Het bestand component.xml wordt hier weergegeven:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<component xmlns="http://adobe.com/idp/dsc/component/document">
<!-- Unique id identifying this component -->
   <component-id>ZipService</component-id>

<!-- Version -->
   <version>1.0</version>

<!-- Start of the Service definition -->
   <services>
<!-- Unique name for service descriptor.
           The value is used as the default name for
           deployed services -->
      <service name="ZipService">
<!-- service implementation class definition -->
        <implementation-class>nith.lces2.dsc.ZIPService</implementation-class>

<!-- description -->
        <description>Compress or Decompress list of documents</description>

<!--  You can provide your own icons for a distinct look   -->
          <small-icon>icons/Zip_icon16.png</small-icon>
          <large-icon>icons/Zip_icon32.png</large-icon>


<!-- automatically deploys the service and starts it after installation -->
         <auto-deploy service-id="ZipService" />

         <operations>
<!-- method name in the interface setSmtpHost-->
            <operation name="UnzipDocument">
<!-- input parameters to the "send" method -->
              <input-parameter name="zipDocument" title="Input ZIP Document" type="com.adobe.idp.Document">
                    <hint>A ZIP File to be decompressed</hint>
                </input-parameter>
                <output-parameter name="resultList" title="Decompressed list of documents" type="java.util.List">
                    <hint>Decompressed ZIP list</hint>
                </output-parameter>
            </operation>
            <operation name="ZipDocuments">
<!-- input parameters to the "send" method -->
              <input-parameter name="listOfDocuments" title="List of Documents" type="java.util.List">
                    <hint>A list of documents to be Compressed</hint>
                </input-parameter>
                <input-parameter name="zipFileName" title="Result File Name" type="java.lang.String">
                    <hint>The name of compressed file (optional)</hint>
                </input-parameter>

                <output-parameter name="zippedDoc" title="Compressed Zip file" type="com.adobe.idp.Document">
                    <hint>Compressed ZIP File</hint>
                </output-parameter>
            </operation>
             </operations>
      </service>
   </services>
</component>
```

## Het verpakken en het opstellen van de component {#packaging-deploying-component}

1. Compileer het Java-project en maak een JAR-bestand.
1. Implementeer de component (.JAR-bestand) in JEE-runtime naar de AEM Forms via Workbench.
1. Start de service vanuit Workbench (zie onderstaande afbeelding).

![Procesontwerp](assets/process-design.jpg)

## De ZIP-service gebruiken in workflows {#using-zip-service-in-workflows}

De bewerking UnzipDocument van de aangepaste service kan nu een documentvariabele als invoer accepteren en een lijst met documentvariabelen als uitvoer retourneren.

![Document decomprimeren](assets/unzip-doc.jpg)

Op dezelfde manier kan de verrichting ZipDocuments van de douanecomponent een lijst van documenten als input goedkeuren, hen als zip dossier comprimeren en het samengeperste document terugkeren.

![Document overslaan](assets/zip-doc.jpg)

De volgende werkschemaorchestratie toont hoe te om het bepaalde dossier van het PIT te decomprimeren, hen terug naar een ander dossier van het PIT comprimeren, en output terugkeert (zie hieronder Figuur).

![ZIP-workflow ongedaan maken](assets/unzip-zip-process.jpg)

## Bepaalde zaken voor zakelijk gebruik {#business-use-cases}

U kunt deze ZIP-service voor de volgende gebruiksgevallen gebruiken:

* Alle bestanden in een bepaalde map zoeken en de bestanden terugsturen als gecomprimeerd document.

* Geef een ZIP-bestand op dat een aantal PDF-documenten bevat die door de lezer kunnen worden uitgebreid nadat deze is gedecomprimeerd. Hiervoor is AEM Forms op de JEE Reader Extensions-module vereist.

* Geef een ZIP-bestand op met een heterogeen type document dat kan worden gedecomprimeerd en geconverteerd als PDF-document met de service PDF genereren.

* Met beleid wordt een lijst met documenten beveiligd en geretourneerd als een ZIP-bestand.

* Gebruikers toestaan alle bijlagen van een procesinstantie als één ZIP-bestand te downloaden.



