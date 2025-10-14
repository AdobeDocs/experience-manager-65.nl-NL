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

Nadat ExactTarget is geconfigureerd, kunt u nieuwsbrieven of e-mails naar ExactTarget publiceren. Zie [&#x200B; het Publiceren Nieuwsbrieven aan een E-maildienst &#x200B;](/help/sites-authoring/personalization.md).

## Een ExactTarget-configuratie maken {#creating-an-exacttarget-configuration}

De configuraties ExactTarget kunnen door middel van de Diensten van de Wolk of Hulpmiddelen worden toegevoegd. Beide methoden worden in deze sectie beschreven.

### Het vormen ExactTarget door middel van Cloudservices {#configuring-exacttarget-via-cloudservices}

Om een configuratie ExactTarget in Cloud Servicen tot stand te brengen:

1. Voor de welkomstpagina, klik **Cloud Servicen**. (Of u hebt rechtstreeks toegang vanaf `https://<hostname>:<port>/etc/cloudservices.html`.)
1. Klik **ExactTarget** en dan **vormen**. Het ExactTarget configuratievenster opent.

   ![&#x200B; chlimage_1-19 &#x200B;](assets/chlimage_1-19.png)

1. Ga een titel en naar keuze, een naam in en klik **creëren**. Het **ExactTarget 1&rbrace; configuratievenster van Montages opent.**

   ![&#x200B; chlimage_1 &#x200B;](assets/chlimage_1.jpeg)

1. Ga gebruikersbenaming, wachtwoord in, en selecteer een API eindpunt (bijvoorbeeld, **https://webservice.exacttarget.com/Service.asmx**).
1. Klik **verbinden met ExactTarget.** Wanneer de verbinding tot stand is gebracht, wordt het dialoogvenster met succes weergegeven. de doos klikt **O.K.** om het venster weg te gaan.

   ![&#x200B; chlimage_1-1 &#x200B;](assets/chlimage_1-1.jpeg)

1. Selecteer een account, indien beschikbaar. De account is bestemd voor Enterprise 2.0-klanten. Klik **OK**.

   ExactTarget is gevormd. U kunt de configuratie uitgeven door **te klikken geeft** uit. U kunt naar ExactTarget gaan door **te klikken gaat naar ExactTarget**.

1. AEM beschikt nu over een functie voor gegevensextensie. U kunt ExactTarget-gegevensextensiekolommen importeren. Het kan worden gevormd door &quot;+&quot;teken te klikken dat behalve met succes tot stand gebrachte configuratie ExactTarget verschijnt. U kunt een van de bestaande gegevensextensies selecteren in de vervolgkeuzelijst. Voor meer informatie over hoe te om gegevensuitbreidingen te vormen, zie [&#x200B; documentatie ExactTarget &#x200B;](https://help.salesforce.com/s/articleView?id=sf.mc_es_data_extension_data_relationships_classic.htm&type=5).

   De ingevoerde kolommen van de gegevensuitbreiding kunnen later door de **Tekst en Personalization** component worden gebruikt.

   ![&#x200B; chlimage_1-2 &#x200B;](assets/chlimage_1-2.jpeg)

### ExactTarget configureren met behulp van gereedschappen {#configuring-exacttarget-via-tools}

Om een configuratie ExactTarget in Hulpmiddelen tot stand te brengen:

1. Voor de welkomstpagina, klik **Hulpmiddelen**. Of navigeer daar rechtstreeks door naar `https://<hostname>:<port>/misadmin#/etc` te gaan.
1. Selecteer **Hulpmiddelen**, toen **de Configuraties van Cloud Servicen,** toen **ExactTarget**.
1. Klik **Nieuw** om **Create Pagina &#x200B;** venster te openen.

   ![&#x200B; chlimage_1-34 &#x200B;](assets/chlimage_1-3.jpeg)

1. Ga **Titel** en naar keuze de **Naam** in, en klik **creeer**.
1. Voer de configuratiegegevens in zoals beschreven in stap 4 van de vorige procedure. Volg die procedure om klaar te zijn met het vormen ExactTarget.

### Meerdere configuraties toevoegen {#adding-multiple-configurations}

Meerdere configuraties toevoegen:

1. Voor de welkome pagina, klik **Cloud Servicen** en klik **ExactTarget**. Klik **tonen Configuraties** die verschijnen als één of meerdere configuraties ExactTarget beschikbaar zijn. Alle beschikbare configuraties worden vermeld.
1. Klik op het **+** -teken naast Beschikbare configuraties. Dit opent **leidt tot Configuraties** venster. Volg de vorige configuratieprocedure om een configuratie tot stand te brengen.
