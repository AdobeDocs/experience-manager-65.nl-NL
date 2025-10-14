---
title: Wat is documentbeveiliging?
description: Leer hoe u vooraf gedefinieerde instellingen voor vertrouwelijkheid kunt maken, opslaan en toepassen en uw gegevens veilig kunt verspreiden met documentbeveiliging.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Document Security
exl-id: 0cdc9ee3-0172-43be-9b62-ed768534c074
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '3219'
ht-degree: 0%

---

# Documentbeveiliging {#about-document-security}

Documentbeveiliging zorgt ervoor dat alleen geautoriseerde gebruikers uw documenten kunnen gebruiken. Met documentbeveiliging kunt u veilig alle informatie verspreiden die u in een ondersteunde indeling hebt opgeslagen. Tot de ondersteunde bestandsindelingen behoren:

* Adobe PDF-bestanden
* Microsoft® Word-, Excel- en PowerPoint-bestanden

Voor meer informatie over hoe het beleid gesteunde dossiertypes beschermt, zie [&#x200B; meer informatie van de documentveiligheid &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-security/document-security-offerings.html?lang=nl-NL).

Met documentbeveiliging kunt u eenvoudig vooraf gedefinieerde instellingen voor vertrouwelijkheid maken, opslaan en toepassen op uw documenten. Als u wilt voorkomen dat gegevens buiten uw bereik worden verspreid, kunt u ook controleren en bepalen hoe ontvangers uw documenten gebruiken nadat u ze hebt verspreid.

U kunt documenten beschermen door beleid te gebruiken. A *beleid* is een inzameling van informatie die vertrouwelijkheidsmontages en een lijst van erkende gebruikers omvat. De vertrouwelijkheidsmontages die u in een beleid specificeert bepalen hoe een ontvanger een document kan gebruiken waarop u het beleid toepast. U kunt bijvoorbeeld opgeven of ontvangers tekst kunnen afdrukken of kopiëren, tekst kunnen bewerken of handtekeningen en opmerkingen kunnen toevoegen aan beveiligde documenten.

Gebruikers met documentbeveiliging maken beleid via de webpagina&#39;s van eindgebruikers. Beheerders gebruiken de webpagina&#39;s voor documentbeveiliging om beleidssets te maken die gedeeld beleid bevatten dat beschikbaar is voor alle geautoriseerde gebruikers.

Hoewel het beleid in documentveiligheid wordt opgeslagen, past u hen op documenten door uw cliënttoepassing toe. Hoe te om beleid op de documenten van PDF toe te passen wordt beschreven in *Hulp van Acrobat*. Het toepassen van beleid door andere toepassingen, zoals Microsoft® Office te gebruiken, wordt gedocumenteerd in de *Hulp van de Uitbreidingen van Acrobat Reader DC* voor de toepassing.

Wanneer u een beleid op een document toepast, beschermen de vertrouwelijkheidsmontages die in het beleid worden gespecificeerd de informatie die het document bevat. Met de instellingen voor vertrouwelijkheid worden ook bestanden (tekst, audio of video) in een PDF-document beveiligd. U kunt het document dat met een beleid is beveiligd, verspreiden onder ontvangers die door het beleid zijn gemachtigd.

**de toegangscontrole en controle van het Document**

Als u een beleid gebruikt om een document te beschermen, hebt u controle over dat document, zelfs nadat u het hebt verspreid. U kunt het document controleren, het beleid wijzigen, voorkomen dat gebruikers het document blijven openen en het beleid wijzigen dat op het document wordt toegepast.

Via documentbeveiliging kunt u met beleid beveiligde documenten controleren en gebeurtenissen bijhouden, zoals wanneer een geautoriseerde of niet-geautoriseerde gebruiker het document probeert te openen.

**Onderdelen**

Documentbeveiliging bestaat uit een server- en gebruikersinterface:

**Server:** de centrale component waardoor de documentveiligheid transacties zoals gebruikersauthentificatie, beheer in real time van beleid, en toepassing van vertrouwelijkheid uitvoert. De server biedt ook een centrale opslagplaats voor beleidsregels, auditrecords en andere gerelateerde informatie.

**Web-pagina&#39;s:** de interface waar u beleid creeert, uw beleid-beschermde documenten beheert, en gebeurtenissen controleert die met beleid-beschermde documenten worden geassocieerd. Beheerders kunnen ook globale opties configureren, zoals gebruikersverificatie, controle en berichten voor uitgenodigde gebruikers, en uitgenodigde gebruikersaccounts beheren.

![&#x200B; rm_psworkflow &#x200B;](assets/rm_psworkflow.png)

De stappen in de illustratie zijn als volgt:

1. De eigenaar van het document maakt beleidsregels op basis van de webpagina&#39;s. Documenteigenaars kunnen persoonlijke beleidsregels maken die alleen voor hen toegankelijk zijn. Beheerders en beleidssetcoördinatoren kunnen gezamenlijk beleid maken binnen beleidssets die toegankelijk zijn voor geautoriseerde gebruikers.
1. De eigenaar van het document past het beleid toe en slaat het document op en verspreidt het. Het document kan via e-mail, via een netwerkmap of op een website worden verspreid.
1. De ontvanger opent het document in de aangewezen cliënttoepassing. De ontvanger kan het document volgens zijn beleid gebruiken.
1. De eigenaar van het document, de beleidssetcoördinator of de beheerder kan documenten bijhouden en de toegang tot deze documenten wijzigen met behulp van de webpagina&#39;s.

## Gebruikers voor documentbeveiliging {#about-document-security-users}

Verschillende typen gebruikers werken met documentbeveiliging om verschillende taken uit te voeren:

* De systeembeheerder of andere informatiesystemen (IS) persoon installeert en vormt documentveiligheid. Deze persoon kan ook verantwoordelijk zijn voor het configureren van algemene instellingen voor de server, webpagina&#39;s en beleidsregels en documenten.

  Deze instellingen kunnen bijvoorbeeld een URL voor de beveiliging van basisdocumenten, audits en privacymeldingen, kennisgevingen voor de registratie van uitgenodigde gebruikers en standaardleaseperioden voor offline gebruikers bevatten.

* De beheerders van de veiligheid van het document creëren beleid en beleidsreeksen, en beheren beleid-beschermde documenten voor gebruikers zoals vereist. Zij creëren ook uitgenodigde gebruikersrekeningen, en monitorsysteem, document, gebruiker, beleid, beleidsreeks, en douanegebeurtenissen. Zij kunnen ook verantwoordelijk voor het vormen van de globale server, en Web-pagina en beleidsmontages met een systeembeheerder zijn.

  De beheerders kunnen gebruikers de volgende rollen op het gebied van het Beheer van de Gebruiker van beleidsconsole toewijzen. De gebruikers die deze rollen worden toegewezen voeren hun taken op het gebied van het gebruikersinterface van de documentveiligheid van beleidsconsole uit.

  **superbeheerder van de veiligheid van het Document**

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

  **de veiligheidsbeheerder van het Document**

  De gebruikers met deze rol kunnen de server van de documentveiligheid vormen, gebruikend de pagina van de Configuratie in de sectie van de documentveiligheid van beleidsconsole. Deze toestemming wordt geassocieerd met de rol, leidt Configuratie.

  >[!NOTE]
  >
  >De gebruikers met deze rol moeten de rol van de Gebruiker van de beleidsconsole ook hebben om aan beleidsconsole kunnen login en om het even welke op configuratie betrekking hebbende montages uitgeven.

  **de geplaatste beheerder van het veiligheidsbeleid van het Document**

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

  **de veiligheid van het Document beheert uitgenodigde en lokale gebruikers**

  Gebruikers met deze rol kunnen de taken uitvoeren die nodig zijn om alle uitgenodigde en lokale gebruikers op de relevante webpagina&#39;s voor documentbeveiliging te beheren. Deze machtigingen zijn gekoppeld aan de rol:

   * Uitgenodigde en lokale gebruikers beheren
   * Externe gebruikers uitnodigen
   * Webpagina&#39;s voor eindgebruikers openen

  >[!NOTE]
  >
  >De gebruikers met deze rol moeten de rol van de Gebruiker van de beleidsconsole ook hebben om aan beleidsconsole kunnen login en om het even welke op configuratie betrekking hebbende montages uitgeven.

  **de veiligheidsuitnodiging van het Document gebruiker**

  Gebruikers met deze rol kunnen gebruikers uitnodigen. Deze machtigingen zijn gekoppeld aan de rol:

   * Externe gebruikers uitnodigen
   * Webpagina&#39;s voor eindgebruikers openen

  **eind van de veiligheid van het Document gebruiker**

  Gebruikers met deze rol hebben toegang tot webpagina&#39;s van eindgebruikers met documentbeveiliging. Deze rol kan ook aan beheerders worden toegewezen om beheerders toe te staan om beleid tot stand te brengen gebruikend de eindgebruikerpagina&#39;s. Deze toestemming wordt geassocieerd met de rol de eindgebruikerWeb-pagina&#39;s van de Toegang.

* De gebruikers binnen de organisatie die geldige rekeningen van de documentveiligheid hebben creëren hun eigen beleid, gebruiken beleid om documenten te beschermen, hun beleid-beschermde documenten te volgen en te beheren, en gebeurtenissen te controleren die met hun documenten verwant zijn.
* Coördinatoren van beleidssets beheren documenten, gebeurtenissen weergeven en andere beleidssetcoördinatoren beheren (op basis van hun machtigingen). Beheerders wijzen gebruikers aan als beleidssetcoördinatoren voor bepaalde beleidssets.
* Gebruikers die zich buiten uw organisatie bevinden (bijvoorbeeld een zakelijke partner), kunnen documenten met een beleid beveiligd als ze zich in de map met documentbeveiliging bevinden, als de beheerder een account voor hen maakt of als ze zich met documentbeveiliging registreren via een geautomatiseerd e-mailuitnodigingsproces. Afhankelijk van hoe de beheerder de toegangsmontages toelaat, kunnen de uitgenodigde gebruikers ook toestemming hebben om beleid op documenten toe te passen, om, hun beleid tot stand te brengen te wijzigen en te schrappen, en andere externe gebruikers uit te nodigen om hun beleid-beschermde documenten te gebruiken.
* Ontwikkelaars gebruiken de SDK van AEM Forms om aangepaste toepassingen te integreren met documentbeveiliging.

De beheerders van de veiligheid van het document kunnen douanerollen tot stand brengen door de volgende toestemmingen in Gebruikersbeheer te gebruiken:

* Configuratie van documentbeveiliging beheren
* Beveiliging van documenten Uitgenodigde en lokale gebruikers beheren
* Beleidssets voor documentbeveiliging beheren
* Beleidssets voor documentbeveiliging beheren
* Gebeurtenissen weergaveserver voor documentbeveiliging
* Beleidseigenaar wijzigen van documentbeveiliging

## Beleid en documenten die door beleid worden beschermd {#policies-and-policy-protected-documents}

A *beleid* bepaalt een reeks vertrouwelijkheidsmontages en gebruikers die tot een document kunnen toegang hebben waarop het beleid wordt toegepast. Met een beleid kunnen ook de machtigingen voor een document dynamisch worden gewijzigd. Het geeft de persoon die het document verzekert toestemming om de vertrouwelijkheidsmontages te veranderen om toegang tot het document in te trekken of het beleid te veranderen.

Beleidsbescherming kan worden toegepast op een PDF-document met Adobe Acrobat® Pro en Acrobat Standard. Beleidsbeveiliging kan worden toegepast op andere bestandstypen, zoals Microsoft® Word-, Excel- en PowerPoint-bestanden, door de clienttoepassing te gebruiken terwijl de juiste Acrobat Reader DC Extensions is geïnstalleerd.

### Hoe beleid werkt {#how-policies-work}

Het beleid bevat informatie over de geautoriseerde gebruikers en de vertrouwelijkheidsinstellingen die op documenten moeten worden toegepast. De gebruikers kunnen om het even wie in uw organisatie zijn, en mensen die aan uw organisatie extern zijn die een rekening hebben. Als de beheerder de functie voor gebruikersuitnodigingen inschakelt, is het zelfs mogelijk om nieuwe gebruikers aan het beleid toe te voegen en wordt daarom een e-mailproces voor een registratieuitnodiging gestart.

De vertrouwelijkheidsinstellingen in een beleid bepalen hoe de ontvangers het document kunnen gebruiken. U kunt bijvoorbeeld opgeven of ontvangers tekst kunnen afdrukken of kopiëren, wijzigingen kunnen aanbrengen of handtekeningen en opmerkingen kunnen toevoegen aan beveiligde documenten. In hetzelfde beleid kunnen ook verschillende instellingen voor vertrouwelijkheid voor specifieke gebruikers worden opgegeven.

>[!NOTE]
>
>De instellingen voor vertrouwelijkheid die via een beleid worden toegepast, overschrijven instellingen die mogelijk op een PDF-document in Acrobat zijn toegepast met behulp van de beveiligingsopties voor wachtwoorden of certificaten. (Zie Acrobat Help voor meer informatie.)

Gebruikers en beheerders maken beleid via de webpagina&#39;s voor documentbeveiliging. Er kan slechts één beleid tegelijk worden toegepast op een document. U kunt een beleid toepassen door een van de volgende methoden te gebruiken:

* Open het document in Acrobat of een andere clienttoepassing en selecteer een beleid om het document te beveiligen.
* Een document verzenden als e-mailbijlage in Microsoft® Outlook. In dit geval kunt u een beleid selecteren in een lijst met beleidsregels. U kunt ook een automatisch gegenereerd beleid selecteren dat door Acrobat wordt gemaakt met een standaardset met instellingen voor vertrouwelijkheid om het document alleen voor de ontvangers van e-mailberichten te beschermen.

Een beleid kan uit een document worden verwijderd door de cliënttoepassing te gebruiken.

![&#x200B; rm_psonline_policy &#x200B;](assets/rm_psonline_policy.png)

De stappen in het diagram zijn als volgt:

1. De eigenaar van het document beveiligt het document vanaf een ondersteunde clienttoepassing met een beleid dat onlinegebruik toestaat.
1. Met documentbeveiliging maakt u een documentlicentie en documentsleutels en versleutelt u het beleid. De documentlicentie, het gecodeerde beleid en de documentsleutel worden geretourneerd aan de clienttoepassing.
1. Het document wordt versleuteld met de documentsleutel en de documentsleutel wordt verwijderd. Het document bevat nu de licentie en het beleid. Deze taken worden uitgevoerd in de ondersteunde clienttoepassing.

Wanneer u een beleid op een document toepast, wordt de informatie in het, met inbegrip van om het even welke bevat dossiers (tekst, audio, of video) in de documenten van PDF, beschermd door de vertrouwelijkheidsmontages die in het beleid worden gespecificeerd. Documentbeveiliging genereert een licentie- en versleutelingsinformatie die vervolgens in het document wordt ingesloten. Wanneer u het document verspreidt, kan de documentbeveiliging de ontvangers verifiëren die proberen het document te openen en toegang autoriseren volgens de rechten die in het beleid zijn opgegeven.

Als offlinegebruik is ingeschakeld, kunnen ontvangers met een beleid beveiligde documenten ook offline gebruiken (zonder actieve internet- of netwerkverbinding) gedurende de periode die in het beleid is opgegeven.

### Hoe beleidsbeveiligde documenten werken {#how-policy-protected-documents-work}

Als u met een beleid beveiligde documenten wilt openen en gebruiken, moet het beleid uw naam als ontvanger bevatten en moet u over een geldige account voor documentbeveiliging beschikken. Voor PDF-documenten hebt u Acrobat of Adobe Reader® nodig. Voor andere bestandstypen hebt u de juiste toepassing nodig voor het bestand waarop de Acrobat Reader DC Extensions is geïnstalleerd.

Als u een document opent dat met een beleid is beveiligd, maakt Acrobat, Adobe Reader of Acrobat Reader DC Extensions verbinding met documentbeveiliging om u te verifiëren. Vervolgens kunt u doorgaan met het aanmelden. Als het documentgebruik wordt gecontroleerd, verschijnt een berichtbericht. Nadat de documentveiligheid bepaalt welke documenttoestemmingen te verlenen, beheert het de decryptie van het document. Vervolgens kunt u het document gebruiken op basis van de instellingen voor vertrouwelijkheid van het beleid.

![&#x200B; rm_psopen_online &#x200B;](assets/rm_psopen_online.png)

De stappen in het diagram zijn als volgt:

1. De documentgebruiker opent het document in een gesteunde cliënttoepassing en verklaart met de server voor authentiek. De document-id wordt naar de documentbeveiligingsserver verzonden.
1. Met Documentbeveiliging worden de gebruikers geverifieerd, wordt gecontroleerd of er toestemming is gegeven en wordt een voucher gemaakt. De voucher (die de documentsleutel en de toestemmingen bevat) wordt teruggekeerd aan de cliënttoepassing.
1. Het document wordt met de documentsleutel ontsleuteld en de documentsleutel wordt genegeerd. Het document kan vervolgens worden gebruikt met inachtneming van de vertrouwelijkheidsinstellingen van het beleid. Deze taken worden uitgevoerd in de ondersteunde clienttoepassing.

U kunt een document onder de volgende omstandigheden blijven gebruiken:

* Voor onbepaalde tijd of voor de geldigheidsperiode die in het beleid wordt gespecificeerd
* Totdat de beheerder of de persoon die het beleid toepaste, de toegang tot het document herroept of het beleid wijzigt

U kunt documenten die met een beleid zijn beveiligd ook offline gebruiken (zonder internet- of netwerkverbinding) als het beleid offline toegang toestaat. Meld u eerst aan bij de documentbeveiliging om het document te synchroniseren. Vervolgens kunt u het document gebruiken tijdens de offline leaseperiode die in het beleid is opgegeven.

Wanneer de offline leaseperiode afloopt, synchroniseert u het document opnieuw met documentbeveiliging door online te gaan en een document te openen dat met een beleid is beveiligd of door een opdracht te gebruiken in de clienttoepassing. Zie *Hulp van Acrobat* of de aangewezen *Hulp van de Uitbreidingen van Acrobat Reader DC* voor details.

Als u een kopie van een document dat met een beleid is beveiligd opslaat met de opdracht Opslaan of Opslaan als, wordt het beleid automatisch toegepast en afgedwongen voor het nieuwe document. Gebeurtenissen zoals pogingen om het nieuwe document te openen, worden ook gecontroleerd en geregistreerd voor het oorspronkelijke document.

## Beleidssets {#policy-sets}

*de reeksen van het Beleid* worden gebruikt om een reeks beleid te groeperen dat een gemeenschappelijk bedrijfsdoel heeft. Deze beleidsreeksen worden dan ter beschikking gesteld aan een ondergroep van gebruikers in het systeem.

Elke beleidsreeks kan één of meerdere bijbehorende beleidssetcoördinatoren hebben. De coördinator van de beleidsreeks is een beheerder of een gebruiker die meer toestemmingen heeft. De *coördinator van de beleidsreeks* is typisch een specialist in de organisatie die het beleid in een bepaalde beleidsreeks het best kan schrijven.

Beleidssetcoördinatoren kunnen de volgende taken uitvoeren:

* Beleid maken
* Beleid in de beleidsset bewerken en verwijderen
* Beleidssetinstellingen bewerken
* Coördinatoren voor beleidssets toevoegen en verwijderen
* Beleid en documentgebeurtenissen weergeven voor beleid of document binnen de beleidsset
* Toegang tot documenten intrekken
* Van beleid wisselen voor het document.

>[!NOTE]
>
>U kunt maximaal 1000 namen van beleidssets ophalen uit de database met behulp van `getAllPolicysetnames()` API.

De reeksen van het beleid worden gecreeerd en in de Web-pagina&#39;s van het beleid van de documentveiligheid geschrapt door beheerders en beleidsvastgestelde coördinatoren die toestemming hebben om dit te doen.

De reeksen van het beleid worden ter beschikking gesteld aan een beperkt aantal gebruikers door te specificeren welke gebruikers of groepen binnen een domein het beleid van de beleidsreeks kunnen gebruiken om documenten te beschermen.

Wanneer de documentveiligheid wordt geïnstalleerd, wordt een standaardbeleidsreeks gecreeerd genoemd *Globale Reeks van het Beleid*. De beheerder die de software heeft geïnstalleerd, beheert deze beleidsset.

## Aanbevolen procedures {#best-practices}

Het beleid is herbruikbare reeksen toestemmingen en gebruikersgroepen die op diverse documenten kunnen worden toegepast. Voor de beveiligde documenten. Met dit beleid zorgt u ervoor dat alleen geautoriseerde gebruikers de toegestane functies kunnen gebruiken. Het aantal beleid en beleidsreeksen zullen naar verwachting met een toename in verschillende gebruikersrollen en documenten binnen een afdeling groeien. Om beleid tot stand te brengen en te beheren, zijn sommige overwegingen en beste praktijken:

* **creeer herbruikbaar beleid:** de Adobe adviseert het hergebruiken van beleid over diverse documenten. Het helpt het aantal beleidsregels tot een minimum te beperken, biedt optimale prestaties en maakt het eenvoudiger om het beleid te beheren. Een herbruikbaar beleid maken:

1. Identificeer en bepaal de vereisten van de toegangscontrole op afdelingen en organisatieniveau.

1. Maak gebruikersgroepen en voeg gebruikers toe aan deze groepen.

1. Maak een beleidsset.

1. Open de beleidsset en maak een beleid. Voeg gebruikersgroepen toe en plaats vertrouwelijkheid (toegang-controle) montages voor het beleid.

Voeg gebruikersgroepen aan beleid in plaats van individuele gebruikers toe. Het maakt het gemakkelijker om beleid op vele gebruikers te beheren en toe te passen.

* **creeer de Reeksen van het Beleid van de Douane:** Een beleidsreeks combineert veelvoudige beleid in een handelbare entiteit. Creeer de reeksen van het douanebeleid voor uw organisatie of afdeling, gebruik hen om verwant beleid te groeperen, en hen ter beschikking te stellen van een ondergroep van gebruikers in het systeem.

  Het gebruiken van beleidsreeksen maakt het gemakkelijker om verwant beleid aan specifieke gebruikers in een organisatie of een afdeling toe te wijzen en te beheren. Zo kunnen afzonderlijke beleidssets voor de afdeling financiën en personeel u helpen bij het eenvoudig beheren en toepassen van gerelateerde beleidslijnen op documenten die zijn aangewezen voor de overeenkomstige afdelingen.

* **Gebruik een externe auteur om toestemmingen dynamisch toe te passen:** u kunt [&#x200B; externe auteur &#x200B;](https://help.adobe.com/en_US/livecycle/11.0/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-6f26.2.html) gebruiken om toestemmingen te evalueren en dynamisch toe te passen die op externe voorwaarde worden gebaseerd. Wanneer de toestemmingen dynamisch, gebaseerd op externe voorwaarde worden geëvalueerd, dan kunt u:

   * Zorg voor gecentraliseerde toegangscontrole voor documenten in uw organisatie.

   * De toegang tot beleid-beschermde documenten door dynamisch te bepalen of een gebruiker tot een beleid-beschermd document kan toegang hebben. Hiermee wordt bijvoorbeeld dynamisch bepaald of een gebruiker een document kan afdrukken dat met een beleid is beveiligd.

   * Gebruik een toegangsbeheermechanisme dat uw inhoudsbeheersysteem, naast het standaardproces van de beleidsevaluatie gebruikt. Bijvoorbeeld, wanneer de dienst bepaalt of een gebruiker een beleid-beschermd document kan drukken, kan het het standaardproces van de beleidsevaluatie gebruiken. En, kan het het toegangsbeheermechanisme ook gebruiken dat uw inhoudsbeheersysteem gebruikt.

  Hoewel het mogelijk is om het de beleidsevaluatieproces van de Veiligheid van het Document met een externe toestemmingsmanager volledig te vervangen, adviseert men dat u een externe vergunningsmanager met het proces van de beleidsevaluatie gebruikt. Hierdoor kan de toegang tot documenten worden beheerd met hetzelfde besturingsmechanisme als het contentbeheersysteem. Wanneer de documentbeveiligingsservice bijvoorbeeld bepaalt of een gebruiker een document kan afdrukken dat met een beleid is beveiligd, wordt het standaardproces voor beleidsevaluatie gebruikt. Het gebruikt ook het toegangsbeheermechanisme dat uw inhoudsbeheersysteem gebruikt. Voor meer informatie, zie [&#x200B; Creërend Externe Handlers van de Vergunning &#x200B;](https://help.adobe.com/en_US/livecycle/11.0/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-6f26.2.html).

* **houd de beleidsreeksen aan een beperkt aantal:** Verscheidene factoren leiden tot de constante groei van beleid en beleidsreeksen. Enkele gangbare factoren zijn:

   * De verhoging van gebruikersrollen, afdelingen, en documenten binnen een organisatie over een periode.
   * De afdelingen van een organisatie werken afzonderlijk en houden een strenge controle op het departementspecifieke beleid. Het leidt tot identieke beleidsvormen binnen een organisatie.

  Adobe beveelt aan het aantal beleidslijnen en beleidsreeksen tot een minimum te beperken. Het helpt beleid en beleidsreeksen gemakkelijk te beheren en betere prestaties te verstrekken. Het aantal tot een minimum beperken:

   * Maak herbruikbaar beleid. Dit beleid kan over veelvoudige afdelingen worden gedeeld.
   * Overweeg het creëren van organisatie-brede beleidsreeksen, als sommige beleid op veelvoudige afdelingen in plaats van een individueel beleid van toepassing is dat voor elke afdeling wordt geplaatst.
   * Groepsgerelateerd beleid in een beleidsset. Maak geen aparte beleidsset voor elk beleid.
   * Gebruik een externe autorisator om gebruikerstoestemmingen dynamisch te controleren.

  >[!NOTE]
  >
  >U kunt [&#x200B; getAllPolicy gebruiken () &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/programlc/javadoc/com/adobe/livecycle/rightsmanagement/client/PolicyManager.html) API om een maximum van 1000 namen van beleidsreeksen terug te winnen. Intern, wint API een maximum van 1000 beleid terug waarvoor de API aanroeper de toestemming van de documentuitgever heeft en creeert en keert dan een lijst van unieke vastgestelde namen verbonden aan teruggewonnen beleid aan u terug. Wanneer de API bijvoorbeeld 1000 beleidsregels ophaalt en het opgehaalde beleid is gekoppeld aan 200 beleidssets in totaal, retourneert de API slechts 200 beleidssetnamen.
