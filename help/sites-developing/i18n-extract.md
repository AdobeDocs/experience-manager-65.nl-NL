---
title: Tekenreeksen uitnemen voor vertaling
seo-title: Tekenreeksen uitnemen voor vertaling
description: Met de Xgettext-maven-plug-in kunt u tekenreeksen uit uw broncode extraheren die moeten worden vertaald
seo-description: Met de Xgettext-maven-plug-in kunt u tekenreeksen uit uw broncode extraheren die moeten worden vertaald
uuid: 2c586ecb-8494-4f8f-b31a-1ed73644d611
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
discoiquuid: 034f70f1-fbd2-4f6b-b07a-5758f0461a5b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Tekenreeksen uitnemen voor vertaling{#extracting-strings-for-translating}

Gebruik de xgettext-maven-plug-in om tekenreeksen uit uw broncode te extraheren die moeten worden vertaald. Met de plug-in Maven worden tekenreeksen geëxtraheerd naar een XLIFF-bestand dat u verzendt voor vertaling. Tekenreeksen worden geëxtraheerd van de volgende locaties:

* Java-bronbestanden
* Javascript-bronbestanden
* XML-representaties van SVN-bronnen (JCR-knooppunten)

## Tekenreeksovername configureren {#configuring-string-extraction}

Configureer hoe de functie voor het insteekmodule xgettext-maven tekenreeksen voor uw project extraheert.

```xml
/filter { }
/parsers {
   /vaultxml { }
   /javascript { }
   /regexp {
      /files {
         /java { }
         /jsp { }
         /extjstemplate { }
      }
   }
}
/potentials { }
```

| Sectie | Beschrijving |
|---|---|
| /filter | Hiermee worden de geparseerde bestanden aangegeven. |
| /parsers/vaultxml | Hiermee configureert u het parseren van Vault-bestanden. Identificeert de JCR-knooppunten die extern gegeneraliseerde tekenreeksen en lokalisatietips bevatten. Identificeert ook JCR-knooppunten die moeten worden genegeerd. |
| /parsers/javascript | Identificeert de JavaScript-functies die tekenreeksen extern maken. U hoeft deze sectie niet te wijzigen. |
| /parsers/regexp | Vormt het ontleden van Java-, JSP-, en ExtJS malplaatjedossiers. U hoeft deze sectie niet te wijzigen. |
| /potentials | De formule voor het detecteren van tekenreeksen die moeten worden geïnternationaliseerd. |

### De te parseren bestanden identificeren {#identifying-the-files-to-parse}

Het /filter gedeelte van het i18n.any-bestand identificeert de bestanden die met het gereedschap Xgettext-maven-plugin worden geparseerd. Voeg verschillende include- en uitsluitingsregels toe die respectievelijk geparseerde en genegeerde bestanden identificeren. Neem alle bestanden op en sluit de bestanden uit die u niet wilt parseren. Gewoonlijk sluit u bestandstypen uit die geen bijdrage leveren aan de interface, of bestanden die wel UI definiëren maar niet worden omgezet. De regels include en exclude hebben de volgende indeling:

```
{ /include "pattern" }
{ /exclude "pattern" }
```

Het patroongedeelte van een regel wordt gebruikt om de namen van de bestanden die moeten worden opgenomen of uitgesloten, te benaderen. Het patroonvoorvoegsel geeft aan of u overeenkomt met een JCR-knooppunt (de weergave in de vault) of met het bestandssysteem.

| Voorvoegsel | Effect |
|---|---|
| / | Geeft een JCR-pad aan. Dit voorvoegsel komt daarom overeen met bestanden onder de map jcr_root. |
|  &amp;ast; | Geeft een normaal bestand op het bestandssysteem aan. |
| none | Geen voorvoegsel of patroon dat begint met een map of bestandsnaam, geeft een normaal bestand op het bestandssysteem aan. |

Bij gebruik in een patroon geeft het teken / een submap en het teken &amp;ast aan; alle tekens. In de volgende tabel staan verschillende voorbeeldregels.

<table>
 <tbody>
  <tr>
   <th>Voorbeeldregel</th>
   <th>Effect</th>
  </tr>
  <tr>
   <td><code>{ /include "*" }</code></td>
   <td>Alle bestanden opnemen.</td>
  </tr>
  <tr>
   <td><code>{ /exclude "*.pdf" }</code></td>
   <td>Sluit alle PDF-bestanden uit.</td>
  </tr>
  <tr>
   <td><code> { /exclude "*/pom.xml" }</code></td>
   <td>POM-bestanden uitsluiten.</td>
  </tr>
  <tr>
   <td><code class="code">{ /exclude "/content/*" }
      { /include "/content/catalogs/geometrixx/templatepages" }
      { /include "/content/catalogs/geometrixx/templatepages/*" }</code></td>
   <td><p>Sluit alle bestanden onder het knooppunt /content uit.</p> <p>Neem het knooppunt /content/catalogs/geometrixx/templatepages op.</p> <p>Inclusief alle onderliggende knooppunten van /content/catalogs/geometrixx/sjablonen.</p> </td>
  </tr>
 </tbody>
</table>

### De tekenreeksen extraheren {#extracting-the-strings}

geen POM:

```shell
mvn -N com.adobe.granite.maven:xgettext-maven-plugin:1.2.2:extract  -Dxgettext.verbose=true -Dxgettext.target=out -Dxgettext.rules=i18n.any -Dxgettext.root=.
```

Met POM: Dit toevoegen aan POM:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>com.adobe.granite.maven</groupId>
            <artifactId>xgettext-maven-plugin</artifactId>
            <version>1.1</version>
            <configuration>
                <rules>i18n.any</rules>
                <root>jcr_root</root>
                <xliff>cq.xliff</xliff>
                <verbose>true</verbose>
            </configuration>
        </plugin>
    </plugins>
</build>
```

de opdracht:

```shell
mvn xgettext:extract
```

### Uitvoerbestanden {#output-files}

* `raw.xliff`: geëxtraheerde tekenreeksen
* `warn.log`: eventuele waarschuwingen als de `CQ.I18n.getMessage()` API onjuist wordt gebruikt. Deze moeten altijd worden opgelost en vervolgens opnieuw worden uitgevoerd.

* `parserwarn.log`: parserwaarschuwingen (indien aanwezig), bv. JS-parserproblemen
* `potentials.xliff`: &quot;potentiële&quot; kandidaten die niet worden geëxtraheerd, maar leesbare tekenreeksen kunnen zijn die vertaald moeten worden (kan worden genegeerd, levert nog steeds een enorme hoeveelheid valse positieven op)
* `strings.xliff`: afgevlakt xliff-bestand, te importeren in ALF
* `backrefs.txt`: staat voor snelle raadpleging van broncodeplaatsen voor een bepaalde koord toe

