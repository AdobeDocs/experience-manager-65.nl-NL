---
title: Forms-gebruikersbeheer | Gebruikersgegevens verwerken
description: Leer hoe u met AEM Forms JEE-gebruikersbeheercomponent gebruikers die toegang tot AEM Forms nodig hebben, kunt maken, autoriseren en beheren.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
exl-id: eeeab5d1-073a-4e13-a781-391dfe70bb37
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Forms-gebruikersbeheer | Gebruikersgegevens verwerken {#forms-user-management-handling-user-data}

Gebruikersbeheer is een AEM Forms JEE-component waarmee AEM Forms-gebruikers toegang kunnen krijgen tot AEM Forms en waarmee ze deze kunnen maken, beheren en autoriseren. Gebruikersbeheer gebruikt domeinen als mappen voor het verkrijgen van gebruikersinformatie. De volgende domeintypen worden ondersteund:

**Lokale domeinen**: Dit type domein is niet verbonden met een opslagsysteem van derden. In plaats daarvan worden gebruikers en groepen lokaal gemaakt en bevinden ze zich in de gebruikersbeheerdatabase. De wachtwoorden worden lokaal opgeslagen, en de authentificatie wordt gedaan gebruikend een lokaal gegevensbestand.

**Hybride domeinen**: Dit type domein is niet verbonden met een opslagsysteem van derden. In plaats daarvan worden gebruikers en groepen lokaal gemaakt en bevinden ze zich in de gebruikersbeheerdatabase. In tegenstelling tot lokale domeinen, gebruiken de hybride domeinen een externe authentificatieleverancier, die LDAP, Kerberos, SAML, of een leverancier van de douaneauthentificatie kan zijn.

**Enterprise-domeinen**: Bestaat uit gebruikers en groepen die zich in een opslagsysteem van derden bevinden, zoals een LDAP-directory. Gebruikersbeheer schrijft niet naar het opslagsysteem van derden. In plaats daarvan synchroniseert Gebruikersbeheer de gebruikers- en groepsgegevens met de gebruikersbeheerdatabase. De domeinen van de onderneming gebruiken ook een externe authentificatieleverancier, die LDAP, Kerberos, SAML, of een leverancier van de douaneauthentificatie kan zijn.

<!-- Fix broken links For more information about how user management works and configured, see AEM Forms JEE administration help. -->

## Gebruikersgegevens en gegevensopslag {#user-data-and-data-stores}

Gebruikersbeheer slaat gebruikersgegevens op in een database, zoals Mijn SQL, Oracle, MS® SQL Server en IBM® DB2®. Bovendien elke gebruiker die zich minstens één keer heeft aangemeld bij Forms-toepassingen op AEM ontwerper op `https://'[server]:[port]'lc`, wordt de gebruiker gemaakt in AEM opslagplaats. Daarom wordt het gebruikersbeheer opgeslagen in de volgende gegevensopslag:

* Database
* AEM
* Externe opslag, zoals LDAP-directory

>[!NOTE]
>
>Gegevens die zijn opgeslagen in externe opslagruimten vallen buiten het bereik van dit document. Neem rechtstreeks contact op met de externe leverancier om gebruikersgegevens in dergelijke opslagruimten te beheren.

### Database {#database}

Gebruikersbeheer slaat gebruikersgegevens op in de volgende databasetabellen:

<table>
 <tbody>
  <tr>
   <td>Databasetabel</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td><code>EdcPrincipalEntity</code></td>
   <td><p>Hiermee slaat u informatie op over de belangrijkste entiteiten. Een principal kan een gebruiker, een groep, of een rol zijn.</p> <p> </p> </td>
  </tr>
  <tr>
   <td><code>EdcPrincipalUserEntity</code></td>
   <td>Hiermee worden PII-gegevens (Persoonlijk identificeerbare gegevens) van gebruikers opgeslagen. Het bevat een ingang voor elke gebruiker van lokale, onderneming, en hybride domeinen.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalLocalAccountEntity</code></p> <p><code class="code">EdcPrincipalLocalAccount
       </code>(Oracle- en MS® SQL-databases)</p> </td>
   <td>Hiermee worden gegevens alleen voor lokale gebruikers opgeslagen.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalEmailAliasEntity</code></p> <p><code class="code">EdcPrincipalEmailAliasEn
       </code>(Oracle- en MS® SQL-databases)</p> </td>
   <td>Bevat ingangen van alle gebruikers van lokale, onderneming, en hybride domeinen. Deze bevat e-mailadressen van gebruikers.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalGrpCtmntEntity</code></p> <p><code>EdcPrincipalGrpCtmntEnti</code><br /> (Oracle- en MS® SQL-databases)</p> </td>
   <td>Hiermee slaat u de toewijzing tussen gebruikers en groepen op.</td>
  </tr>
  <tr>
   <td><code>EdcPrincipalRoleEntity</code></td>
   <td>Slaat de afbeelding tussen rollen en hoofden voor zowel gebruikers als groepen op.</td>
  </tr>
  <tr>
   <td><code>EdcPriResPrmEntity</code></td>
   <td>Slaat de afbeelding tussen hoofd en toestemmingen voor zowel gebruikers als groepen op.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalMappingEntity</code></p> <p><code>EdcPrincipalMappingEntit</code><br /> (Oracle- en MS® SQL-databases)</p> </td>
   <td>Hiermee slaat u oude en nieuwe kenmerkwaarden op die overeenkomen met een principal.<br /> </td>
  </tr>
 </tbody>
</table>

### AEM {#aem-repository}

Gebruikersbeheergegevens voor gebruikers die minimaal één keer toegang hebben tot de Forms-toepassingen onder `https://'[server]:[port]'lc` wordt ook in AEM opslagplaats opgeslagen.

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

U kunt gegevens van het gebruikersbeheer voor gebruikers in de gebruikersbeheergegevensbestanden en AEM bewaarplaats toegang hebben en uitvoeren, en indien nodig, het permanent schrappen.

### Database {#database-1}

Als u gebruikersgegevens wilt exporteren of verwijderen uit een gebruikersbeheerdatabase, moet u verbinding maken met de database met behulp van een databaseclient en de belangrijkste id opzoeken op basis van sommige PII&#39;s van de gebruiker. Bijvoorbeeld, om belangrijkste identiteitskaart van een gebruiker terug te winnen die een login identiteitskaart gebruikt, stel het volgende in werking `select` gebruiken in de database.

In de `select` de opdracht vervangen `<user_login_id>` met de login identiteitskaart van de gebruiker waarvan belangrijkste identiteitskaart u wilt terugwinnen.

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Zodra u de belangrijkste identiteitskaart kent, kunt u de gebruikersgegevens uitvoeren of schrappen.

#### Gebruikersgegevens exporteren {#export-user-data}

Voer de volgende databaseopdrachten uit, zodat u gebruikersbeheergegevens voor een hoofd-id uit databasetabellen kunt exporteren. In de `select` opdracht, vervangen `<principal_id>` met de hoofd-id van de gebruiker wiens gegevens u wilt exporteren.

>[!NOTE]
>
>De volgende opdrachten gebruiken databasetabelnamen in My SQL- en IBM® DB2®-databases. Wanneer u deze opdrachten uitvoert voor Oracle- en MS® SQL-databases, vervangt u de volgende tabelnamen in de opdrachten:
>
>* Vervangen `EdcPrincipalLocalAccountEntity` with `EdcPrincipalLocalAccount`
>
>* Vervangen `EdcPrincipalEmailAliasEntity` with `EdcPrincipalEmailAliasEn`
>
>* Vervangen `EdcPrincipalMappingEntity` with `EdcPrincipalMappingEntit`
>
>* Vervangen `EdcPrincipalGrpCtmntEntity` with `EdcPrincipalGrpCtmntEnti`
>

```sql
Select * from EdcPrincipalLocalAccountEntity where refuserprincipalid in (Select id from EdcPrincipalUserEntity where refprincipalid in (Select id from EDCPRINCIPALENTITY where id='<principal_id>'));

Select * from EdcPrincipalEmailAliasEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalRoleEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPriResPrmEntity where refprinid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalUserEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalMappingEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalGrpCtmntEntity where refchildprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalEntity where id='<principal_id>';
```

#### Gebruikersgegevens verwijderen {#delete-user-data}

Ga als volgt te werk om gebruikersbeheergegevens voor een hoofd-id uit databasetabellen te verwijderen.

1. Verwijder gebruikersgegevens uit AEM opslagplaats, indien van toepassing, zoals beschreven in [Gebruikersgegevens verwijderen](/help/forms/using/user-management-handling-user-data.md#delete-aem).
1. Sluit de AEM Forms-server af.
1. Voer de volgende databaseopdrachten uit, zodat u gegevens voor gebruikersbeheer voor een hoofd-id uit databasetabellen kunt verwijderen. In de `Delete` opdracht, vervangen `<principal_id>` met de hoofd-id van de gebruiker van wie u de gegevens wilt verwijderen.

   ```sql
   Delete from EdcPrincipalLocalAccountEntity where refuserprincipalid in (Select id from EdcPrincipalUserEntity where refprincipalid in (select id from EdcPrincipalEntity where id='<principal_id>'));
   
   Delete from EdcPrincipalEmailAliasEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalRoleEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPriResPrmEntity where refprinid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalUserEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalMappingEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalGrpCtmntEntity where refchildprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalEntity where id='<principal_id>';
   ```

1. Start de AEM Forms-server.

### AEM {#aem-repository-1}

Forms JEE-gebruikers hebben hun gegevens in AEM gegevensopslagruimte als ze minstens één instantie van de AEM Forms-auteur hebben geopend. U kunt hun gebruikersgegevens uit AEM opslagplaats openen en verwijderen.

#### Gebruikersgegevens openen {#access-user-data}

Om gebruiker te bekijken die in AEM bewaarplaats wordt gecreeerd, login `https://'[server]:[port]'/lc/useradmin` met AEM beheerdersreferenties. Let op: `server` en `port` in de URL is dat van de AEM auteur. Hier kunt u naar gebruikers zoeken met hun gebruikersnaam. Dubbelklik op een gebruiker zodat u informatie kunt weergeven zoals eigenschappen, machtigingen en groepen voor de gebruiker. De `Path` eigenschap voor een gebruiker geeft het pad aan naar het gebruikersknooppunt dat in AEM opslagplaats is gemaakt.

#### Gebruikersgegevens verwijderen {#delete-aem}

Een gebruiker verwijderen:

1. Ga naar `https://'[server]:[port]'/lc/useradmin` met AEM beheerdersreferenties.
1. Zoek naar een gebruiker en klik de gebruikersbenaming tweemaal om gebruikerseigenschappen te openen. De `Path` eigenschap.
1. Ga naar AEM CRXDE Lite om `https://'[server]:[port]'/lc/crx/de/index.jsp` en navigeer of doorzoek het gebruikerspad.
1. Het pad verwijderen en klikken **[!UICONTROL Save All]** om de gebruiker permanent uit AEM opslagplaats te verwijderen.
