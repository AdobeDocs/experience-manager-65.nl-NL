---
title: Beveiligingsaanbod van documenten
seo-title: Document security offerings
description: Meer informatie over de verschillende gereedschappen en functies van AEM documentbeveiliging
seo-description: Learn about various tools and features of AEM Document Security
uuid: 24e3275c-cd44-47c0-a6a0-e4cfb1bced8a
contentOwner: khsingh
geptopics: SG_AEMFORMS/categories/working_with_document_security
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 91e85e86-2361-4d1d-aa73-c3cce46ab1f1
docset: aem65
feature: Document Security
exl-id: d00ae232-b018-44e5-b04b-376d4cd9c6eb
source-git-commit: 18c180a491af10b41393ad841f2fa74d02ec9cd9
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 0%

---

# Beveiligingsaanbod van documenten{#document-security-offerings}

Met de beveiliging van Adobe Experience Manager Forms-documenten kunt u ervoor zorgen dat alleen geautoriseerde gebruikers uw documenten kunnen gebruiken. Met documentbeveiliging kunt u veilig alle informatie verspreiden die u in een ondersteunde indeling hebt opgeslagen. Tot de ondersteunde bestandsindelingen behoren de bestanden Adobe Portable Document Format (PDF) en Microsoft Word, Excel en PowerPoint.

U kunt documenten beschermen door beleid te gebruiken. De vertrouwelijkheidsmontages u in een beleid specificeert bepalen hoe een ontvanger een document kan gebruiken waarop u het beleid toepast. U kunt bijvoorbeeld opgeven of ontvangers tekst kunnen afdrukken of kopiëren, tekst kunnen bewerken of handtekeningen en opmerkingen kunnen toevoegen aan beveiligde documenten.

Het beleid wordt opgeslagen op de server van de Veiligheid van het Document; u past het beleid op documenten toe door uw cliënttoepassing. Wanneer u een beleid op een document toepast, beschermen de vertrouwelijkheidsmontages die in het beleid worden gespecificeerd de informatie die het document bevat. U kunt het document dat met een beleid is beveiligd, verspreiden onder ontvangers die door het beleid zijn gemachtigd.

In het volgende diagram ziet u de typische architectuur voor AEM Forms Document Security:

![Documentbeveiliging - Aanbevolen architectuur](do-not-localize/document_security_architecture.png)

## Documentbeveiligingsclients {#document-security-clients}

Documentbeveiliging biedt verschillende clients om documenten te beveiligen, beveiligde documenten weer te geven en te bewerken, en indexeerders om zoeken in volledige tekst op beveiligde documenten mogelijk te maken. U kunt een client kiezen op basis van uw vereisten en de mogelijkheden van de client.

De server van de Veiligheid van het Document is de centrale component waardoor de Veiligheid van het Document transacties zoals gebruikersauthentificatie, beheer in real time van beleid, en toepassing van vertrouwelijkheid uitvoert. De server biedt ook een centrale opslagplaats voor beleidsregels, auditrecords en andere gerelateerde informatie.

De server van de Veiligheid van het Document verstrekt een web-based interface (Web-pagina) om beleid tot stand te brengen, beleid-beschermde documenten te beheren, en gebeurtenissen te controleren die met beleid-beschermde documenten worden geassocieerd. Beheerders kunnen ook globale opties configureren, zoals gebruikersverificatie, controle en berichten voor uitgenodigde gebruikers, en uitgenodigde gebruikersaccounts beheren.

De server wordt opgenomen in de add-on service voor documentbeveiliging van AEM Forms. U kunt contact opnemen met AEM Forms [verkoopteam](https://www.adobe.com/products/request-consultation/marketing-cloud.html?s_osc=70114000002JNwKAAW&amp;s_iid=70114000002JHs3AAG) om de add-on Documentbeveiliging aan te schaffen.

### Protect-documenten {#protect-documents}

AEM Forms Document Security biedt verschillende gereedschappen om beveiligingsbeleid toe te passen. U kunt een gereedschap kiezen op basis van uw vereisten en specificaties.

![document-veiligheid-dienstenaanbod](assets/document-security-offerings.png)

U kunt de SDK van de Veiligheid van het Document, Adobe Acrobat, de Uitbreiding van de Veiligheid van het Document voor Microsoft Office, of de Bibliotheek van de Draagbare Bescherming gebruiken om het veiligheidsbeleid toe te passen en te volgen:

* **SDK voor documentbeveiliging:** De SDK is een veelzijdige client. Met de SDK voor documentbeveiliging hebt u toegang tot de functionaliteit van de documentserver, kunt u documenten met een beleid openen en kunt u aangepaste extensies, plug-ins of toepassingen ontwikkelen. U kunt bijvoorbeeld extensies ontwikkelen om aangepaste bestandsindelingen te beschermen of SDK te integreren met DLP-oplossingen (Data Loss Prevention). Extensies, toepassingen en plug-ins die zijn ontwikkeld met Document Security SDK verzenden documenten naar de aangewezen AEM Forms-server en het beleid wordt toegepast op de server. Let ook op: CSDK (AEM Forms document security client SDK) kan de beveiliging van documenten die zijn beveiligd met een draagbare beveiligingsbibliotheek (PPL) en omgekeerd niet opheffen.

   De SDK van Documentbeveiliging is beschikbaar voor zowel Java als C++. Java SDK is inbegrepen in de aanbieding van de Veiligheid van het Document van AEM Forms en het is geïnstalleerd bij het opstellen van AEM vormen op JEE. U kunt contact opnemen met [Ondersteuningsteam AEM](https://helpx.adobe.com/marketing-cloud/contact-support.html) om C++ SDK aan te schaffen. C++ SDK kan met Microsoft Visual Studio 2013 worden gecompileerd. U kunt [Documentbeveiliging API-documentatie](https://help.adobe.com/en_US/livecycle/11.0/Services/WS92d06802c76abadb76c48dfe12dbeb3e281-7ff0.2.html) om functies van de SDK te leren en te gebruiken.

* **Adobe Acrobat:** Met Adobe Acrobat kunt u beveiligingsbeleid toepassen op PDF-documenten die zijn gemaakt met populaire bureaubladtoepassingen, zoals Microsoft Office, webbrowsers of elke toepassing die afdrukken in PDF-indeling ondersteunt.

   U kunt Adobe Acrobat kopen en downloaden van [Adobe-website](https://acrobat.adobe.com/us/en/free-trial-download.html). Adobe Acrobat-artikel [beveiligingsbeleid voor PDF instellen](https://helpx.adobe.com/acrobat/using/setting-security-policies-pdfs.html) biedt gedetailleerde informatie over het maken en toepassen van beleid in Adobe Acrobat.

* **Documentbeveiligingsextensie voor Microsoft Office**: U kunt de Uitbreiding van de Veiligheid van het Document voor Microsoft Office gebruiken om vooraf bepaald beleid op uw dossiers van Microsoft toe te passen Office binnen de programma&#39;s van Microsoft Office. De extensie zorgt ervoor dat alleen geautoriseerde personen met een beleid beveiligde Microsoft Word-, Excel- en PowerPoint-bestanden kunnen gebruiken. Alleen geautoriseerde gebruikers die de plug-in hebben geïnstalleerd, kunnen de bestanden gebruiken die met een beleid zijn beveiligd.

   De extensie Documentbeveiliging is beschikbaar als een Microsoft Office-plug-in. U kunt contact opnemen met [Ondersteuningsteam AEM](https://helpx.adobe.com/ca/marketing-cloud/contact-support.html) om de extensie aan te schaffen. Later kunt u naar [Documentbeveiligingsextensie voor Microsoft Office](https://helpx.adobe.com/aem-forms/aem-document-security/download-installer.html) Help voor meer informatie over het installeren, configureren en gebruiken van de extensie.

* **Portable Protection-bibliotheek:** Met de PPL (Portable Protection Library) wordt een document lokaal beveiligd, zonder dat het document naar de AEM Forms-server wordt verzonden. Alleen beveiligingsgegevens en beleidsdetails reizen over het netwerk. PPL staat u ook toe om de toegang van de beleidsherwinning tot slechts het programma geopende gebruikers te beperken. U kunt beleid met de context ophalen van de gebruiker AEM gebruiker het programma opent.

   Samen met het bovenstaande heeft de Prortable Protection Library alle functies van Document Security SDK. Met de SDK voor documentbeveiliging hebt u toegang tot de functionaliteit van de documentserver, kunt u documenten met een beleid openen en kunt u aangepaste extensies, plug-ins of toepassingen ontwikkelen. Let ook op: de draagbare beveiligingsbibliotheek (PPL) kan de beveiliging van documenten die zijn beveiligd met de AEM Forms-documentbeveiligingsclient SDK (CSDK) en vice versa, niet opheffen.

   De Portable Protection Library is beschikbaar voor Java- en C++-talen in 32-bits en 64-bits versies. Het is ook beschikbaar als OSGi-bundel voor AEM Forms op OSGi. C++ PPL kan met Microsoft Visual Studio 2013 worden gecompileerd. Als u een AEM Forms Document Security Add-on met licentie hebt, kunt u contact opnemen met [Beveiliging van AEM Forms-documenten](https://helpx.adobe.com/marketing-cloud/contact-support.html) ondersteuningsteam voor het aanschaffen van de Portable Protection Library. Later kunt u de Help van de Portable Protection Library (meegeleverd bij de bibliotheek) gebruiken om de Portable Protection Library in te stellen en te gebruiken.

### Beveiligde documenten weergeven of bewerken {#view-or-edit-protected-documents}

* Voor **PDF-documenten**, kunt u Adobe Acrobat DC, Acrobat Reader en Acrobat Reader Mobile gebruiken om beveiligde PDF-documenten weer te geven. De meeste gebruikers hebben Acrobat Reader al op hun apparaten geïnstalleerd, zodat zij geen extra software hoeven te verkrijgen of te leren om beschermde documenten te bekijken. U kunt de Acrobat Reader ook downloaden van [Acrobat Reader-downloadwebsite](https://get.adobe.com/reader/).

* Voor **Microsoft Office-documenten** hebt u Microsoft Office- en AEM Forms Document Security-extensie voor Microsoft Office nodig. De extensie Documentbeveiliging is beschikbaar als een Microsoft Office-plug-in. U kunt de extensie downloaden van de Adobe-website.

### Beveiligde documenten indexeren {#index-protected-documents}

Microsoft Windows-zoekprogramma&#39;s voor volledige tekst (SharePoint Index-server) en Adobe Experience Manager (AEM) kunnen zoeken in volledige tekst op veelgebruikte documentindelingen, zoals bestanden met normale tekst, Microsoft Office-documenten en PDF-documenten. U kunt indexen van de Veiligheid van het Document gebruiken om fullText onderzoeksmotoren toe te laten om beschermde PDF documenten te zoeken:

* **Index iFilter:** Met de iFilter-indexeerfunctie kunt u beveiligde PDF-documenten indexeren en Microsoft Windows-zoekprogramma&#39;s met volledige tekst (Desktop Indexing Service en SharePoint Indexserver) inschakelen om beveiligde PDF-documenten te doorzoeken. Zie voor meer informatie [SharePoint IFilter AEM voor beveiligde documenten](assets/sharepoint-ifilter-doc-security.pdf).

* **AEM Forms Document Security Index:** U kunt de AEM Forms Document Security-index gebruiken om beveiligde PDF-documenten te indexeren en Adobe Experience Manager in staat te stellen beveiligde PDF-documenten te doorzoeken. De indexeerders maken deel uit van de AEM Forms Document Security-service. Deze zijn opgenomen in AEM Forms op JEE-installatieprogramma&#39;s.
