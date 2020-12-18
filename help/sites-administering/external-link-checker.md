---
title: De koppelingencontrole
description: Met de koppelingencontrole kunt u zowel interne als externe koppelingen valideren en het herschrijven van koppelingen toestaan.
translation-type: tm+mt
source-git-commit: 8a551cce581056cb274b1d8567f579fc73a95d3c
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---


# De koppelingencontrole {#the-link-checker}

Inhoudsauteurs hoeven zich niet bezig te houden met het valideren van elke koppeling die ze in hun inhoudspagina&#39;s opnemen.

De functie Koppelingencontrole stelt auteurs van inhoud automatisch bij met hun koppelingen, waaronder:

* Koppelingen valideren terwijl deze aan inhoud worden toegevoegd
* Een lijst met alle externe koppelingen in de inhoud weergeven
* Koppelingtransformaties uitvoeren

De controleur van de Verbinding heeft een aantal [configuratieopties](#configuring) zoals het bepalen van interne bevestiging, die bepaalde verbindingen of verbindingspatters toestaat om van bevestiging worden weggelaten, en het herschrijven van verbinding herschrijvend regels.

De koppelingencontrole valideert zowel [interne koppelingen](#internal) als [externe koppelingen.](#external)

>[!NOTE]
>
>Omdat de koppelingencontrole de koppelingen van elke inhoudspagina controleert, kan de koppelingencontrole de prestaties op grote opslagplaatsen beïnvloeden. In dergelijke gevallen moet u mogelijk [configureren hoe vaak de koppelingencontrole wordt uitgevoerd](#configuring) of [uitschakelen.](#disabling)

## Interne koppelingencontrole {#internal}

Interne koppelingen zijn koppelingen naar andere inhoud in uw AEM. Interne koppelingen kunnen worden toegevoegd met de padkiezer voor de RTE of met een aangepaste component. Bijvoorbeeld:

* Uw pagina `/content/wknd/us/en/adventures/ski-touring.html`
* Bevat een koppeling naar `/content/wknd/us/en/adventures/extreme-ironing.html` in een [Tekstcomponent.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

Interne koppelingen worden gevalideerd zodra de auteur van de inhoud een interne koppeling naar een pagina toevoegt. Als de koppeling ongeldig wordt:

* Deze wordt uit de uitgever verwijderd. De tekst van de koppeling blijft behouden, maar de koppeling zelf wordt verwijderd.
* Het wordt getoond als gebroken verbinding in de auteursinterface.

![Interne verbroken koppeling bij het ontwerpen van een pagina](assets/link-checker-invalid-link-internal.png)

## Controle van externe koppeling {#external}

Externe koppelingen zijn koppelingen naar inhoud buiten de AEM opslagplaats. De externe verbindingen kunnen worden toegevoegd gebruikend RTE of gebruikend een douanecomponent. Bijvoorbeeld:

* Uw pagina `/content/wknd/us/en/adventures/ski-touring.html`
* Bevat een koppeling naar `https://bunwarmerthermalunderwear.com` in een [Tekstcomponent.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

Externe koppelingen worden gevalideerd voor syntaxis en door de beschikbaarheid ervan te controleren. Deze controle wordt asynchroon gedaan bij een configureerbare intern. Als de koppelingencontrole een externe koppeling ongeldig vindt:

* Deze wordt uit de uitgever verwijderd. De tekst van de koppeling blijft behouden, maar de koppeling zelf wordt verwijderd.
* Het wordt getoond als gebroken verbinding in de auteursinterface.

![Interne verbroken koppeling bij het ontwerpen van een pagina](assets/link-checker-invalid-link-external.png)

Daarnaast biedt de [External Link Checker](#external-link-checker)-interface een overzicht van alle externe koppelingen op uw inhoudspagina&#39;s.

### De externe koppelingencontrole {#external-link-checker} gebruiken

De External Link Checker gebruiken:

1. Selecteer **Navigatie**, selecteer **Gereedschappen** en **Sites**.
1. Selecteer **External Link Checker** en er wordt een lijst met alle externe koppelingen weergegeven.

![Het venster Externe koppelingencontrole](assets/external-link-checker.png)

De volgende informatie wordt weergegeven:

* **Status**  - De validatiestatus van de koppeling die een van de volgende kan zijn:
   * **Geldig**  - de externe verbinding is bereikbaar door de Controle van de Verbinding
   * **In behandeling**  - De externe koppeling is toegevoegd aan de site-inhoud, maar is nog niet gevalideerd door de koppelingencontrole
   * **Ongeldig**  - De externe koppeling kan niet worden bereikt door de koppelingencontrole
* **URL**  - De externe koppeling
* **Referrer**  - De inhoudspagina die de externe verbinding bevat
   * Dit is slechts bevolkt [indien gevormd.](#configuring)
* **Laatste keer gecontroleerd**  - De laatste keer dat de koppelingencontrole de externe koppeling heeft gevalideerd
   * Hoe vaak de verbindingen [configureerbaar zijn.](#configuring)
* **Laatste status**  - De laatste HTML-statuscode die werd geretourneerd toen de koppeling voor het laatst werd gecontroleerd op de externe koppeling
* **Laatst beschikbaar**  - Tijd sinds de koppeling voor het laatst beschikbaar was voor de koppelingencontrole
* **Laatst geopend**  - tijd sinds de pagina met de externe koppeling voor het laatst is geopend in de ontwerpinterface

U kunt de inhoud van het venster bewerken met de twee knoppen boven aan de lijst met koppelingen:

* **Vernieuwen**  - De inhoud van de lijst vernieuwen
* **Controleren**  - Een afzonderlijke externe koppeling controleren die in de lijst is geselecteerd

### Hoe de External Link Checker {#how-it-works} werkt

Hoewel gemakkelijk te gebruiken, vertrouwt de Externe Controle van de Verbinding op een aantal diensten en het begrip van hoe zij werken helpt u begrijpen hoe te om de Controle van de Verbinding [te vormen om aan uw behoeften te voldoen.](#configuring)

1. Wanneer een inhoudsontwerper een koppeling naar een pagina opslaat, wordt een gebeurtenishandler geactiveerd.
1. De gebeurtenishandler doorloopt alle inhoud onder `/content` en controleert op nieuwe of bijgewerkte koppelingen en voegt deze toe aan een cache voor de koppelingencontrole.
1. De **Day CQ Link Checker Service** voert vervolgens volgens een regelmatig schema uit om de vermeldingen in de cache op geldige syntaxis te controleren.
1. De syntaxis-bevestigde verbindingen verschijnen dan in [External Link Checker](#external-link-checker) venster. Nochtans zullen zij in een **Pending** staat zijn.
1. De **dag CQ Taak van de Controle van de Verbinding** voert dan op een regelmatige basis uit om de verbindingen te bevestigen door een vraag van de GET te maken.
1. **De Taak van de Controle van de Verbinding van CQ van de Dag CQ** werkt dan de ingangen in het Externe venster van de Controleur van de Verbinding met de resultaten van de vraag van de GET bij.

## De koppelingencontrole {#configuring} configureren

De koppelingencontrole is automatisch in AEM beschikbaar. Nochtans zijn er een aantal configuraties OSGi die kunnen worden gewijzigd om zijn gedrag te veranderen:

* **De Dienst**  van de Opslag van de Info van de Verbinding van dag CQ - Deze dienst bepaalt de grootte van het geheime voorgeheugen van de Controle van de Verbinding in de bewaarplaats.
* **De Dienst**  van de Controle van de Verbinding van dag CQ - Deze dienst voert asynchrone controle van de syntaxis van externe verbindingen uit. U kunt de controleperiode bepalen en welke typen koppelingen door de controleur onder andere worden overgeslagen.
* **De Taak**  van de Controle van de Verbinding van dag CQ - Deze dienst voert de bevestiging van de GET van externe verbindingen uit. Het staat afzonderlijke definities van intervallen toe om slechte en goede verbindingen onder andere opties te controleren.
* **De Transformator**  van de Controle van de Verbinding van dag CQ - staat voor het omzetten van verbindingen toe die op een user-defined regelreeks worden gebaseerd.

Zie het document [OSGi de Montages van de Configuratie](/help/sites-deploying/osgi-configuration-settings.md) voor meer details op hoe te om montages te veranderen OSGi.

## De koppelingencontrole {#disabling} uitschakelen

U kunt de koppelingencontrole volledig uitschakelen. Daartoe:

1. Open de OSGi-console.
1. Bewerk de **Day CQ Link Checker Transformer**
1. Selecteer de optie(s) die u wilt uitschakelen:
   * **Schakel Controleren**  uit om validatie van koppelingen uit te schakelen
   * **Herschrijven**  uitschakelen om koppelingtransformaties uit te schakelen

>[!NOTE]
>
>Als u het controleren van koppelingen uitschakelt nadat u bent begonnen met het maken van uw inhoud, ziet u mogelijk nog vermeldingen in het venster [Externe koppelingencontrole](#external-link-checker), maar deze worden niet meer bijgewerkt.
