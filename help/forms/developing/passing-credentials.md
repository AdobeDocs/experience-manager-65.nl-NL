---
title: Geef geloofsbrieven door gebruikend WS-veiligheidskopballen
description: Leer hoe u referenties doorgeeft met WS-beveiligingskoppen
exl-id: 519d57ad-81ab-4caf-ae25-4390ae2eee13
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Gegevens doorgeven met WS-beveiligingskoppen {#using-execute-script-service-aem-forms-jee-workbench}

Wanneer u een AEM Forms op JEE-service aanroept met behulp van webservices, kunt u WS-Security-headers gebruiken om verificatie-informatie voor de client door te geven die AEM Forms op JEE vereist. WS-Security definieert SOAP extensies voor het implementeren van clientverificatie, vertrouwelijkheid van berichten en integriteit van berichten. Dientengevolge, kunt u AEM Forms op de diensten van JEE aanhalen wanneer AEM Forms op JEE als stand-alone server of binnen een gegroepeerde milieu wordt opgesteld.

Hoe u WS-Veiligheid kopballen tot AEM Forms op JEE overgaat hangt van of u de as-geproduceerde klassen van Java of een .NET cliëntassemblage gebruikt die de inheemse SOAP van de dienst stapel verbruikt.

>[!NOTE]
>
>Als voorbeeld om de dienst aan te halen gebruikend WS-Veiligheid kopballen, codeert dit onderwerp een document van PDF met een wachtwoord door de dienst van de Encryptie aan te halen.

In dit document worden de volgende onderwerpen behandeld:

* Clientverificatie doorgeven met Java-klassen die door As zijn gegenereerd

* Het produceren van de bibliotheekdossiers van de As die worden vereist om de dienst van de Encryptie aan te halen

* De coderingsservice aanroepen met een WS-Security-header

* Het overgaan van cliëntauthentificatie gebruikend een .NET cliëntassemblage

* De coderingsservice aanroepen met een WS-Security-header


## Vereisten {#requirements}

Om dit document optimaal te benutten, hebt u een goed begrip nodig van de AEM Forms op JEE-software.

>[!MORELIKETHIS]
>
>* [&#x200B; het overgaan geloofsbrieven gebruikend WS-Veiligheid kopballen &#x200B;](assets/passing-credentials-using-ws-security-headers.pdf)
