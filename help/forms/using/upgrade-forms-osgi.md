---
title: Upgrade naar AEM 6,5 Forms op OSGi
description: U kunt een directe verbetering van AEM 6.1 Forms, AEM 6.2 Forms, en LiveCycle ES4 SP1 aan AEM 6.3 Forms uitvoeren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
role: Admin,User
exl-id: 1e39455e-f588-42a2-91f5-daefcfed82a0
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on OSGi, AEM Forms Upgrade
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---

# Upgrade naar AEM 6,5 Forms op OSGi {#upgrade-to-aem-forms-osgi}

U kunt een directe upgrade uitvoeren van AEM 6.3 Forms of AEM 6.4 Forms naar AEM 6.5 Forms.

De directe verbeteringsweg van **AEM 6.0 Forms, AEM 6.1 Forms**, en **AEM 6.2 Forms** aan AEM 6.5 Forms is niet beschikbaar. Voer een tussenliggende [&#x200B; verbetering aan AEM 6.2 Forms &#x200B;](https://helpx.adobe.com/nl/experience-manager/6-2/forms/using/upgrade.html) uit, [&#x200B; verbetering aan AEM 6.3 Forms &#x200B;](https://helpx.adobe.com/nl/experience-manager/6-3/forms/using/upgrade.html), of [&#x200B; verbetering aan AEM 6.4 Forms &#x200B;](/help/forms/using/upgrade.md) en dan verbetering van AEM 6.3 Forms, of AEM 6.4 Forms aan AEM 6.5.

Ga als volgt te werk om een upgrade uit te voeren van AEM 6.3 Forms of AEM 6.4 Forms naar AEM 6.5 Forms:

1. Upgrade de bestaande AEM naar AEM 6.5. De stappen worden hieronder weergegeven:

   1. Installeer het nieuwste servicepakket en de nieuwste patches voor AEM 6.3 Forms of AEM 6.4 Forms. Voor details, zie [&#x200B; AEM de Hub van de Aanpassing &#x200B;](https://helpx.adobe.com/nl/experience-manager/aem-releases-updates.html).
   1. Bereid de broninstantie voor de verbetering voor. Voor gedetailleerde stappen, zie [&#x200B; Bevorderend aan AEM 6.5 &#x200B;](/help/sites-deploying/upgrade.md).
   1. Download [&#x200B; AEM 6.5 QuickStart &#x200B;](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Unix/Linux-Gebaseerde installaties slechts)** als u UNIX of Linux als onderliggend werkend systeem gebruikt, open het eindvenster, navigeer aan de omslag die crx-quickstart bevat, en stel het volgende bevel in werking:

      `chmod -R 755 ../crx-quickstart`

   1. Voer een upgrade uit van uw AEM naar AEM 6.3. Voor geleidelijke instructies, zie [&#x200B; Bevorderend aan AEM 6.5 &#x200B;](/help/sites-deploying/upgrade.md).

      Wacht voordat u verdergaat met de volgende stappen tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer worden weergegeven in het bestand &lt;crx-repository>/error.log.

      >[!NOTE]
      >
      >Nadat de server is gestart, blijven enkele AEM Forms-bundels in de installatiestatus staan. Het aantal bundels kan voor elke installatie variëren. U kunt de status van deze pakketten veilig negeren. De bundels zijn vermeld in https://&#39; [ server ]:[ haven ]&#39;/system/console/.

1. Installeer het AEM Forms-invoegtoepassingspakket. De stappen worden hieronder weergegeven:

   1. Open [&#x200B; Distributie van de Software &#x200B;](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
   1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
   1. In de sectie **[!UICONTROL Filters]** :
      1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
      1. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
   1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
   1. Open [&#x200B; Manager van het Pakket &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=nl-NL) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
   1. Selecteer het pakket en klik op **[!UICONTROL Install]** .

      U kunt het pakket ook downloaden gebruikend de directe verbinding die in [&#x200B; wordt vermeld versies van AEM Forms &#x200B;](https://helpx.adobe.com/nl/aem-forms/kb/aem-forms-releases.html) artikel.

      >[!NOTE]
      >
      >Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM opnieuw te starten. **stop niet onmiddellijk de server.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer worden weergegeven in het bestand &lt;crx-repository>/error.log en het logbestand stabiel is. Houd er rekening mee dat een aantal pakketten in de installatiestatus kunnen blijven staan. U kunt de status van deze verpakkingen veilig negeren.

1. Start de AEM opnieuw.

   >[!NOTE]
   >
   >Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

1. Nainstallatie uitvoeren.

   * **het Nut van de Migratie van de Looppas**

     Het migratiehulpprogramma maakt de adaptieve formulieren en het beheer van correspondentie van eerdere versies compatibel met AEM 6.5-formulieren. U kunt het hulpprogramma downloaden van AEM softwaredistributie. Voor geleidelijke informatie om het migratienut te vormen en te gebruiken, zie [&#x200B; migratienut &#x200B;](../../forms/using/migration-utility.md).

     Als u [&#x200B; Steekproef voor het integreren van concepten &amp; voorleggingscomponent &#x200B;](https://helpx.adobe.com/nl/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) met het gegevensbestand en de bevordering van een vorige versie gebruikt, dan stel de volgende SQL vragen na het uitvoeren van de verbetering in werking:

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

   * **(Als u een upgrade uitvoert van alleen AEM 6.2 Forms of eerdere versies) Adobe Sign opnieuw configureren**

     Als u Adobe Sign in de vorige versie van AEM Forms had geconfigureerd, configureert u Adobe Sign opnieuw vanaf AEM Cloud-services. Voor meer details, zie [&#x200B; Adobe Sign met AEM Forms &#x200B;](../../forms/using/adobe-sign-integration-adaptive-forms.md) integreren.

   * **Steun voor jQuery**

     In AEM 6.5 Forms wordt de versie van jQuery bijgewerkt naar versie 3.2.1 en de versie van jQuery-gebruikersinterface naar versie 1.12.1. AEM het gebruik JQuery van de Vorm op **noConflict** wijze. Als u dus een andere jQuery-versie gebruikt, worden er geen problemen weergegeven tijdens het uitvoeren van een upgrade. Wanneer u echter een upgrade uitvoert naar AEM 6.5 Forms:

      * Controleer of uw aangepaste componenten, indien aanwezig, compatibel zijn met ondersteunde jQuery-versies.
      * Verwijder niet-ondersteunde API&#39;s uit de aangepaste componenten. Zie [&#x200B; verbeteringsgids &#x200B;](https://jquery.com/upgrade-guide/3.0/) voor de lijst van verwijderde APIs. Ondersteuning voor de API&#39;s load(), .unload() en .error() wordt bijvoorbeeld verwijderd. Gebruik de methode .on() in plaats van de eerder genoemde API&#39;s. Wijzig bijvoorbeeld $(&quot;img&quot;).load(fn) in $(&quot;img&quot;).on(&quot;load&quot;, fn).

   * **(Als u een upgrade uitvoert van alleen AEM 6.2 Forms of eerdere versies) Analyses en rapporten opnieuw samenstellen**

     In AEM 6.4 Forms, zijn de verkeersvariabele voor bron en succesgebeurtenis voor indruk niet beschikbaar. Als u dus een upgrade uitvoert van AEM 6.2 Forms of eerdere versies, stopt AEM Forms met het verzenden van gegevens naar de Adobe Analytics-server en zijn er geen analyserapporten voor adaptieve formulieren beschikbaar. Bovendien introduceert AEM 6.4 Forms verkeersvariabele voor de versie van formulieranalyse en succesgebeurtenis voor de hoeveelheid tijd die aan een veld wordt doorgebracht. Configureer daarom analyses en rapporten voor uw AEM Forms-omgeving. Voor gedetailleerde stappen, zie [&#x200B; het Vormen analyses en rapporten &#x200B;](../../forms/using/configure-analytics-forms-documents.md).

1. Controleer of de upgrade van de server is geslaagd, of alle gegevens zijn gemigreerd en of deze op de normale manier kunnen werken.

   * **verifieer het statuut van de bundels:** zorg ervoor dat alle bundels in actieve staat zijn.
   * **verifieer replicatie en omgekeerde replicatie:** Publish, vul, en verzend een paar gemigreerde vormen. Controleer ook de verzonden gegevens.
   * **verifieer toegang tot admin en het gebruikersinterfaces van de ontwikkelaar:** Login aan AEM instantie van een admin rekening en verifieer dat u toegang tot volgende URLs hebt:

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   >
   >In AEM 6.4 Forms is de structuur van crx-repository veranderd. Als u een upgrade uitvoert van 6.3 Forms naar AEM 6.5 Forms, gebruikt u de gewijzigde paden voor aanpassing die u opnieuw maakt. Voor de volledige lijst van veranderde wegen, zie [&#x200B; Herstructurering van de Bewaarplaats van Forms in AEM &#x200B;](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md).
