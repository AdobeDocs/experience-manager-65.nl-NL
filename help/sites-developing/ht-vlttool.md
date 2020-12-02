---
title: Het gereedschap VLT gebruiken
seo-title: Het gereedschap VLT gebruiken
description: Het Jackrabbit FileVault-hulpprogramma (VLT) is ontwikkeld door de Apache Foundation die de inhoud van een Jackrabbit/AEM-instantie toewijst aan uw bestandssysteem
seo-description: Het Jackrabbit FileVault-hulpprogramma (VLT) is ontwikkeld door de Apache Foundation die de inhoud van een Jackrabbit/AEM-instantie toewijst aan uw bestandssysteem
uuid: 579e7785-8b50-4366-b562-8e79b6451464
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: a76425e9-fd3b-4c73-80f9-0ebabb8fd94f
translation-type: tm+mt
source-git-commit: 2da3da1a36f074593e276ddd15ed8331239ab70f
workflow-type: tm+mt
source-wordcount: '2748'
ht-degree: 2%

---


# Hoe te om het Hulpmiddel te gebruiken VLT {#how-to-use-the-vlt-tool}

Het hulpprogramma Jackrabbit FileVault (VLT) is een hulpprogramma dat is ontwikkeld door de Apache Foundation[ en waarmee de inhoud van een Jackrabbit/AEM-instantie wordt toegewezen aan uw bestandssysteem. ](https://www.apache.org/) Het hulpmiddel VLT heeft gelijkaardige functies zoals de cliënt van het broncontrolesysteem (zoals een cliënt van de Subversion (SVN)), die normale controle, controle en beheersverrichtingen, evenals configuratieopties voor flexibele vertegenwoordiging van de projectinhoud verstrekt.

U voert het gereedschap VLT uit vanaf de opdrachtregel. In dit document wordt beschreven hoe u het gereedschap kunt gebruiken, inclusief hoe u aan de slag kunt en hoe u hulp kunt krijgen, en een lijst met alle [opdrachten](#vlt-commands) en beschikbare [opties](#vlt-global-options).

## Concepten en architectuur {#concepts-and-architecture}

Zie de pagina [FileVault Overview](https://jackrabbit.apache.org/filevault/overview.html) en [Vault FS](https://jackrabbit.apache.org/filevault/vaultfs.html) van de officiële [Apache Jackrabbit FileVault-documentatie](https://jackrabbit.apache.org/filevault/index.html) voor een uitgebreid overzicht van de concepten en structuur van het FileVault-gereedschap.

## Aan de slag met VLT {#getting-started-with-vlt}

Als u VLT wilt gaan gebruiken, moet u het volgende doen:

1. Installeer VLT, werk omgevingsvariabelen bij en werk algemene genegeerde subversiebestanden bij.
1. Stel de AEM opslagplaats in (als u dat nog niet hebt gedaan).
1. Bekijk de AEM opslagplaats.
1. Synchroniseren met de repository.
1. Test of de synchronisatie heeft gewerkt.

### Het gereedschap VLT installeren {#installing-the-vlt-tool}

Als u het gereedschap VLT wilt gebruiken, moet u het eerst installeren. Het is niet standaard geïnstalleerd omdat het een aanvullend gereedschap is. Daarnaast moet u de omgevingsvariabele van uw systeem instellen.

1. Download het archiefbestand FileVault van de [gegevensopslagruimte voor artefacten.](https://repo1.maven.org/maven2/org/apache/jackrabbit/vault/vault-cli/)
   >[!NOTE]
   >
   >De bron van het hulpmiddel VLT is [beschikbaar op GitHub.](https://github.com/apache/jackrabbit-filevault)
1. Extraheer het archief.
1. Voeg `<archive-dir>/vault-cli-<version>/bin` aan uw milieu `PATH` toe zodat de beveldossiers `vlt` of `vlt.bat` worden betreden zoals aangewezen. Bijvoorbeeld:

   `<aem-installation-dir>/crx-quickstart/opt/helpers/vault-cli-3.1.16/bin>`

1. Open een opdrachtregelshell en voer `vlt --help` uit. Zorg ervoor de output aan het volgende hulpscherm gelijkaardig is:

   ```shell
   vlt --help
   -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   Jackrabbit FileVault [version 3.1.16] Copyright 2013 by Apache Software Foundation. See LICENSE.txt for more information.
   -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   Usage:
     vlt [options] <command> [arg1 [arg2 [arg3] ..]]
   -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   
   Global options:
   
     -Xjcrlog <arg>           Extended JcrLog options (omit argument for help)
     -Xdavex <arg>            Extended JCR remoting options (omit argument for help)
     --credentials <arg>      The default credentials to use
     --update-credentials     if present the credentials-to-host list is updated in the ~/.vault/auth.xml
     --config <arg>           The JcrFs config to use
     -v (--verbose)           verbose output
     -q (--quiet)             print as little as possible
     --version                print the version information and exit
     --log-level <level>      the log4j log level
     -h (--help) <command>    print this help
   ```

Nadat u deze hebt geïnstalleerd, moet u algemene genegeerde subversiebestanden bijwerken. Bewerk uw SVN-instellingen en voeg het volgende toe:

```xml
[miscellany]
### Set global-ignores to a set of whitespace-delimited globs
### which Subversion will ignore in its 'status' output, and
### while importing or adding files and directories.
global-ignores = .vlt
```

### Het vormen van het Eind van het Karakter van de Lijn {#configuring-the-end-of-line-character}

VLT verwerkt automatisch het einde van regel (EOF) volgens de volgende regels:

* lijnen van dossiers die op het eind van Vensters met een `CRLF` worden gecontroleerd
* Bestandsregels die zijn uitgecheckt aan het Linux/Unix-uiteinde met een `LF`
* regels bestanden die worden toegewezen aan de repository eindigen met een `LF`

Om ervoor te zorgen dat VLT en SVN configuratie aanpassen, zou u `svn:eol-style` bezit aan `native` voor de uitbreiding van de dossiers moeten plaatsen die in de bewaarplaats worden opgeslagen. Bewerk uw SVN-instellingen en voeg het volgende toe:

```xml
[auto-props]
*.css = svn:eol-style=native
*.cnd = svn:eol-style=native
*.java = svn:eol-style=native
*.js = svn:eol-style=native
*.json = svn:eol-style=native
*.xjson = svn:eol-style=native
*.jsp = svn:eol-style=native
*.txt = svn:eol-style=native
*.html = svn:eol-style=native
*.xml = svn:eol-style=native
*.properties = svn:eol-style=native
```

### Bewaarplaats {#checking-out-the-repository} uitchecken

Ontdek de opslagplaats met behulp van het broncontrolesysteem. Typ in svn bijvoorbeeld het volgende (vervang de URI en het pad door de repository):

```shell
svn co https://svn.server.com/repos/myproject
```

### Synchroniseren met de gegevensopslagruimte {#synchronizing-with-the-repository}

U moet het bestand synchroniseren met de opslagplaats. Dit doet u als volgt:

1. Navigeer op de opdrachtregel naar `content/jcr_root`.
1. Ontdek de opslagplaats door het volgende te typen (uw poortnummer te vervangen door **4502** en uw beheerderswachtwoorden):

   ```shell
   vlt --credentials admin:admin co --force http://localhost:4502/crx
   ```

   >[!NOTE]
   >
   >De referenties hoeven slechts eenmaal te worden opgegeven bij het eerste afrekenen. Zij zullen dan in uw huisfolder binnen `.vault/auth.xml` worden opgeslagen.

### Testen of de synchronisatie {#testing-whether-the-synchronization-worked} heeft gewerkt

Nadat u de opslagplaats hebt uitgecheckt en gesynchroniseerd, moet u testen of alle functies correct werken. Een gemakkelijke manier om dit te doen is een **.jsp** dossier uit te geven en te zien of uw veranderingen na het bevestigen van de veranderingen worden weerspiegeld.

De synchronisatie testen:

1. Ga naar `.../jcr_content/libs/foundation/components/text`.
1. Bewerk iets in `text.jsp`.
1. De gewijzigde bestanden bekijken door `vlt st` te typen
1. De wijzigingen bekijken door `vlt diff text.jsp` te typen
1. De wijzigingen vastleggen: `vlt ci test.jsp`.
1. Laad een pagina met een tekstcomponent opnieuw en controleer of de wijzigingen aanwezig zijn.

## Hulp krijgen met het Hulpmiddel VLT {#getting-help-with-the-vlt-tool}

Na het installeren van het hulpmiddel VLT, kunt u tot zijn dossier van de Hulp van de bevellijn toegang hebben:

```shell
vlt --help
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Jackrabbit FileVault [version 3.1.16] Copyright 2013 by Apache Software Foundation. See LICENSE.txt for more information.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Usage:
  vlt [options] <command> [arg1 [arg2 [arg3] ..]]
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Global options:
  -Xjcrlog <arg>           Extended JcrLog options (omit argument for help)
  -Xdavex <arg>            Extended JCR remoting options (omit argument for help)
  --credentials <arg>      The default credentials to use
  --update-credentials     if present the credentials-to-host list is updated in the ~/.vault/auth.xml
  --config <arg>           The JcrFs config to use
  -v (--verbose)           verbose output
  -q (--quiet)             print as little as possible
  --version                print the version information and exit
  --log-level <level>      the log4j log level
  -h (--help) <command>    print this help
Commands:
  export                   Export the Vault filesystem
  import                   Import a Vault filesystem
  checkout (co)            Checkout a Vault file system
  status (st)              Print the status of working copy files and directories.
  update (up)              Bring changes from the repository into the working copy.
  info                     Displays information about a local file.
  commit (ci)              Send changes from your working copy to the repository.
  revert (rev)             Restore pristine working copy file (undo most local edits).
  resolved (res)           Remove 'conflicted' state on working copy files or directories.
  propget (pg)             Print the value of a property on files or directories.
  proplist (pl)            Print the properties on files or directories.
  propset (ps)             Set the value of a property on files or directories.
  add                      Put files and directories under version control.
  delete (del,rm)          Remove files and directories from version control.
  diff (di)                Display the differences between two paths.
  rcp                      Remote copy of repository content.
  sync                     Control vault sync service
  console                  Run an interactive console
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```

Voor hulp op een bepaald bevel, typ het hulpbevel dat door de naam van het bevel wordt gevolgd. Bijvoorbeeld:

```shell
vlt --help export
Usage:
 export -v|-t <arg>|-p <uri> <jcr-path> <local-path>

Description:
  Export the Vault filesystem mounted at <uri> to the local filesystem at <local-path>. An optional <jcr-path> can be specified in order to export just a sub tree.
  Example:
    vlt export http://localhost:4502/crx /apps/geometrixx myproject

Options:
  -v (--verbose)          verbose output
  -t (--type) <arg>       specifies the export type. either 'platform' or 'jar'.
  -p (--prune-missing)    specifies if missing local files should be deleted.
  <uri>                   mountpoint uri
  <jcr-path>              the jcr path
  <local-path>            the local path
```

## Gemeenschappelijke Taken die in VLT {#common-tasks-performed-in-vlt} worden uitgevoerd

Hier volgen enkele algemene taken die in VLT worden uitgevoerd. Voor gedetailleerde informatie over elk bevel zie individuele [commands](#vlt-commands).

### Een substructuur {#checking-out-a-subtree} uitchecken

Als u alleen een substructuur van de repository wilt uitchecken, bijvoorbeeld `/apps/geometrixx`, kunt u dit doen door het volgende te typen:

```shell
vlt co http://localhost:4502/crx/-/jcr:root/apps/geometrixx geo
```

Als u dit doet, wordt er een nieuwe exporthoofdmap `geo` gemaakt met een map `META-INF` en `jcr_root` en worden alle bestanden onder `/apps/geometrixx` in `geo/jcr_root` geplaatst.

### Uitchecken via filters {#performing-a-filtered-checkout} uitvoeren

Als u een bestaand werkruimtefilter hebt en u het voor controle wilt gebruiken, kunt u of eerst de `META-INF/vault` folder tot stand brengen en het filter daar plaatsen, of het specificeren op de bevellijn als volgt:

```shell
$ vlt co --filter filter.xml http://localhost:4502/crx/-/jcr:root geo
```

Een voorbeeldfilter:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<workspaceFilter version="1.0">
    <filter root="/etc/designs/geometrixx" />
    <filter root="/apps/geometrixx"/>
</workspaceFilter>
```

### Importeren/exporteren gebruiken in plaats van .vlt-besturingselement {#using-import-export-instead-of-vlt-control}

U kunt inhoud importeren en exporteren tussen een JCR-opslagplaats en het lokale bestandssysteem zonder besturingsbestanden te gebruiken.

Inhoud importeren en exporteren zonder `.vlt`-besturingselement te gebruiken:

1. Stel aanvankelijk de opslagplaats in:

   ```shell
   $ cd /projects
   $ svn mkdir https://svn.server.com/repos/myproject
   $ svn co https://svn.server.com/repos/myproject
   $ vlt export -v http://localhost:4502/crx /apps/geometrixx geometrixx
   $ cd geometrixx/
   $ svn add META-INF/ jcr_root/
   $ svn ci
   ```

1. Wijzig de externe kopie en werk de JCR bij:

   ```shell
   $ cd /projects/geometrixx
   $ vlt -v import http://localhost:4502/crx . /
   ```

1. Wijzig de externe kopie en werk de bestandsserver bij:

   ```shell
   $ cd /projects/geometrixx
   $ vlt export -v http://localhost:4502/crx /apps/geometrixx .
   $ svn st
   M      META-INF/vault/properties.xml
   M      jcr_root/apps/geometrixx/components/contentpage/.content.xml
   $ svn ci
   ```

## VLT {#using-vlt} gebruiken

Om bevelen in VLT uit te geven, typ het volgende bij de bevellijn:

```shell
vlt [options] <command> [arg1 [arg2 [arg3] ..]]  
```

Opties en opdrachten worden in de volgende secties uitgebreid beschreven.

## Algemene VLT-opties {#vlt-global-options}

Hieronder volgt een lijst met VLT-opties, die beschikbaar zijn voor alle opdrachten. Zie de afzonderlijke opdrachten voor meer informatie over extra beschikbare opties.

|  |  |
|--- |--- |
| Optie | Beschrijving |
| `-Xjcrlog <arg>` | Uitgebreide JcrLog-opties |
| `-Xdavex <arg>` | Uitgebreide opties voor JCR-verwijdering |
| `--credentials <arg>` | De standaardreferenties die moeten worden gebruikt |
| `--config <arg>` | De JcrFs-configuratie die moet worden gebruikt |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `--version` | Drukt de versieinformatie en uitgang VLT af |
| `--log-level <level>` | Geeft het logniveau aan, bijvoorbeeld het logniveau log4j. |
| `-h (--help) <command>` | Hiermee wordt de Help voor die opdracht afgedrukt |

## VLT-opdrachten {#vlt-commands}

In de volgende tabel worden alle beschikbare VLT-opdrachten beschreven. Zie de afzonderlijke opdrachten voor meer informatie over syntaxis, beschikbare opties en voorbeelden.

|  |  |  |
|--- |--- |--- |
| Opdracht | Afkorting van opdracht | Beschrijving |
| `export` |  | Exporteert van een JCR-opslagplaats (vault file system) naar het lokale bestandssysteem zonder controlebestanden. |
| `import` |  | Hiermee wordt een lokaal bestandssysteem geïmporteerd naar een JCR-opslagplaats (vault file system). |
| `checkout` | `co` | Hiermee wordt een Vault-bestandssysteem uitgecheckt. Gebruik dit voor een eerste JCR-opslagplaats naar het lokale bestandssysteem. (Opmerking: U moet de repository eerst uitchecken in subversion.) |
| `analyze` |  | Hiermee analyseert u pakketten. |
| `status` | `st` | Hiermee wordt de status van bestanden en mappen met werkkopieën afgedrukt. |
| `update` | `up` | Hiermee importeert u wijzigingen uit de opslagplaats in de werkkopie. |
| `info` |  | Geeft informatie weer over een lokaal bestand. |
| `commit` | `ci` | Hiermee verzendt u wijzigingen van uw werkkopie naar de opslagplaats. |
| `revert` | `rev` | Hiermee herstelt u de oorspronkelijke staat van het bestand met de werkkopie en maakt u de meeste lokale bewerkingen ongedaan. |
| `resolved` | `res` | Hiermee verwijdert u een conflicterende status uit werkkopiebestanden of -mappen. |
| `propget` | `pg` | Hiermee wordt de waarde van een eigenschap afgedrukt op bestanden of mappen. |
| `proplist` | `pl` | Hiermee worden de eigenschappen afgedrukt op bestanden of mappen. |
| `propset` | `ps` | Hiermee wordt de waarde van een eigenschap voor bestanden of mappen ingesteld. |
| `add` |  | Hiermee plaatst u bestanden en mappen onder versiebeheer. |
| `delete` | `del` or `rm` | Hiermee verwijdert u bestanden en mappen uit versiebeheer. |
| `diff` | `di` | Hiermee geeft u de verschillen tussen twee paden weer. |
| `console` |  | Hiermee wordt een interactieve console uitgevoerd. |
| `rcp` |  | Kopieert een knooppuntenstructuur van de ene externe opslagplaats naar een andere. |
| `sync` |  | Hiermee kunt u de vault sync-service besturen. |

### {#export} exporteren

Exporteert het Vault-bestandssysteem dat op &lt;uri> is geïnstalleerd naar het lokale bestandssysteem op &lt;local-path>. U kunt een optionele &lt;jcr-path> opgeven om alleen een substructuur te exporteren.

#### Syntaxis {#syntax}

```shell
export -v|-t <arg>|-p <uri> <jcr-path> <local-path>
```

#### Opties {#options}

|  |  |
|--- |--- |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-t (--type) <arg>` | Hiermee geeft u het exporttype op: platform of jar. |
| `-p (--prune-missing)` | geeft aan of ontbrekende lokale bestanden moeten worden verwijderd |
| `<uri>` | uri van het montagepunt |
| `<jcrPath>` | JCR-pad |
| `<localPath>` | lokaal pad |

#### Voorbeelden {#examples}

```shell
vlt export http://localhost:4502/crx /apps/geometrixx myproject
```

### Importeren {#import}

Hiermee wordt het lokale bestandssysteem geïmporteerd (vanaf `<local-path>` naar het vault-bestandssysteem op `<uri>`. U kunt een `<jcr-path>` opgeven als importbasis. Als `--sync` wordt gespecificeerd, worden de ingevoerde dossiers automatisch gezet onder controle van de kluis.

#### Syntaxis {#syntax-1}

```shell
import -v|-s <uri> <local-path> <jcr-path>
```

#### Opties {#options-1}

|  |  |
|--- |--- |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-s (-- sync)` | plaatst de lokale bestanden onder de vault-controle |
| `<uri>` | uri van het montagepunt |
| `<jcrPath>` | JCR-pad |
| `<localPath>` | lokaal pad |

#### Voorbeelden {#examples-1}

```shell
vlt import http://localhost:4502/crx . /
```

### Afhandeling (co) {#checkout-co}

Voert een eerste uitchecking uit van een JCR-opslagplaats naar het lokale bestandssysteem vanaf &lt;uri> naar het lokale bestandssysteem op &lt;local-path>. U kunt ook een &lt;jcrPath>-argument toevoegen om een submap van de externe boomstructuur uit te checken. Werkruimtefilters kunnen worden opgegeven die naar de map META-INF worden gekopieerd.

#### Syntaxis {#syntax-2}

```shell
checkout --force|-v|-q|-f <file> <uri> <jcrPath> <localPath>  
```

#### Opties {#options-2}

|  |  |
|--- |--- |
| `--force` | forceert uitchecken om lokale bestanden te overschrijven als deze al bestaan |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `-f (--filter) <file>` | Hiermee worden automatische filters opgegeven als er geen zijn gedefinieerd |
| `<uri>` | uri van het montagepunt |
| `<jcrPath>` | (optioneel) extern pad |
| `<localPath>` | (optioneel) lokaal pad |

#### Voorbeelden {#examples-2}

JCR-verwijdering gebruiken:

```shell
vlt --credentials admin:admin co http://localhost:8080/crx/server/crx.default/jcr_root/
```

Met de standaardwerkruimte:

```shell
vlt --credentials admin:admin co http://localhost:8080/crx/server/-/jcr_root/
```

Als URI onvolledig is, wordt deze uitgebreid:

```shell
vlt --credentials admin:admin co http://localhost:8080/crx
```

### {#analyze} analyseren

Hiermee analyseert u pakketten.

#### Syntaxis {#syntax-3}

```shell
analyze -l <format>|-v|-q <localPaths1> [<localPaths2> ...]
```

#### Opties {#options-3}

|  |  |
|--- |--- |
| `-l (--linkFormat) <format>` | printf-indeling voor hotfix-koppelingen (naam,id), bijvoorbeeld `[CQ520_HF_%s|%s]` |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `<localPaths> [<localPaths> ...]` | lokaal pad |

### Status {#status}

Hiermee wordt de status van bestanden en mappen met werkkopieën afgedrukt.

Als `--show-update` wordt gespecificeerd, wordt elk dossier gecontroleerd tegen de verre versie. De tweede letter geeft vervolgens aan welke actie door een updatebewerking wordt uitgevoerd.

#### Syntaxis {#syntax-4}

```shell
status -v|-q|-u|-N <file1> [<file2> ...]
```

#### Opties {#options-4}

|  |  |
|--- |--- |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `-u (--show-update)` | updategegevens weergeven |
| `-N (--non-recursive)` | werkt op één directory |
| `<file> [<file> ...]` | bestand of map om de status weer te geven |

### {#update} bijwerken

Hiermee worden wijzigingen van de opslagplaats naar de werkkopie gekopieerd.

#### Syntaxis {#syntax-5}

```shell
update -v|-q|--force|-N <file1> [<file2> ...]
```

#### Opties {#options-5}

|  |  |
|--- |--- |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `--force` | forceert het overschrijven van lokale bestanden |
| `-N (--non-recursive)` | werkt op één directory |
| `<file> [<file> ...]` | bestand of map dat moet worden bijgewerkt |

### Info {#info}

Geeft informatie weer over een lokaal bestand.

#### Syntaxis {#syntax-6}

```shell
info -v|-q|-R <file1> [<file2> ...]
```

#### Opties {#options-6}

|  |  |
|--- |--- |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `-R (--recursive)` | recursief |
| `<file> [<file> ...]` | bestand of map om informatie weer te geven |

### {#commit} vastleggen

Hiermee verzendt u wijzigingen van uw werkkopie naar de opslagplaats.

#### Syntaxis {#syntax-7}

```shell
commit -v|-q|--force|-N <file1> [<file2> ...]
```

#### Opties {#options-7}

|  |  |
|--- |--- |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `--force` | forceert het toezeggen zelfs als het verre exemplaar wordt gewijzigd |
| `-N (--non-recursive)` | werkt op één directory |
| `<file> [<file> ...]` | bestand of map om vast te leggen |

### {#revert} herstellen

Hiermee herstelt u het bestand met de werkkopie naar de oorspronkelijke staat en maakt u de meeste lokale bewerkingen ongedaan.

#### Syntaxis {#syntax-8}

```shell
revert -q|-R <file1> [<file2> ...]
```

#### Opties {#options-8}

|  |  |
|--- |--- |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `-R (--recursive)` | recursief afneemt |
| `<file> [<file> ...]` | bestand of map om vast te leggen |

### Opgelost {#resolved}

Hiermee verwijdert u de status **conflicted** uit werkkopiebestanden of -mappen.

>[!NOTE]
>
>Met deze opdracht worden conflicten niet semantisch opgelost of worden conflictiemarkeringen verwijderd. het verwijdert alleen de conflicterende artefactbestanden en staat toe dat PATH opnieuw wordt toegewezen.

#### Syntaxis {#syntax-9}

```shell
resolved -q|-R|--force <file1> [<file2> ...]  
```

#### Opties {#options-9}

|  |  |
|--- |--- |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `-R (--recursive)` | recursief afneemt |
| `--force` | lost op, zelfs als er conflicttellers zijn |
| `<file> [<file> ...]` | bestand of map om op te lossen |

### Propget {#propget}

Hiermee wordt de waarde van een eigenschap afgedrukt op bestanden of mappen.

#### Syntaxis {#syntax-10}

```shell
propget -q|-R <propname> <file1> [<file2> ...]
```

#### Opties {#options-10}

|  |  |
|--- |--- |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `-R (--recursive)` | recursief afneemt |
| `<propname>` | de eigenschapsnaam |
| `<file> [<file> ...]` | bestand of map om de eigenschap op te halen |

### Proplist {#proplist}

Hiermee worden de eigenschappen afgedrukt op bestanden of mappen.

#### Syntaxis {#syntax-11}

```shell
proplist -q|-R <file1> [<file2> ...]
```

#### Opties {#options-11}

|  |  |
|--- |--- |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `-R (--recursive)` | recursief afneemt |
| `<file> [<file> ...]` | bestand of map om de eigenschappen van |

### Propset {#propset}

Hiermee wordt de waarde van een eigenschap voor bestanden of mappen ingesteld.

>[!NOTE]
>
>VLT herkent de volgende speciale versioned eigenschappen:
>
>`vlt:mime-type`
>
>Het mimetype van het bestand. Wordt gebruikt om te bepalen of het bestand moet worden samengevoegd. Een mimetype dat begint met &#39;text/&#39; (of een afwezig mimetype) wordt behandeld als tekst. Al het andere wordt als binair beschouwd.

#### Syntaxis {#syntax-12}

```shell
propset -q|-R <propname> <propval> <file1> [<file2> ...]
```

#### Opties {#options-12}

|  |  |
|--- |--- |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `-R (--recursive)` | recursief afneemt |
| `<propname>` | de eigenschapsnaam |
| `<propval>` | de eigenschapswaarde |
| `<file> [<file> ...]` | bestand of map waarin de eigenschap moet worden ingesteld |

### Toevoegen {#add}

Hiermee plaatst u bestanden en mappen onder versiebeheer, zodat deze naast de opslagplaats worden gepland. Deze worden toegevoegd bij volgende commit.

#### Syntaxis {#syntax-13}

```shell
add -v|-q|-N|--force <file1> [<file2> ...]
```

#### Opties {#options-13}

|  |  |
|--- |--- |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `-N (--non-recursive)` | werkt op één directory |
| `--force` | de operatie moet worden uitgevoerd |
| `<file> [<file> ...]` | lokaal bestand of lokale map dat moet worden toegevoegd |

### Verwijderen {#delete}

Hiermee verwijdert u bestanden en mappen uit versiebeheer.

#### Syntaxis {#syntax-14}

```shell
delete -v|-q|--force <file1> [<file2> ...]
```

#### Opties {#options-14}

|  |  |
|--- |--- |
| `-v (--verbose)` | uitgebreide uitvoer |
| `-q (--quiet)` | zo weinig mogelijk afdrukken |
| `--force` | de operatie moet worden uitgevoerd |
| `<file> [<file> ...]` | lokaal te verwijderen bestand of map |

### Diff {#diff}

Hiermee geeft u de verschillen tussen twee paden weer.

#### Syntaxis {#syntax-15}

```shell
diff -N <file1> [<file2> ...]
```

#### Opties {#options-15}

|  |  |
|--- |--- |
| `-N (--non-recursive)` | werkt op één directory |
| `<file> [<file> ...]` | bestand of map om de verschillen weer te geven |

### Console {#console}

Hiermee wordt een interactieve console uitgevoerd.

#### Syntaxis {#syntax-16}

```shell
console -F <file>
```

#### Opties {#options-16}

|  |  |
|--- |--- |
| `-F (--console-settings) <file>` | geeft het bestand met consolemontages aan. Het standaardbestand is console.properties. |

### Rcp {#rcp}

Kopieert een knooppuntenstructuur van de ene externe opslagplaats naar een andere. `<src>` wijst naar het bronknooppunt en  `<dst>` geeft het doelpad aan, waar het bovenliggende knooppunt moet bestaan. Rcp verwerkt de knopen door de gegevens te stromen.

#### Syntaxis {#syntax-17}

```shell
rcp -q|-r|-b <size>|-t <seconds>|-u|-n|-e <arg1> [<arg2> ...] <src> <dst>
```

#### Opties {#options-17}

|  |  |
|--- |--- |
| `-q (--quiet)` | Drukt zo weinig mogelijk af. |
| `-r (--recursive)` | Vervalt recursief. |
| `-b (--batchSize) <size>` | Aantal knooppunten dat moet worden verwerkt vóór een tussentijdse opslag. |
| `-t (--throttle) <seconds>` | Aantal seconden dat moet worden gewacht na een tussentijdse opslag. |
| `-u (--update)` | Bestaande knooppunten overschrijven/verwijderen. |
| `-n (--newer)` | De eigenschappen lastModified voor update respecteren. |
| `-e (--exclude) <arg> [<arg> ...]` | Regexp van uitgesloten bronpaden. |
| `<src>` | Het opslagplaats adres van de bronboom. |
| `<dst>` | Het opslagplaats adres van de bestemmingsknoop. |

#### Voorbeelden {#examples-3}

```shell
vlt rcp http://localhost:4502/crx/-/jcr:root/content  https://admin:admin@localhost:4503/crx/-/jcr:root/content_copy  
```

>[!NOTE]
>
>De `--exclude` opties moeten door een andere optie vóór `<src>` en `<dst>` argumenten worden gevolgd. Bijvoorbeeld:
>
>`vlt rcp -e ".*\.txt" -r`

### Synchroniseren {#sync}

Hiermee kunt u de vault sync-service besturen. Zonder argumenten probeert deze opdracht de huidige werkmap onder synchronisatiecontrole te zetten. Indien uitgevoerd binnen een vlt controle, gebruikt het de respectieve filter en gastheer om de synchronisatie te vormen. Als deze buiten een vlt-uitchecking wordt uitgevoerd, wordt de huidige map alleen geregistreerd voor synchronisatie als de map leeg is.

#### Syntaxis {#syntax-18}

```shell
sync -v|--force|-u <uri> <command> <localPath>
```

#### Opties {#options-18}

|  |  |
|--- |--- |
| `-v (--verbose)` | uitgebreide uitvoer. |
| `--force` | bepaalde opdrachten uitvoeren. |
| `-u (--uri) <uri>` | geeft de URI van de synchronisatiehost aan. |
| `<command>` | uit te voeren synchronisatieopdracht. |
| `<localPath>` | lokale map die moet worden gesynchroniseerd. |

### Statuscodes {#status-codes}

De statuscodes die door VLT worden gebruikt zijn:

* &#39; Geen wijzigingen
* &#39;A&#39; toegevoegd
* C-conflict
* &#39;D&#39; Verwijderd
* &#39;I&#39; genegeerd
* &#39;M&#39; gewijzigd
* &quot;R&quot; vervangen
* &#39;?&#39; item bevindt zich niet onder versiebeheer
* &#39;!&#39; item ontbreekt (verwijderd door niet-svn-opdracht) of is onvolledig
* &#39;~&#39; versioned item geblokkeerd door een ander item

## FileVault-synchronisatie instellen {#setting-up-filevault-sync}

De vault sync-service wordt gebruikt om inhoud in de opslagplaats te synchroniseren met een lokale bestandssysteemweergave en andersom. Dit wordt bereikt door een OSGi-service te installeren die luistert naar wijzigingen in de opslagplaats en de inhoud van het bestandssysteem periodiek zal scannen. Het gebruikt het zelfde rangschikkingsformaat zoals vault voor het in kaart brengen van de inhoud van de bewaarplaats aan schijf.

>[!NOTE]
>
>De vault sync-service is een ontwikkelingsprogramma en het is zeer ontmoedigend om het op een productief systeem te gebruiken. Merk ook op dat de dienst slechts met het lokale filesystem kan synchroniseren en niet voor verre ontwikkeling kan worden gebruikt.

### De service installeren met vlt {#installing-the-service-using-vlt}

Met de opdracht `vlt sync install` kunt u de bundel en configuratie van de kluissynchronisatieservice automatisch installeren.

De bundel wordt geïnstalleerd onder `/libs/crx/vault/install` en de config knoop wordt gecreeerd bij `/libs/crx/vault/com.day.jcr.sync.impl.VaultSyncServiceImpl`. Aanvankelijk wordt de dienst toegelaten maar geen synchronisatiewortels worden gevormd.

In het volgende voorbeeld wordt de synchronisatieservice geïnstalleerd naar de CRX-instantie die toegankelijk is voor de opgegeven uri.

```shell
$ vlt --credentials admin:admin sync --uri http://localhost:4502/crx install
```

### De servicestatus {#displaying-the-service-status} weergeven

De opdracht `status` kan worden gebruikt om informatie weer te geven over de actieve synchronisatieservice. &quot;

```shell
$ vlt sync status --uri http://localhost:4502/crx
Connecting via JCR remoting to http://localhost:4502/crx/server
Listing sync status for http://localhost:4502/crx/server/-/jcr:root
- Sync service is enabled.
- No sync directories configured.
```

>[!NOTE]
>
>Met de opdracht `status` worden geen live gegevens opgehaald van de service, maar wordt de configuratie gelezen op `/libs/crx/vault/com.day.jcr.sync.impl.VaultSyncServiceImpl`.

### Een synchronisatiemap {#adding-a-sync-folder} toevoegen

Met de opdracht `register` voegt u een map toe die u wilt synchroniseren met de configuratie.

```shell
$ vlt sync register
Connecting via JCR remoting to http://localhost:4502/crx/server
Added new sync directory: /tmp/workspace/vltsync/jcr_root
```

>[!NOTE]
>
>De opdracht `register` activeert geen synchronisatie totdat u de configuratie `sync-once` configureert.

### Een synchronisatiemap {#removing-a-sync-folder} verwijderen

De opdracht `unregister` wordt gebruikt om een map te verwijderen die uit de configuratie moet worden gesynchroniseerd.

```shell
$  vlt sync unregister
Connecting via JCR remoting to http://localhost:4502/crx/server
Removed sync directory: /tmp/workspace/vltsync/jcr_root
```

>[!NOTE]
>
>U moet de registratie van een synchronisatiemap ongedaan maken voordat u de map zelf verwijdert.

### Synchronisatie {#configuring-synchronization} configureren

#### Serviceconfiguratie {#service-configuration}

Zodra de dienst in werking stelt kan het met de volgende parameters worden gevormd:

* `vault.sync.syncroots`: Een of meer lokale bestandsysteempaden die de synchronisatiebasis definiëren.

* `vault.sync.fscheckinterval`: Frequentie (in seconden) waarvan het bestandssysteem op wijzigingen moet worden gescand. De standaardwaarde is 5 seconden.
* `vault.sync.enabled`: Algemene vlag die de dienst toelaat/onbruikbaar maakt.

>[!NOTE]
>
>De service kan worden geconfigureerd met de webconsole of een `sling:OsgiConfig`-knooppunt (met de naam `com.day.jcr.sync.impl.VaultSyncServiceImpl`) in de opslagplaats.
>
>Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [Het vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor volledige details.

#### Configuratie van mappen synchroniseren {#sync-folder-configuration}

In elke synchronisatiemap worden configuratie en status in drie bestanden opgeslagen:

* `.vlt-sync-config.properties`: configuratiebestand.

* `.vlt-sync.log`: logbestand dat informatie bevat over de bewerkingen die tijdens het synchroniseren zijn uitgevoerd.
* `.vlt-sync-filter.xml`: filters die definiëren welke delen van de opslagplaats worden gesynchroniseerd. De indeling van dit bestand wordt beschreven in de sectie [Uitchecken via filters uitvoeren](#performing-a-filtered-checkout).

Met het bestand `.vlt-sync-config.properties` kunt u de volgende eigenschappen configureren:

**** disabledHiermee schakelt u de synchronisatie in of uit. Deze parameter is standaard ingesteld op false om synchronisatie toe te staan.

**sync-** onceAls de volgende scan niet leeg is, wordt de map in de gegeven richting gesynchroniseerd, dan wordt de parameter gewist. Twee waarden worden ondersteund:

* `JCR2FS`: exporteert alle inhoud in de JCR-opslagplaats en schrijft naar de lokale schijf.
* `FS2JCR`: Hiermee importeert u alle inhoud van de schijf naar de JCR-opslagplaats.

**sync-** logDefinieert de logbestandsnaam. De standaardwaarde is .vlt-sync.log

### VLT-sync gebruiken voor ontwikkeling {#using-vlt-sync-for-development}

Ga als volgt te werk als u een ontwikkelomgeving wilt instellen op basis van een synchronisatiemap:

1. De gegevensopslagruimte uitchecken via de opdrachtregel voor vlt:

   ```shell
   $ vlt --credentials admin:admin co --force http://localhost:4502/crx dev
   ```

   >[!NOTE]
   >
   >Met filters kunt u alleen de juiste paden uitchecken. Zie de sectie [Uitgefilterde uitchecken](#performing-a-filtered-checkout) voor meer informatie.

1. Ga naar de hoofdmap van uw werkkopie:

   ```shell
   $ cd dev/jcr_root/
   ```

1. Installeer de synchronisatieservice in uw opslagplaats:

   ```xml
   $ vlt sync install
   Connecting via JCR remoting to http://localhost:4502/crx/server
   Preparing to install vault-sync-2.4.24.jar...
   Updated bundle: vault-sync-2.4.24.jar
   Created new config at /libs/crx/vault/config/com.day.jcr.sync.impl.VaultSyncServiceImpl
   ```

1. De synchronisatieservice initialiseren:

   ```shell
   $ vlt sync
   Connecting via JCR remoting to http://localhost:4502/crx/server
   Starting initialization of sync service in existing vlt checkout /Users/colligno/Applications/cq5/vltsync/sandbox/dev/jcr_root for http://localhost:4502/crx/server/-/jcr:root
   Added new sync directory: /Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root
   
   The directory /Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root is now enabled for syncing.
   You might perform a 'sync-once' by setting the
   appropriate flag in the /Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/.vlt-sync-config.properties file.
   ```

1. Bewerk het `.vlt-sync-config.properties` verborgen bestand en configureer synchronisatie om de inhoud van uw opslagplaats te synchroniseren:

   ```xml
   sync-once=JCR2FS
   ```

   >[!NOTE]
   >
   >Deze stap downloadt de hele opslagplaats volgens uw filterconfiguratie.

1. Controleer het logbestand `.vlt-sync.log` om de voortgang te zien:

   ```xml
   ***
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/core/
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/core/product/
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/core/product/GeoProduct.java
   ***
   ```

Uw lokale map is nu gesynchroniseerd met de opslagplaats. De synchronisatie is bidirectioneel, zodat de wijziging van de opslagplaats wordt toegepast op uw lokale synchronisatiemap en andersom.

>[!NOTE]
>
>De functie VLT-synchronisatie ondersteunt alleen eenvoudige bestanden en mappen, maar detecteert speciale geserialiseerde bestanden (.content.xml, dialog.xml, enz.) met vault en negeert deze op ongemerkt. Het is dus mogelijk om vault sync te gebruiken bij een standaard vlt-afhandeling.
