---
title: Integreren met ExactTarget
description: Leer hoe u Adobe Experience Manager kunt integreren met ExactTarget.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 4183fe78-5055-4b77-8a54-55666e86a04e
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Integreren met ExactTarget{#integrating-with-exacttarget}

Door Adobe Experience Manager (AEM) te integreren met Exact Target kunt u in AEM gemaakte e-mails beheren en verzenden via Exact Target. U kunt hiermee ook de beheerfuncties voor leads van Exact Target gebruiken als AEM formulieren op AEM pagina&#39;s.

De integratie biedt u de volgende functies:

* De capaciteit om E-mail in AEM tot stand te brengen en hen te publiceren aan Exact Doel voor distributie.
* De capaciteit om actie van een AEM vorm te plaatsen om een Exact abonnee van het Doel tot stand te brengen.

Nadat ExactTarget is geconfigureerd, kunt u nieuwsbrieven of e-mails naar ExactTarget publiceren. Zie [Nieuwsbrieven publiceren naar een e-mailservice](/help/sites-authoring/personalization.md).

## Een ExactTarget-configuratie maken {#creating-an-exacttarget-configuration}

De configuraties ExactTarget kunnen door middel van de Diensten van de Wolk of Hulpmiddelen worden toegevoegd. Beide methoden worden in deze sectie beschreven.

### Het vormen ExactTarget door middel van Cloudservices {#configuring-exacttarget-via-cloudservices}

Om een configuratie ExactTarget in Cloud Servicen tot stand te brengen:

1. Klik op de welkomstpagina op **Cloud Servicen**. (Of rechtstreeks toegang tot `https://<hostname>:<port>/etc/cloudservices.html`.)
1. Klikken **ExactTarget** en vervolgens **Configureren**. Het ExactTarget configuratievenster opent.

   ![chlimage_1-19](assets/chlimage_1-19.png)

1. Voer een titel en eventueel een naam in en klik op **Maken**. De **ExactTarget-instellingen** configuratievenster wordt geopend.

   ![chlimage_1](assets/chlimage_1.jpeg)

1. Voer de gebruikersnaam en het wachtwoord in en selecteer een API-eindpunt (bijvoorbeeld **https://webservice.exacttarget.com/Service.asmx**).
1. Klikken **Verbind met ExactTarget.** Als de verbinding tot stand is gebracht, wordt het dialoogvenster geslaagd. vak klikken **OK** om het venster te sluiten.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Selecteer een account, indien beschikbaar. De account is bestemd voor Enterprise 2.0-klanten. Klikken **OK**.

   ExactTarget is gevormd. U kunt de configuratie bewerken door op **Bewerken**. U kunt naar ExactTarget gaan door te klikken **Ga naar ExactTarget**.

1. AEM beschikt nu over een functie voor gegevensextensie. U kunt ExactTarget-gegevensextensiekolommen importeren. Het kan worden gevormd door &quot;+&quot;teken te klikken dat behalve met succes tot stand gebrachte configuratie ExactTarget verschijnt. U kunt een van de bestaande gegevensextensies selecteren in de vervolgkeuzelijst. Voor meer informatie over hoe te om gegevensuitbreidingen te vormen, zie [ExactTarget-documentatie](https://help.salesforce.com/s/articleView?id=sf.mc_es_data_extension_data_relationships_classic.htm&amp;type=5).

   De ingevoerde kolommen van de gegevensuitbreiding kunnen later door **Tekst en personalisatie** component.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

### ExactTarget configureren met behulp van gereedschappen {#configuring-exacttarget-via-tools}

Om een configuratie ExactTarget in Hulpmiddelen tot stand te brengen:

1. Klik op de welkomstpagina op **Gereedschappen**. Of navigeer daar rechtstreeks door naar `https://<hostname>:<port>/misadmin#/etc`.
1. Selecteren **Gereedschappen** vervolgens **configuraties van Cloud Servicen,** dan **ExactTarget**.
1. Klikken **Nieuw** om het venster **Pagina maken **te openen.

   ![chlimage_1-34](assets/chlimage_1-3.jpeg)

1. Voer de **Titel** en eventueel de **Naam** en klik op **Maken**.
1. Voer de configuratiegegevens in zoals beschreven in stap 4 van de vorige procedure. Volg die procedure om klaar te zijn met het vormen ExactTarget.

### Meerdere configuraties toevoegen {#adding-multiple-configurations}

Meerdere configuraties toevoegen:

1. Klik op de welkomstpagina op **Cloud Servicen** en klik op **ExactTarget**. Klikken **Configuraties tonen** die verschijnt als één of meerdere configuraties ExactTarget beschikbaar zijn. Alle beschikbare configuraties worden vermeld.
1. Klik op de knop **+** ondertekenen naast Beschikbare configuraties. Hierdoor wordt het **Configuraties maken** venster. Volg de vorige configuratieprocedure om een configuratie tot stand te brengen.
