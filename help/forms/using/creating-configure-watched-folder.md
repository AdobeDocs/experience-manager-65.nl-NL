---
title: Een gecontroleerde map maken of configureren
description: Leer hoe u een controlemap maakt of verwijdert, of de eigenschappen van een bestaande controlemap wijzigt.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
exl-id: b15d8d3b-5e47-4c33-95fe-440fcf96be83
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1831'
ht-degree: 0%

---

# Een gecontroleerde map maken of configureren {#create-or-configure-a-watched-folder}

Een beheerder kan een netwerkomslag vormen, die als a *wordt bekend gecontroleerde omslag*, zodat wanneer een gebruiker een dossier (zoals een dossier van PDF) in de gelete op omslag plaatst, een pre-gevormde verrichting is begonnen en het dossier manipuleert. Nadat de opgegeven bewerking is uitgevoerd, slaat de bewerking het gewijzigde bestand op in een opgegeven uitvoermap. Voor gedetailleerde informatie over het beheren van een gelete op omslag, zie [ Hulp van het Beleid ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md).

U kunt de gebruikersinterface voor gecontroleerde mappen gebruiken voor:

* Een controlemap maken
* Eigenschappen van een bestaande controlemap wijzigen
* Een gecontroleerde map verwijderen

## Een controlemap maken {#create-a-watched-folder}

Controleer het volgende voordat u een gecontroleerde map configureert:

* Gecontroleerde mappen zijn een geavanceerde functie voor AEM formulieren. U kunt hiervoor AEM formulierinvoegpakket gebruiken. Zorg ervoor dat het juiste AEM Forms-invoegtoepassingspakket is geïnstalleerd en geconfigureerd.
* U kunt de controlemap maken op een gedeelde opslag of op een lokale opslaglocatie. Zorg ervoor dat AEM gebruiker die is geconfigureerd om de gecontroleerde map uit te voeren, lees- en schrijfmachtigingen heeft voor de gecontroleerde map.
* U kunt een service, workflow of script gebruiken om een bewerking met een gecontroleerde map te automatiseren. Zorg ervoor dat de bijbehorende service, workflow of een script is gemaakt en klaar is om te worden uitgevoerd. Voor informatie over het creëren van de Dienst, het Werkschema, en het Manuscript, zie [ Diverse methodes om dossiers ](/help/forms/using/watched-folder-in-aem-forms.md#various-methods-for-processing-files) te verwerken.
* Een gecontroleerde omslag heeft diverse eigenschappen, zie [ Gecontroleerde Eigenschappen van de Omslag ](watched-folder-in-aem-forms.md#watchedfolderproperties).

Voer de volgende stappen uit om een controlemap te maken:

1. Selecteer **Adobe Experience Manager** pictogram op de upper-left hoek van het scherm.
1. Selecteer **Hulpmiddelen** > **Forms** > **Vorm Gecontroleerde Omslag.** Er wordt een lijst met al geconfigureerde gecontroleerde mappen weergegeven.
1. Selecteer **Nieuw**. Er wordt een lijst weergegeven met velden die vereist zijn om de controlemap te maken:

   * **Naam**: Identificeert de gecontroleerde omslag. Gebruik voor de naam alleen alfanumerieke tekens.
   * **Weg**: Specificeert de gecontroleerde omslagplaats. In een gegroepeerd milieu, moet dit plaatsen aan een gedeelde netwerkomslag richten die voor elke gebruiker toegankelijk is die AEM op verschillende knopen van een cluster in werking stelt.
   * **Dossiers die van het Proces** gebruiken: Het type van het te beginnen proces. U kunt werkschema, manuscript, of de dienst specificeren.
   * **de Naam van de Dienst/de Weg van het Manuscript van het Manuscript/van het Werkschema**: Het gedrag van het gebied is gebaseerd op de waarde die voor de **Dossiers van het Proces wordt gespecificeerd die** gebied gebruiken. U kunt de volgende waarden opgeven:

      * Geef voor Workflow het workflowmodel op dat moet worden uitgevoerd. Bijvoorbeeld /etc/workflow/models/&lt;workflow_naam>/jcr:content/model
      * Geef bij Script het JCR-pad op van het script dat moet worden uitgevoerd. Bijvoorbeeld /etc/watchfolder/test/testScript.ecma
      * Voor de Dienst, specificeer de filter die voor de plaats van de plaats van een dienst OSGi wordt gebruikt. De service is geregistreerd als een implementatie van com.adobe.aemfd.watchfolder.service.api.ContentProcessor Interface. De volgende code is bijvoorbeeld een aangepaste implementatie van de interface ContentProcessor met een aangepaste eigenschap (foo=bar).

   >[!NOTE]
   >
   >Als u **de Dienst** voor het **Gebruik van de Dossiers van het Proces** gebied hebt geselecteerd, moet de waarde van het gebied van de Naam van de Dienst (inputProcessorType) tussen haakjes worden ingesloten. Bijvoorbeeld (foo=bar).

   ```java
   @Component(metatype = true, immediate = true, label = "WF Test Service", description = "WF Test Service")
   @Service(value = {OutputWriter.class, ContentProcessor.class})
   @Property(name = "foo", value = "bar")
   public class OutputWriter implements ContentProcessor {
   ```

   * **Patroon van het Dossier van de Output**: specificeer een puntkomma (;) afgebakende lijst van patronen die een gecontroleerde omslag gebruikt om de naam en de plaats van outputdossiers en omslagen te bepalen. Voor meer informatie over dossierpatronen, zie [ Ongeveer dossierpatronen ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).

1. Selecteer **Geavanceerd**. Het geavanceerde tabblad bevat meer velden. De meeste van deze velden bevatten een standaardwaarde.

   * **Filter van de Toewijzing van de Lading:** wanneer u een gelete op omslag creeert, leidt het tot een omslagstructuur binnen de omslag die wordt gecontroleerd. De mapstructuur heeft mappen voor werkgebied, resultaat, behoud, invoer en mislukking. De mappenstructuur kan dienen als invoerlading aan het werkschema en output van een werkschema goedkeuren. Het kan ook een lijst van mislukkingspunten maken, als om het even welk. De structuur van een lading is verschillend van de structuur van een gelete op omslag. U kunt aangepaste scripts schrijven om de structuur van een gecontroleerde map toe te wijzen aan de payload. Een dergelijk script wordt een payload mapfilter genoemd. Er zijn twee uitvoeringen beschikbaar voor de payload mapper box. Als u [ geen douaneimplementatie ](/help/forms/using/watched-folder-in-aem-forms.md#creating-a-custom-payload-mapper-filter) hebt, gebruik één van uit-van-de-doos implementatie:

      * **Standaard mapper:** gebruik standaard ladingkaart om input en outputinhoud van de gecontroleerde omslagen in afzonderlijke input en outputomslagen in de lading te houden.
      * **Eenvoudige op dossier-gebaseerde payload mapper:** gebruik de Eenvoudige op dossier-gebaseerde payload mapper om input en outputinhoud in de ladingsomslag direct te houden. Er wordt geen extra hiërarchie gemaakt, zoals de standaardmapper.

   * **Wijze van de Looppas**: Specificeer de komma-gescheiden lijst van toegestane looppas-wijzen voor werkschemauitvoering.
   * **Tijd uit Staged Dossiers na**: Specificeer het aantal seconden om te wachten alvorens een inputdossier/een omslag die reeds voor verwerking is opgepikt wordt behandeld zoals uit vastgesteld en duidelijk als mislukking. Het time-outmechanisme activeert alleen wanneer de waarde voor deze eigenschap een positief getal is.
   * **Schrapping Timed-out Staged Dossiers toen Verdraaide**: Als toegelaten, wordt de **Tijd uit Staged Dossiers na** mechanisme geactiveerd slechts wanneer het vertragen voor de gelete op omslag wordt aangezet.
   * **de Omslag van de Invoer van het Scannen na om:** specificeer het tijdinterval, in seconden, voor het aftasten van de gecontroleerde omslag voor input. Tenzij de Throttle-instelling is ingeschakeld, moet het Interval van de opiniepeiling langer zijn dan de tijd voor het verwerken van een gemiddelde taak. Anders kan het systeem overbelast raken. De waarde van het interval moet groter dan of gelijk aan één zijn.
   * **Uitsluit het Patroon van het Dossier**: Specificeer een puntkomma (;) afgebakende lijst van patronen die een gecontroleerde omslag gebruikt om te bepalen welke dossiers en omslagen om te scannen en op te nemen. Bestanden of mappen met het opgegeven patroon worden niet gescand voor verwerking. Voor meer informatie over dossierpatronen, zie [ Ongeveer dossierpatronen ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **omvat het Patroon van het Dossier**: Specificeer een puntkomma (;) afgebakende lijst van patronen die de gecontroleerde omslag gebruikt om te bepalen welke omslagen en dossiers aan aftasten en op te nemen. Als het Include-bestandspatroon bijvoorbeeld input&amp;amp is;ast; worden alle bestanden en mappen opgehaald die overeenkomen met de invoer&ast;. De standaardwaarde is &amp;ast en geeft alle bestanden en mappen aan. Voor meer informatie over dossierpatronen, zie [ Ongeveer de Patronen van het Dossier ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **wacht Tijd:** specificeer tijd, in milliseconden, om te wachten alvorens u een omslag of een dossier aftasten nadat het wordt gecreeerd. Als de wachttijd bijvoorbeeld 3.600.000 milliseconden (een uur) is en het bestand een minuut geleden is gemaakt, wordt dit bestand opgepikt nadat 59 minuten zijn verstreken. De standaardwaarde is 0.

     Deze instelling is handig om ervoor te zorgen dat alle inhoud van een bestand of map naar de invoermap wordt gekopieerd. Als u bijvoorbeeld een groot bestand hebt dat moet worden verwerkt en het downloaden van het bestand duurt tien minuten, stelt u de wachttijd in op 10&ast;60 &ast;1000 milliseconden. Met dit interval wordt voorkomen dat de gecontroleerde map het bestand scant als het nog geen tien minuten oud is.

   * **de Resultaten van de Schrapping ouder dan:** specificeer tijd, in aantal dagen, om te wachten alvorens de Dossiers en omslagen ouder dan de gespecificeerde waarde te schrappen. Deze instelling is handig om ervoor te zorgen dat de resultaatmap niet vol wordt. De waarde -1 dagen geeft aan dat u de resultatenmap nooit wilt verwijderen. De standaardwaarde is -1.
   * **Naam van de Omslag van het Resultaat:** specificeer de naam van de omslag om de resultaten op te slaan. Als de resultaten niet in deze map worden weergegeven, controleert u de map met foutmeldingen. Alleen-lezen bestanden worden niet verwerkt en opgeslagen in de map met foutmeldingen. U kunt een absoluut of relatief pad gebruiken met de volgende bestandspatronen:

      * %F = voorvoegsel bestandsnaam
      * %E = bestandsnaamextensie
      * %Y = jaar (volledig)
      * %y = jaar (laatste twee cijfers)
      * %M = maand
      * %D = dag van de maand
      * %d = dag van het jaar
      * %H = uur (24-uurs klok)
      * %h = uur (12-uurs klok)
      * %m = minuut
      * %s = seconde
      * %l = millisecond
      * %R = willekeurig getal (tussen 0 en 9)
      * %P = proces- of taak-id
      * Als het op 17 juli 2009 bijvoorbeeld 8 uur &#39;s middags is en u C:/Test/WF0/failure/%Y/%M/%D/%H/ opgeeft, is de resultatenmap C:/Test/WF0/failure/2009/07/17/20.
      * Als het pad niet absoluut maar relatief is, wordt de map in de controlemap gemaakt. De standaardwaarde is result/%Y/%M/%D/. Dit is de resultatenmap in de gecontroleerde map. Voor meer informatie over dossierpatronen, zie [ Ongeveer dossierpatronen ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).

   * **Naam van de Omslag van de Mislukking:** specificeer de omslag waar de ontbroken dossiers worden bewaard. Deze locatie is altijd relatief ten opzichte van de gecontroleerde map. U kunt bestandspatronen gebruiken, zoals beschreven in Resultaatmap.
   * **de Naam van de Omslag van het Behoud:** specificeer de omslag waar de dossiers na succesvol aftasten en opname worden opgeslagen. Het pad kan een absolute, relatieve of null-map zijn. U kunt bestandspatronen gebruiken, zoals beschreven in Resultaatmap. De standaardwaarde is preserve/%Y/%M/%D/.
   * **Grootte van de Partij:** specificeer het aantal dossiers of omslagen dat per aftasten moet worden opgenomen. Hiermee wordt overbelasting op het systeem voorkomen. Het scannen van te veel bestanden in één keer kan ertoe leiden dat de toepassing vastloopt. De standaardwaarde is 2.

     Als het scaninterval klein is, scannen de threads de invoermap vaak. Als bestanden vaak in de controlemap worden neergezet, moet u het scaninterval klein houden. Als de dossiers niet vaak worden gelaten vallen, gebruik een groter aftasteninterval zodat de andere diensten de draden kunnen gebruiken.

   * **Throttle:** wanneer deze optie wordt toegelaten, beperkt het het aantal gelete op omslagbanen die vormen op om het even welk bepaald tijdstip AEM. De waarde voor Batchgrootte bepaalt het maximale aantal taken. Voor meer informatie, zie [ throttling ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-throttling)
   * **beschrijft Bestaande Dossiers met Vergelijkbare Naam**: Wanneer geplaatst aan Waar, worden de dossiers in de resultatenomslag en bewaren omslag beschreven. Wanneer ingesteld op Onwaar, worden bestanden en mappen met het numerieke indexachtervoegsel gebruikt voor de naam. De standaardwaarde is False.
   * **de Dossiers van het Behoud op Mislukking:** Wanneer geplaatst aan Waar, worden de inputdossiers bewaard als er mislukking is. De standaardwaarde is true.
   * **omvat Dossiers met Patroon:** specificeer een puntkomma (;) afgebakende lijst van patronen die de gecontroleerde omslag gebruikt om te bepalen welke omslagen en dossiers aan aftasten en op te nemen. Als bijvoorbeeld het Include-bestandspatroon wordt ingevoerd, worden alle bestanden en mappen opgehaald die overeenkomen met de invoer. Voor meer informatie, zie [ Hulp van het Beleid ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md)
   * **riep Asynchroon Gecontroleerde Omslag aan:** identificeert het aanroepingstype als asynchroon of synchroon. De standaardwaarde is asynchroon. Asynchroon wordt aanbevolen voor langlevende processen, terwijl synchroon wordt aanbevolen voor voorbijgaande of kortstondige processen.
   * **laat Gecontroleerde Omslag toe:** wanneer deze optie wordt toegelaten, wordt de controlemap toegelaten. De standaardwaarde is True.

## Eigenschappen van een bestaande controlemap wijzigen {#modify-properties-of-an-existing-watched-folder}

U kunt niet alleen de naam van de gecontroleerde map wijzigen, maar ook alle eigenschappen van een bestaande controlemap wijzigen. Voer de volgende stappen uit om eigenschappen van een bestaande controlemap te wijzigen:

1. Selecteer het **Adobe Experience Manager** pictogram op de hoogste-linkerhoek van het scherm.
1. Selecteer **Hulpmiddelen** > **Forms** > **Vorm Gecontroleerde Omslag.** Er wordt een lijst met al geconfigureerde gecontroleerde mappen weergegeven.
1. Voor de linkerkant van het Gecontroleerde scherm van de Omslag, selecteer de controleomslag en selecteer **uitgeven.** Er wordt een lijst weergegeven met velden die zijn vereist om de controlemap te maken. De gebieden die in het **Basis** Lusje worden vermeld zijn verplicht. Het geavanceerde tabblad bevat meer velden. De meeste van deze velden bevatten een standaardwaarde. U kunt deze eigenschappen naar wens wijzigen.
1. Na het wijzigen van de eigenschappen, uitgezochte **Update**. De gewijzigde eigenschappen worden opgeslagen.
