---
title: Hoe kan ik Adaptive Forms Core Components inschakelen op AEM 6.5 Forms?
description: Stapsgewijze handleiding voor het inschakelen van adaptieve Forms Core Components in een AEM 6.5 Forms-omgeving.
keywords: Core Components, Core Components Adaptive Forms, Core Components on 6.5, Adaptive Forms Core Components on AEM 6.5, AF Core Components on AEM 6.5, AEM 6.5 Forms Core Components
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
feature: Adaptive Forms,Core Components
exl-id: 6585ea71-6242-47d3-bc59-6f603cf507b6
solution: Experience Manager, Experience Manager Forms
source-git-commit: c75cd7a0cbd0c19fd10cc7512bbfa14fae1e4f92
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 0%

---

# Adaptieve Forms Core-componenten inschakelen op AEM 6.5 Forms {#enable-adaptive-forms-core-components}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/enable-adaptive-forms-core-components.html) |
| AEM 6.5 | Dit artikel |

<!--**Applies to:** ✅ Adaptive Form Core Components ❎ [Adaptive Form Foundation Components](/help/forms/using/create-adaptive-form.md).-->

Het toelaten van de AanpassingsComponenten van de Kern van Forms laat u beginnen, te publiceren en leverend [ de Componenten van de Kern gebaseerd AanpassingsForms ](create-an-adaptive-form-core-components.md) en [ Zwaarloze AanpassingsForms ](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) van uw AEM 6.5 milieu van Forms.

Om de Aangepaste Componenten van de Kern van Forms op uw AEM 6.5 Forms milieu toe te laten, opstelling en stel een [ AEM Archetype 41 of later ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) gebaseerd project (met toegelaten vormenopties) op elk van uw Auteur en publiceer instanties op.

Dit artikel bevat gedetailleerde instructies voor het instellen en implementeren van een op AEM Archetype 41 of hoger gebaseerd project in uw AEM 6.5 Forms-omgeving om Adaptive Forms Core Components in te schakelen. U kunt naar de lijst hieronder voor **AEM 6.5** compatibele versies voor het toelaten van de Componenten van de Kern van Forms verwijzen:

## Vereisten {#prerequisites}

Voordat u Adaptive Forms Core Components inschakelt in een AEM 6.5 Forms-omgeving:

* [ Verbetering aan AEM 6.5 Forms Service Pack 16 (6.5.16.0) of later ](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html).

* Installeer de recentste versie van [ Apache Maven ](https://maven.apache.org/download.cgi).

* Installeer een teksteditor zonder opmaak. Bijvoorbeeld, de Code van Microsoft Visual Studio.

## Het nieuwste AEM Archetype-project maken en implementeren

Om een archetype van AEM te creëren 41 of [ later ](https://github.com/adobe/aem-project-archetype) gebaseerd project en het op elk van uw Auteur en publiceer instanties op te stellen:

1. Meld u aan bij uw computer en host en voer uw AEM 6.5 Forms-exemplaar als beheerder uit.
1. Open de opdrachtregel of terminal en voer de volgende opdracht uit om een AEM Archetype-project te maken (met ingeschakelde formulieropties):

   * Microsoft Windows

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
      -D archetypeGroupId=com.adobe.aem ^
      -D archetypeArtifactId=aem-project-archetype ^
      -D archetypeVersion=41 ^
      -D appTitle="My Form" ^
      -D appId="myform" ^
      -D groupId="com.myform" ^
      -D includeFormsenrollment="y" ^
      -D aemVersion="6.5.23" 
   ```

   * Linux of Apple macOS

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
      -D archetypeGroupId=com.adobe.aem \
      -D archetypeArtifactId=aem-project-archetype \
      -D archetypeVersion=41 \
      -D appTitle="My Form" \
      -D appId="myform" \
      -D groupId="com.myform" \
      -D includeFormsenrollment="y" \
      -D aemVersion="6.5.23" 
   ```

   Houd rekening met de volgende punten wanneer u de bovenstaande opdracht uitvoert:

   * Stel de eigenschap `archetypeVersion` in op `41` of hoger. Voor recentste versie, zie de sectie van systeemvereisten in [ AEM Project Archetype ](https://github.com/adobe/aem-project-archetype) documentatie.

   * Werk de opdracht bij om de specifieke waarden voor uw omgeving weer te geven, inclusief `appTitle` , `appId` en `groupId` . Stel ook de waarde van de eigenschap `includeFormsenrollment` in op `y` . Als u Forms Portal gebruikt, stelt u de optie `includeExamples=y` zo in dat Forms Portal Core-componenten in uw project worden opgenomen.


1. (Alleen voor projecten die zijn gebaseerd op Archetype versie 41) Nadat het AEM Archetype-project is gemaakt, schakelt u thema&#39;s in voor op Core Components gebaseerde Adaptive Forms. Thema&#39;s inschakelen:

   1. Open de ] /ui.apps/src/main/content/jcr_root/apps/__appId__ /components/adaptiveForm/page/customheaderlibs.html van het Project van de Archetype van AEM [.

   1. Voeg de volgende code toe op regel 21:

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![ voeg bovengenoemde code op lijn 21 toe ](/help/forms/using/assets/code-to-enable-themes.png)

   1. Sla het bestand op en sluit het.

1. Project bijwerken met de nieuwste versie van Forms Core Components:

   1. Open de [ Omslag van het Project van de Archetype van AEM ] /pom.xml voor het uitgeven.
   1. Reeks versie van `core.forms.components.version` en `core.forms.components.af.version` aan de [ recentste versie van de Componenten van de Kern van Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/version.html#aem-as-form-version-history) en zorg allebei de zelfde versie zoals **de Componenten van de Kern van Forms** vermeld in de lijst, en vastgestelde versie van `core.wcm.components.version` zoals gegeven in de [ Componenten van de Kern WCM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/versions.html) hebben.

      >[!WARNING]
      >
      >* Wanneer u een project Archetype maakt met versie 45, stelt `[AEM Archetype Project Folder]/pom.xml` in eerste instantie de versie van de kerncomponenten van het formulier in op 1.1.28. Voordat u het project Archetype gaat maken of implementeren, moet u de kerncomponentversie van de formulieren bijwerken naar versie 1.1.26. U kunt de recentste versie in [ AEM 6.5 Forms versiegeschiedenis ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/version.html#aem-as-form-version-history) vinden.

      >[!NOTE]
      >
      >* Als u opstelling een andere topologie, ervoor zorgt dat u verzend toevoegt, vooraf instelt, en andere URLs aan de lijst van gewenste personen bij de laag van Dispatcher.

   1. Sla het bestand op en sluit het.


1. Nadat het AEM Archetype-project met succes is gemaakt, bouwt u het implementatiepakket voor uw omgeving. Het pakket maken:

   1. Navigeer naar de hoofdmap van uw AEM Archetype-project.

   1. Voer de volgende opdracht uit om het AEM Archetype-project voor uw omgeving te maken:

      ```Shell
      mvn clean install
      ```

      ![ archetypebuild-success ](/help/forms/using/assets/corecomponent-build-successful.png)


   Nadat het AEM Archetype-project is voltooid, wordt een AEM Package gegenereerd. U kunt het pakket in [ Archetype van AEM de Omslag van het Project ] \all\target\ [appid].all- [ versie ] .zip vinden

1. Gebruik de [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en) om de [ Archetype Omslag van het Project van AEM ] \all\target\[appid].all- [ versie ] .zip pakket op alle Auteur op te stellen en instanties te publiceren.

>[!NOTE]
>
>
>
> * Als u problemen ondervindt bij het openen van het aanmeldingsvenster op een publicatieexemplaar, kunt u het pakket installeren via Package Manager. Probeer dan de URL: `http://[Publish Server URL]:[PORT]/system/console` te gebruiken om u aan te melden. Hierdoor hebt u toegang tot de aanmeldingspagina op een instantie Publiceren, zodat u verder kunt gaan met het installatieproces.
> * Verwijder of verwijder het project Archetype niet, nadat u het in uw omgeving hebt geïmplementeerd. Het Archetype-project is vereist om aangepaste en nieuwe Adaptive Forms Core Components-thema&#39;s aan uw omgeving toe te voegen.

De Core Components zijn ingeschakeld voor uw omgeving. Een lege die Componenten van de Kern op het Adaptieve malplaatje van de Vorm en het thema van Canvas 3.0 worden opgesteld aan uw milieu, toelatend u om [ tot de Componenten van de Kern te leiden die Adaptieve Forms ](create-an-adaptive-form-core-components.md) worden gebaseerd.

## Veelgestelde vragen

### Wat zijn kerncomponenten?

De [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) zijn een reeks gestandaardiseerde componenten van het Beheer van de Inhoud van het Web (WCM) voor AEM om ontwikkelingstijd te versnellen en onderhoudskosten van uw websites te drukken.

### Wat zijn alle mogelijkheden toegevoegd aan het toelaten van kerncomponenten?


Wanneer de Adaptive Forms Core Components voor uw omgeving is ingeschakeld, worden een leeg, op Core Components gebaseerd adaptief formulier sjabloon en Canvas 3.0 thema toegevoegd aan uw omgeving. Nadat u Adaptive Forms Core Components voor uw omgeving hebt ingeschakeld, kunt u:

* Creëer op basis van adaptieve Forms Core Components.
* Op kerncomponenten gebaseerde adaptieve formuliersjablonen maken.
* Aangepaste thema&#39;s maken voor adaptieve formuliersjablonen die zijn gebaseerd op kerncomponenten.
* De JSON-representaties van de Serve Core Component gebaseerd op adaptieve formulieren naar kanalen zoals mobiel, web, native apps en services waarvoor een weergave zonder kop nodig is.

## Volgende functies

* [Een adaptief formulier op basis van kerncomponenten maken](/help/forms/using/create-an-adaptive-form-core-components.md)
* [Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina of -ervaringsfragment](create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Thema&#39;s maken voor adaptieve Forms op basis van Core Components](create-or-customize-themes-for-adaptive-forms-core-components.md)
* [Een sjabloon maken voor Adaptief Forms op basis van Core Components](template-editor.md)
