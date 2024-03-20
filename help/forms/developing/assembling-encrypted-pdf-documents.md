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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 0%

---

# Gecodeerde PDF-documenten samenstellen {#assembling-encrypted-pdf-documents}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

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

Binnen dit DDX-document wordt de waarde toegewezen aan het bronkenmerk `inDoc`. In situaties waarin slechts één invoerdocument van de PDF wordt overgegaan tot de dienst van de Assembler en één document van de PDF wordt teruggekeerd, en u roept `invokeOneDocument` bewerking, wijs de waarde toe `inDoc` naar het PDF-bronkenmerk. Wanneer het aanhalen van `invokeOneDocument` de `inDoc` waarde is een vooraf gedefinieerde sleutel die in het DDX-document moet worden opgegeven.

Wanneer u daarentegen twee of meer invoerdocumenten van de PDF naar de Assembler-service doorgeeft, kunt u de `invokeDDX` -bewerking. In dit geval wijst u de bestandsnaam van het invoerdocument PDF toe aan het `source` kenmerk.

De versleutelingsservice hoeft geen onderdeel uit te maken van de installatie van uw AEM om een PDF-document met een wachtwoord te versleutelen. Zie [PDF-documenten versleutelen en ontsleutelen](/help/forms/developing/encrypting-decrypting-pdf-documents.md).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DDX-document raadpleegt u [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een versleuteld PDF-document samen te stellen:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar een onbeveiligd PDF-document.
1. Stel runtime-opties in.
1. Codeer het document.
1. Sla het gecodeerde PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Voor informatie over de locatie van alle AEM Forms JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Neem bijvoorbeeld het DDX-document dat in deze sectie is geïntroduceerd. Als u een PDF-document wilt versleutelen, moet het DDX-document de `PasswordEncryptionProfile` element.

**Verwijzen naar een onbeveiligd PDF-document**

Er moet naar een onbeveiligd PDF-document worden verwezen en dat document moet worden doorgegeven aan de Assembler-service om het te versleutelen. Als u verwijst naar een PDF-document dat al is versleuteld, wordt een uitzondering gegenereerd.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Voor informatie over de runtime opties die u kunt plaatsen, zie `AssemblerOptionSpec` klasseverwijzing in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Het document versleutelen**

Nadat u de de dienstcliënt van de Assembler creeert, verwijs het DX- document dat encryptieinformatie bevat, een onbeveiligd document van de PDF van verwijzingen voorziet, en runtime opties plaatst, kunt u aanhalen `invokeOneDocument` -bewerking. Omdat slechts één document van de inputPDF wordt overgegaan tot de dienst van de Assembler (en één document wordt teruggegeven), kunt u gebruiken `invokeOneDocument` in plaats van de `invokeDDX` -bewerking.

**Het gecodeerde PDF-document opslaan**

Als slechts één enkel document van PDF wordt overgegaan tot de dienst van de Assembler, keert de dienst van de Assembler één enkel document in plaats van een inzamelingsvoorwerp terug. Dat wil zeggen, wanneer u het `invokeOneDocument` bewerking, wordt één document geretourneerd. Omdat het DDX-document waarnaar in deze sectie wordt verwezen, versleutelingsgegevens bevat, retourneert de Assembler-service een PDF-document dat met een wachtwoord is versleuteld.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Een gecodeerd PDF-document samenstellen met de Java API {#assemble-an-encrypted-pdf-document-using-the-java-api}

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Assembler-client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `AssemblerServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijs naar een bestaand DDX-document.

   * Een `java.io.FileInputStream` een object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Verwijs naar een onbeveiligd PDF-document.

   * Een `java.io.FileInputStream` object door de constructor ervan te gebruiken en de locatie van een onbeveiligd PDF-document door te geven.
   * Een `com.adobe.idp.Document` en geeft het `java.io.FileInputStream` object dat het PDF-document bevat. Dit `com.adobe.idp.Document` object wordt doorgegeven aan de `invokeOneDocument` methode.

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt het `AssemblerOptionSpec` object `setFailOnError` methode en doorgeven `false`.

1. Codeer het document.

   De `AssemblerServiceClient` object `invokeOneDocument` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat het DDX-document vertegenwoordigt. Zorg ervoor dat dit DDX-document de waarde bevat `inDoc` voor het PDF-bronelement.
   * A `com.adobe.idp.Document` object dat het onbeveiligde PDF-document bevat.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardniveau voor fonts en taaklogbestanden.

   De `invokeOneDocument` methode retourneert een `com.adobe.idp.Document` object dat een met wachtwoord gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op.

   * Een `java.io.File` en zorg ervoor dat de bestandsnaamextensie .pdf is.
   * De `Document` object `copyToFile` methode om de inhoud van de `Document` naar het bestand. Zorg ervoor dat u de `Document` het object dat `invokeOneDocument` geretourneerde methode.

**Zie ook**

[Snel starten (SOAP-modus): een gecodeerd PDF-document samenstellen met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-an-encrypted-pdf-document-using-the-java-api)

## Een gecodeerd PDF-document samenstellen met de webservice-API {#assemble-an-encrypted-pdf-document-using-the-web-service-api}

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Assembler-client.

   * Een `AssemblerServiceClient` object met de standaardconstructor.
   * Een `AssemblerServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `AssemblerServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijs naar een bestaand DDX-document.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het DDX-document op te slaan.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Verwijs naar een onbeveiligd PDF-document.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het invoerdocument PDF op te slaan. Dit `BLOB` object wordt doorgegeven aan de `invokeOneDocument` als argument.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het invoerdocument PDF en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs toe `false` aan de `AssemblerOptionSpec` object `failOnError` lid.

1. Codeer het document.

   De `AssemblerServiceClient` object `invokeOneDocument` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor het DDX-document
   * A `BLOB` object dat staat voor het onbeveiligde PDF-document
   * An `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeOneDocument` methode retourneert een `BLOB` object dat een versleuteld PDF-document bevat.

1. Sla het gecodeerde PDF-document op.

   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` het object dat `invokeOneDocument` geretourneerde methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
