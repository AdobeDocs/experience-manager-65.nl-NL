---
title: Webpagina's voor documentbeveiliging gebruiken
description: Leer hoe u zich kunt aanmelden, door de webpagina's met documentbeveiliging kunt navigeren en deze kunt gebruiken.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: caa31752-a02d-4d20-b7d9-c4aad5d0fae6
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# Webpagina&#39;s voor documentbeveiliging gebruiken {#using-the-document-security-webpages}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Gebruikers en beheerders gebruiken de webpagina&#39;s voor documentbeveiliging om beleid te maken en te beheren, documenten die met een beleid zijn beveiligd te beheren en gebeurtenissen te controleren die aan met een beleid beveiligde documenten zijn gekoppeld. Beheerders gebruiken de webpagina&#39;s ook om beleidssets te maken en beleidssetcoördinatoren aan te wijzen, de standaardinstellingen voor documentbeveiliging te configureren, uitgenodigde gebruikersregistratie en accounts te beheren en server-, beleid-, gebruiker- en documentgerelateerde gebeurtenissen te controleren en te beheren.

>[!NOTE]
>
>U kunt zich ook aanmelden bij de documentbeveiliging via Acrobat en andere clienttoepassingen met uw aanmeldingsaccount voor de gebruiker. (Zie [ Toegang van de Opstelling tot documentveiligheid van cliënttoepassingen ](using-document-security-web-pages.md#setting-up-access-to-document-security-from-client-applications).)

Als u de webpagina&#39;s wilt openen, hebt u voor documentbeveiliging een browser en de URL en uw aanmeldingsgegevens nodig. De URL voor gebruikers is anders dan de URL voor beheerders.

Aangezien documentbeveiliging verwijst naar de bestaande directory&#39;s van uw organisatie voor gebruikersgegevens, kunnen uw aanmeldingsgegevens voor documentbeveiliging dezelfde gegevens zijn als die u gebruikt om u aan te melden bij uw netwerk en andere toepassingen. Raadpleeg de systeembeheerder of beheerder voor meer informatie over uw account.

Als u zich wilt aanmelden als beheerder, moet u de beheerdersrol hebben die aan u is toegewezen. U kunt de standaard superbeheerdersaccount gebruiken die tijdens het installatieproces is gemaakt.

## Aanmelden bij de webpagina&#39;s {#log-in-to-the-web-pages}

Als u zich met een browser wilt aanmelden bij de webpagina&#39;s, hebt u de URL voor documentbeveiliging en een account nodig. De URL voor gebruikers is anders dan de URL voor beheerders. Beheerders kunnen zich ook aanmelden bij de gebruikerspagina&#39;s om beleid te maken.

Als u toegang hebt tot meer dan één installatie van documentbeveiliging, hebt u de URL nodig voor de instantie van documentbeveiliging die u wilt openen. Zie de beheerder als u deze informatie niet hebt. De standaard-URL voor de gebruikerspagina&#39;s is `https://[host]:[port]/edc`. In sommige gevallen is het poortnummer niet vereist. Vraag de beheerder om meer informatie.

De standaard-URL voor beheerders is `https://[host]:[port]/adminui` .

Voor beheerders wordt tijdens de installatie een standaard superbeheerdersaccount gemaakt. U kunt dit account gebruiken om u aan te melden wanneer documentbeveiliging voor het eerst wordt geïnstalleerd.

>[!NOTE]
>
>U kunt de webpagina&#39;s ook openen vanuit Acrobat en andere clienttoepassingen. Raadpleeg de Help bij Acrobat of de betreffende Acrobat Reader DC-extensies voor meer informatie.

1. Typ de URL in uw browser:

   URL van documentbeveiliging: `https://[host]:[port]/edc`

   of beheerconsole-URL: `https://[host]:[port]/adminui`

1. Typ uw gebruikersnaam en wachtwoord in het aanmeldingsvenster en klik op OK.
1. Klik in Beheerconsole op Services > Documentbeveiliging.

>[!NOTE]
>
>Wanneer u met de webpagina&#39;s werkt, vermijd dan de browserknoppen, zoals de knop Vorige, de knop Vernieuwen en de pijlen Vorige en Volgende, omdat deze actie ongewenste gegevensvastlegging en -weergave kan veroorzaken.

## Navigeren door de webpagina&#39;s {#navigating-the-web-pages}

Wanneer u zich aanmeldt bij de webpagina&#39;s van de gebruiker, ziet u koppelingen naar de gebruikerspagina&#39;s Beleid, Documenten en Gebeurtenissen.

Wanneer u login aan beleidsconsole en aan de belangrijkste pagina van de documentveiligheid navigeert, kunt u één of twee extra verbindingen, voor de pagina van de Configuratie en voor de Uitgenodigde en Lokale pagina van Gebruikers ook zien. De pagina Uitgenodigde en Lokale gebruikers wordt alleen weergegeven als de uitgenodigde gebruikersregistratie is ingeschakeld.

Gebruik deze koppelingen om toegang te krijgen tot de verschillende pagina&#39;s, waar u beleidsdocumenten en documenten met een beleidsbescherming maakt en beheert.

**Vertoning een pagina**

1. Klik op de naam van de pagina, bijvoorbeeld op Beleid.

**ga terug naar de vorige pagina**

1. Klik op de navigatiekoppeling boven aan de pagina voor de pagina waarnaar u wilt teruggaan.

**verfrist de gegevens die op een pagina** worden vermeld

1. Klik op de hoofdpagina op de koppeling naar de pagina die u wilt vernieuwen.

>[!NOTE]
>
>Wanneer u met de webpagina&#39;s werkt, vermijd dan de browserknoppen, zoals de knop Vorige, de knop Vernieuwen en de pijltoetsen Vorige en Volgende, omdat deze actie ongewenste gegevensvastlegging en -weergave kan veroorzaken.

## Toegang tot documentbeveiliging instellen vanuit clienttoepassingen {#setting-up-access-to-document-security-from-client-applications}

Clienttoepassingen moeten zijn ingesteld om verbinding te maken met documentbeveiliging om documenten te beveiligen, documenten te openen die met een beleid zijn beveiligd en verbinding te maken met webpagina&#39;s voor documentbeveiliging. Zie *Hulp van Acrobat* of aangewezen *RightsManagementExtension Hulp* voor informatie over het vormen van de verbinding binnen de cliënttoepassing.

Documentbeveiliging is toegankelijk via SSL (Secure Sockets Layer). Installeer het certificaat van de website in het certificaatarchief, zodat u via de clienttoepassingen toegang hebt tot documentbeveiliging.

<!-- Fix broken link See Configuring SSL for information on SSL.-->

Deze instructies gelden specifiek voor Internet Explorer, maar u kunt het certificaat installeren met een ondersteunde webbrowser. Raadpleeg de Help van uw browser voor meer informatie.

**installeer het servercertificaat gebruikend Internet Explorer**

1. Open uw webbrowser en typ de basis-URL voor documentbeveiliging in het vak Adres. Typ bijvoorbeeld `https://[host]:[port]` . Er wordt een dialoogvenster Beveiligingswaarschuwing weergegeven.
1. Klik op Certificaat weergeven en klik vervolgens op Certificaat installeren en selecteer de standaardinstellingen voor de installatie. Het certificaat moet worden geïnstalleerd bij de vertrouwde basiscertificeringsinstanties.
1. Sluit uw browsersessie.
1. Open een ander browservenster en typ dezelfde URL in het vak Adres. Er mag geen dialoogvenster Beveiligingswaarschuwing worden weergegeven. Deze test bevestigt dat het certificaat correct geïnstalleerd is.

## Afmelden bij webpagina&#39;s {#log-out-of-the-web-pages}

Meld u af wanneer u klaar bent met het gebruik van de webpagina&#39;s, zodat u uw webbrowser veilig voor andere doeleinden kunt gebruiken. Afhankelijk van hoe de documentveiligheid wordt gevormd, kunt u uw browser moeten sluiten om volledig uit te loggen.

1. Klik in de rechterbovenhoek van de pagina op Afmelden.
1. Als er een bericht wordt weergegeven op de aanmeldingspagina, sluit u het browservenster om u volledig af te melden. Anders kunt u de browser voor andere doeleinden gebruiken.
