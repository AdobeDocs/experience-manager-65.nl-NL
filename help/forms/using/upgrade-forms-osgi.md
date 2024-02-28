---
title: Upgrade naar AEM 6,5 Forms op OSGi
description: U kunt een directe verbetering van AEM 6.1 Forms, AEM 6.2 Forms, en LiveCycle ES4 SP1 aan AEM 6.3 Forms uitvoeren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
role: Admin
exl-id: 1e39455e-f588-42a2-91f5-daefcfed82a0
source-git-commit: d195ac80ee59439bab5b1219a2c1f16e93e3d22b
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---

# Upgrade naar AEM 6,5 Forms op OSGi {#upgrade-to-aem-forms-osgi}

U kunt een directe upgrade uitvoeren van AEM 6.3 Forms of AEM 6.4 Forms naar AEM 6.5 Forms.

Direct upgradepad van **AEM 6,0 Forms, AEM 6,1 Forms**, en **AEM 6.2 Forms** tot AEM 6.5 Forms is niet beschikbaar. Een tussenpersoon uitvoeren [upgrade naar AEM 6.2 Forms](https://helpx.adobe.com/experience-manager/6-2/forms/using/upgrade.html), [upgrade naar AEM 6.3 Forms](https://helpx.adobe.com/experience-manager/6-3/forms/using/upgrade.html), of [upgrade naar AEM 6.4 Forms](/help/forms/using/upgrade.md) en upgrade dan van AEM 6.3 Forms of AEM 6.4 Forms naar AEM 6.5 Forms.

Ga als volgt te werk om een upgrade uit te voeren van AEM 6.3 Forms of AEM 6.4 Forms naar AEM 6.5 Forms:

1. Upgrade de bestaande AEM naar AEM 6.5. De stappen worden hieronder weergegeven:

   1. Installeer het nieuwste servicepakket en de nieuwste patches voor AEM 6.3 Forms of AEM 6.4 Forms. Zie voor meer informatie [AEM Sustenance Hub](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).
   1. Bereid de broninstantie voor de verbetering voor. Zie voor meer informatie [Upgrade uitvoeren naar AEM 6.5](/help/sites-deploying/upgrade.md).
   1. Download de [AEM 6.5 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Alleen Unix/Linux-gebaseerde installaties)** Als u UNIX of Linux als onderliggend besturingssysteem gebruikt, opent u het terminalvenster, navigeert u naar de map met crx-quickstart en voert u de volgende opdracht uit:

      `chmod -R 755 ../crx-quickstart`

   1. Voer een upgrade uit van uw AEM naar AEM 6.3. Voor instructies die stap voor stap worden uitgevoerd, zie [Upgrade uitvoeren naar AEM 6.5](/help/sites-deploying/upgrade.md).

      Voordat u verdergaat met de volgende stappen, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer worden weergegeven in het dialoogvenster &lt;crx-repository>/error.log.

      >[!NOTE]
      >
      >Nadat de server is gestart, blijven enkele AEM Forms-bundels in de installatiestatus staan. Het aantal bundels kan voor elke installatie variëren. U kunt de status van deze pakketten veilig negeren. De bundels worden weergegeven op https://&#39;[server]:[poort]&quot;/system/console/.

1. Installeer het AEM Forms-invoegtoepassingspakket. De stappen worden hieronder weergegeven:

   1. Openen [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
   1. Selecteren **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
   1. In de **[!UICONTROL Filters]** sectie:
      1. Selecteren **[!UICONTROL Forms]** van de **[!UICONTROL Solution]** vervolgkeuzelijst.
      1. Selecteer de versie en typ voor het pakket. U kunt ook de opdracht **[!UICONTROL Search Downloads]** om de resultaten te filteren.
   1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem. Selecteer **[!UICONTROL Accept EULA Terms]** en selecteert u **[!UICONTROL Download]**.
   1. Openen [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)  en klik op **[!UICONTROL Upload Package]** om het pakket te uploaden.
   1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

      U kunt het pakket ook downloaden via de directe koppeling die wordt vermeld in [AEM Forms-releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) artikel.

      >[!NOTE]
      >
      >Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM opnieuw te starten. **Stop niet onmiddellijk de server.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer worden weergegeven in het dialoogvenster &lt;crx-repository>Het bestand /error.log en het logbestand zijn stabiel. Houd er rekening mee dat een aantal pakketten in de installatiestatus kunnen blijven staan. U kunt de status van deze verpakkingen veilig negeren.

1. Start de AEM opnieuw.

   >[!NOTE]
   >
   Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

1. Nainstallatie uitvoeren.

   * **Migratiehulpprogramma uitvoeren**

     Het migratiehulpprogramma maakt de adaptieve formulieren en het beheer van correspondentie van eerdere versies compatibel met AEM 6.5-formulieren. U kunt het hulpprogramma downloaden van AEM softwaredistributie. Voor geleidelijke informatie om het migratienut te vormen en te gebruiken, zie [migratiehulpprogramma](../../forms/using/migration-utility.md).

     Als u [Voorbeeld voor het integreren van concepten en verzendingscomponenten](https://helpx.adobe.com/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) met de database en upgrade vanaf een vorige versie, voert u de volgende SQL-query&#39;s uit nadat u de upgrade hebt uitgevoerd:

     ```sql
     UPDATE metadata m, additionalmetadatatable am
     SET m.dataType = am.value
     WHERE m.id = am.id
     AND am.key = 'dataType'
     ```

     ```sql
     DELETE from additionalmetadatatable
     WHERE `key` = 'dataType'
     ```

   * **(Als u alleen een upgrade uitvoert van AEM 6.2 Forms of eerdere versies, dient u Adobe Sign opnieuw te configureren**

     Als u Adobe Sign in de vorige versie van AEM Forms had geconfigureerd, configureert u Adobe Sign opnieuw vanaf AEM Cloud-services. Zie voor meer informatie [Adobe Sign integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

   * **Ondersteuning voor jQuery**

     In AEM 6.5 Forms wordt de versie van jQuery bijgewerkt naar versie 3.2.1 en de versie van jQuery-gebruikersinterface naar versie 1.12.1. AEM formulier gebruikt JQuery in **noConflict** -modus. Als u dus een andere jQuery-versie gebruikt, worden er geen problemen weergegeven tijdens het uitvoeren van een upgrade. Wanneer u echter een upgrade uitvoert naar AEM 6.5 Forms:

      * Controleer of uw aangepaste componenten, indien aanwezig, compatibel zijn met ondersteunde jQuery-versies.
      * Verwijder niet-ondersteunde API&#39;s uit de aangepaste componenten. Zie [upgradehulplijn](https://jquery.com/upgrade-guide/3.0/) voor de lijst met verwijderde API&#39;s. Ondersteuning voor de API&#39;s load(), .unload() en .error() wordt bijvoorbeeld verwijderd. Gebruik de methode .on() in plaats van de eerder genoemde API&#39;s. Wijzig bijvoorbeeld $(&quot;img&quot;).load(fn) in $(&quot;img&quot;).on(&quot;load&quot;, fn).

   * **(Als u een upgrade uitvoert van alleen AEM 6.2 Forms of eerdere versies) Analyses en rapporten opnieuw samenstellen**

     In AEM 6.4 Forms, zijn de verkeersvariabele voor bron en succesgebeurtenis voor indruk niet beschikbaar. Als u dus een upgrade uitvoert van AEM 6.2 Forms of eerdere versies, stopt AEM Forms met het verzenden van gegevens naar de Adobe Analytics-server en zijn er geen analyserapporten voor adaptieve formulieren beschikbaar. Bovendien introduceert AEM 6.4 Forms verkeersvariabele voor de versie van formulieranalyse en succesgebeurtenis voor de hoeveelheid tijd die aan een veld wordt doorgebracht. Configureer daarom analyses en rapporten voor uw AEM Forms-omgeving. Zie voor meer informatie [Analyses en rapporten configureren](../../forms/using/configure-analytics-forms-documents.md).

1. Controleer of de upgrade van de server is geslaagd, of alle gegevens zijn gemigreerd en of deze op de normale manier kunnen werken.

   * **Controleer de status van de bundels:** Zorg ervoor dat alle bundels actief zijn.
   * **Verifieer replicatie en omgekeerde replicatie:** Een aantal gemigreerde formulieren publiceren, invullen en verzenden. Controleer ook de verzonden gegevens.
   * **Toegang tot gebruikersinterfaces voor beheer en ontwikkelaar verifiëren:** Meld u aan bij AEM instantie van een beheerdersaccount en controleer of u toegang hebt tot de volgende URL&#39;s:

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   >
   In AEM 6.4 Forms is de structuur van crx-repository veranderd. Als u een upgrade uitvoert van 6.3 Forms naar AEM 6.5 Forms, gebruikt u de gewijzigde paden voor aanpassing die u opnieuw maakt. Zie voor de volledige lijst met gewijzigde paden [Forms Repository Herstructurering in AEM](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md).
