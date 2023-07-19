---
title: Hoe kan ik Adaptive Forms Core Components inschakelen op AEM 6.5 Forms?
seo-title: How to enable Adaptive Forms Core Components on AEM 6.5 Forms?
description: Stapsgewijze handleiding voor het inschakelen van adaptieve Forms Core Components in een AEM 6.5 Forms-omgeving.
seo-description: Step-by-Step guide to help you enable Adaptive Forms Core Components on an AEM 6.5 Forms environment.
keywords: Core Components, Core Components Adaptive Forms, Core Components on 6.5, Adaptive Forms Core Components on AEM 6.5, AF Core Components on AEM 6.5, AEM 6.5 Forms Core Components
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
source-git-commit: 1b97dc536550da8904bc7da09e983e0722c42a3d
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 0%

---


# Adaptieve Forms Core-componenten inschakelen op AEM 6.5 Forms {#enable-adaptive-forms-core-components}

<span class="preview"> Adobe raadt u aan Core Components te gebruiken voor [Adaptieve Forms toevoegen aan een AEM Sites-pagina](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md) of aan [standalone adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md). </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | Dit artikel |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html) |

**Van toepassing op:** ✅ Adaptive Form Core Components ❎ Adaptive Form Foundation Components.

Door Adaptieve Forms Core-componenten in te schakelen kunt u beginnen met het maken, publiceren en leveren van [Adaptieve Forms met basis van kerncomponenten](create-an-adaptive-form-core-components.md) en [Forms zonder hoofdadapter](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) uit uw AEM 6.5 Forms-omgeving.

Om HAdaptive Forms Core Components op uw AEM 6.5 Forms-omgeving mogelijk te maken, stelt u een [Archetype 41 of hoger AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) gebaseerd project (met formulieropties ingeschakeld) op al uw instanties Auteur en Publiceren.

Dit artikel bevat gedetailleerde instructies voor het instellen en implementeren van een project op basis van Archetype 41 of hoger op uw AEM 6.5 Forms-omgeving om Adaptive Forms Core Components (Aangepaste Core-componenten) in te schakelen.


## Vereisten {#prerequisites}

Voordat u Adaptive Forms Core Components inschakelt in een AEM 6.5 Forms-omgeving:

* [Upgrade naar AEM 6.5 Forms Service Pack 16 (6.5.16.0) of hoger](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html).

* Installeer de nieuwste versie van [Apache Maven](https://maven.apache.org/download.cgi).

* Installeer een teksteditor zonder opmaak. Bijvoorbeeld, de Code van Microsoft Visual Studio.

## Maak en implementeer de nieuwste AEM archetype-project

Een AEM Archetype 41 of [later](https://github.com/adobe/aem-project-archetype) gebaseerd project en stel het aan elk van uw Auteur en Publish instanties op:

1. Meld u aan bij uw computer, waarbij u als beheerder uw AEM 6.5 Forms-exemplaar host en uitvoert.
1. Open de opdrachtprompt of terminal en voer de volgende opdracht uit om AEM aardetype-project te maken (met ingeschakelde formulieropties):

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
      -D aemVersion="6.5.15" 
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
      -D aemVersion="6.5.15" 
   ```

   Houd rekening met de volgende punten wanneer u de bovenstaande opdracht uitvoert:

   * Wijzig de waarde van de optie `aemVersion` eigenschap van `6.5.15.0` naar alles.

   * Stel de `archetypeVersion` eigenschap aan `41` of hoger. Voor de meest recente versie raadpleegt u de sectie over systeemvereisten in de [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) documentatie.

   * Werk het bevel bij om op de specifieke waarden voor uw milieu, met inbegrip van te wijzen `appTitle`, `appId`, en `groupId`. Stel ook de waarde van de optie  `includeFormsenrollment` eigenschap aan `y`. Als u Forms Portal gebruikt, stelt u de optie `includeExamples=y` om Forms Portal Core-componenten in uw project op te nemen.


1. (Alleen voor projecten die zijn gebaseerd op Archetype versie 41) Nadat het project Archetype AEM is gemaakt, schakelt u thema&#39;s in voor op Core Components gebaseerde Adaptive Forms. Thema&#39;s inschakelen:

   1. Open de [Projectmap Archetype AEM]/ui.apps/src/main/content/jcr_root/apps/__appId__/components/adaptiveForm/page/customheaderlibs.html voor bewerking:

   1. Voeg de volgende code toe op regel 21:

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![Bovengenoemde code toevoegen op regel 21](/help/forms/using/assets/code-to-enable-themes.png)

   1. Sla het bestand op en sluit het.

1. Project bijwerken met de nieuwste versie van Forms Core Components:

   1. Open de [Projectmap Archetype AEM]/pom.xml voor bewerken.
   1. Versie instellen van `core.forms.components.version` en `core.forms.components.af.version` tot [nieuwste Forms Core-componenten](https://github.com/adobe/aem-core-forms-components/tree/release/650) versie.

   1. Sla het bestand op en sluit het.


1. Nadat het project van Archetype van de AEM met succes wordt gecreeerd, bouw het plaatsingspakket voor uw milieu. Het pakket maken:

   1. Navigeer naar de hoofdmap van het project Archetype van uw AEM.

   1. Voer de volgende opdracht uit om het project Archetype AEM voor uw omgeving te maken:

      ```Shell
      mvn clean install
      ```

      ![archetypebuild-success](/help/forms/using/assets/corecomponent-build-successful.png)


   Nadat het project van Archetype van de AEM met succes wordt gebouwd, wordt een AEM Pakket geproduceerd. U kunt het pakket vinden op [Projectmap Archetype AEM]\all\target\[appid].all-[versie].zip

1. Gebruik de [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en) om [Projectmap Archetype AEM]\all\target\[appid].all-[versie].zip-pakket op alle instanties Auteur en Publiceren.

>[!NOTE]
>
>
>
> * Als u problemen ondervindt bij het openen van het aanmeldingsvenster op een publicatieexemplaar, kunt u het pakket installeren via Pakketbeheer. Probeer dan de URL: `http://[Publish Server URL]:[PORT]/system/console` om u aan te melden. Hierdoor hebt u toegang tot de aanmeldingspagina op een instantie Publish, zodat u kunt doorgaan met het installatieproces.
> * Verwijder of verwijder het project Archetype niet, nadat u het in uw omgeving hebt geïmplementeerd. Het Archetype-project is vereist om aangepaste en nieuwe Adaptive Forms Core Components-thema&#39;s aan uw omgeving toe te voegen.

De Core Components zijn ingeschakeld voor uw omgeving. Een lege, op componenten gebaseerde adaptieve formuliersjabloon en Canvas 3.0-thema worden geïmplementeerd in uw omgeving, zodat u [op Adaptieve Forms gebaseerde Core Components maken](create-an-adaptive-form-core-components.md).

## Veelgestelde vragen

### Wat zijn kerncomponenten?

De [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) zijn een reeks gestandaardiseerde WCM-componenten (Web Content Management) voor AEM om de ontwikkelingstijd te versnellen en de onderhoudskosten van uw websites te verlagen.

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