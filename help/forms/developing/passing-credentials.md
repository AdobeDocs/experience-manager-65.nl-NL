---
title: Hoe te om geloofsbrieven over te gaan gebruikend WS-veiligheidskopballen?
description: Leer hoe u referenties doorgeeft met WS-beveiligingskoppen
source-git-commit: 9b118ef4f852e3df1e717bb27b9be272caeb0456
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Gegevens doorgeven met WS-beveiligingskoppen {#using-execute-script-service-aem-forms-jee-workbench}

Wanneer u een AEM Forms op JEE-service aanroept met behulp van webservices, kunt u WS-Security-headers gebruiken om verificatie-informatie voor de client door te geven die AEM Forms op JEE vereist. WS-Security definieert SOAP-extensies om clientverificatie, berichtvertrouwelijkheid en berichtintegriteit te implementeren. Dientengevolge, kunt u AEM Forms op de diensten van JEE aanhalen wanneer AEM Forms op JEE als stand-alone server of binnen een gegroepeerde milieu wordt opgesteld.

Hoe u WS-Veiligheid kopballen tot AEM Forms op JEE overgaat hangt van of u de as-geproduceerde klassen van Java of een .NET cliëntassemblage gebruikt die de inheemse stapel van de ZEEP van de dienst verbruikt.

>[!NOTE]
>
>Als voorbeeld om de dienst aan te halen gebruikend WS-Veiligheid kopballen, codeert dit onderwerp een PDF document met een wachtwoord door de dienst van de Encryptie aan te halen.

In dit document worden de volgende onderwerpen behandeld:

* Clientverificatie doorgeven met Java-klassen die door As zijn gegenereerd

* Het produceren van de bibliotheekdossiers van de As die worden vereist om de dienst van de Encryptie aan te halen

* De coderingsservice aanroepen met een WS-Security-header

* Het overgaan van cliëntauthentificatie gebruikend een .NET cliëntassemblage

* De coderingsservice aanroepen met een WS-Security-header


## Vereisten {#requirements}

Om dit document optimaal te kunnen benutten, hebt u een gedegen kennis van de AEM Forms op JEE-software nodig.

>[!MORELIKETHIS]
>
>* [Gegevens doorgeven met WS-beveiligingskoppen](assets/passing-credentials-using-ws-security-headers.pdf)

