---
title: Gebruikersbeheer
description: Met Gebruikersbeheer kunt u SSO inschakelen tussen AEM formuliermodules en met Netegrity SiteMinder beveiligde toepassingen door SAML te gebruiken. Dit document bevat meer informatie over Gebruikersbeheer.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1da1f6de-ac0d-4e0d-b8bb-956420e42699
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Gebruikersbeheer {#user-management}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Met Gebruikersbeheer kunt u SSO (Single Sign-On) inschakelen tussen AEM formuliermodules en toepassingen die door Netegrity SiteMinder zijn beveiligd door SAML (Security Assertion Markup Language) te gebruiken. Wanneer SSO is geïmplementeerd, zijn de aanmeldingspagina&#39;s voor AEM formulieren niet vereist en worden deze niet weergegeven als de gebruiker al is geverifieerd via het bedrijfsportaal.

Voor informatie over het verbeteren van het gegevensbestand en de prestaties van de foldersynchronisatie voor DB2, zie [&#x200B; IBM DB2 gegevensbestand: Lopende bevelen voor regelmatig onderhoud &#x200B;](/help/forms/using/admin-help/ibm-db2-database-running-commands.md#ibm-db2-database-running-commands-for-regular-maintenance).

## Gebruikersbeheer configureren voor een LDAP-server met SSL-functionaliteit {#configuring-user-management-for-an-ssl-enabled-ldap-server}

Als u een LDAP-server met SSL-functionaliteit hebt, configureert u Gebruikersbeheer voor samenwerking met deze server. (Zie [&#x200B; Gebruikersbeheer voor een SSL-Toegelaten server LDAP &#x200B;](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server) vormen.)

## Gebruikersrechten instellen voor gebruik met Documentbeveiliging {#setting-user-privileges-for-use-with-document-security}

Maak een beheerder die over de juiste rechten beschikt voor het maken van gebruikers en groepen. Als uw AEM formulieromgeving documentbeveiliging bevat, geeft u de gebruiker het recht uitgenodigde en lokale gebruikers te beheren. Dit is de beheerder van deze gebruikers. Wijs ook de rol van de Gebruiker van de beleidsconsole toe om de gebruiker van toegang tot beleidsconsole te voorzien. (Zie [&#x200B; Creërend en vormend rollen &#x200B;](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).)

Om gebruikers en groepen in geselecteerde domeinen tijdens de onderzoeken van de beleidsgebruiker te bekijken, moet een superbeheerder of beheerder van de beleidsreeks domeinen (die in Beheer van de Gebruiker worden gecreeerd) selecteren en toevoegen aan de zichtbare gebruiker en groepslijst voor elke gemaakte beleidsreeks.

De zichtbare gebruiker en de groepslijst zijn zichtbaar aan de coördinator van de beleidsreeks en gebruikt om te beperken welke domeinen de eindgebruiker kan doorbladeren wanneer het kiezen van gebruikers of groepen om aan beleid toe te voegen. Als deze taak niet wordt uitgevoerd, zal de coördinator van de beleidsreeks geen gebruikers of groepen vinden om aan het beleid toe te voegen. Er kunnen voor elke beleidsset meerdere beleidssetcoördinatoren zijn.

>[!NOTE]
>
>Het creëren van domeinen moet worden gedaan alvorens om het even welk beleid kan worden gecreeerd.

### Zichtbare gebruikers en groepen instellen {#set-visible-users-and-groups}

Nadat u de AEM formulieromgeving hebt geïnstalleerd en geconfigureerd met Documentbeveiliging, stelt u alle relevante domeinen in Gebruikersbeheer in.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Beleid en klik vervolgens op het tabblad Beleidssets.
1. Selecteer Globale beleidsset en klik vervolgens op het tabblad Zichtbare gebruikers en groepen.
1. Klik op Domein(s) toevoegen en voeg desgewenst bestaande domeinen toe.
1. Navigeer naar Services > Documentbeveiliging > Configuratie > Mijn beleid en klik op het tabblad Zichtbare gebruikers en groepen.
1. Klik op Domein(s) toevoegen en voeg desgewenst bestaande domeinen toe.

## Gebruikersbeperkingen voor beheerders {#administrator-user-restrictions}

Gebruikers met bepaalde beheerdersrechten hebben uit veiligheidsoverwegingen geen toegang tot de Workspace-webpagina&#39;s voor eindgebruikers. Omdat deze webpagina&#39;s buiten een firewall kunnen bestaan, kan het toestaan van taken op beheerniveau een beveiligingsrisico opleveren. Alleen gebruikers met de Workspace Administrator- of Workspace-gebruikersrechten hebben toegang tot de webpagina&#39;s van de eindgebruiker.

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor AEM formulierrelease.
