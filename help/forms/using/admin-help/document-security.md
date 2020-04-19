---
title: 'Documentbeveiliging '
seo-title: 'Documentbeveiliging '
description: Leer hoe u vooraf gedefinieerde instellingen voor vertrouwelijkheid kunt maken, opslaan en toepassen en uw gegevens veilig kunt verspreiden met documentbeveiliging.
seo-description: Leer hoe u vooraf gedefinieerde instellingen voor vertrouwelijkheid kunt maken, opslaan en toepassen en uw gegevens veilig kunt verspreiden met documentbeveiliging.
uuid: e4fba2a4-f3c1-4b20-8e05-8e241b40ebd0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 1820cb38-ba70-4cce-8895-290524bdd9bf
docset: aem65
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Documentbeveiliging {#about-document-security}

Documentbeveiliging zorgt ervoor dat alleen geautoriseerde gebruikers uw documenten kunnen gebruiken. Met documentbeveiliging kunt u veilig alle informatie verspreiden die u in een ondersteunde indeling hebt opgeslagen. Tot de ondersteunde bestandsindelingen behoren:

* Adobe PDF-bestanden
* Microsoft® Word-, Excel- en PowerPoint-bestanden

Zie [Aanvullende informatie over documentbeveiliging voor meer informatie over hoe ondersteunde bestandstypen door beleid worden beveiligd](https://www.adobe.com/go/learn_aemforms_doc_security_63).

Met documentbeveiliging kunt u eenvoudig vooraf gedefinieerde instellingen voor vertrouwelijkheid maken, opslaan en toepassen op uw documenten. Als u wilt voorkomen dat gegevens buiten uw bereik worden verspreid, kunt u ook controleren en bepalen hoe ontvangers uw documenten gebruiken nadat u ze hebt verspreid.

U kunt documenten beschermen door beleid te gebruiken. Een *beleid* is een inzameling van informatie die vertrouwelijkheidsmontages en een lijst van erkende gebruikers omvat. De vertrouwelijkheidsmontages u in een beleid specificeert bepalen hoe een ontvanger een document kan gebruiken waarop u het beleid toepast. U kunt bijvoorbeeld opgeven of ontvangers tekst kunnen afdrukken of kopiëren, tekst kunnen bewerken of handtekeningen en opmerkingen kunnen toevoegen aan beveiligde documenten.

Gebruikers met documentbeveiliging maken beleid via de webpagina&#39;s van eindgebruikers. Beheerders gebruiken de webpagina&#39;s voor documentbeveiliging om beleidssets te maken die gedeeld beleid bevatten dat beschikbaar is voor alle geautoriseerde gebruikers.

Hoewel het beleid in documentveiligheid wordt opgeslagen, past u hen op documenten door uw cliënttoepassing toe. Hoe u beleid toepast op PDF-documenten wordt gedetailleerd beschreven in de Help bij *Acrobat*. Het toepassen van beleid met andere toepassingen, zoals Microsoft Office, wordt beschreven in de Hulp *van de uitbreidingen van* Acrobat Reader van gelijkstroom voor de toepassing.

Wanneer u een beleid op een document toepast, beschermen de vertrouwelijkheidsmontages die in het beleid worden gespecificeerd de informatie die het document bevat. Met de instellingen voor vertrouwelijkheid worden ook bestanden (tekst, audio of video) in een PDF-document beveiligd. U kunt het document dat met een beleid is beveiligd, verspreiden onder ontvangers die door het beleid zijn gemachtigd.

**Documenttoegangsbeheer en -controle**

Als u een beleid gebruikt om een document te beschermen, hebt u controle over dat document, zelfs nadat u het hebt verspreid. U kunt het document controleren, wijzigingen in het beleid aanbrengen, voorkomen dat gebruikers het document blijven openen en schakelen tussen het beleid dat op het document wordt toegepast.

Via documentbeveiliging kunt u met beleid beveiligde documenten controleren en gebeurtenissen bijhouden, zoals wanneer een geautoriseerde of niet-geautoriseerde gebruiker het document probeert te openen.

**Onderdelen**

Documentbeveiliging bestaat uit een server- en gebruikersinterface:

**Server:** De centrale component waardoor de documentveiligheid transacties zoals gebruikersauthentificatie, beheer in real time van beleid, en toepassing van vertrouwelijkheid uitvoert. De server biedt ook een centrale opslagplaats voor beleidsregels, auditrecords en andere gerelateerde informatie.

**Webpagina&#39;s:** De interface waar u beleid creeert, uw beleid-beschermde documenten beheert, en gebeurtenissen controleert die met beleid-beschermde documenten worden geassocieerd. Beheerders kunnen ook globale opties configureren, zoals gebruikersverificatie, controle en berichten voor uitgenodigde gebruikers, en uitgenodigde gebruikersaccounts beheren.

![rm_psworkflow](assets/rm_psworkflow.png)

De stappen in de illustratie zijn als volgt:

1. De eigenaar van het document maakt beleidsregels op basis van de webpagina&#39;s. Documenteigenaars kunnen persoonlijke beleidsregels maken die alleen voor hen toegankelijk zijn. Beheerders en beleidssetcoördinatoren kunnen gezamenlijk beleid maken binnen beleidssets die toegankelijk zijn voor geautoriseerde gebruikers.
1. De eigenaar van het document past het beleid toe en slaat het document op en verspreidt het. Het document kan via e-mail, via een netwerkmap of op een website worden verspreid.
1. De ontvanger opent het document in de aangewezen cliënttoepassing. De ontvanger kan het document volgens zijn beleid gebruiken.
1. De eigenaar van het document, de beleidssetcoördinator of de beheerder kan documenten bijhouden en de toegang tot deze documenten wijzigen met behulp van de webpagina&#39;s.

## Gebruikers voor documentbeveiliging {#about-document-security-users}

Verschillende typen gebruikers werken met documentbeveiliging om verschillende taken uit te voeren:

* De systeembeheerder of andere informatiesystemen (IS) persoon installeert en vormt documentveiligheid. Deze persoon kan ook verantwoordelijk zijn voor het configureren van algemene instellingen voor de server, webpagina&#39;s en beleidsregels en documenten.

   Deze instellingen kunnen bijvoorbeeld een URL voor de beveiliging van basisdocumenten, audits en privacymeldingen, kennisgevingen voor de registratie van uitgenodigde gebruikers en standaardleaseperioden voor offline gebruikers bevatten.

* De beheerders van de veiligheid van het document creëren beleid en beleidsreeksen, en beheren beleid-beschermde documenten voor gebruikers zoals vereist. Zij creëren ook uitgenodigde gebruikersrekeningen, en monitorsysteem, document, gebruiker, beleid, beleidsreeks, en douanegebeurtenissen. Zij kunnen ook verantwoordelijk voor het vormen van de globale server, en Web-pagina en beleidsmontages samen met een systeembeheerder zijn.

   De beheerders kunnen gebruikers de volgende rollen op het gebied van het Beheer van de Gebruiker van beleidsconsole toewijzen. De gebruikers die deze rollen worden toegewezen voeren hun taken op het gebied van het gebruikersinterface van de documentveiligheid van beleidsconsole uit.

   **Hoofdbeheerder documentbeveiliging**

   Gebruikers met deze rol hebben toegang tot alle beveiligingsinstellingen van het document in de beheerconsole. Deze machtigingen zijn gekoppeld aan de rol:

   * Configuratie beheren
   * Beleid beheren
   * Beleidssets beheren
   * Documenten beheren
   * Documentuitgevers beheren
   * Uitgenodigde en lokale gebruikers beheren
   * Gebeurtenissen weergeven
   * Delegeren
   * Externe gebruikers uitnodigen
   **Documentbeveiligingsbeheerder**

   De gebruikers met deze rol kunnen de server van de documentveiligheid vormen, gebruikend de pagina van de Configuratie in de sectie van de documentveiligheid van beleidsconsole. Deze toestemming wordt geassocieerd met de rol, leidt Configuratie.

   >[!NOTE]
   >
   >De gebruikers met deze rol moeten de rol van de Gebruiker van de beleidsconsole ook hebben om aan beleidsconsole kunnen login en om het even welke op configuratie betrekking hebbende montages uitgeven.

   **Beheerder voor beveiligingsbeleid voor documenten**

   De gebruikers met deze rol kunnen de sectie van de documentveiligheid van beleidsconsole gebruiken om het beleid van andere gebruikers uit te geven en, beleidsreeksen tot stand te brengen uit te geven en te schrappen. Wanneer een beheerder van een beleidsreeks een beleidsreeks creeert, kunnen zij een coördinator van de beleidsreeks aan die beleidsreeks toewijzen. Deze machtigingen zijn gekoppeld aan de rol:

   * Beleid beheren
   * Beleidssets beheren
   * Documenten beheren
   * Documentuitgevers beheren
   * Gebeurtenissen weergeven
   * Delegeren
   >[!NOTE]
   >
   >De gebruikers met deze rol moeten de rol van de Gebruiker van de beleidsconsole ook hebben om aan beleidsconsole kunnen login en om het even welke op configuratie betrekking hebbende montages uitgeven.

   **Documentbeveiliging uitgenodigde en lokale gebruikers beheren**

   Gebruikers met deze rol kunnen de taken uitvoeren die nodig zijn om alle uitgenodigde en lokale gebruikers op de relevante webpagina&#39;s voor documentbeveiliging te beheren. Deze machtigingen zijn gekoppeld aan de rol:

   * Uitgenodigde en lokale gebruikers beheren
   * Externe gebruikers uitnodigen
   * Webpagina&#39;s voor eindgebruikers openen
   >[!NOTE]
   >
   >De gebruikers met deze rol moeten de rol van de Gebruiker van de beleidsconsole ook hebben om aan beleidsconsole kunnen login en om het even welke op configuratie betrekking hebbende montages uitgeven.

   **Gebruikers voor uitnodigen voor documentbeveiliging**

   Gebruikers met deze rol kunnen gebruikers uitnodigen. Deze machtigingen zijn gekoppeld aan de rol:

   * Externe gebruikers uitnodigen
   * Webpagina&#39;s voor eindgebruikers openen
   **Eindgebruiker van documentbeveiliging**

   Gebruikers met deze rol hebben toegang tot webpagina&#39;s van eindgebruikers met documentbeveiliging. Deze rol kan ook aan beheerders worden toegewezen om beheerders toe te staan om beleid tot stand te brengen gebruikend de eindgebruikerpagina&#39;s. Deze toestemming wordt geassocieerd met de rol de eindgebruikerWeb-pagina&#39;s van de Toegang.

* De gebruikers binnen de organisatie die geldige rekeningen van de documentveiligheid hebben creëren hun eigen beleid, gebruiken beleid om documenten te beschermen, hun beleid-beschermde documenten te volgen en te beheren, en gebeurtenissen te controleren die met hun documenten verwant zijn.
* Coördinatoren van beleidssets beheren documenten, gebeurtenissen weergeven en andere beleidssetcoördinatoren beheren (op basis van hun machtigingen). Beheerders wijzen gebruikers aan als beleidssetcoördinatoren voor bepaalde beleidssets.
* Gebruikers die zich buiten uw organisatie bevinden (bijvoorbeeld een zakelijke partner), kunnen documenten met een beveiligingsbeleid gebruiken als zij zich in de beveiligingsmap van het document bevinden, als de beheerder een account voor hen maakt of als zij zich met documentbeveiliging registreren via een geautomatiseerd e-mailuitnodigingsproces. Afhankelijk van hoe de beheerder de toegangsmontages toelaat, kunnen de uitgenodigde gebruikers ook toestemming hebben om beleid op documenten toe te passen, om hun beleid tot stand te brengen te wijzigen en te schrappen, en andere externe gebruikers uit te nodigen om hun beleid-beschermde documenten te gebruiken.
* Ontwikkelaars gebruiken de SDK voor AEM-formulieren om aangepaste toepassingen te integreren met documentbeveiliging.

De beheerders van de veiligheid van het document kunnen douanerollen tot stand brengen door de volgende toestemmingen in Gebruikersbeheer te gebruiken:

* Configuratie van documentbeveiliging beheren
* Beveiliging van documenten Uitgenodigde en lokale gebruikers beheren
* Beleidssets voor documentbeveiliging beheren
* Beleidssets voor documentbeveiliging beheren
* Gebeurtenissen weergaveserver voor documentbeveiliging
* Beleidseigenaar wijzigen van documentbeveiliging

## Beleid en documenten die door beleid worden beschermd {#policies-and-policy-protected-documents}

Een *beleid* bepaalt een reeks vertrouwelijkheidsmontages en gebruikers die tot een document kunnen toegang hebben waarop het beleid wordt toegepast. Met een beleid kunnen ook de machtigingen voor een document dynamisch worden gewijzigd. Het geeft de persoon die het document verzekert toestemming om de vertrouwelijkheidsmontages te veranderen om toegang tot het document in te trekken of het beleid te veranderen.

Beleidsbeveiliging kan op een PDF-document worden toegepast met Adobe Acrobat® Pro en Acrobat Standard. Beleidsbeveiliging kan worden toegepast op andere bestandstypen, zoals Microsoft Word-, Excel- en PowerPoint-bestanden, door de clienttoepassing te gebruiken terwijl de juiste Acrobat Reader DC-extensies zijn geïnstalleerd.

### Hoe beleid werkt {#how-policies-work}

Het beleid bevat informatie over de geautoriseerde gebruikers en de vertrouwelijkheidsinstellingen die op documenten moeten worden toegepast. De gebruikers kunnen om het even wie in uw organisatie zijn, evenals mensen die buiten uw organisatie zijn die een rekening hebben. Als de beheerder de functie voor gebruikersuitnodigingen inschakelt, is het zelfs mogelijk om nieuwe gebruikers aan het beleid toe te voegen en wordt daarom een e-mailproces voor een registratieuitnodiging gestart.

De vertrouwelijkheidsinstellingen in een beleid bepalen hoe de ontvangers het document kunnen gebruiken. U kunt bijvoorbeeld opgeven of ontvangers tekst kunnen afdrukken of kopiëren, wijzigingen kunnen aanbrengen of handtekeningen en opmerkingen kunnen toevoegen aan beveiligde documenten. In hetzelfde beleid kunnen ook verschillende instellingen voor vertrouwelijkheid voor specifieke gebruikers worden opgegeven.

>[!NOTE]
>
>De instellingen voor vertrouwelijkheid die via een beleid worden toegepast, overschrijven instellingen die mogelijk op een PDF-document in Acrobat zijn toegepast met behulp van de beveiligingsopties voor wachtwoorden of certificaten. (Zie de Help van Acrobat voor meer informatie.)

Gebruikers en beheerders maken beleid via de webpagina&#39;s voor documentbeveiliging. Er kan slechts één beleid tegelijk worden toegepast op een document. U kunt een beleid toepassen door een van de volgende methoden te gebruiken:

* Open het document in Acrobat of een andere clienttoepassing en selecteer een beleid om het document te beveiligen.
* Een document verzenden als e-mailbijlage in Microsoft Outlook. In dit geval kunt u een beleid selecteren in een lijst met beleidsregels of een automatisch gegenereerd beleid selecteren dat Acrobat maakt met standaardinstellingen voor vertrouwelijkheid om het document alleen voor de ontvangers van e-mailberichten te beschermen.

Een beleid kan uit een document worden verwijderd door de cliënttoepassing te gebruiken.

![rm_psonline_policy](assets/rm_psonline_policy.png)

De stappen in het diagram zijn als volgt:

1. De eigenaar van het document beveiligt het document vanaf een ondersteunde clienttoepassing met een beleid dat onlinegebruik toestaat.
1. Met documentbeveiliging maakt u een documentlicentie en documentsleutels en versleutelt u het beleid. De documentlicentie, het gecodeerde beleid en de documentsleutel worden geretourneerd aan de clienttoepassing.
1. Het document wordt versleuteld met de documentsleutel en de documentsleutel wordt verwijderd. Het document bevat nu de licentie en het beleid. Deze taken worden uitgevoerd in de ondersteunde clienttoepassing.

Wanneer u een beleid toepast op een document, wordt de informatie die het document bevat, met inbegrip van om het even welke ingebedde dossiers (tekst, audio, of video) in Pdf- documenten, beschermd door de vertrouwelijkheidsmontages die in het beleid worden gespecificeerd. Documentbeveiliging genereert een licentie- en versleutelingsinformatie die vervolgens in het document wordt ingesloten. Wanneer u het document verspreidt, kan de documentbeveiliging de ontvangers verifiëren die proberen het document te openen en toegang autoriseren volgens de rechten die in het beleid zijn opgegeven.

Als offlinegebruik is ingeschakeld, kunnen ontvangers met een beleid beveiligde documenten ook offline gebruiken (zonder actieve internet- of netwerkverbinding) gedurende de periode die in het beleid is opgegeven.

### Hoe beleidsbeveiligde documenten werken {#how-policy-protected-documents-work}

Als u met een beleid beveiligde documenten wilt openen en gebruiken, moet het beleid uw naam als ontvanger bevatten en moet u over een geldige account voor documentbeveiliging beschikken. Voor PDF-documenten hebt u Acrobat of Adobe Reader® nodig. Voor andere bestandstypen hebt u de juiste toepassing voor het bestand nodig als de Acrobat Reader DC-extensies zijn geïnstalleerd.

Wanneer u probeert een document te openen dat met een beleid is beveiligd, maken Acrobat, Adobe Reader of de Acrobat Reader DC-extensies verbinding met documentbeveiliging om u te verifiëren. Vervolgens kunt u doorgaan met het aanmelden. Als het documentgebruik wordt gecontroleerd, verschijnt een berichtbericht. Nadat de documentveiligheid bepaalt welke documenttoestemmingen te verlenen, beheert het de decryptie van het document. Vervolgens kunt u het document gebruiken op basis van de instellingen voor vertrouwelijkheid van het beleid.

![rm_psopen_online](assets/rm_psopen_online.png)

De stappen in het diagram zijn als volgt:

1. De documentgebruiker opent het document in een gesteunde cliënttoepassing en verklaart met de server voor authentiek. De document-id wordt naar de documentbeveiligingsserver verzonden.
1. Met Documentbeveiliging worden de gebruikers geverifieerd, wordt gecontroleerd of er toestemming is gegeven en wordt een voucher gemaakt. De voucher (die de documentsleutel en de toestemmingen bevat) wordt teruggekeerd aan de cliënttoepassing.
1. Het document wordt met de documentsleutel ontsleuteld en de documentsleutel wordt genegeerd. Het document kan vervolgens worden gebruikt met inachtneming van de vertrouwelijkheidsinstellingen van het beleid. Deze taken worden uitgevoerd in de ondersteunde clienttoepassing.

U kunt een document onder de volgende omstandigheden blijven gebruiken:

* Voor onbepaalde tijd of voor de geldigheidsperiode die in het beleid wordt gespecificeerd
* Totdat de beheerder of de persoon die het beleid toepaste, de toegang tot het document herroept of het beleid wijzigt

U kunt documenten die met een beleid zijn beveiligd ook offline gebruiken (zonder internet- of netwerkverbinding) als het beleid offline toegang toestaat. U moet zich eerst aanmelden bij de documentbeveiliging om het document te synchroniseren. Vervolgens kunt u het document gebruiken voor de duur van de offline leaseperiode die in het beleid is opgegeven.

Wanneer de offline leaseperiode afloopt, moet u het document opnieuw synchroniseren met documentbeveiliging door online te gaan en een document te openen dat met een beleid is beveiligd of door een opdracht te gebruiken in de clienttoepassing. (Zie *Acrobat Help* of de juiste Help bij ** Acrobat Reader DC-extensies voor meer informatie.)

Als u een kopie van een document dat met een beleid is beveiligd opslaat met de opdracht Opslaan of Opslaan als, wordt het beleid automatisch toegepast en afgedwongen voor het nieuwe document. Gebeurtenissen zoals pogingen om het nieuwe document te openen, worden ook gecontroleerd en geregistreerd voor het oorspronkelijke document.

## Beleidssets {#policy-sets}

*De reeksen* van het beleid worden gebruikt om een reeks beleid te groeperen dat een gemeenschappelijk bedrijfsdoel heeft. Deze beleidsreeksen worden dan ter beschikking gesteld aan een ondergroep van gebruikers in het systeem.

Elke beleidsreeks kan één of meerdere bijbehorende beleidssetcoördinatoren hebben. De beleidssetcoördinator is een beheerder of een gebruiker die aanvullende machtigingen heeft. De *beleidssetcoördinator* is typisch een specialist in de organisatie die het beleid in een bepaalde beleidreeks het best kan ontwerpen.

Beleidssetcoördinatoren kunnen de volgende taken uitvoeren:

* Nieuw beleid maken
* Beleid in de beleidsset bewerken en verwijderen
* Beleidssetinstellingen bewerken
* Coördinatoren voor beleidssets toevoegen en verwijderen
* Beleid en documentgebeurtenissen weergeven voor beleid of document binnen de beleidsset
* Toegang tot documenten intrekken
* Van beleid wisselen voor het document.

De reeksen van het beleid worden gecreeerd en in de Web-pagina&#39;s van het beleid van de documentveiligheid geschrapt door beheerders en beleidsvastgestelde coördinatoren die toestemming hebben om dit te doen.

De reeksen van het beleid worden over het algemeen ter beschikking gesteld aan een beperkt aantal gebruikers door te specificeren welke gebruikers of groepen binnen een domein het beleid van de beleidsreeks kunnen gebruiken om documenten te beschermen.

Wanneer documentbeveiliging is geïnstalleerd, wordt een standaardbeleidsset gemaakt met de naam *Globale beleidsset*. De beheerder die de software heeft geïnstalleerd, beheert deze beleidsset.
