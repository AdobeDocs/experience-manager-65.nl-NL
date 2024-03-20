---
title: Single Sign On en timeout handlers
description: Hoe kan ik de time-outwaarde voor sessies instellen voor de AEM Forms-werkruimte.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 4f824d80-f3f8-4010-9583-5a9ab1151a7b
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Single Sign On en timeout handlers {#single-sign-on-and-timeout-handlers}

AEM Forms-werkruimte is SSO ingeschakeld. Als een gebruiker zich heeft aangemeld bij een AEM Forms-toepassing, zoals Forms Manager of de gebruikersinterface van PDF Generatoren, en AEM Forms-werkruimte binnen dezelfde browsersessie benadert, wordt de gebruiker aangemeld bij de werkruimte van AEM Forms en omgekeerd.

## Time-out van server afhandelen in AEM Forms-werkruimte {#handling-server-timeout-in-nbsp-aem-forms-workspace}

De onderbreking van de zitting voor een gebruiker kan in de Console van het Beleid worden gevormd.

Meld u aan om de time-out in te stellen `https://'[server]:[port]'/adminui`, navigeer naar **Instellingen > Gebruikersbeheer > Configuratie > Geavanceerde systeemkenmerken configureren** en stelt de gewenste instellingen in.

In de AEM Forms-werkruimte wordt de time-out verwerkt als:

* De sessieduur voor een gebruiker is beschikbaar als reactie op `initialize` vraag die gebruikerszitting initialiseert.
* Een pop-updialoogvenster geeft een melding aan de gebruiker dat de sessie bijna verlopen is, 15 seconden voor de sessievervaldatum.

In dit pop-updialoogvenster:

* Klik op OK om de gebruikerssessie te beëindigen.
* Klik op Annuleren om de gebruikerssessie opnieuw te initialiseren.

>[!NOTE]
>
>Als geen actie wordt ondernomen, wordt de gebruiker automatisch geregistreerd uit de werkruimte van AEM Forms drie seconden vóór de zittingsafloop.
