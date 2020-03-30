---
title: Upgrade naar AEM 6.5-formulieren
seo-title: Upgrade naar AEM 6.5-formulieren
description: U kunt een directe upgrade uitvoeren van AEM 6.1-formulieren, AEM 6.2-formulieren en LiveCycle ES4 SP1 naar AEM 6.3-formulieren.
seo-description: U kunt een directe upgrade uitvoeren van AEM 6.1-formulieren, AEM 6.2-formulieren en LiveCycle ES4 SP1 naar AEM 6.3-formulieren.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Upgrade naar AEM 6.5-formulieren op OSGi {#upgrade-to-aem-forms-osgi}

U kunt een directe upgrade uitvoeren van AEM 6.3 Forms of AEM 6.4 Forms naar AEM 6.5 Forms.

Het directe upgradepad van **AEM 6.0-formulieren, AEM 6.1-formulieren** en **AEM 6.2-formulieren** naar AEM 6.5-formulieren is niet beschikbaar. Voer een tussentijdse [upgrade uit naar AEM 6.2 Forms](https://helpx.adobe.com/experience-manager/6-2/forms/using/upgrade.html), [upgrade naar AEM 6.3 Forms](https://helpx.adobe.com/experience-manager/6-3/forms/using/upgrade.html)of [upgrade naar AEM 6.4 Forms](/help/forms/using/upgrade.md) en werk vervolgens een upgrade uit van AEM 6.3 Forms of AEM 6.4 Forms naar AEM 6.5 Forms.

Ga als volgt te werk om een upgrade uit te voeren van AEM 6.3 Forms of AEM 6.4 Forms naar AEM 6.5 Forms:

1. Upgrade de bestaande AEM-instantie naar AEM 6.5. De stappen worden hieronder weergegeven:

   1. Installeer het nieuwste servicepakket en de nieuwste patches voor AEM 6.3 Forms of AEM 6.4 Forms. Voor details, zie de Hub [van de Aanpassing](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)AEM.
   1. Bereid de broninstantie voor de verbetering voor. Zie [Upgraden naar AEM 6.5](/help/sites-deploying/upgrade.md)voor gedetailleerde stappen.
   1. Download de [AEM 6.5 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Alleen Unix/Linux-gebaseerde installaties)** Als u UNIX of Linux als onderliggend besturingssysteem gebruikt, opent u het terminalvenster, navigeert u naar de map met crx-quickstart en voert u de volgende opdracht uit:

      `chmod -R 755 ../crx-quickstart`

   1. Upgrade uw AEM-instantie naar AEM 6.3. Zie [Upgrade naar AEM 6.5](/help/sites-deploying/upgrade.md)voor stapsgewijze instructies.

      Wacht voordat u verdergaat met de volgende stappen tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer worden weergegeven in het bestand &lt;crx-repository>/error.log.

      >[!NOTE]
      >
      >Nadat de server is gestart, blijven er nog enkele AEM Forms-bundels in de installatiestatus staan. Het aantal bundels kan voor elke installatie variëren. U kunt de status van deze bundels veilig negeren. De bundels worden vermeld op https://&#39;[server]:[port]&#39;/system/console/.

1. AEM Forms add-on-pakket installeren. De stappen worden hieronder weergegeven:

   1. Meld u als beheerder aan bij de AEM-server en open het gedeelde pakket. De standaard-URL van het gedeelde pakket is `https://'[server]:[port]'/crx/packageshare`.
   1. Zoek in **AEM 6.5 Forms Add-on-pakketten** in het gedeelde pakket naar het pakket dat op uw besturingssysteem van toepassing is en klik op **Download**. Lees en accepteer de licentieovereenkomst en klik op **OK**. Het downloaden begint. Nadat u het bestand hebt gedownload, staat het woord **Gedownload** naast het pakket.

      U kunt ook de hyperlinks in de [AEM Forms-releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) gebruiken om een pakket handmatig te downloaden.

   1. Klik op **Gedownload** nadat het downloaden is voltooid. U wordt omgeleid naar pakketbeheer. Zoek in pakketbeheer naar het gedownloade pakket en klik op **Installeren**.

      Als u het pakket handmatig downloadt via de directe koppeling die wordt vermeld in de [AEM Forms-releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html), opent u AEM Package Manager, klikt u op Pakket **** uploaden, selecteert u het gedownloade pakket en klikt u op Uploaden. Nadat het pakket is geüpload, klikt u op de pakketnaam en klikt u op **Installeren.**

      >[!NOTE]
      >
      >Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM-instantie opnieuw te starten. **Stop niet onmiddellijk de server.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer worden weergegeven in het bestand &lt;crx-repository>/error.log en het logbestand stabiel is. Houd er rekening mee dat een aantal pakketten in de installatiestatus kunnen blijven staan. U kunt de status van deze verpakkingen veilig negeren.

   1. Start de AEM-instantie opnieuw.

1. Voer activiteiten na de installatie uit.

   * **Migratiehulpprogramma uitvoeren**

      Het migratiehulpprogramma maakt de adaptieve formulieren en correspondentiebeheermiddelen van eerdere versies compatibel met AEM 6.5-formulieren. U kunt het hulpprogramma downloaden van AEM-pakketten delen. Voor geleidelijke informatie om het migratienut te vormen en te gebruiken, zie [migratienut](../../forms/using/migration-utility.md).

      Als u [Steekproef voor het integreren van concepten &amp; verzendingscomponent](https://helpx.adobe.com/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) met het gegevensbestand en bevordering van een vorige versie gebruikt, dan stel de volgende SQL vragen na het uitvoeren van de verbetering in werking:

      ```
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(Als u alleen een upgrade uitvoert vanuit AEM 6.2 Forms of eerdere versies, dient u Adobe Sign opnieuw te configureren**

      Als Adobe Sign was geconfigureerd in de vorige versie van AEM Forms, configureert u Adobe Sign vervolgens opnieuw vanuit AEM Cloud Services. Zie [Adobe Sign with AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)integreren voor meer informatie.

   * **Ondersteuning voor jQuery**

      In AEM 6.5 Forms wordt de versie van jQuery bijgewerkt naar 3.2.1 en de versie van jQuery UI wordt bijgewerkt naar 1.12.1. AEM-formulier gebruikt JQuery in de modus **Geen conflict** . Als u dus een andere jQuery-versie gebruikt, worden er geen problemen weergegeven tijdens het uitvoeren van een upgrade. Wanneer u echter een upgrade uitvoert naar AEM 6.5 Forms:

      * Controleer of uw aangepaste componenten, indien aanwezig, compatibel zijn met ondersteunde jQuery-versies.
      * Verwijder niet-ondersteunde API&#39;s uit de aangepaste componenten. Zie [upgradehandleiding](https://jquery.com/upgrade-guide/3.0/) voor de lijst met verwijderde API&#39;s. Ondersteuning voor de API&#39;s load(), .unload() en .error() wordt bijvoorbeeld verwijderd. Gebruik de methode .on() in plaats van de eerder genoemde API&#39;s. Wijzig bijvoorbeeld $(&quot;img&quot;).load(fn) in $(&quot;img&quot;).on(&quot;load&quot;, fn).
   * **(Als u alleen een upgrade uitvoert van AEM 6.2 Forms of eerdere versies) Configureer analyses en rapporten opnieuw**

      In AEM 6.4 Vormen, zijn de verkeersvariabele voor bron en succesgebeurtenis voor indruk niet beschikbaar. Als u dus een upgrade uitvoert van AEM 6.2 Forms of eerdere versies, stopt AEM Forms met het verzenden van gegevens naar de Adobe Analytics-server en zijn er geen analyserapporten voor adaptieve formulieren beschikbaar. Bovendien introduceert AEM 6.4 Forms verkeersvariabele voor de versie van vormanalyse en succesgebeurtenis voor de hoeveelheid tijd die aan een gebied wordt doorgebracht. Zo, hervorm analyses en rapporten voor uw milieu van Vormen AEM. Voor gedetailleerde stappen, zie het [Vormen analyses en rapporten](../../forms/using/configure-analytics-forms-documents.md).


1. Controleer of de upgrade van de server is geslaagd, of alle gegevens zijn gemigreerd en of deze op de normale manier kunnen werken.

   * **Controleer de status van de bundels:** Zorg ervoor dat alle bundels actief zijn.
   * **Verifieer replicatie en omgekeerde replicatie:** Een aantal gemigreerde formulieren publiceren, invullen en verzenden. Controleer ook de verzonden gegevens.
   * **Toegang tot gebruikersinterfaces voor beheer en ontwikkelaar verifiëren:** Meld u aan bij een AEM-instantie via een beheerdersaccount en controleer of u toegang hebt tot de volgende URL&#39;s:

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`
   >[!NOTE]
   In AEM 6.4 Forms is de structuur van crx-gegevensopslagruimte gewijzigd. Als u een upgrade uitvoert van 6.3-formulieren naar AEM 6.5-formulieren, gebruikt u de gewijzigde paden voor aanpassing die u opnieuw maakt. Zie [Forms Repository Reform in AEM voor een volledige lijst met gewijzigde paden](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md).

