---
title: Gecodeerde PDF-documenten samenstellen
seo-title: Gecodeerde PDF-documenten samenstellen
description: 'null'
seo-description: 'null'
uuid: d0948ec9-ab67-4fe4-9062-1c4938460b43
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 6d75c7b1-9c0e-47f3-bdb1-61acf16b97f9
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---


# Gecodeerde PDF-documenten samenstellen {#assembling-encrypted-pdf-documents}

U kunt een PDF-document met een wachtwoord versleutelen met de Assembler-service. Nadat een PDF-document met een wachtwoord is versleuteld, moet de gebruiker het wachtwoord opgeven om het PDF-document in Adobe Reader of Acrobat weer te geven. Als u een PDF-document met een wachtwoord wilt versleutelen, moet het DDX-document waarden voor versleutelingselementen bevatten die vereist zijn om een PDF-document te versleutelen.

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

Binnen dit DDX-document ziet u dat aan het bronkenmerk de waarde `inDoc` is toegewezen. In situaties waarin slechts één invoer-PDF-document wordt doorgegeven aan de Assembler-service en één PDF-document wordt geretourneerd en u de `invokeOneDocument`-bewerking aanroept, wijst u de waarde `inDoc` toe aan het PDF-bronkenmerk. Wanneer de `invokeOneDocument` verrichting aanhaalt, is de `inDoc` waarde een vooraf bepaalde sleutel die in het DDX document moet worden gespecificeerd.

Wanneer u daarentegen twee of meer invoer-PDF-documenten doorgeeft aan de service Assembler, kunt u de bewerking `invokeDDX` aanroepen. In dit geval wijst u de bestandsnaam van het invoer-PDF-document toe aan het `source`-kenmerk.

De versleutelingsservice hoeft geen onderdeel uit te maken van de installatie van AEM formulieren om een PDF-document met een wachtwoord te versleutelen. Zie [PDF-documenten versleutelen en ontsleutelen](/help/forms/developing/encrypting-decrypting-pdf-documents.md).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie [de Dienst van de Assembler en DX Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van stappen {#summary-of-steps}

Voer de volgende stappen uit om een versleuteld PDF-document samen te stellen:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijzen naar een onbeveiligd PDF-document.
1. Stel runtime-opties in.
1. Codeer het document.
1. Sla het versleutelde PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Zie [Including AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files) voor informatie over de locatie van alle AEM Forms JAR-bestanden.

**Een Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Neem bijvoorbeeld het DDX-document dat in deze sectie is geïntroduceerd. Als u een PDF-document wilt versleutelen, moet het DDX-document het element `PasswordEncryptionProfile` bevatten.

**Verwijzen naar een onbeveiligd PDF-document**

Er moet naar een onbeveiligd PDF-document worden verwezen en dat document moet worden doorgegeven aan de Assembler-service om het te versleutelen. Als u verwijst naar een PDF-document dat al is versleuteld, wordt een uitzondering gegenereerd.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Zie de `AssemblerOptionSpec`-klasseverwijzing in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en) voor informatie over de runtime-opties die u kunt instellen.

**Het document versleutelen**

Nadat u de Assembler-serviceclient hebt gemaakt, verwijst u naar het DDX-document dat versleutelingsinformatie bevat, verwijst u naar een onbeveiligd PDF-document en stelt u runtime-opties in. Hiervoor kunt u de `invokeOneDocument`-bewerking activeren. Omdat slechts één invoer-PDF-document wordt doorgegeven aan de Assembler-service (en er wordt één document geretourneerd), kunt u de `invokeOneDocument`-bewerking gebruiken in plaats van de `invokeDDX`-bewerking.

**Het versleutelde PDF-document opslaan**

Als slechts één PDF-document wordt doorgegeven aan de Assembler-service, retourneert de Assembler-service één document in plaats van een verzamelingsobject. Dat wil zeggen dat bij het aanroepen van de `invokeOneDocument`-bewerking één document wordt geretourneerd. Omdat het DDX-document waarnaar in deze sectie wordt verwezen, versleutelingsgegevens bevat, retourneert de Assembler-service een PDF-document dat met een wachtwoord is versleuteld.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Een versleuteld PDF-document samenstellen met de Java API {#assemble-an-encrypted-pdf-document-using-the-java-api}

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Assembler-client.

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream`-object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Verwijzen naar een onbeveiligd PDF-document.

   * Maak een `java.io.FileInputStream`-object door de constructor ervan te gebruiken en de locatie van een onbeveiligd PDF-document door te geven.
   * Maak een `com.adobe.idp.Document`-object en geef het `java.io.FileInputStream`-object door dat het PDF-document bevat. Dit `com.adobe.idp.Document`-object wordt doorgegeven aan de methode `invokeOneDocument`.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt de `AssemblerOptionSpec` methode `setFailOnError` van objecten aan en gaat `false` over.

1. Codeer het document.

   Roep de methode `invokeOneDocument` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document`-object dat het DDX-document vertegenwoordigt. Controleer of dit DDX-document de waarde `inDoc` voor het PDF-bronelement bevat.
   * Een `com.adobe.idp.Document`-object dat het onbeveiligde PDF-document bevat.
   * Een object `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` dat de runtime-opties opgeeft, inclusief het standaardniveau voor lettertypen en taaklogbestanden.

   De methode `invokeOneDocument` retourneert een `com.adobe.idp.Document`-object dat een met wachtwoord gecodeerd PDF-document bevat.

1. Sla het versleutelde PDF-document op.

   * Maak een `java.io.File`-object en zorg dat de bestandsnaamextensie .pdf is.
   * Roep de methode `Document` van het object `copyToFile` aan om de inhoud van het object `Document` naar het bestand te kopiëren. Zorg ervoor dat u het `Document` voorwerp gebruikt dat de `invokeOneDocument` methode terugkeerde.

**Zie ook**

[Snel starten (SOAP-modus): Een versleuteld PDF-document samenstellen met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-an-encrypted-pdf-document-using-the-java-api)

## Een versleuteld PDF-document samenstellen met de webservice-API {#assemble-an-encrypted-pdf-document-using-the-web-service-api}

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Assembler-client.

   * Maak een `AssemblerServiceClient`-object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `AssemblerServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `AssemblerServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB`-object met de constructor ervan. Het object `BLOB` wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB`-object door het `MTOM`-veld toe te wijzen met de inhoud van de bytearray.

1. Verwijzen naar een onbeveiligd PDF-document.

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt het invoer-PDF-document opgeslagen. Dit `BLOB` voorwerp wordt overgegaan tot `invokeOneDocument` als argument.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het invoer-PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB`-object door het `MTOM`-veld toe te wijzen met de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs `false` aan `AssemblerOptionSpec` het gegevenslid van `failOnError` van het voorwerp toe.

1. Codeer het document.

   Roep de methode `invokeOneDocument` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat het DDX-document vertegenwoordigt
   * Een `BLOB`-object dat het onbeveiligde PDF-document vertegenwoordigt
   * Een `AssemblerOptionSpec`-object dat uitvoeringsopties opgeeft

   De methode `invokeOneDocument` retourneert een `BLOB`-object dat een versleuteld PDF-document bevat.

1. Sla het versleutelde PDF-document op.

   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB`-object dat door de methode `invokeOneDocument` is geretourneerd. Vul de bytearray met de waarde van het `BLOB`-gegevenslid van het object `MTOM`.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
