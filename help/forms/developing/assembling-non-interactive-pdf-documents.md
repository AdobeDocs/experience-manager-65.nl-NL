---
title: Niet-interactieve PDF-documenten samenstellen
seo-title: Niet-interactieve PDF-documenten samenstellen
description: 'null'
seo-description: 'null'
uuid: 0c7adeb4-9a3a-4ec5-ba33-c3642928d4ea
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 8a75c201-bd88-4809-be08-69de94656489
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1760'
ht-degree: 0%

---


# Niet-interactieve PDF-documenten samenstellen {#assembling-non-interactive-pdf-documents}

U kunt een niet-interactief PDF-document samenstellen wanneer u een interactief PDF-formulier als invoer gebruikt. Dat wil zeggen dat u een formulier hebt dat gebruikers kunnen gebruiken om gegevens in te voeren in de velden. U kunt dat formulier doorgeven aan de Assembler-service, waardoor de Assembler-service een PDF-document retourneert dat voorkomt dat gebruikers gegevens in de desbetreffende velden invoeren. Dit document is een niet-interactief PDF-formulier. In de volgende afbeelding ziet u bijvoorbeeld een hypotheektoepassing die een interactief formulier vertegenwoordigt.

Voor deze bespreking, veronderstel dat het volgende DDX- document wordt gebruikt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDF result="out.pdf">
        <PDF source="inDoc"/>
        <NoXFA/>
      </PDF>
 </DDX>
```

Binnen dit DDX-document wordt de waarde toegewezen aan het bronkenmerk `inDoc`. In situaties waarin slechts één invoer-PDF-document wordt doorgegeven aan de Assembler-service en één PDF-document wordt geretourneerd en u de `invokeOneDocument` bewerking aanroept, wijst u de waarde toe `inDoc` aan het PDF-bronkenmerk. Wanneer de `invokeOneDocument` bewerking wordt aangeroepen, is de `inDoc` waarde een vooraf gedefinieerde sleutel die in het DDX-document moet worden opgegeven.

Wanneer u daarentegen twee of meer invoer-PDF-documenten doorgeeft aan de Assembler-service, kunt u de `invokeDDX` bewerking activeren. In dit geval wijst u de bestandsnaam van het invoer-PDF-document toe aan het `source` kenmerk.

Dit DDX-document bevat het `NoXFA` element dat de Assembler-service opgeeft een niet-interactief PDF-document te retourneren.

De service Assembler kan niet-interactieve PDF-documenten samenstellen zonder dat de uitvoerservice onderdeel is van de installatie van AEM-formulieren als het invoer-PDF-document is gebaseerd op een Acrobat-formulier of een statisch XFA-formulier. Als het invoer-PDF-document echter een dynamisch XFA-formulier is, moet de uitvoerservice onderdeel zijn van de installatie van AEM-formulieren. Als de Output-service geen onderdeel is van uw AEM-formulierinstallatie wanneer een dynamisch XFA-formulier wordt geassembleerd, wordt een uitzondering gegenereerd. Zie [Documentuitvoerstromen](/help/forms/developing/creating-document-output-streams.md)maken.

>[!NOTE]
>
>Voordat u deze sectie leest, is het raadzaam om vertrouwd te zijn met het samenstellen van PDF-documenten met de Assembler-service. Deze sectie bespreekt geen concepten, zoals het creëren van een inzamelingsvoorwerp dat inputdocumenten of het leren hoe te om de resultaten uit het teruggekeerde inzamelingsvoorwerp te halen bevat. (Zie PDF-documenten [programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie de Dienst van de [Assembler en de Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63)DDX.

## Overzicht van de stappen {#summary-of-steps}

U kunt als volgt een niet-interactief PDF-document samenstellen:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijzen naar een interactief PDF-document.
1. Stel runtime-opties in.
1. Stel het PDF-document samen.
1. Sla het niet-interactieve PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

als AEM Forms worden geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd.

**Een Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Dit DDX-document moet het `NoXFA` element bevatten dat de Assembler-service opgeeft een niet-interactief PDF-document te retourneren.

**Verwijzen naar een interactief PDF-document**

Er moet naar een interactief PDF-document worden verwezen en dat document moet worden doorgegeven aan de Assembler-service om een niet-interactief PDF-document terug te krijgen.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt.

**Het PDF-document samenstellen**

Nadat u de Assembler-serviceclient hebt gemaakt, naar het DDX-document verwijst, naar een interactief PDF-document verwijst en runtime-opties hebt ingesteld, kunt u de `invokeOneDocument` bewerking activeren. Omdat slechts één invoer-PDF-document wordt doorgegeven aan de Assembler-service en er één document wordt geretourneerd, kunt u de `invokeOneDocument` bewerking gebruiken in plaats van de `invokeDDX` bewerking.

**Het niet-interactieve PDF-document opslaan**

Als slechts één PDF-document wordt doorgegeven aan de Assembler-service, retourneert de Assembler-service één document in plaats van een verzamelingsobject. Dat wil zeggen dat bij het aanroepen van de `invokeOneDocument` bewerking één document wordt geretourneerd. Omdat het DDX-document waarnaar in deze sectie wordt verwezen, instructies bevat voor het maken van een niet-interactief PDF-document, retourneert de Assembler-service een niet-interactief PDF-document dat kan worden opgeslagen als een PDF-bestand.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Een niet-interactief PDF-document samenstellen met de Java API {#assemble-a-non-interactive-pdf-document-using-the-java-api}

U kunt een niet-interactief PDF-document samenstellen met behulp van de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Assembler-client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Verwijzen naar een interactief PDF-document.

   * Maak een `java.io.FileInputStream` object door de constructor ervan te gebruiken en de locatie van een interactief PDF-document door te geven.
   * Maak een `com.adobe.idp.Document` object en geef het `java.io.FileInputStream` object met het PDF-document door. Dit `com.adobe.idp.Document` object wordt aan de `invokeOneDocument` methode doorgegeven.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` object behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt de methode van `AssemblerOptionSpec` objecten aan en gaat over `setFailOnError` `false`.

1. Stel het PDF-document samen.

   Roep de methode van het `AssemblerServiceClient` `invokeOneDocument` object aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` object dat het DDX-document vertegenwoordigt. Controleer of dit DDX-document de waarde bevat `inDoc` voor het PDF-bronelement.
   * Een `com.adobe.idp.Document` object dat het interactieve PDF-document bevat.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft, inclusief standaardniveau voor lettertypen en taaklogbestanden.

   De `invokeOneDocument` methode retourneert een `com.adobe.idp.Document` object dat een niet-interactief PDF-document bevat.

1. Sla het niet-interactieve PDF-document op.

   * Maak een `java.io.File` object en zorg dat de bestandsnaamextensie .pdf is.
   * Roep de `Document` methode van het `copyToFile` object aan om de inhoud van het `Document` object naar het bestand te kopiëren. Zorg ervoor dat u het `Document` object gebruikt dat de `invokeOneDocument` methode heeft geretourneerd.

* &quot;Snel starten (SOAP-modus): Een niet-interactief PDF-document samenstellen met de Java API&quot;

## Een niet-interactief PDF-document samenstellen met de webservice-API {#assemble-a-non-interactive-pdf-document-using-the-web-service-api}

U kunt een niet-interactief PDF-document samenstellen met behulp van de API (webservice) van de Assembler Service:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Assembler-client.

   * Maak een `AssemblerServiceClient` object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `AssemblerServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijzen naar een interactief PDF-document.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het invoer-PDF-document op te slaan. Dit `BLOB` object wordt als een argument `invokeOneDocument` aan het object doorgegeven.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het invoer-PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` object behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs `false` aan het de `AssemblerOptionSpec` gegevenslid van het `failOnError` voorwerp toe.

1. Stel het PDF-document samen.

   Roep de methode van het `AssemblerServiceClient` `invokeOneDocument` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat staat voor het DDX-document
   * Een `BLOB` object dat staat voor het interactieve PDF-document
   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeOneDocument` methode retourneert een `BLOB` object dat een niet-interactief PDF-document bevat.

1. Sla het niet-interactieve PDF-document op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het niet-interactieve PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` object dat door de `invokeOneDocument` methode wordt geretourneerd. Vul de bytearray met de waarde van het `BLOB` veld van het `MTOM` object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

* &quot;Snel starten (MTOM): Een niet-interactief PDF-document samenstellen met de webservice-API&quot;.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
