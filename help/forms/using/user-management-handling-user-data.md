---
title: Forms-gebruikersbeheer | Gebruikersgegevens verwerken
seo-title: Forms-gebruikersbeheer | Gebruikersgegevens verwerken
description: Forms-gebruikersbeheer | Gebruikersgegevens verwerken
uuid: 2b76b69f-6f3a-4f1a-a2a4-d39f5e529f75
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a88fc933-f1af-4798-b72f-10e7b0d2fd11
translation-type: tm+mt
source-git-commit: a873cf3e7efd3bc9cd4744bf09078d9040efcdda
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 0%

---


# Forms-gebruikersbeheer | Gebruikersgegevens verwerken {#forms-user-management-handling-user-data}

Gebruikersbeheer is een AEM Forms JEE-component waarmee AEM Forms-gebruikers toegang kunnen krijgen tot AEM Forms en waarmee ze deze kunnen maken, beheren en autoriseren. Gebruikersbeheer gebruikt domeinen als map voor het verkrijgen van gebruikersinformatie. De volgende domeintypen worden ondersteund:

**Lokale domeinen**: Dit type domein is niet verbonden met een opslagsysteem van derden. In plaats daarvan, worden de gebruikers en de groepen gecreeerd plaatselijk en verblijven in het gegevensbestand van het Beheer van de Gebruiker. De wachtwoorden worden lokaal opgeslagen, en de authentificatie wordt gedaan gebruikend een lokaal gegevensbestand.

**Hybride domeinen**: Dit type domein is niet verbonden met een opslagsysteem van derden. In plaats daarvan, worden de gebruikers en de groepen gecreeerd plaatselijk en verblijven in het gegevensbestand van het Beheer van de Gebruiker. In tegenstelling tot lokale domeinen, gebruiken de hybride domeinen een externe authentificatieleverancier, die LDAP, Kerberos, SAML, of een leverancier van de douaneauthentificatie kan zijn.

**Ondernemingsdomeinen**: Bestaat uit gebruikers en groepen die zich in een opslagsysteem van derden bevinden, zoals een LDAP-directory. Gebruikersbeheer schrijft niet naar het opslagsysteem van derden. In plaats daarvan synchroniseert Gebruikersbeheer de gebruikers- en groepsgegevens met de gebruikersbeheerdatabase. De domeinen van de onderneming gebruiken ook een externe authentificatieleverancier, die LDAP, Kerberos, SAML, of een leverancier van de douaneauthentificatie kan zijn.

<!-- Fix broken links For more information about how user management works and configured, see AEM Forms JEE administration help. -->

## Gebruikersgegevens en gegevensopslag {#user-data-and-data-stores}

Gebruikersbeheer slaat gebruikersgegevens op in een database, zoals Mijn SQL, Oracle, MS SQL Server en IBM DB2. Bovendien wordt elke gebruiker die zich minstens één keer heeft aangemeld in Forms-toepassingen op AEM auteur op `https://'[server]:[port]'lc`, gemaakt in AEM opslagplaats. Daarom wordt het gebruikersbeheer opgeslagen in de volgende gegevensopslag:

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
       </code>(Oracle- en MS SQL-databases)</p> </td>
   <td>Hiermee worden gegevens alleen voor lokale gebruikers opgeslagen.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalEmailAliasEntity</code></p> <p><code class="code">EdcPrincipalEmailAliasEn
       </code>(Oracle- en MS SQL-databases)</p> </td>
   <td>Bevat ingangen van alle gebruikers van lokale, onderneming, en hybride domeinen. Deze bevat e-mailadressen van gebruikers.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalGrpCtmntEntity</code></p> <p><code>EdcPrincipalGrpCtmntEnti</code> (Oracle- en MS SQL-databases)</p> </td>
   <td>Hiermee slaat u de toewijzing tussen gebruikers en groepen op.</td>
  </tr>
  <tr>
   <td><code>EdcPrincipalRoleEntity</code></td>
   <td>Slaat de afbeelding tussen rollen en hoofd voor zowel gebruikers als groepen op.</td>
  </tr>
  <tr>
   <td><code>EdcPriResPrmEntity</code></td>
   <td>Slaat de afbeelding tussen hoofd en toestemmingen voor zowel gebruikers als groepen op.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalMappingEntity</code></p> <p><code>EdcPrincipalMappingEntit</code> (Oracle- en MS SQL-databases)</p> </td>
   <td>Hiermee slaat u oude en nieuwe kenmerkwaarden op die overeenkomen met een principal.<br /> </td>
  </tr>
 </tbody>
</table>

### AEM {#aem-repository}

Gebruikersbeheergegevens voor gebruikers die minstens één keer toegang hebben gekregen tot de Forms-toepassingen onder `https://'[server]:[port]'lc` worden ook in AEM opslagplaats opgeslagen.

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

U kunt gegevens van het gebruikersbeheer voor gebruikers in de gebruikersbeheergegevensbestanden en AEM bewaarplaats toegang hebben en uitvoeren, en indien nodig, het permanent schrappen.

### Database {#database-1}

Als u gebruikersgegevens wilt exporteren of verwijderen uit een gebruikersbeheerdatabase, moet u verbinding maken met de database met behulp van een databaseclient en de belangrijkste id opzoeken op basis van sommige PII&#39;s van de gebruiker. Bijvoorbeeld, om belangrijkste identiteitskaart van een gebruiker terug te winnen die een login identiteitskaart gebruikt, stel het volgende `select` bevel op het gegevensbestand in werking.

In het `select` bevel, vervang `<user_login_id>` met login identiteitskaart van de gebruiker de waarvan belangrijkste identiteitskaart u wilt terugwinnen.

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Zodra u de belangrijkste identiteitskaart kent, kunt u de gebruikersgegevens uitvoeren of schrappen.

#### Gebruikersgegevens exporteren {#export-user-data}

Voer de volgende databaseopdrachten uit om gebruikersbeheergegevens voor een hoofd-id uit databasetabellen te exporteren. In het `select` bevel, vervang `<principal_id>` met belangrijkste identiteitskaart van de gebruiker de waarvan gegevens u wilt uitvoeren.

>[!NOTE]
>
>De volgende bevelen gebruiken de namen van de gegevensbestandlijst in Mijn SQL en de gegevensbestanden van IBM DB2. Wanneer u deze opdrachten uitvoert op Oracle- en MS SQL-databases, vervangt u de volgende tabelnamen in de opdrachten:
>
>* Vervangen `EdcPrincipalLocalAccountEntity` door `EdcPrincipalLocalAccount`
   >
   >
* Vervangen `EdcPrincipalEmailAliasEntity` door `EdcPrincipalEmailAliasEn`
   >
   >
* Vervangen `EdcPrincipalMappingEntity` door `EdcPrincipalMappingEntit`
   >
   >
* Vervangen `EdcPrincipalGrpCtmntEntity` door `EdcPrincipalGrpCtmntEnti`

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

1. Verwijder gebruikersgegevens uit AEM opslagplaats, indien van toepassing, zoals beschreven in [Gebruikersgegevens](/help/forms/using/user-management-handling-user-data.md#delete-aem)verwijderen.
1. Sluit de AEM Forms-server af.
1. Voer de volgende databaseopdrachten uit om gebruikersbeheergegevens voor een hoofd-id uit databasetabellen te verwijderen. In het `Delete` bevel, vervang `<principal_id>` met belangrijkste identiteitskaart van de gebruiker de waarvan gegevens u wilt schrappen.

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

Als u een gebruiker wilt bekijken die in AEM opslagplaats is gemaakt, meldt u zich aan `https://'[server]:[port]'/lc/useradmin` met AEM beheerdersreferenties. Merk op dat `server` en `port` in URL die van de AEM auteurinstantie zijn. Hier kunt u naar gebruikers zoeken met hun gebruikersnaam. Dubbelklik op een gebruiker om informatie weer te geven, zoals eigenschappen, machtigingen en groepen voor de gebruiker. De `Path` eigenschap voor een gebruiker geeft het pad aan naar het gebruikersknooppunt dat in AEM opslagplaats is gemaakt.

#### Gebruikersgegevens verwijderen {#delete-aem}

Een gebruiker verwijderen:

1. Ga naar `https://'[server]:[port]'/lc/useradmin` met AEM beheerdersreferenties.
1. Zoek naar een gebruiker en klik de gebruikersbenaming tweemaal om gebruikerseigenschappen te openen. Kopieer de `Path` eigenschap.
1. Ga naar AEM CRX DELite op `https://'[server]:[port]'/lc/crx/de/index.jsp` en navigeer of zoek het gebruikerspad.
1. Verwijder het pad en klik **[!UICONTROL Save All]** om de gebruiker definitief uit AEM opslagplaats te verwijderen.

