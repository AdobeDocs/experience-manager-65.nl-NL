---
title: Integreren met ExactTarget
seo-title: Integreren met ExactTarget
description: Leer hoe u AEM kunt integreren met ExactTarget.
seo-description: Leer hoe u AEM kunt integreren met ExactTarget.
uuid: a53bbdaa-98f7-4035-b842-aa7ea63712ca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 5b2f624d-e5b8-4484-a773-7784ebce58bd
docset: aem65
translation-type: tm+mt
source-git-commit: 0eda6ee61acf737abc91d1e5df731e719663b3f2
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Integreren met ExactTarget{#integrating-with-exacttarget}

Door AEM te integreren met Exact Target kunt u in AEM gemaakte e-mailberichten beheren en verzenden via Exact Target. U kunt hiermee ook de beheerfuncties voor leads van Exact Target gebruiken via AEM formulieren op AEM pagina&#39;s.

De integratie biedt u de volgende functies:

* De capaciteit om E-mail in AEM tot stand te brengen en hen te publiceren aan Exact Doel voor distributie.
* De capaciteit om actie van een AEM vorm te plaatsen om een Exact abonnee van het Doel tot stand te brengen.

Nadat ExactTarget is geconfigureerd, kunt u nieuwsbrieven of e-mails naar ExactTarget publiceren. Zie [Nieuwsbrieven publiceren naar een e-mailservice](/help/sites-authoring/personalization.md).

## Een ExactTarget-configuratie {#creating-an-exacttarget-configuration} maken

De configuraties ExactTarget kunnen via de Diensten van de Wolk of Hulpmiddelen worden toegevoegd. Beide methoden worden in deze sectie beschreven.

### ExactTarget configureren via Cloudservices {#configuring-exacttarget-via-cloudservices}

Om een configuratie ExactTarget in Cloud Services te creëren:

1. Voor de welkomstpagina, klik **Cloud Services**. (Of directe toegang bij `https://<hostname>:<port>/etc/cloudservices.html`.)
1. Klik **ExactTarget** en dan **Configure**. Het ExactTarget configuratievenster opent.

   ![chlimage_1-19](assets/chlimage_1-19.png)

1. Voer een titel en eventueel een naam in en klik op **Maken**. Het **ExactTarget Settings** configuratievenster wordt geopend.

   ![chlimage_1](assets/chlimage_1.jpeg)

1. Voer de gebruikersnaam en het wachtwoord in en selecteer een API-eindpunt (bijvoorbeeld **https://webservice.exacttarget.com/Service.asmx**).
1. Klik **Verbinding maken met ExactTarget.** Wanneer de verbinding tot stand is gebracht, wordt het dialoogvenster geslaagd. Klik **OK** om het venster te sluiten.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Selecteer een account, indien beschikbaar. De account is bestemd voor Enterprise 2.0-klanten. Klik **OK**.

   ExactTarget is gevormd. U kunt de configuratie uitgeven door **Edit** te klikken. U kunt naar ExactTarget gaan door **Ga naar ExactTarget** te klikken.

1. AEM beschikt nu over een functie voor gegevensextensie. U kunt ExactTarget-gegevensextensiekolommen importeren. Dit kan worden gevormd door &quot;+&quot;teken te klikken dat behalve met succes tot stand gebrachte configuratie ExactTarget verschijnt. U kunt een van de bestaande gegevensextensies selecteren in de vervolgkeuzelijst. Raadpleeg [ExactTarget-documentatie](https://help.exacttarget.com/en/documentation/exacttarget/subscribers/data_extensions_and_data_relationships) voor meer informatie over het configureren van gegevensextensies.

   De ingevoerde kolommen van de gegevensuitbreiding kunnen later door **Tekst en Personalisatie** worden gebruikt component.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

### ExactTarget configureren via Tools {#configuring-exacttarget-via-tools}

Om een configuratie ExactTarget in Hulpmiddelen tot stand te brengen:

1. Voor de welkomstpagina, klik **Hulpmiddelen**. Of navigeer daar rechtstreeks door naar `https://<hostname>:<port>/misadmin#/etc` te gaan.
1. Selecteer **Extra**, dan **Cloud Services Configuraties,** dan **ExactTarget**.
1. Klik **Nieuw** om het venster **Create Page **window te openen.

   ![chlimage_1-34](assets/chlimage_1-3.jpeg)

1. Voer de **Titel** en eventueel de **Naam** in en klik op **Maken**.
1. Ga de configuratieinformatie in zoals die in stap 4 in de vorige procedure wordt geschetst. Volg die procedure om het vormen ExactTarget te beëindigen.

### Meerdere configuraties toevoegen {#adding-multiple-configurations}

Meerdere configuraties toevoegen:

1. Voor de welkomstpagina, klik **Cloud Services** en klik **ExactTarget**. Klik op **De knoop van Configuraties** tonen die verschijnt als één of meerdere configuraties ExactTarget beschikbaar zijn. Alle beschikbare configuraties worden vermeld.
1. Klik **+** teken naast Beschikbare configuraties. Hiermee opent u het venster **Configuraties maken**. Volg de vorige configuratieprocedure om een nieuwe configuratie tot stand te brengen.