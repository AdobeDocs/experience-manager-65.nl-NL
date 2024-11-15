---
title: De Universal Editor
description: Leer meer over de flexibiliteit van de Universal Editor en hoe deze uw ervaringen zonder kop kan helpen gebruiken met AEM 6.5.
feature: Developing
role: Developer
exl-id: 7bdf1fcc-02b9-40bc-8605-e6508a84d249
source-git-commit: 6301f0fdba9f7a6fa8fa998759b9ebad6b4fa9a6
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---


# De Universal Editor {#universal-editor}

Leer meer over de flexibiliteit van de Universal Editor en hoe deze uw ervaringen zonder kop kan helpen gebruiken met AEM 6.5.

## Overzicht {#overview}

De Universal Editor is een veelzijdige visuele editor die deel uitmaakt van Adobe Experience Manager Sites. Auteurs kunnen hiermee &#39;what-you-see-is-what-you-get&#39; (WYSIWYG)-bewerkingen uitvoeren voor een headless experience.

* Auteurs profiteren van de flexibiliteit van de Universal Editor, omdat deze ondersteuning biedt voor dezelfde consistente visuele bewerking voor alle vormen van inhoud zonder kop.
* Ontwikkelaars profiteren van de veelzijdigheid van de Universal Editor, omdat deze ook werkelijke ontkoppeling van de implementatie ondersteunt. Het stelt ontwikkelaars in staat om vrijwel elk kader of architectuur van hun keuze te gebruiken, zonder enige SDK of technologiebeperkingen op te leggen.

Gelieve te zien de [ documentatie van AEM as a Cloud Service op de Universele Redacteur ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) voor meer detail.

## Architectuur {#architecture}

De Universele Redacteur is de dienst die samen met AEM aan auteursinhoud volkomen werkt.

* De Universal Editor wordt gehost op `https://experience.adobe.com/#/aem/editor/canvas` en kan pagina&#39;s bewerken die zijn weergegeven door AEM 6.5.
* De AEM pagina wordt gelezen door de Universal Editor via de verzender van de AEM auteur-instantie.
* De Universal Editor Service, die op dezelfde host als de Dispatcher wordt uitgevoerd, schrijft wijzigingen terug naar de AEM auteur-instantie.

![ stroom van de Auteur gebruikend de Universele Redacteur ](assets/author-flow.png)

## Instellen {#setup}

Als u de Universal Editor wilt testen, moet u:

1. [Werk en vorm uw AEM auteursinstantie bij.](#update-configure-aem)
1. [Stel een lokale Universal Editor-service in.](#set-up-ue)
1. [Pas de verzender aan om de Universal Editor Service toe te staan.](#update-dispatcher)

Zodra u de opstelling hebt voltooid, kunt u [ instrument uw toepassingen om de Universele Redacteur te gebruiken.](#instrumentation)

### AEM bijwerken {#update-aem}

Service pack 21 of 22 en een functiepakket voor AEM zijn vereist om de Universal Editor met AEM 6.5 te kunnen gebruiken.

#### Nieuwste Service Pack toepassen {#latest}

Zorg ervoor dat u minstens de dienstpak 21 of 22 voor AEM 6.5 in werking stelt. U kunt het recentste de dienstpak van [ Distributie van de Software downloaden.](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)

#### Universal Editor-functiepakket installeren {#feature-pack}

Installeer het **Universele Pak van de Eigenschap van de Redacteur voor AEM 6.5** [ beschikbaar op de Distributie van de Software.](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/cq-6.5.21-universal-editor-1.0.0.zip)

Als u reeds de dienstpak 23 of hoger in werking stelt, is het eigenschappak niet noodzakelijk.

### Services configureren {#configure-services}

Het eigenschappak installeert een aantal nieuwe pakketten waarvoor extra configuratie nodig is.

#### Stel het kenmerk SameSite in voor het cookie `login-token` . {#samesite-attribute}

1. Open de Manager van de Configuratie.
   * `http://<host>:<port>/system/console/configMgr`
1. Bepaal de plaats van **Adobe graniet Symbolische de Handler van de Authentificatie** in de lijst en klik **verander de configuratiewaarden**.
1. In de dialoog, verander het **attribuut SameSite voor login-symbolische koekje** (`token.samesite.cookie.attr`) waarde in `Partitioned`.
1. Klik **sparen**.

#### Verwijder de optie `SAMEORIGIN` Kopteksten X-Frame. {#sameorigin}

1. Open de Manager van de Configuratie.
   * `http://<host>:<port>/system/console/configMgr`
1. Bepaal de plaats **Apache Sling HoofdServlet** in de lijst en klik **geef de configuratiewaarden** uit.
1. Schrap de `X-Frame-Options=SAMEORIGIN` waarde van het **Extra attribuut van de reactiekopballen** (`sling.additional.response.headers`) als het bestaat.
1. Klik **sparen**.

#### Vorm de de authentificatiemanager van de Vraag van de Adobe Granite. {#query-parameter}

1. Open de Manager van de Configuratie.
   * `http://<host>:<port>/system/console/configMgr`
1. Bepaal de plaats van **Adobe granite de Handler van de Authentificatie van de Vraag** in de lijst en klik **geef de configuratiewaarden** uit.
1. Op het **Pad** gebied (`path`), voeg `/` toe om toe te laten.
   * Een lege waarde maakt de authentificatiemanager onbruikbaar.
1. Klik **sparen**.

#### Definieer voor welke inhoudspaden of `sling:resourceTypes` de universele editor moet worden geopend. {#paths}

1. Open de Manager van de Configuratie.
   * `http://<host>:<port>/system/console/configMgr`
1. Bepaal de plaats van **Universele Dienst URL van de Redacteur** in de lijst en klik **geef de configuratiewaarden** uit.
1. Definieer voor welke inhoudspaden of `sling:resourceTypes` de universele editor moet worden geopend.
   * Op het **Universele gebied van de Toewijzing van de Redacteur die** opent, verstrek de wegen waarvoor de Universele Redacteur wordt geopend.
   * In **Sling:resourceTypes die door Universeel gebied van de Redacteur** zal worden geopend, verstrek een lijst van middelen die direct door de Universele Redacteur worden geopend.
1. Klik **sparen**.

AEM opent de Universal Editor voor pagina&#39;s die op deze configuratie zijn gebaseerd.

1. AEM controleert de toewijzingen onder `Universal Editor Opening Mapping` en als de inhoud zich onder de aldaar gedefinieerde paden bevindt, wordt de Universal Editor geopend.
1. Voor inhoud niet onder wegen die in `Universal Editor Opening Mapping` worden bepaald, AEM controleert als `resourceType` van de inhoud die in **worden bepaald Sling aanpast:resourceTypes die door Universele Redacteur** zullen worden geopend en als de inhoud één van die types aanpast, wordt de Universele Redacteur voor het bij `${author}${path}.html` geopend.
1. Anders opent AEM de Pagina-editor.

De volgende variabelen zijn beschikbaar om uw toewijzingen onder `Universal Editor Opening Mapping` te bepalen.

* `path`: Inhoudspad van de bron die moet worden geopend
* `localhost`: ExternalAlizer-item voor `localhost` zonder schema, bijvoorbeeld `localhost:4502`
* `author`: ExternalAlizer-item voor auteur zonder schema, bijvoorbeeld `localhost:4502`
* `publish`: ExternalAlizer-item voor publiceren zonder schema, bijvoorbeeld `localhost:4503`
* `preview`: ExternalAlizer-item voor voorvertoning zonder schema, bijvoorbeeld `localhost:4504`
* `env`: `prod`, `stage` `dev` op basis van de gedefinieerde uitvoeringsmodi voor Verschuiven
* `token`: Zoektoken vereist voor de `QueryTokenAuthenticationHandler`

Voorbeeldtoewijzingen:

* Open alle pagina&#39;s onder `/content/foo` op de AEM Auteur:
   * `/content/foo:${author}${path}.html?login-token=${token}`
   * Dit leidt tot het openen van `https://localhost:4502/content/foo/x.html?login-token=<token>`
* Open alle pagina&#39;s onder `/content/bar` op een externe NextJS-server, waarbij alle variabelen als informatie worden opgegeven
   * `/content/bar:nextjs.server${path}?env=${env}&author=https://${author}&publish=https://${publish}&login-token=${token}`
   * Dit leidt tot het openen van `https://nextjs.server/content/bar/x?env=prod&author=https://localhost:4502&publish=https://localhost:4503&login-token=<token>`

### Universal Editor-service instellen {#set-up-ue}

Met AEM bijgewerkt en geconfigureerd, kunt u een lokale Universal Editor-service instellen voor uw eigen lokale ontwikkeling en testen.

1. Installeer Node.js versie >=20.
1. De download en unpack de recentste Universele Dienst van de Redacteur van [ Distributie van de Software ](https://experienceleague.adobe.com/en/docs/experience-cloud/software-distribution/home)
1. Configureer Universal Editor Service via omgevingsvariabelen of `.env` -bestand.
   * [ zie de Universele documentatie van de Redacteur van AEM as a Cloud Service voor details.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/local-dev#setting-up-service)
   * Mogelijk moet u de optie `UES_MAPPING` gebruiken als interne IP-herschrijving vereist is.
1. Uitvoeren `universal-editor-service.cjs`

### Dispatcher bijwerken {#update-dispatcher}

Met AEM gevormd en een lokale Universele dienst die van de Redacteur in werking stellen, zult u een omgekeerde volmacht voor de nieuwe dienst [ in de dispatcher moeten toestaan.](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/dispatcher)

1. Pas het hostbestand van de auteurinstantie aan om een reverse-proxy op te nemen.

   ```html
   <IfModule mod_proxy.c>
    ProxyPass "/universal-editor" "http://localhost:8080"
    ProxyPassReverse "/universal-editor" "http://localhost:8080"
   </IfModule>
   ```

   >[!NOTE]
   >
   >8080 is de standaardpoort. Als u dit gebruikend de `UES_PORT` parameter in [ uw `.env` dossier veranderde, ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/local-dev#setting-up-service) u moet de havenwaarde hier dienovereenkomstig aanpassen.

1. Start Apache opnieuw.

## Uw app Instrument {#instrumentation}

Wanneer AEM bijgewerkt en een lokale Universal Editor-service actief is, kunt u inhoud zonder kop gaan bewerken met de Universal Editor.

Uw app moet echter van instrumenten zijn voorzien om te kunnen profiteren van de Universal Editor. Hierbij moeten metatags worden opgenomen om de editor op te geven hoe en waar de inhoud moet blijven bestaan. De details van deze instrumentatie zijn beschikbaar in de [ Universele documentatie van de Redacteur voor AEM as a Cloud Service.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/getting-started#instrument-page)

Wanneer u documentatie voor de Universal Editor met AEM as a Cloud Service volgt, zijn de volgende wijzigingen van toepassing wanneer u deze gebruikt met AEM 6.5.

* Het protocol in de metatag moet `aem65` in plaats van `aem` zijn.

  ```html
  <meta name="urn:adobe:aue:system:aemconnection" content={`aem65:${getAuthorHost()}`}/>
  ```

* Het universele eindpunt van de Dienst van de Redacteur moet via een metatag worden aangekondigd.

  ```html
  <meta name="urn:adobe:aue:config:service" content={`${getAuthorHost()}/universal-editor`}/>
  ```

* In de sectie `plugins` van de componentdefinitie moet `aem65` worden gebruikt in plaats van `aem` .

>[!TIP]
>
>Voor een uitvoerige gids voor ontwikkelaars die met de Universele Redacteur beginnen, te zien gelieve het document [ Universele Overzicht van de Redacteur voor AEM Ontwikkelaars ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/developer-overview) in de documentatie van AEM as a Cloud Service terwijl het houden van de noodzakelijke veranderingen nodig voor AEM 6.5 steun zoals vermeld in deze sectie.
