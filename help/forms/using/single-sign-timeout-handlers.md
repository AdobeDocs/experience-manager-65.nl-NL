---
title: Single Sign On en timeout handlers
seo-title: Single Sign On en timeout handlers
description: Hoe kan ik de time-outwaarde voor de sessie instellen voor de werkruimte van AEM Forms.
seo-description: Hoe kan ik de time-outwaarde voor de sessie instellen voor de werkruimte van AEM Forms.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Single Sign On en timeout handlers {#single-sign-on-and-timeout-handlers}

De werkruimte van AEM-formulieren is SSO ingeschakeld. Als een gebruiker zich heeft aangemeld bij een toepassing met AEM-formulieren, zoals Forms Manager of de gebruikersinterface van PDF Generator, en in dezelfde browsersessie toegang heeft tot de werkruimte van AEM-formulieren, wordt de gebruiker aangemeld bij de werkruimte van AEM-formulieren en andersom.

## Tijdslimiet van server afhandelen in AEM Forms-werkruimte {#handling-server-timeout-in-nbsp-aem-forms-workspace}

De onderbreking van de zitting voor een gebruiker kan in de Console van het Beleid worden gevormd.

Als u de time-out wilt instellen, meldt u zich aan `https://'[server]:[port]'/adminui`en gaat u naar **Instellingen > Gebruikersbeheer > Configuratie > Geavanceerde systeemkenmerken** configureren en geeft u de gewenste instellingen op.

In de werkruimte van AEM-formulieren wordt de time-out verwerkt als:

* De duur van de zitting voor een gebruiker is beschikbaar in antwoord op `initialize` vraag die gebruikerszitting initialiseert.
* Een pop-updialoogvenster geeft een melding aan de gebruiker dat de sessie bijna verlopen is, 15 seconden voor de sessievervaldatum.

In dit pop-updialoogvenster:

* Klik op OK om de gebruikerssessie te beëindigen.
* Klik op Annuleren om de gebruikerssessie opnieuw te initialiseren.

>[!NOTE]
>
>Als er geen actie wordt ondernomen, wordt de gebruiker automatisch drie seconden voor het verstrijken van de sessie afgemeld bij de werkruimte van AEM Forms.

**[Contact opnemen met ondersteuning](https://www.adobe.com/account/sign-in.supportportal.html)**
