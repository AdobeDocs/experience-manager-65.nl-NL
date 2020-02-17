---
title: Gebruikersbeheer
seo-title: Gebruikersbeheer
description: Met gebruikersbeheer kunt u SSO inschakelen tussen AEM-formuliermodules en met Netegrity SiteMinder beveiligde toepassingen door gebruik te maken van SAML. Dit document bevat meer informatie over Gebruikersbeheer.
seo-description: Met gebruikersbeheer kunt u SSO inschakelen tussen AEM-formuliermodules en met Netegrity SiteMinder beveiligde toepassingen door gebruik te maken van SAML. Dit document bevat meer informatie over Gebruikersbeheer.
uuid: f0c8331a-d995-483d-97b7-259df53b1a1a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 10e6177a-8228-4515-aba9-bbe59bede449
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Gebruikersbeheer {#user-management}

Met Gebruikersbeheer kunt u SSO (Single Sign-On) inschakelen tussen AEM-formuliermodules en toepassingen die met Netegrity SiteMinder zijn beveiligd door SAML (Security Assertion Markup Language) te gebruiken. Wanneer SSO is geïmplementeerd, zijn de aanmeldingspagina&#39;s voor AEM-formulieren niet vereist en worden deze niet weergegeven als de gebruiker al is geverifieerd via het bedrijfsportaal.

Zie de [IBM DB2-database voor informatie over het verbeteren van de prestaties van de database en directorysynchronisatie voor DB2: Opdrachten uitvoeren voor normaal onderhoud](/help/forms/using/admin-help/ibm-db2-database-running-commands.md#ibm-db2-database-running-commands-for-regular-maintenance).

## Gebruikersbeheer configureren voor een LDAP-server met SSL-functionaliteit {#configuring-user-management-for-an-ssl-enabled-ldap-server}

Als u een LDAP-server met SSL-functionaliteit hebt, configureert u Gebruikersbeheer voor samenwerking met deze server. (Zie Gebruikersbeheer [configureren voor een LDAP-server](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server)waarvoor SSL is ingeschakeld.)

## Gebruikersrechten instellen voor gebruik met Documentbeveiliging {#setting-user-privileges-for-use-with-document-security}

Maak een beheerder die over de juiste rechten beschikt voor het maken van gebruikers en groepen. Als uw AEM-formulieromgeving documentbeveiliging bevat, verleent u een gebruiker die de beheerder van deze gebruikers is, het recht uitgenodigde en lokale gebruikers te beheren. Wijs ook de rol van de Gebruiker van de beleidsconsole toe om de gebruiker van toegang tot beleidsconsole te voorzien. (Zie Rollen [](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles)maken en configureren.)

Om gebruikers en groepen in geselecteerde domeinen tijdens de onderzoeken van de beleidsgebruiker te bekijken, moet een superbeheerder of beheerder van de beleidsreeks domeinen (die in Beheer van de Gebruiker worden gecreeerd) selecteren en toevoegen aan de zichtbare gebruiker en groepslijst voor elke gemaakte beleidsreeks.

De zichtbare gebruiker en de groepslijst zijn zichtbaar aan de coördinator van de beleidsreeks en gebruikt om te beperken welke domeinen de eindgebruiker kan doorbladeren wanneer het kiezen van gebruikers of groepen om aan beleid toe te voegen. Als deze taak niet wordt uitgevoerd, zal de coördinator van de beleidsreeks geen gebruikers of groepen vinden om aan het beleid toe te voegen. Er kunnen voor elke beleidsset meerdere beleidssetcoördinatoren zijn.

>[!NOTE]
>
> Het creëren van domeinen moet worden gedaan alvorens om het even welk beleid kan worden gecreeerd.

### Zichtbare gebruikers en groepen instellen {#set-visible-users-and-groups}

Nadat u de AEM-formulieromgeving hebt geïnstalleerd en geconfigureerd met Documentbeveiliging, stelt u alle relevante domeinen in Gebruikersbeheer in.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Beleid en klik vervolgens op het tabblad Beleidssets.
1. Selecteer Globale beleidsset en klik vervolgens op het tabblad Zichtbare gebruikers en groepen.
1. Klik op Domein(s) toevoegen en voeg desgewenst bestaande domeinen toe.
1. Navigeer naar Services > Documentbeveiliging > Configuratie > Mijn beleid en klik op het tabblad Zichtbare gebruikers en groepen.
1. Klik op Domein(s) toevoegen en voeg desgewenst bestaande domeinen toe.

## Gebruikersbeperkingen voor beheerders {#administrator-user-restrictions}

Gebruikers met bepaalde beheerdersrechten hebben uit veiligheidsoverwegingen geen toegang tot de webpagina&#39;s van eindgebruikers in Workspace. Omdat deze webpagina&#39;s buiten een firewall kunnen bestaan, kan het toestaan van taken op beheerniveau een beveiligingsrisico opleveren. Alleen gebruikers met de bevoegdheden van Workspace Administrator of Workspace User hebben toegang tot de webpagina&#39;s van de eindgebruiker.

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor de release van AEM-formulieren.

