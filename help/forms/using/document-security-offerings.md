---
title: Beveiligingsaanbod van documenten
seo-title: Beveiligingsaanbod van documenten
description: Meer informatie over de verschillende gereedschappen en functies van AEM Document Security
seo-description: Meer informatie over de verschillende gereedschappen en functies van AEM Document Security
uuid: 24e3275c-cd44-47c0-a6a0-e4cfb1bced8a
contentOwner: khsingh
geptopics: SG_AEMFORMS/categories/working_with_document_security
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 91e85e86-2361-4d1d-aa73-c3cce46ab1f1
docset: aem65
translation-type: tm+mt
source-git-commit: e45e335d433f17a48ba1bf27a93c5b1003369512

---


# Beveiligingsaanbod van documenten{#document-security-offerings}

De documentbeveiliging van Adobe Experience Manager Forms zorgt ervoor dat alleen geautoriseerde gebruikers uw documenten kunnen gebruiken. Met documentbeveiliging kunt u veilig alle informatie verspreiden die u in een ondersteunde indeling hebt opgeslagen. Ondersteunde bestandsindelingen zijn onder andere Adobe Portable Document Format (PDF)- en Microsoft Word-, Excel- en PowerPoint-bestanden.

U kunt documenten beschermen door beleid te gebruiken. De vertrouwelijkheidsmontages u in een beleid specificeert bepalen hoe een ontvanger een document kan gebruiken waarop u het beleid toepast. U kunt bijvoorbeeld opgeven of ontvangers tekst kunnen afdrukken of kopiëren, tekst kunnen bewerken of handtekeningen en opmerkingen kunnen toevoegen aan beveiligde documenten.

Het beleid wordt opgeslagen op de server van de Veiligheid van het Document; u past het beleid op documenten toe door uw cliënttoepassing. Wanneer u een beleid op een document toepast, beschermen de vertrouwelijkheidsmontages die in het beleid worden gespecificeerd de informatie die het document bevat. U kunt het document dat met een beleid is beveiligd, verspreiden onder ontvangers die door het beleid zijn gemachtigd.

In het volgende diagram wordt de typische architectuur voor AEM Forms Document Security weergegeven:

![Documentbeveiliging - Aanbevolen architectuur](do-not-localize/document_security_architecture.png)

## Documentbeveiligingsclients {#document-security-clients}

Documentbeveiliging biedt verschillende clients om documenten te beveiligen, beveiligde documenten weer te geven en te bewerken, en indexeerders om zoeken in volledige tekst op beveiligde documenten mogelijk te maken. U kunt een client kiezen op basis van uw vereisten en de mogelijkheden van de client.

De server van de Veiligheid van het Document is de centrale component waardoor de Veiligheid van het Document transacties zoals gebruikersauthentificatie, beheer in real time van beleid, en toepassing van vertrouwelijkheid uitvoert. De server biedt ook een centrale opslagplaats voor beleidsregels, auditrecords en andere gerelateerde informatie.

De server van de Veiligheid van het Document verstrekt een web-based interface (Web-pagina) om beleid tot stand te brengen, beleid-beschermde documenten te beheren, en gebeurtenissen te controleren die met beleid-beschermde documenten worden geassocieerd. Beheerders kunnen ook globale opties configureren, zoals gebruikersverificatie, controle en berichten voor uitgenodigde gebruikers, en uitgenodigde gebruikersaccounts beheren.

De server is opgenomen in de add-on service voor documentbeveiliging van AEM Forms. U kunt contact opnemen met het [verkoopteam](https://www.adobe.com/products/request-consultation/marketing-cloud.html?s_osc=70114000002JNwKAAW&s_iid=70114000002JHs3AAG) van AEM Forms om de add-on Documentbeveiliging aan te schaffen.

### Documenten beveiligen {#protect-documents}

AEM Forms Document Security biedt verschillende gereedschappen om beveiligingsbeleid toe te passen. U kunt een gereedschap kiezen op basis van uw vereisten en specificaties.

![document-veiligheid-dienstenaanbod](assets/document-security-offerings.png)

U kunt de SDK van de Beveiliging van het Document, de Acrobaat van Adobe, de Uitbreiding van de Veiligheid van het Document voor Microsoft Office, of de Bibliotheek van de Portable Bescherming gebruiken om het veiligheidsbeleid toe te passen en te volgen:

* **SDK voor documentbeveiliging:** De SDK is een veelzijdige client. Met de SDK voor documentbeveiliging hebt u toegang tot de functionaliteit van de documentserver, kunt u documenten met een beleid openen en kunt u aangepaste extensies, plug-ins of toepassingen ontwikkelen. U kunt bijvoorbeeld extensies ontwikkelen om aangepaste bestandsindelingen te beschermen of SDK te integreren met DLP-oplossingen (Data Loss Prevention). Extensies, toepassingen en insteekmodules die zijn ontwikkeld met gebruik van Document Security SDK verzenden documenten naar de aangewezen AEM Forms-server en het beleid wordt toegepast op de server. Let ook op: de beveiligingsclient SDK (CSDK) van AEM Forms document kan de beveiliging van documenten die zijn beveiligd met een draagbare beveiligingsbibliotheek (PPL) en omgekeerd niet opheffen.

   De SDK van Documentbeveiliging is beschikbaar voor zowel Java als C++. De SDK van Java is inbegrepen in de aanbieding van de Veiligheid van het Document van AEM- Vormen en het is geïnstalleerd bij het opstellen van AEM- formulieren op JEE. U kunt contact opnemen met het [AEM-ondersteuningsteam](https://helpx.adobe.com/marketing-cloud/contact-support.html) om C++ SDK aan te schaffen. C++ SDK kan met Microsoft Visual Studio 2013 worden gecompileerd. Ga naar de documentatiesite van de API voor [documentbeveiliging](https://help.adobe.com/en_US/livecycle/11.0/Services/WS92d06802c76abadb76c48dfe12dbeb3e281-7ff0.2.html) voor meer informatie over en gebruik van functies in de SDK.

* **Adobe Acrobat:** Met Adobe Acrobat kunt u beveiligingsbeleid toepassen op PDF-documenten die zijn gemaakt met populaire bureaubladtoepassingen, zoals Microsoft Office, webbrowsers of elke toepassing die afdrukken in PDF-indeling ondersteunt.

   U kunt Adobe Acrobat aanschaffen en downloaden van de [Adobe-website](https://acrobat.adobe.com/us/en/free-trial-download.html). In het Adobe Acrobat-artikel waarin beveiligingsbeleid voor PDF&#39;s [wordt](https://helpx.adobe.com/acrobat/using/setting-security-policies-pdfs.html) ingesteld, wordt gedetailleerde informatie gegeven over het maken en toepassen van beleid in Adobe Acrobat.

* **Documentbeveiligingsextensie voor Microsoft Office**: U kunt de Uitbreiding van de Veiligheid van het Document voor Microsoft Office gebruiken om vooraf bepaald beleid op uw dossiers van Microsoft Office van binnen de programma&#39;s van Microsoft Office toe te passen. De extensie zorgt ervoor dat alleen geautoriseerde personen met een beleid beveiligde Microsoft Word-, Excel- en PowerPoint-bestanden kunnen gebruiken. Alleen geautoriseerde gebruikers die de plug-in hebben geïnstalleerd, kunnen de bestanden gebruiken die met een beleid zijn beveiligd.

   De extensie Documentbeveiliging is beschikbaar als een Microsoft Office-plug-in. U kunt contact opnemen met het [AEM-ondersteuningsteam](https://helpx.adobe.com/ca/marketing-cloud/contact-support.html) om de extensie aan te schaffen. Later, kunt u de Uitbreiding van de Veiligheid van het [Document voor de hulp van Microsoft Office](https://helpx.adobe.com/aem-forms/aem-document-security/download-installer.html) bezoeken om over het installeren, het vormen, en het gebruiken van de uitbreiding te leren.

* **Portable Protection-bibliotheek:** Met de PPL (Portable Protection Library) wordt een document lokaal beveiligd, zonder dat het document naar de AEM Forms-server wordt verzonden. Alleen beveiligingsgegevens en beleidsdetails reizen over het netwerk. PPL staat u ook toe om de toegang van de beleidsherwinning tot slechts het programma geopende gebruikers te beperken. U kunt beleid ophalen met de context van de gebruiker die AEM-gebruiker heeft aangemeld.

   Samen met het bovenstaande heeft de Prortable Protection Library alle functies van Document Security SDK. Met de SDK voor documentbeveiliging hebt u toegang tot de functionaliteit van de documentserver, kunt u documenten met een beleid openen en kunt u aangepaste extensies, plug-ins of toepassingen ontwikkelen. Let ook op: de draagbare beveiligingsbibliotheek (PPL) kan de beveiliging van documenten die zijn beveiligd met AEM Forms document security client SDK (CSDK) en vice versa, niet opheffen.

   De Portable Protection Library is beschikbaar voor Java- en C++-talen in 32-bits en 64-bits versies. Het is ook beschikbaar als een OSGi-bundel voor AEM Forms op OSGi. C++ PPL kan met Microsoft Visual Studio 2013 worden gecompileerd. Als u een AEM Forms Document Security-add-on met licentie hebt, kunt u contact opnemen met het ondersteuningsteam [voor documentbeveiliging](https://helpx.adobe.com/marketing-cloud/contact-support.html) van AEM Forms om de Portable Protection Library aan te schaffen. Later kunt u de Help van de Portable Protection Library (meegeleverd bij de bibliotheek) gebruiken om de Portable Protection Library in te stellen en te gebruiken.

### Beveiligde documenten weergeven of bewerken {#view-or-edit-protected-documents}

* Voor **PDF-documenten** kunt u beveiligde PDF-documenten weergeven met Adobe Acrobat DC, Acrobat Reader en Acrobat Reader Mobile. De meeste gebruikers hebben Acrobat Reader al op hun apparaten geïnstalleerd, dus ze hoeven geen extra software te verkrijgen of te leren om beveiligde documenten te kunnen bekijken. U kunt Acrobat Reader ook downloaden van de downloadwebsite [van](https://get.adobe.com/reader/)Acrobat Reader.

* Voor documenten **van** Microsoft Office, vereist u de uitbreiding van de Veiligheid van het Document van Microsoft Office en van de Vormen AEM voor Microsoft Office. De extensie Documentbeveiliging is beschikbaar als een Microsoft Office-plug-in. U kunt de extensie downloaden van de Adobe-website.

### Beveiligde documenten indexeren {#index-protected-documents}

Microsoft Windows-zoekprogramma&#39;s met volledige tekst (SharePoint Index-server) en Adobe Experience Manager (AEM) kunnen zoeken in volledige tekst op veelgebruikte documentindelingen, zoals bestanden met onbewerkte tekst, Microsoft Office-documenten en PDF-documenten. Met de documentbeveiligingsindexen kunt u zoekprogramma&#39;s met volledige tekst toestaan om beveiligde PDF-documenten te doorzoeken:

* **Index iFilter:** U kunt de iFilter-index gebruiken om beveiligde PDF-documenten te indexeren en Microsoft Windows-zoekprogramma&#39;s met volledige tekst (Desktop Indexing Service en SharePoint Indexserver) inschakelen om beveiligde PDF-documenten te doorzoeken. Zie [AEM SharePoint IFilter voor beveiligde documenten](assets/sharepoint-ifilter-doc-security.pdf)voor gedetailleerde informatie.

* **AEM Forms Document Security Index:** U kunt de AEM Forms Document Security-index gebruiken om beveiligde PDF-documenten te indexeren en Adobe Experience Manager in staat te stellen beveiligde PDF-documenten te doorzoeken. De indexeerders maken deel uit van het AEM Forms Document Security-aanbod. Deze vindt u in AEM Forms op JEE-installatieprogramma&#39;s.

