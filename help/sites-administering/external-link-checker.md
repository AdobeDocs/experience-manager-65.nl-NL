---
title: De koppelingencontrole
description: Met de koppelingencontrole kunt u zowel interne als externe koppelingen valideren en het herschrijven van koppelingen toestaan.
exl-id: 8ec4c399-b192-46fd-be77-3f49b83ce711
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '969'
ht-degree: 0%

---

# De koppelingencontrole {#the-link-checker}

Inhoudsauteurs hoeven zich niet bezig te houden met het valideren van elke koppeling die ze in hun inhoudspagina&#39;s opnemen.

De koppelingencontrole wordt automatisch uitgevoerd om inhoudsauteurs bij te staan met hun koppelingen, waaronder:

* Koppelingen valideren terwijl deze aan inhoud worden toegevoegd
* Een lijst met alle externe koppelingen in de inhoud weergeven
* Koppelingtransformaties uitvoeren

De koppelingencontrole bevat verschillende [configuratieopties](#configuring) zoals het definiëren van de interne validatie, het toestaan van het weglaten van bepaalde koppelingen of koppelingspatters voor validatie, en het herschrijven van regels voor het herschrijven van koppelingen.

De koppelingencontrole valideert beide [interne koppelingen](#internal) en [externe koppelingen.](#external)

>[!NOTE]
>
>Omdat de koppelingencontrole de koppelingen van elke inhoudspagina controleert, kan de koppelingencontrole de prestaties op grote opslagplaatsen beïnvloeden. In dergelijke gevallen kan het nodig zijn [vormen hoe vaak de looppas van de Controle van de Verbinding](#configuring) of [uitschakelen.](#disabling)

## Interne koppelingencontrole {#internal}

Interne koppelingen zijn koppelingen naar andere inhoud in uw AEM. Interne koppelingen kunnen worden toegevoegd met de padkiezer voor de RTE of met een aangepaste component. Bijvoorbeeld:

* Uw pagina `/content/wknd/us/en/adventures/ski-touring.html`
* Bevat een koppeling naar `/content/wknd/us/en/adventures/extreme-ironing.html` in een [Tekstcomponent.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

Interne koppelingen worden gevalideerd zodra de auteur van de inhoud een interne koppeling naar een pagina toevoegt. Als de koppeling ongeldig wordt:

* Deze wordt verwijderd uit de uitgever. De tekst van de koppeling blijft behouden, maar de koppeling zelf wordt verwijderd.
* Het wordt getoond als gebroken verbinding in de auteursinterface.

![Interne verbroken koppeling bij het ontwerpen van een pagina](assets/link-checker-invalid-link-internal.png)

## Controleren van externe koppeling {#external}

Externe koppelingen zijn koppelingen naar inhoud buiten de AEM opslagplaats. De externe verbindingen kunnen worden toegevoegd gebruikend RTE of gebruikend een douanecomponent. Bijvoorbeeld:

* Uw pagina `/content/wknd/us/en/adventures/ski-touring.html`
* Bevat een koppeling naar `https://bunwarmerthermalunderwear.com` in een [Tekstcomponent.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

Externe koppelingen worden gevalideerd voor syntaxis en door de beschikbaarheid ervan te controleren. Deze controle wordt asynchroon gedaan bij een configureerbare intern. Als de koppelingencontrole een externe koppeling ongeldig vindt:

* Deze wordt verwijderd uit de uitgever. De tekst van de koppeling blijft behouden, maar de koppeling zelf wordt verwijderd.
* Het wordt getoond als gebroken verbinding in de auteursinterface.

![Interne verbroken koppeling bij het ontwerpen van een pagina](assets/link-checker-invalid-link-external.png)

Bovendien [Externe koppelingencontrole](#external-link-checker) biedt een overzicht van alle externe koppelingen op uw inhoudspagina&#39;s.

### De externe koppelingencontrole gebruiken {#external-link-checker}

De External Link Checker gebruiken:

1. Gebruiken **Navigatie**, selecteert u **Gereedschappen** vervolgens **Sites**.
1. Selecteren **Externe koppelingencontrole** en er wordt een lijst met alle externe koppelingen weergegeven.

![Het venster Externe koppelingencontrole](assets/external-link-checker.png)

De volgende informatie wordt weergegeven:

* **Status** - De validatiestatus van de koppeling, die een van de volgende kan zijn:
   * **Geldig** - De externe verbinding is bereikbaar door de Controle van de Verbinding
   * **In behandeling** - De externe koppeling is toegevoegd aan de site-inhoud, maar is nog niet gevalideerd door de koppelingencontrole
   * **Ongeldig** - De externe koppeling kan niet worden bereikt door de koppelingencontrole
* **URL** - De externe koppeling
* **Referenter** - De inhoudspagina die de externe koppeling bevat
   * Deze is alleen gevuld [indien geconfigureerd.](#configuring)
* **Laatst gecontroleerd** - De laatste keer dat de koppelingencontrole de externe koppeling heeft gevalideerd
   * Hoe vaak koppelingen worden gecontroleerd [kan worden geconfigureerd.](#configuring)
* **Laatste status** - De laatste HTML statuscode die is geretourneerd toen de koppeling als laatste de externe koppeling heeft gecontroleerd
* **Laatst beschikbaar** - Tijd sinds de koppeling voor het laatst beschikbaar was voor de koppelingencontrole
* **Laatst geopend** - tijd sinds de pagina met de externe koppeling voor het laatst is geopend in de ontwerpinterface

U kunt de inhoud van het venster bewerken met de twee knoppen boven aan de lijst met koppelingen:

* **Vernieuwen** - De inhoud van de lijst vernieuwen
* **Controleren** - Een afzonderlijke externe koppeling controleren die in de lijst is geselecteerd

### De werking van de externe koppelingencontrole {#how-it-works}

Hoewel gemakkelijk te gebruiken, vertrouwt de Externe Controle van de Verbinding op verscheidene diensten en het begrijpen van hoe zij werken helpt u begrijpen hoe te [vorm de Controle van de Verbinding](#configuring) om aan uw behoeften te voldoen.

1. Wanneer een inhoudsontwerper een koppeling naar een pagina opslaat, wordt een gebeurtenishandler geactiveerd.
1. De gebeurtenishandler doorloopt alle inhoud onder `/content` en zoekt naar nieuwe of bijgewerkte koppelingen en voegt deze toe aan een cache voor de koppelingencontrole.
1. De **Day CQ Link Checker Service** wordt vervolgens regelmatig uitgevoerd om te controleren of de gegevens in de cache geldig zijn.
1. De syntaxisgevalideerde koppelingen worden vervolgens weergegeven in het dialoogvenster [Externe koppelingencontrole](#external-link-checker) venster. Ze zullen echter in een **In behandeling** status.
1. De **Taak voor de controle op de dag-CQ-koppeling** voert dan op een regelmatige basis uit om de verbindingen te bevestigen door een vraag van de GET te maken.
1. De **Taak voor de controle op de dag-CQ-koppeling** werkt dan de ingangen in het Externe venster van de Controleur van de Verbinding met de resultaten van de vraag van de GET bij.

## De koppelingencontrole configureren {#configuring}

De koppelingencontrole is automatisch in AEM beschikbaar. Nochtans, zijn er verscheidene configuraties OSGi die kunnen worden gewijzigd om zijn gedrag te veranderen:

* **Day CQ Link Checker Info Storage Service** - Deze service definieert de grootte van de Link Checker-cache in de opslagplaats.
* **Day CQ Link Checker Service** - Deze service controleert asynchroon de syntaxis van externe koppelingen. U kunt de controleperiode bepalen en welke typen koppelingen door de controleur onder andere worden overgeslagen.
* **Taak voor de controle op de dag-CQ-koppeling** - Deze service voert de validatie van externe koppelingen uit. Het staat afzonderlijke definities van intervallen toe om slechte en goede verbindingen onder andere opties te controleren.
* **Day CQ Link Checker Transformer** - Hiermee kunt u koppelingen omzetten op basis van een door de gebruiker gedefinieerde regelset.

Zie het document [OSGi-configuratie-instellingen](/help/sites-deploying/osgi-configuration-settings.md) voor meer details over hoe te om montages te veranderen OSGi.

## De koppelingencontrole uitschakelen {#disabling}

U kunt de koppelingencontrole volledig uitschakelen. Daartoe:

1. Open de OSGi-console.
1. Bewerk de **Day CQ Link Checker Transformer**
1. Selecteer de optie(s) die u wilt uitschakelen:
   * **Controleren uitschakelen** - validatie van koppelingen uitschakelen
   * **Herschrijven uitschakelen** - koppelingtransformaties uitschakelen

>[!NOTE]
>
>Als u het controleren van koppelingen uitschakelt nadat u bent begonnen met het maken van de inhoud, ziet u mogelijk nog steeds items in het dialoogvenster [Het venster Externe koppelingencontrole](#external-link-checker), maar deze worden niet meer bijgewerkt.
