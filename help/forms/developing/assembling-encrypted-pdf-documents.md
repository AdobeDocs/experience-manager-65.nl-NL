---
title: Gecodeerde PDF-documenten samenstellen
description: Stel gecodeerde PDF-documenten samen met de Java API en Web Service API.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 2caaca74-640a-4257-a81b-3e8b295cd182
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 0%

---

# Gecodeerde PDF-documenten samenstellen {#assembling-encrypted-pdf-documents}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

U kunt een document van de PDF met een wachtwoord coderen door de dienst van de Assembler te gebruiken. Nadat een PDF-document met een wachtwoord is versleuteld, moet de gebruiker het wachtwoord opgeven om het PDF-document in Adobe Reader of Acrobat weer te geven. Als u een PDF-document met een wachtwoord wilt versleutelen, moet het DDX-document waarden voor versleuteling bevatten die vereist zijn voor het versleutelen van een PDF-document.

Voor deze bespreking, veronderstel dat het volgende DDX- document wordt gebruikt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
        <PDF result="EncryptLoan.pdf" encryption="userProtect">
         <PDF source="inDoc" />
     </PDF>
     <PasswordEncryptionProfile name="userProtect" compatibilityLevel="Acrobat7">
         <OpenPassword>AdobeOpen</OpenPassword>
        </PasswordEncryptionProfile>
 </DDX>
```

In dit DDX-document wordt de waarde `inDoc` toegewezen aan het bronkenmerk. In situaties waarin slechts één invoerdocument van de PDF wordt overgegaan tot de dienst van de Assembler en één document van de PDF wordt teruggegeven, en u `invokeOneDocument` aanhaalt verrichting, wijs de waarde `inDoc` aan het PDF bronattribuut toe. Wanneer de `invokeOneDocument` -bewerking wordt aangeroepen, is de `inDoc` -waarde een vooraf gedefinieerde sleutel die in het DDX-document moet worden opgegeven.

Wanneer u daarentegen twee of meer invoerdocumenten van de PDF naar de Assembler-service doorgeeft, kunt u de `invokeDDX` -bewerking aanroepen. In dit geval wijst u de bestandsnaam van het invoerdocument PDF toe aan het kenmerk `source` .

De versleutelingsservice hoeft geen onderdeel uit te maken van de installatie van uw AEM om een PDF-document met een wachtwoord te versleutelen. Zie [&#x200B; Coderend en Decrypterend de Documenten van PDF &#x200B;](/help/forms/developing/encrypting-decrypting-pdf-documents.md).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een document DDX, zie [&#x200B; de Dienst van de Assembler en de Verwijzing DDX &#x200B;](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een versleuteld PDF-document samen te stellen:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar een onbeveiligd PDF-document.
1. Stel runtime-opties in.
1. Codeer het document.
1. Sla het gecodeerde PDF-document op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Voor informatie over de plaats van alle dossiers van AEM Forms JAR, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt van de Assembler**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzing een bestaand document DDX**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Neem bijvoorbeeld het DDX-document dat in deze sectie is geïntroduceerd. Als u een PDF-document wilt versleutelen, moet het DDX-document het element `PasswordEncryptionProfile` bevatten.

**Verwijzing een onbeveiligd document van PDF**

Er moet naar een onbeveiligd PDF-document worden verwezen en dat document moet worden doorgegeven aan de Assembler-service om het te versleutelen. Als u verwijst naar een PDF-document dat al is versleuteld, wordt een uitzondering gegenereerd.

**vastgestelde runtime opties**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Voor informatie over de runtime opties die u kunt plaatsen, zie de `AssemblerOptionSpec` klassenverwijzing in [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**codeer het document**

Nadat u de de dienstcliënt van de Assembler creeert, van verwijzingen het DX- document dat encryptieinformatie bevat, een onbeveiligd PDF- document van verwijzingen voorziet, en runtime opties plaatst, kunt u de `invokeOneDocument` verrichting aanhalen. Omdat slechts één invoerdocument van de PDF wordt overgegaan tot de dienst van de Assembler (en één document wordt teruggegeven), kunt u de `invokeOneDocument` verrichting in plaats van de `invokeDDX` verrichting gebruiken.

**sparen het gecodeerde document van PDF**

Als slechts één enkel document van PDF wordt overgegaan tot de dienst van de Assembler, keert de dienst van de Assembler één enkel document in plaats van een inzamelingsvoorwerp terug. Dat wil zeggen dat bij het aanroepen van de `invokeOneDocument` -bewerking één document wordt geretourneerd. Omdat het DDX-document waarnaar in deze sectie wordt verwezen, versleutelingsgegevens bevat, retourneert de Assembler-service een PDF-document dat met een wachtwoord is versleuteld.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Een gecodeerd PDF-document samenstellen met de Java API {#assemble-an-encrypted-pdf-document-using-the-java-api}

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Assembler-client.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` -object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Verwijs naar een onbeveiligd PDF-document.

   * Maak een `java.io.FileInputStream` -object door de constructor ervan te gebruiken en de locatie van een onbeveiligd PDF-document door te geven.
   * Maak een `com.adobe.idp.Document` -object en geef het `java.io.FileInputStream` -object door dat het PDF-document bevat. Dit `com.adobe.idp.Document` -object wordt doorgegeven aan de methode `invokeOneDocument` .

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service de instructie wilt geven een taak te blijven verwerken wanneer een fout optreedt, roept u de methode `setFailOnError` van het object `AssemblerOptionSpec` aan en geeft u deze door `false` .

1. Codeer het document.

   Roep de methode `invokeOneDocument` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` -object dat het DDX-document vertegenwoordigt. Zorg ervoor dat dit DDX-document de waarde `inDoc` bevat voor het PDF-bronelement.
   * Een `com.adobe.idp.Document` -object dat het onbeveiligde PDF-document bevat.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardniveau voor lettertypen en taaklogbestanden.

   De methode `invokeOneDocument` retourneert een `com.adobe.idp.Document` -object dat een met een wachtwoord gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op.

   * Maak een `java.io.File` -object en controleer of de bestandsnaamextensie .pdf is.
   * Roep de methode `copyToFile` van het object `Document` aan om de inhoud van het object `Document` naar het bestand te kopiëren. Zorg ervoor dat u het object `Document` gebruikt dat de methode `invokeOneDocument` heeft geretourneerd.

**zie ook**

[Snel starten (SOAP modus): een gecodeerd PDF samenstellen met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-an-encrypted-pdf-document-using-the-java-api)

## Een gecodeerd PDF-document samenstellen met de webservice-API {#assemble-an-encrypted-pdf-document-using-the-web-service-api}

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende WSDL-definitie gebruikt wanneer u een serviceverwijzing instelt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Assembler-client.

   * Maak een `AssemblerServiceClient` -object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `AssemblerServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `AssemblerServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar een onbeveiligd PDF-document.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het invoer-PDF-document op te slaan. Dit `BLOB` -object wordt als een argument aan `invokeOneDocument` doorgegeven.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het invoerdocument en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service wilt instrueren een taak te blijven verwerken wanneer een fout optreedt, wijst u `false` toe aan het gegevenslid van het `AssemblerOptionSpec` object `failOnError` .

1. Codeer het document.

   Roep de methode `invokeOneDocument` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het DDX-document vertegenwoordigt
   * Een `BLOB` -object dat het onbeveiligde PDF-document vertegenwoordigt
   * Een `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft

   De methode `invokeOneDocument` retourneert een `BLOB` -object dat een gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op.

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het object `BLOB` dat door de methode `invokeOneDocument` wordt geretourneerd. Vul de bytearray met de waarde van het gegevenslid `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
