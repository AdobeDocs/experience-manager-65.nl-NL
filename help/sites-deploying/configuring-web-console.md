---
title: Webconsole in AEM
description: Leer hoe u de webconsole in AEM gebruikt.
uuid: 047274ff-4d7d-4c7d-95be-06f363beae2e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
discoiquuid: f934eb02-1f84-44f2-9f14-3f17250c9a90
exl-id: bdfeaf85-e832-40c1-8769-7d027cdb021e
source-git-commit: a17b25e55a0bf16a0df42a7ba4768503618a19e2
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# Webconsole{#web-console}

De webconsole in AEM (Adobe Experience Manager) is gebaseerd op de [Apache Felix Web Management Console](https://felix.apache.org/documentation/subprojects/apache-felix-web-console.html). Apache Felix is een communautaire inspanning om het Platform van de Dienst van OSGi R4 uit te voeren, dat het kader OSGi en de standaarddiensten omvat.

>[!NOTE]
>
>Op de console van het Web om het even welke beschrijvingen die standaardmontages vermelden hebben op het Verschuiven gebreken.
>
>AEM heeft zijn eigen gebreken en zo zouden de geplaatste gebreken van die op de console kunnen verschillen worden gedocumenteerd.

De console van het Web biedt een selectie lusjes voor het handhaven van de bundels OSGi aan, die omvatten:

* [Configuratie](#configuration): gebruikt voor het vormen van de bundels OSGi, en is daarom het onderliggende mechanisme om AEM systeemparameters te vormen
* [Bundels](#bundles): gebruikt voor het installeren van bundels
* [Componenten](#components): gebruikt voor de controle van de status van onderdelen die vereist zijn voor AEM

Alle aangebrachte wijzigingen worden onmiddellijk toegepast op het actieve systeem. U hoeft de computer niet opnieuw op te starten.

De console is toegankelijk vanaf `../system/console`; bijvoorbeeld:

`http://localhost:4502/system/console/components`

## Configuratie {#configuration}

De **Configuratie** tab wordt gebruikt voor het vormen van de bundels OSGi, en is daarom het onderliggende mechanisme voor het vormen van AEM systeemparameters.

>[!NOTE]
>
>Zie [OSGi Configuratie met de Console van het Web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) voor nadere bijzonderheden.

De **Configuratie** tab kan worden benaderd door:

* Het vervolgkeuzemenu:

   **OSGi >**

* de URL; bijvoorbeeld:

   `http://localhost:4502/system/console/configMgr`

Er wordt een lijst met configuraties weergegeven:

![screen_shot_2012-02-15at52308pm-1](assets/screen_shot_2012-02-15at52308pm-1.png)

Er zijn twee soorten configuraties beschikbaar bij de drop-down lijsten op dit scherm:

* **Configuraties**

   Hiermee kunt u de bestaande configuraties bijwerken. Deze hebben een Persistent Identity (PID) en kunnen:

   * standaard en integraal van AEM; deze zijn vereist als de waarden worden verwijderd en de standaardinstellingen worden hersteld.
   * instanties die zijn gemaakt op basis van fabrieksconfiguraties; Deze instanties worden gemaakt door de gebruiker. Verwijderen verwijdert de instantie.

* **Fabrieksconfiguraties**

   Hiermee kunt u een instantie maken van het vereiste functionaliteit-object.

   Dit krijgt een blijvende identiteit toegewezen en wordt vervolgens vermeld in de vervolgkeuzelijst Configuraties.

Als u een item in de lijst selecteert, worden de parameters met betrekking tot die configuratie weergegeven:

![chlimage_1-61](assets/chlimage_1-61.png)

Vervolgens kunt u de parameters naar wens bijwerken en:

* **Opslaan**

   Sla de aangebrachte wijzigingen op.

   Voor een Configuratie van de Fabriek zal dit tot een nieuwe instantie met een Blijvende Identiteit leiden. Het nieuwe exemplaar zal dan onder Configuraties worden vermeld.

* **Herstellen**

   Herstel de parameters die op het scherm worden getoond aan die het laatst worden bewaard.

* **Verwijderen**

   Verwijder de huidige configuratie. Indien standaard, worden de parameters teruggegeven aan de standaardmontages. Indien gecreeerd van een Configuratie van de Fabriek, dan wordt de specifieke instantie geschrapt.

* **Binding ongedaan maken**

   Koppel de huidige configuratie los van de bundel.

* **Annuleren**

   Alle huidige wijzigingen annuleren.

## Bundels {#bundles}

De **Bundels** tab is het mechanisme voor het installeren van de OSGi-bundels die vereist zijn voor AEM. Het tabblad is toegankelijk op een van de volgende manieren:

* Het vervolgkeuzemenu:

   **OSGi >**

* de URL; bijvoorbeeld:

   `http://localhost:4502/system/console/bundles`

Er wordt een lijst met bundels weergegeven:

![screen_shot_2012-02-15at44740pm-1](assets/screen_shot_2012-02-15at44740pm-1.png)

Met dit tabblad kunt u:

* **Installeren of bijwerken**

   U kunt **Bladeren** om het bestand te zoeken dat uw bundel bevat en op te geven of dit nodig is **Start** onmiddellijk **Beginniveau**.

* **Opnieuw laden**

   Hiermee vernieuwt u de weergegeven lijst.

* **Pakketten vernieuwen**

   Hiermee controleert u de referenties van alle pakketten en vernieuwt u deze waar nodig.

   Na een update kan de oude en de nieuwe versie bijvoorbeeld nog steeds actief zijn vanwege eerdere verwijzingen. Met deze optie worden alle verwijzingen naar de nieuwe versie gecontroleerd en verplaatst, zodat de oude versie stopt.

* **Start**

   Hiermee wordt een bundel gestart op basis van het opgegeven beginniveau.

* **Stoppen**

   Stopt de bundel.

* **Verwijderen**

   Hiermee wordt de bundel van het systeem verwijderd.

* **zie de status**

   In de lijst wordt de huidige status van de bundel vermeld. klikken op de naam van een specifieke bundel met meer informatie.

>[!NOTE]
>
>Na **Bijwerken** het wordt aanbevolen een **Pakketten vernieuwen**.

## Onderdelen {#components}

De **Componenten** kunt u de verschillende componenten in- en/of uitschakelen. Het kan worden benaderd door:

* Het vervolgkeuzemenu:

   **Hoofd >**

* de URL; bijvoorbeeld:

   `http://localhost:4502/system/console/components`

Er wordt een lijst met componenten weergegeven. Er zijn verschillende pictogrammen beschikbaar waarmee u configuratiedetails voor een specifieke component kunt inschakelen, uitschakelen of (waar van toepassing) openen.

![screen_shot_2012-02-15at52144pm-1](assets/screen_shot_2012-02-15at52144pm-1.png)

Als u op de naam van een bepaalde component klikt, wordt meer informatie over de status weergegeven. Hier kunt u de component ook in-, uitschakelen of opnieuw laden.

![chlimage_1-62](assets/chlimage_1-62.png)

>[!NOTE]
>
>Als u een component inschakelt of uitschakelt, wordt deze alleen van toepassing tot AEM/CRX opnieuw wordt gestart.
>
>De begintoestand wordt gedefinieerd binnen de componentdescriptor, die tijdens de ontwikkeling wordt gegenereerd en in de bundel wordt opgeslagen op het moment dat de bundel wordt gemaakt.
