---
title: SAML-serviceleverinstellingen configureren
seo-title: Configure SAML service provider settings
description: U kunt de instellingen van SAML-serviceproviders zodanig configureren dat gebruikers zich kunnen aanmelden en zich kunnen verifiëren bij AEM formulieren via een opgegeven externe identiteitsprovider (IDP).
seo-description: You can configure SAML service provider settings to allow users to login and authenticate to AEM forms via a specified third-party identity provider (IDP).
uuid: 14c706ad-8b1c-4c03-9cd4-97424f2162bc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 1169d0d1-cbfb-486b-acca-9b9de3d410dc
exl-id: dd302cfb-eae1-4189-aa7b-9f2533ebd164
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---

# SAML-serviceleverinstellingen configureren{#configure-saml-service-provider-settings}

SAML (Security Assertion Markup Language) is een van de opties die u kunt selecteren wanneer u een machtiging voor een onderneming of hybride domein configureert. SAML wordt hoofdzakelijk gebruikt om SSO over veelvoudige domeinen te steunen. Als SAML is geconfigureerd als uw verificatieprovider, kunnen gebruikers zich aanmelden en zich via een opgegeven externe identiteitsprovider (IDP) verifiëren bij AEM formulieren.

Voor een uitleg van SAML, zie [SAML (Security Assertion Markup Language) V2.0 - Technisch overzicht](https://www.oasis-open.org/committees/download.php/20645/sstc-saml-tech-overview-2%200-draft-10.pdf).

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > SAML Service Provider Settings.
1. Typ in het vak Id van Service Provider-entiteit een unieke id die u wilt gebruiken als id voor de implementatie van de AEM-provider. U geeft deze unieke id ook op wanneer u uw IDP configureert (bijvoorbeeld `um.lc.com`.) U kunt ook de URL gebruiken die wordt gebruikt om toegang te krijgen tot AEM formulieren (bijvoorbeeld `https://AEMformsserver`).
1. Typ in het vak Basis-URL van serviceprovider de basis-URL voor uw formulierserver (bijvoorbeeld `https://AEMformsserver:8080`).
1. (Optioneel) Als u wilt dat AEM formulieren ondertekende verificatieaanvragen naar de IDP kunnen verzenden, voert u de volgende taken uit:

   * Gebruik Betrouwbaarheidsbeheer om een referentie in de PKCS #12-indeling te importeren, waarbij Referentie voor documenthandtekening is geselecteerd als Betrouwbaarheidswinkeltype. (Zie [Lokale referenties beheren](/help/forms/using/admin-help/local-credentials.md#managing-local-credentials).)
   * Selecteer in de lijst Referentietoets Service Provider de alias die u aan de referentie in Trust Store hebt toegewezen.
   * Klik op Exporteren om de URL-inhoud op te slaan in een bestand en importeer dat bestand vervolgens in uw IDP.

1. (Facultatief) in de lijst van het Beleid van de Naam van de Dienstverlener identiteitskaart, selecteer het naamformaat dat IDP gebruikt om de gebruiker in een bevestiging van SAML te identificeren. De opties zijn Niet opgegeven, E-mail, en Gekwalificeerde Naam van het Domein van Vensters.

   >[!NOTE]
   >
   >Naamnotaties zijn niet hoofdlettergevoelig.

1. (Optioneel) Selecteer Verificatieverzoek voor lokale gebruikers inschakelen. Als deze optie is geselecteerd, zien gebruikers twee koppelingen:

   * een koppeling naar de aanmeldingspagina van de externe SAML-identiteitsprovider, waar gebruikers die tot een Enterprise-domein behoren, zich kunnen verifiëren.
   * een koppeling naar de aanmeldingspagina voor AEM formulieren, waar gebruikers die tot een lokaal domein behoren, zich kunnen verifiëren.

   Als deze optie niet is geselecteerd, worden gebruikers rechtstreeks doorgestuurd naar de aanmeldingspagina van de externe SAML-identiteitsprovider, waar gebruikers die tot een Enterprise-domein behoren, zich kunnen verifiëren.

1. (Optioneel) Selecteer Artefactbinding inschakelen om ondersteuning voor artefactbinding in te schakelen. Door gebrek, wordt de band van de POST gebruikt met SAML. Maar als u de Binding van Artefact hebt gevormd, selecteer deze optie. Als deze optie is geselecteerd, wordt de feitelijke gebruikersbewering niet doorgegeven via de Browser-aanvraag. In plaats daarvan, wordt een wijzer tot de bewering overgegaan en de bewering wordt teruggewonnen gebruikend een de dienstvraag van het achterste deel van het Web.
1. (Optioneel) Selecteer Enable Re-Direct Binding om SAML-bindingen te ondersteunen die omleidingen gebruiken.
1. (Optioneel) Geef in Aangepaste eigenschappen aanvullende eigenschappen op. De extra eigenschappen zijn name=value paren die door nieuwe lijnen worden gescheiden.

   * U kunt AEM vormen om een bevestiging van SAML voor een geldigheidsperiode uit te geven die de geldigheidsperiode van een derdebewering aanpast. Als u de SAML-assertietime-out van derden wilt respecteren, voegt u de volgende regel toe in Aangepaste eigenschappen:

     `saml.sp.honour.idp.assertion.expiry=true`

   * Voeg het volgende douanebezit voor het gebruiken van RelayState toe om URL te bepalen waar de gebruiker na succesvolle authentificatie opnieuw zal worden gericht.

     `saml.sp.use.relaystate=true`

   * Voeg het volgende douanebezit toe om URL voor de Pagina&#39;s van de Server van douaneJava (JSP) te vormen, die wordt gebruikt om de geregistreerde lijst van identiteitsleveranciers terug te geven. Als u geen aangepaste webtoepassing hebt geïmplementeerd, wordt de standaardpagina Gebruikersbeheer gebruikt om de lijst weer te geven.

   `saml.sp.discovery.url=/custom/custom.jsp`

1. Klik op Opslaan.
