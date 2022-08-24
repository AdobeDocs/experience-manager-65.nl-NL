---
title: We.Doorloop van de referentiewebsite voor Verzekering van financiële automatische vernieuwing
seo-title: We.Finance Auto Insurance Renewal reference site walkthrough
description: We.Doorloop van de referentiewebsite voor Verzekering van financiële automatische vernieuwing
uuid: c749a6f7-71f1-4f47-b824-9c7b699072c7
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
discoiquuid: ad450124-49a5-4afb-aac3-ed3733d6504b
docset: aem65
exl-id: b6ded6ac-4fb1-49f9-b272-16774c3e89a3
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# We.Doorloop van de referentiewebsite voor Verzekering van financiële automatische vernieuwing{#we-finance-auto-insurance-renewal-reference-site-walkthrough}

## We.Finance Reference Site-scenario  {#we-finance-reference-site-scenario}

Wij.Finance-site is een site voor financiële services die u helpt interactieve communicatiemogelijkheden van AEM Forms te leren kennen.

Lees meer over de uitgebreide doorlichting van We.Finance Auto Insurance gebruikscase die laat zien hoe AEM formulieren en de integratie ervan met Microsoft Dynamics de klantervaring in een bedrijf voor financiële services helpen personaliseren. De interactieve analyse wordt ontworpen om implementatie van complexe digitale transacties en klantenmededeling in een financieel bedrijf te vergemakkelijken.

**De rit begint met de gebruikscase:**

Sarah Rose is een bestaande We.Finance-klant en heeft een autoverzekeringspolis gekocht. Het is nu de tijd van het jaar voor de verlenging van haar verzekeringspolis. Gloria Rios, verzekeringsagent, We.Finance stuurt een herinnering aan Sarah over haar beleidsvernieuwing. Sarah volgt de instructies in de e-mail en voltooit het proces.

## Doorloop van toepassing voor automatische verzekering {#auto-insurance-application-walkthrough}

Het Auto-Verzekeringstoepassingsscenario van Web.Finance is een visuele gesproken tekst voor de gebruiker en is gebaseerd op twee personen:

* Sarah Rose, een klant van We.Finance
* Gloria Rios, Verzekeringsagent, We.Finance

### Gloria stuurt een mededeling over de verlenging van het verzekeringsbeleid van We.Finance {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria logt in AEM instantie, klikt **Verlenging autoverzekering** en klikt u vervolgens **Gebruikersinterface van agent openen.** Klik vooraf vult het verzekeringsdocument met beleidsdetails van Sarah Rose. Gloria kliks **Verzenden** en er wordt een bericht weergegeven op het scherm &quot;Verzending geïnitieerd&quot; en vervolgens in enkele seconden &quot;Verzenden voltooid&quot;.

Sarah ontvangt een e-mail met het onderwerp &quot;Uw automatische Verzekering Verlenging&quot;.

![Gebruikersinterface van agent](assets/agent_ui_email_new.png)

#### Zie het zelf {#see-it-yourself}

Ga naar **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten** > **Wij.Financiën** > **Automatische verzekering**. Verzekering automatisch vernieuwen selecteren **interactieve communicatie** en klik op **Gebruikersinterface van agent openen**. De interactieve mededeling opent omhoog in de Agent UI. Voer een geldig e-mailadres in om de e-mail te ontvangen met het bijgevoegde beleidsdocument en klik op Verzenden.

U hebt rechtstreeks vanuit `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.`

### Sarah ontvangt een mededeling over de verlenging van verzekeringsovereenkomsten van We.Finance en besluit te verlengen {#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah ontvangt een e-mail met een bijlage van We.Finance die haar eraan herinnert dat haar Autoverzekeringspolis op het punt staat te verlopen. De bijlage is de afdrukversie van haar brief voor automatische verzekering.

Sarah kliks **Nu vernieuwen** en wordt verwezen naar de webversie van haar brief over automatische verzekering. Naast deze brief vindt Sarah nog een aantal dagen dat haar beleid moet verlopen. De pagina biedt Sarah een basisoverzicht van haar verzekeringsbeleidsdetails zoals het aantal van het Beleid, het Gelverschuldigd Bedrag, en andere informatie zoals kortingsaanbiedingen en loyaliteitsbeloningen. Sarah klikt opnieuw **Nu vernieuwen** onderaan het beleid.

![ref1](assets/ref1.png)

#### Hoe werkt het {#how-it-works}

Het Web en de drukoutput van uw brief van de Verzekering van de Auto worden gecreeerd gebruikend de multikanaalsmogelijkheden van Interactieve Mededelingen.

De knop Nu vernieuwen in de e-mail is gekoppeld aan de toepassing voor automatisch vernieuwen van verzekering. Dit is een interactieve communicatie over een publicatie-instantie.

#### Zie het zelf {#see-it-yourself-1}

U moet een e-mail met een bijgevoegde PDF hebben ontvangen. De PDF is een afdrukversie van uw brief voor automatische verzekering. Klikken **Nu vernieuwen** om de webversie van het beleid te bereiken. Controleer uw persoonlijke gegevens en beleidsgegevens en klik op **Nu vernieuwen** Hiermee gaat u naar een andere interactieve communicatie.

De **Nu vernieuwen** in de e-mail stuurt Sarah naar de webversie van het beleid. U kunt de volgende URL bezoeken:

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

U kunt de gedetailleerde samenvatting van de verlenging van de autoverzekering controleren en klikken **Nu vernieuwen** onder aan de pagina.

### Sarah bereikt de betalingspagina {#sarah-reaches-the-payment-page}

We. Finance brengt Sarah naar de betalingspagina. Sarah controleert haar Aantal van het Beleid en Datum van Vervalsing met haar verslagen opnieuw. Aan de rechterkant van de pagina controleert ze het betalingsoverzicht van haar verlenging met een premiekorting van 10% op het totale bedrag.

#### Hoe werkt het {#how-it-works-1}

Met de knop Nu vernieuwen wordt Sarah naar de betalingspagina geleid. De betalingspagina is een adaptief formulier.

#### Zie het zelf {#see-it-yourself-2}

Klikken **Nu vernieuwen** om naar de betalingspagina te gaan. Vul je creditcardgegevens in en klik op **Betaling maken**.

U kunt de betalingspagina bereiken in de ontwerpinstantie op

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah doet de betaling en voltooit het proces {#sarah-makes-the-payment-and-completes-the-process}

Sarah invult haar creditcardgegevens en klikt op **Betaling maken**.

#### Hoe werkt het {#how-it-works-2}

Als Sarah de creditcardgegevens invult en op Indienen klikt, wordt de betaling van haar creditcard verwerkt en verschijnt een bedankbericht dat in het adaptieve formulier is geconfigureerd, op het scherm.

#### Zie het zelf {#see-it-yourself-3}

Je kunt het bevestigingsbericht bekijken nadat je op Betaling maken hebt geklikt op

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
