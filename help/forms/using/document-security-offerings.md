---
title: Beveiligingsaanbod van documenten
description: Meer informatie over de verschillende gereedschappen en functies van AEM documentbeveiliging.
contentOwner: khsingh
geptopics: SG_AEMFORMS/categories/working_with_document_security
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Document Security
exl-id: d00ae232-b018-44e5-b04b-376d4cd9c6eb
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 0%

---

# Beveiligingsaanbod van documenten{#document-security-offerings}

Met de beveiliging van Adobe Experience Manager Forms-documenten kunt u ervoor zorgen dat alleen geautoriseerde gebruikers uw documenten kunnen gebruiken. Met documentbeveiliging kunt u veilig alle informatie verspreiden die u in een ondersteunde indeling hebt opgeslagen. Tot de ondersteunde bestandsindelingen behoren PDF (Adobe Portable Document Format) en Microsoft® Word-, Excel- en PowerPoint-bestanden.

U kunt documenten beschermen door beleid te gebruiken. De vertrouwelijkheidsmontages die u in een beleid specificeert bepalen hoe een ontvanger een document kan gebruiken waarop u het beleid toepast. U kunt bijvoorbeeld opgeven of ontvangers tekst kunnen afdrukken of kopiëren, tekst kunnen bewerken of handtekeningen en opmerkingen kunnen toevoegen aan beveiligde documenten.

Het beleid wordt opgeslagen op de Document Security-server. U past het beleid toe op documenten via de clienttoepassing. Wanneer u een beleid op een document toepast, beschermen de vertrouwelijkheidsmontages die in het beleid worden gespecificeerd de informatie die het document bevat. U kunt het document dat met een beleid is beveiligd, verspreiden onder ontvangers die door het beleid zijn gemachtigd.

In het volgende diagram ziet u de typische architectuur voor AEM Forms Document Security:

![Documentbeveiliging - Aanbevolen architectuur](do-not-localize/document_security_architecture.png)

## Documentbeveiligingsclients {#document-security-clients}

Documentbeveiliging biedt verschillende clients om documenten te beveiligen, beveiligde documenten weer te geven en te bewerken, en indexeerders om zoeken in volledige tekst op beveiligde documenten mogelijk te maken. U kunt een client kiezen op basis van uw vereisten en de mogelijkheden van de client.

De server van de Veiligheid van het Document is de centrale component waardoor de Veiligheid van het Document transacties zoals gebruikersauthentificatie, beheer in real time van beleid, en toepassing van vertrouwelijkheid uitvoert. De server biedt ook een centrale opslagplaats voor beleidsregels, auditrecords en andere gerelateerde informatie.

De server van de Veiligheid van het Document verstrekt een web-based interface (Web-pagina) om beleid tot stand te brengen, beleid-beschermde documenten te beheren, en gebeurtenissen te controleren die met beleid-beschermde documenten worden geassocieerd. Beheerders kunnen ook globale opties configureren, zoals gebruikersverificatie, controle en berichten voor uitgenodigde gebruikers, en uitgenodigde gebruikersaccounts beheren.

De server is opgenomen in de add-on service voor documentbeveiliging van AEM Forms. U kunt contact opnemen met AEM Forms [verkoopteam](https://business.adobe.com/request-consultation/experience-cloud.html?s_osc=70114000002JNwKAAW&amp;s_iid=70114000002JHs3AAG) om de add-on Documentbeveiliging aan te schaffen.

### Protect-documenten {#protect-documents}

AEM Forms Document Security biedt verschillende gereedschappen om beveiligingsbeleid toe te passen. U kunt een gereedschap kiezen op basis van uw vereisten en specificaties.

![document-veiligheid-dienstenaanbod](assets/document-security-offerings.png)

U kunt de SDK van de Veiligheid van het Document, Adobe Acrobat, de Uitbreiding van de Veiligheid van het Document voor Microsoft® Office, of de Bibliotheek van de Draagbare Bescherming gebruiken om het veiligheidsbeleid toe te passen en te volgen:

* **SDK voor documentbeveiliging:** De SDK is een veelzijdige client. Met de SDK voor documentbeveiliging hebt u toegang tot de functionaliteit van de documentserver, kunt u documenten met een beleid openen en aangepaste extensies, plug-ins of toepassingen ontwikkelen. U kunt bijvoorbeeld extensies ontwikkelen om aangepaste bestandsindelingen te beschermen of de SDK integreren met DLP-oplossingen (Data Loss Prevention). Extensies, toepassingen en insteekmodules die zijn ontwikkeld met de Document Security SDK om documenten naar de aangewezen AEM Forms Server te verzenden en het beleid wordt toegepast op de server. De SDK (CSDK) van de AEM Forms-documentbeveiligingsclient kan de beveiliging van documenten die zijn beveiligd met de Portable Protection Library (PPL) en omgekeerd niet opheffen.

  De SDK voor documentbeveiliging is beschikbaar voor zowel Java™ als C++. Java™ SDK is inbegrepen bij het AEM Forms Document Security-aanbod en is geïnstalleerd bij het implementeren van AEM formulieren op JEE. Contact [AEM Klantenondersteuning](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home#support) om C++ SDK aan te kopen. C++ SDK kan met Microsoft® Visual Studio 2013 worden gecompileerd. Ga naar [Documentbeveiliging API-documentatie](https://help.adobe.com/en_US/livecycle/11.0/Services/WS92d06802c76abadb76c48dfe12dbeb3e281-7ff0.2.html) site waar u functies van de SDK kunt leren en gebruiken.

* **Adobe Acrobat:** Met Adobe Acrobat kunt u beveiligingsbeleid toepassen op PDF-documenten die zijn gemaakt met populaire bureaubladtoepassingen, zoals Microsoft® Office, webbrowsers of elke toepassing die afdrukken in PDF-indeling ondersteunt.

  U kunt Adobe Acrobat aanschaffen en downloaden via het [Adobe website](https://www.adobe.com/acrobat/free-trial-download.html). Adobe Acrobat-artikel [beveiligingsbeleid voor PDF instellen](https://helpx.adobe.com/acrobat/using/setting-security-policies-pdfs.html) biedt gedetailleerde informatie over het maken en toepassen van beleid in Adobe Acrobat.

* **Documentbeveiligingsextensie voor Microsoft® Office**: Met de Document Security Extension for Microsoft® Office kunt u vooraf gedefinieerde beleidsregels toepassen op uw Microsoft® Office-bestanden vanuit de Microsoft® Office-programma&#39;s. De extensie zorgt ervoor dat alleen geautoriseerde personen Microsoft® Word-, Excel- en PowerPoint-bestanden die met een beleid zijn beveiligd, kunnen gebruiken. Alleen geautoriseerde gebruikers die de plug-in hebben geïnstalleerd, kunnen de bestanden gebruiken die met een beleid zijn beveiligd.

  De extensie Documentbeveiliging is beschikbaar als een Microsoft® Office-plug-in. Contact [AEM Klantenondersteuning](https://helpx.adobe.com/ca/marketing-cloud/contact-support.html) om de extensie aan te schaffen. Later kunt u naar [Documentbeveiligingsextensie voor Microsoft® Office](https://experienceleague.adobe.com/docs/experience-manager-document-security/using/download-installer.html?lang=en) Help voor meer informatie over het installeren, configureren en gebruiken van de extensie.

* **Portable Protection-bibliotheek:** De PPL beschermt een document lokaal, zonder het document naar de AEM Forms-server te verzenden. Alleen beveiligingsgegevens en beleidsdetails reizen over het netwerk. PPL laat u ook de toegang van de beleidsherwinning tot slechts het programma geopende gebruikers beperken. U kunt beleid met de context ophalen van de gebruiker AEM gebruiker het programma opent.

  Samen met het bovenstaande heeft de PPL alle functies van Document Security SDK. Met de SDK voor documentbeveiliging hebt u toegang tot de functionaliteit van de documentserver, kunt u documenten met een beleid openen en aangepaste extensies, plug-ins of toepassingen ontwikkelen. De PPL kan de beveiliging van documenten die zijn beveiligd met de AEM Forms-documentbeveiligingsclient SDK (CSDK) en omgekeerd niet opheffen.

  De PPL is beschikbaar voor Java™- en C++-talen in 32-bits en 64-bits versies. Het is ook beschikbaar als OSGi-bundel voor AEM Forms op OSGi. C++ PPL kan met Microsoft® Visual Studio 2013 worden gecompileerd. Als u een AEM Forms Document Security Add-on met licentie hebt, kunt u contact opnemen met de [Beveiliging van AEM Forms-documenten](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home#support) ondersteuningsteam om de PPL aan te schaffen. Later kunt u de PPL Help (meegeleverd bij de bibliotheek) gebruiken om de PPL in te stellen en te gebruiken.

### Beveiligde documenten weergeven of bewerken {#view-or-edit-protected-documents}

* Voor **PDF-documenten**, kunt u Adobe Acrobat DC, Acrobat Reader en Acrobat Reader Mobile gebruiken om beveiligde PDF-documenten weer te geven. De meeste gebruikers hebben Acrobat Reader al op hun apparaten geïnstalleerd, zodat zij geen extra software hoeven te verkrijgen of te leren om beschermde documenten te bekijken. U kunt de Acrobat Reader ook downloaden via de [Acrobat Reader-downloadwebsite](https://get.adobe.com/reader/).

* Voor **Microsoft® Office-documenten** hebt u Microsoft® Office- en AEM Forms Document Security-extensie nodig voor Microsoft® Office. De extensie Documentbeveiliging is beschikbaar als een Microsoft® Office-plug-in. U kunt de extensie downloaden van de website van de Adobe.

### Beveiligde documenten indexeren {#index-protected-documents}

Microsoft® Windows full-text zoekprogramma&#39;s (SharePoint Index Server) en Adobe Experience Manager (AEM) kunnen full-text zoekopdrachten uitvoeren op veelgebruikte documentindelingen, zoals bestanden in onbewerkte tekst, Microsoft® Office-documenten en PDF-documenten. U kunt indexen van de Veiligheid van het Document gebruiken om fullText onderzoeksmotoren toe te laten om beschermde PDF documenten te zoeken:

* **Index iFilter:** U kunt de iFilter-index gebruiken om beveiligde PDF-documenten te indexeren en Microsoft® Windows full-text zoekmachines (Desktop Indexing Service en SharePoint Index-server) inschakelen om beveiligde PDF-documenten te doorzoeken. Zie voor meer informatie [SharePoint IFilter AEM voor beveiligde documenten](assets/sharepoint-ifilter-doc-security.pdf).

* **AEM Forms Document Security Index:** U kunt de AEM Forms Document Security-index gebruiken om beveiligde PDF-documenten te indexeren en Adobe Experience Manager in staat te stellen om beveiligde PDF-documenten te doorzoeken. De indexen maken deel uit van het AEM Forms Document Security-aanbod. Deze zijn opgenomen in AEM Forms op JEE-installatieprogramma&#39;s.
