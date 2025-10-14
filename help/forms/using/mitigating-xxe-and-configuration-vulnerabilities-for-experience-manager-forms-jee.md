---
title: Het verminderen van XXE, de Configuratie van de Wijze van de Struts Dev, en de Vulnerabilities van de Uitvoering van de Verre Code voor AEM Forms op JEE
description: Het verminderen van de kwetsbaarheid van XXE, Configuratie, en de Verre Code van de Uitvoering voor AEM Forms op JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
exl-id: 9fade12f-a038-4fd6-8767-1c30966574c5
solution: Experience Manager, Experience Manager Forms
release-date: 2025-08-05T00:00:00Z
source-git-commit: 3f64cfa688ef1f0090b7ce0d821324593cbea693
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 3%

---

# Beperkende RCE (CVE-2025-49533), standaard-ontwikkelmodus configuratie (CVE-2025-54253), XXE (CVE-2025-54254) en kwetsbaarheden voor AEM Forms op JEE {#mitigating-xxe-configuration-rce-vulnerabilities-aem-forms}

## Snelle naslag

| **Niveau van de Gevolgen** | **beïnvloede Versies** | **Aanbevolen Actie** |
|---|---|---|
| **Kritiek** | AEM 6.5 Forms on JEE Service Pack 23 (6.5.23.0) | [&#x200B; installeer recentste hotfix &#x200B;](#option-1-for-users-on-version-65230-install-latest-hotfix) |
| **Kritiek** | AEM 6.5 Forms op JEE Service Pack 18 tot 22 (6.5.18.0 - 6.5.22.0) | [&#x200B; installeer manueel de moeilijke situaties &#x200B;](#option-2-for-users-on-65180---65220-manual-hotfix-installation) |
| **Kritiek** | AEM 6.5 Forms on JEE Service Pack 17 (6.5.17.0) of eerder | Voer een upgrade uit naar een ondersteunde versie van Service Pack en pas vervolgens de aanbevolen stappen voor het beperken van uw nieuwe versie toe |
| **niet Beïnvloed** | AEM Forms op OSGi, Workbench, Cloud Service | Geen actie vereist |

**Geadresseerde Vulnerabilities:**

- Uitvoering van externe code (CVE-2025-49533)
- Configuratiebeveiligingsproblemen (CVE-2025-54253)
- Verwerking externe entiteit (XXE) in XML (CVE-2025-54254)

## Overzicht

### Betrokken functies

| Kwetsbaarheid | Gevolgen | Betrokken onderdelen |
|---|---|---|
| **CVE-2025-49533**: De Verre Uitvoering van de Code | Niet-geverifieerde code-uitvoering in GetDocumentServlet | AEM 6.5 Forms on JEE Service Pack 23 (6.5.23.0) en eerder |
| **CVE-2025-54253**: De Problemen van de configuratie | Strues ontwikkelingsmodus ingeschakeld in admin UI | AEM 6.5 Forms on JEE Service Pack 23 (6.5.23.0) en eerder |
| **CVE-2025-54254**: XXE-verwerking | De module Documentbeveiliging biedt ongeoorloofde toegang tot bestanden | AEM 6.5 Forms on JEE Service Pack 23 (6.5.23.0) en eerder |


### Wat is niet van invloed

- Experience Manager Forms Workbench (alle versies)
- Experience Manager Forms op OSGi (alle versies)
- Experience Manager Forms as a Cloud Service

## Opties voor resolutie


### Voordat u begint

Maak een back-up van het EAR- of DSC-bestand dat u wilt wijzigen of bijwerken voordat u wijzigingen aanbrengt:

- Zoek het oorspronkelijke EAR- of DSC-bestand in de implementatiemap.
- Kopieer het bestand naar een beveiligde back-uplocatie buiten de implementatiemap.
- Zorg ervoor dat de back-up volledig en toegankelijk is voordat u verdergaat met updates.

Met deze voorzorg kunt u de oorspronkelijke staat herstellen voor het geval u tijdens het updateproces problemen ondervindt.

### Optie 1: (Voor gebruikers op versie 6.5.23.0) Nieuwste hotfix installeren

1. [&#x200B; Download hotfix voor 6.5.23.0](/help/release-notes/aem-forms-hotfix.md).
1. Volg standaard [&#x200B; hotfix/flardinstallatie instructies &#x200B;](/help/release-notes/jee-patch-installer-65.md)
1. Als u Documentbeveiliging (voorheen Rights Management) gebruikt op IBM WebSphere of Oracle WebLogic, stelt u de volgende Java-systeemeigenschap (JVM-argument) in voordat u de AEM Forms-server start:

   ```
   -Dcom.adobe.forms.jee.services.allowDoctypeDeclaration=true
   ```

1. De toepassingsserver opnieuw starten

### Optie 2: (Voor gebruikers met 6.5.18.0 - 6.5.22.0) Handmatige hotfix-installatie

+++Handmatige hotfix-installatie voor 6.5.18.0 via 6.5.22.0

**Stap 1: De download en trekt het Hotfix Pakket** uit

- Download [&#x200B; hotfix voor 6.5.18.0 - 6.5.22.](/help/release-notes/aem-forms-hotfix.md) van het Portaal van de Distributie van de Software van Adobe
- Lokaal extraheren

**Stap 2: Navigeer aan de Correcte Omslag van de Versie**

- Op basis van de versie Service Pack die op uw omgeving is geïnstalleerd, gaat u naar de overeenkomende map.

  Voorbeeld voor Service Pack 20 is de map:

  ```
  <extracted-hotfix>/SP20/
  ```

**Stap 3: Bepaal de plaats van de Folder van de Plaatsing**

- Ga op uw AEM Forms op de JEE-server naar:

  ```
  [AEM installation directory]/deploy
  ```

  Voorbeeld: `adobe/adobe-experience-manager-forms/deploy`



**Stap 4: Werk en vervang de dossiers van het EAR** bij

>[!BEGINTABS]

>[!TAB  JBoss ]

1. `adobe-core-jboss.ear` openen en `adminui.war` vervangen door

   ```
   adobe-xxe-configuration-hotfix/SP[version]/jboss/adminui.war
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/jboss/adminui.war`

1. Ga in de `adobe-core-jboss.ear` naar de `lib/` map en vervang `adobe-uisupport.jar` door:

   ```
   adobe-xxe-configuration-hotfix/SP[version]/adobe-uisupport.jar
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/adobe-uisupport.jar`

1. Sla het EAU op. Controleer of de wijzigingen correct zijn opgeslagen.


1. `adobe-edcserver-jboss.ear` vervangen door

   ```
   adobe-xxe-configuration-hotfix/SP[version]/jboss/adobe-edcserver-jboss.ear
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/jboss/adobe-edcserver-jboss.ear`

1. `adobe-forms-jboss.ear` vervangen door

   ```
   adobe-xxe-configuration-hotfix/SP[version]/jboss/adobe-forms-jboss.ear
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/jboss/adobe-forms-jboss.ear`



>[!TAB  WebLogic ]

1. `adobe-core-weblogic.ear` openen en `adminui.war` vervangen door

   ```
   adobe-xxe-configuration-hotfix/SP[version]/weblogic/adminui.war
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/weblogic/adminui.war`

1. In de `adobe-core-weblogic.ear` vervangt u `adobe-uisupport.jar` door:

   ```
   adobe-xxe-configuration-hotfix/SP[version]/adobe-uisupport.jar
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/adobe-uisupport.jar`

1. Sla het EAU op. Controleer of de wijzigingen correct zijn opgeslagen.


1. `adobe-edcserver-weblogic.ear` vervangen door

   ```
   adobe-xxe-configuration-hotfix/SP[version]/weblogic/adobe-edcserver-weblogic.ear
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/weblogic/adobe-edcserver-weblogic.ear`

1. `adobe-forms-weblogic.ear` vervangen door

   ```
   adobe-xxe-configuration-hotfix/SP[version]/weblogic/adobe-forms-weblogic.ear
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/weblogic/adobe-forms-weblogic.ear`

>[!TAB  WebSphere ]

1. `adobe-core-websphere.ear` openen en `adminui.war` vervangen door

   ```
   adobe-xxe-configuration-hotfix/SP[version]/websphere/adminui.war
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/websphere/adminui.war`

1. In de `adobe-core-websphere.ear` vervangt u `adobe-uisupport.jar` door:

   ```
   adobe-xxe-configuration-hotfix/SP[version]/adobe-uisupport.jar
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/adobe-uisupport.jar`

1. Sla het EAU op. Controleer of de wijzigingen correct zijn opgeslagen.


1. `adobe-edcserver-websphere.ear` vervangen door

   ```
   adobe-xxe-configuration-hotfix/SP[version]/websphere/adobe-edcserver-websphere.ear
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/websphere/adobe-edcserver-websphere.ear`

1. `adobe-forms-websphere.ear` vervangen door

   ```
   adobe-xxe-configuration-hotfix/SP[version]/websphere/adobe-forms-websphere.ear
   ```

   Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/websphere/adobe-forms-websphere.ear`

>[!ENDTABS]



**Stap 5: Update `adobe-rightsmanagement-<appserver>-dsc.jar` dossier met**

```
adobe-xxe-configuration-hotfix/SP[version]/<appserver>/adobe-rightsmanagement-<appserver>-dsc.jar
```

Bijvoorbeeld: `adobe-xxe-configuration-hotfix/SP20/jboss/adobe-rightsmanagement-jboss-dsc.jar`

**Stap 6: De extra Configuratie voor de Veiligheid van het Document op WebSphere en WebLogic**:

Als u Documentbeveiliging gebruikt (voorheen Rights Management), stelt u de volgende Java-systeemeigenschap (JVM-argument) in voordat u de AEM Forms-server start:

```
-Dcom.adobe.forms.jee.services.allowDoctypeDeclaration=true
```


**Stap 7: Voer de Manager van de Configuratie** opnieuw in

- Start de configuratiemanager om het bijgewerkte EAR opnieuw te implementeren en de hotfix toe te passen

+++

### Optie 3: (Voor gebruikers op 6.5.17.0 en eerder) Upgradepad

1. [Upgrade naar een ondersteunde versie van Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md)
1. Optie 1 of Optie 2 volgen op basis van uw nieuwe versie

## Verwijzingen

- [&#x200B; CWE-611: Onjuiste Beperking van de Verwijzing van de Entiteit van XML Externe &#x200B;](https://cwe.mitre.org/data/definitions/611.html)
- [&#x200B; CWE-16: Configuratie &#x200B;](https://cwe.mitre.org/data/definitions/16.html)
- [&#x200B; OWASP XXE Preventie het Blad &#x200B;](https://owasp.org/www-community/vulnerabilities/XML_External_Entity_XXE_Processing)
- [&#x200B; Beste praktijken van de Veiligheid van Adobe Experience Manager Forms &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=nl-NL)