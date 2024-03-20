---
title: Documentbeveiliging | Gebruikersgegevens verwerken
description: Leer hoe u met AEM Forms Document Security gebruikersgegevens en gegevensopslag kunt beheren en gebruikersgegevens kunt openen, verwijderen en exporteren.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin
exl-id: 00c01a12-1180-4f35-9179-461bf177c787
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 0%

---

# Documentbeveiliging | Gebruikersgegevens verwerken {#document-security-handling-user-data}

Met de beveiliging van AEM Forms-documenten kunt u vooraf gedefinieerde beveiligingsinstellingen maken, opslaan en toepassen op uw documenten. Hiermee zorgt u ervoor dat alleen geautoriseerde gebruikers de documenten kunnen gebruiken. U kunt documenten beschermen door beleid te gebruiken. Een beleid is een inzameling van informatie die veiligheidsmontages en een lijst van erkende gebruikers omvat. U kunt een beleid op één of meerdere documenten toepassen en gebruikers machtigen die in het gebruikersbeheer van AEM Forms JEE worden toegevoegd.

<!-- Fix broken link For more information about how document security works, see AEM Forms JEE administration help. -->

## Gebruikersgegevens en gegevensopslag {#user-data-and-data-stores}

Met documentbeveiliging worden beleidsregels en gegevens met betrekking tot beveiligde documenten, waaronder gebruikersgegevens, opgeslagen in een database, zoals Mijn SQL, Oracle, MS® SQL Server en IBM® DB2®. Bovendien de gegevens voor geautoriseerde gebruikers in een beleid in opslag in gebruikersbeheer. Voor informatie over gegevens die in gebruikersbeheer worden opgeslagen, zie [Forms-gebruikersbeheer: gebruikersgegevens verwerken](/help/forms/using/user-management-handling-user-data.md).

In de volgende tabel wordt aangegeven hoe gegevens in databasetabellen worden gerangschikt door documentbeveiliging.

<table>
 <tbody>
  <tr>
   <td>Databasetabel</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td><code>EdcPrincipalKeyEntity</code></td>
   <td>Hiermee slaat u informatie op over de belangrijkste sleutels voor de gebruikers. De toetsen worden gebruikt in workflows voor offlinedocumentbeveiliging.</td>
  </tr>
  <tr>
   <td><code>EdcAuditEntity</code></td>
   <td>Slaat informatie over controlegebeurtenissen zoals gebruikersgebeurtenissen, documentgebeurtenissen, en beleidsgebeurtenissen op.</td>
  </tr>
  <tr>
   <td><p><code>EdcLicenseEntity</code></p> </td>
   <td>Hiermee wordt een record van een beveiligd document opgeslagen. Er worden licentiegegevens opgeslagen voor elk beveiligd document.</td>
  </tr>
  <tr>
   <td><p><code>EdcDocumentEntity</code></p> </td>
   <td>Hiermee slaat u de documentnaam op voor elke licentie die in het systeem is gemaakt.</td>
  </tr>
  <tr>
   <td><p><code>EdcRevokationEntity</code></p> </td>
   <td>Hiermee slaat u informatie op over de intrekking en herinvoering van beveiligde documenten.</td>
  </tr>
  <tr>
   <td><code>EdcMyPolicyListEntity</code></td>
   <td>Hiermee slaat u informatie op over gebruikers die persoonlijk beleid kunnen maken dat wordt weergegeven onder het tabblad Mijn beleid op de pagina Beleid. </td>
  </tr>
  <tr>
   <td><code>EdcPolicyEntity</code></td>
   <td>Hiermee wordt informatie over beleid opgeslagen. Elk beleid komt overeen met een rij in deze tabel.</td>
  </tr>
  <tr>
   <td><code>EdcPolicyXmlEntity</code></td>
   <td>Hiermee worden XML-bestanden opgeslagen voor actief beleid. Een XML-beleid<sup> </sup>bevat verwijzingen naar belangrijkste IDs van gebruikers verbonden aan het beleid. Beleid-XML wordt opgeslagen als een object Blob.</td>
  </tr>
  <tr>
   <td><code>EdcPolicyArchiveEntity</code></td>
   <td>Hiermee wordt informatie over gearchiveerd beleid opgeslagen. Een gearchiveerd beleid bevat zijn beleid-XML die als voorwerp van de Blob wordt opgeslagen.</td>
  </tr>
  <tr>
   <td><p><code>EdcPolicySetPrincipalEntity</code></p> <p><code>EdcPolicySetPrincipalEnt</code><br /> (Oracle- en MS® SQL-databases)</p> </td>
   <td>Hiermee wordt de koppeling tussen de beleidsset en de gebruikers opgeslagen.</td>
  </tr>
  <tr>
   <td><code>EdcInvitedUserEntity</code></td>
   <td>Hiermee worden gegevens over uitgenodigde gebruiker opgeslagen.</td>
  </tr>
 </tbody>
</table>

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

U kunt de gegevens van de documentveiligheid voor gebruikers in de gegevensbestanden toegang hebben en uitvoeren, en indien nodig, het permanent schrappen.

Om gebruikersgegevens uit een gegevensbestand uit te voeren of te schrappen, moet u met het gegevensbestand verbinden gebruikend een gegevensbestandcliënt en te weten komen belangrijkste identiteitskaart die op sommige persoonlijk identificeerbare informatie van de gebruiker wordt gebaseerd. Bijvoorbeeld, om belangrijkste identiteitskaart van een gebruiker terug te winnen die een login identiteitskaart gebruikt, stel het volgende in werking `select` gebruiken in de database.

In de `select` de opdracht vervangen `<user_login_id>` met login identiteitskaart van de gebruiker de waarvan belangrijkste identiteitskaart u van terug wilt winnen `EdcPrincipalUserEntity` databasetabel.

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Zodra u de belangrijkste identiteitskaart kent, kunt u de gebruikersgegevens uitvoeren of schrappen.

### Gebruikersgegevens exporteren {#export-user-data}

Voer de volgende databaseopdrachten uit, zodat u gebruikersgegevens voor een hoofd-id uit databasetabellen kunt exporteren. In de `select` opdracht, vervangen `<principal_id>` met de hoofd-id van de gebruiker wiens gegevens u wilt exporteren.

>[!NOTE]
>
>De volgende opdrachten gebruiken databasetabelnamen in My SQL- en IBM® DB2®-databases. Wanneer u deze opdrachten uitvoert op Oracle- en MS® SQL-databases, vervangt u `EdcPolicySetPrincipalEntity` with `EdcPolicySetPrincipalEnt` in de opdrachten.

```sql
Select * from EdcPrincipalKeyEntity where principalid = '<principal_id>';

Select * from EdcLicenseEntity where publisherId = '<principal_id>';

Select * from EdcDocumentEntity where id in (Select documentid from EdcLicenseEntity where publisherId = '<principal_id>');

Select * from EdcRevokationEntity where licenseid in (Select id from EdcLicenseEntity where publisherId = '<principal_id>');

Select * from EdcMyPolicyListEntity where principalId = '<principal_id>';

Select * from edcpolicyentity where policyownerId = '<principal_id>';

Select * from edcpolicyxmlentity where policyidref in (Select id from edcpolicyentity where policyownerId = '<principal_id>');

Select * from edcpolicyarchiveentity where policyownerId = '<principal_id>';

Select * from edcpolicysetprincipalentity where principalId = '<principal_id>';

Select * from edcinviteduserentity where principalId = '<principal_id>';
```

>[!NOTE]
>
>Gegevens exporteren uit de `EdcAuditEntity` de tabel gebruiken [EventManager.exportEvents](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/programlc/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) API die [EventSearchFilter](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/programlc/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) als parameter voor het exporteren van auditgegevens op basis van `principalId`, `policyId`, of `licenseId`.

Om volledige gegevens over een gebruiker in het systeem te krijgen, moet u tot gegevens van het gebruikersbeheergegevensbestand toegang hebben en uitvoeren. Zie voor meer informatie [Forms-gebruikersbeheer: gebruikersgegevens verwerken](/help/forms/using/user-management-handling-user-data.md).

### Gebruikersgegevens verwijderen {#delete-user-data}

Ga als volgt te werk om documentbeveiligingsgegevens voor een hoofd-id uit databasetabellen te verwijderen.

1. Sluit de AEM Forms-server af.
1. Voer de volgende databaseopdrachten uit, zodat u gegevens voor de hoofd-id uit databasetabellen kunt verwijderen voor documentbeveiliging. In de `Delete` opdracht, vervangen `<principal_id>` met de hoofd-id van de gebruiker van wie u de gegevens wilt verwijderen.

   ```sql
   Delete from EdcPrincipalKeyEntity where principalid = '<principal_id>';
   
   Delete from EdcMyPolicyListEntity where principalId = '<principal_id>';
   
   Delete from edcpolicyarchiveentity where policyownerId = '<principal_id>';
   
   Delete from edcpolicysetprincipalentity where principalId = '<principal_id>';
   
   Delete from edcinviteduserentity where principalId = '<principal_id>';
   ```

   >[!NOTE]
   >
   >Gegevens verwijderen uit het dialoogvenster `EdcAuditEntity` de tabel gebruiken [EventManager.deleteEvents](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/programlc/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) API die [EventSearchFilter](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/programlc/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) als parameter voor het verwijderen van auditgegevens op basis van `principalId`, `policyId`, of `licenseId`.

1. De actieve en gearchiveerde dossiers van beleidXML worden opgeslagen in `EdcPolicyXmlEntity` en `EdcPolicyArchiveEntity` databasetabellen. Ga als volgt te werk om gegevens voor een gebruiker uit deze tabellen te verwijderen:

   1. De XML-blob van elke rij openen in het dialoogvenster `EdcPolicyXMLEntity` of `EdcPolicyArchiveEntity` tabel en extraheer het XML-bestand. Het XML-bestand is vergelijkbaar met het onderstaande bestand.
   1. Bewerk het XML-bestand zodat u de blob voor de hoofd-id kunt verwijderen.
   1. Herhaal stap 1 en 2 voor het andere bestand.

   >[!NOTE]
   >
   >Verwijder de volledige blob binnen de `Principal` -tag voor een hoofd-id of de beleids-XML kan beschadigd of onbruikbaar worden.

   ```xml
   <ns2:Principal PrincipalNameType="USER">
       <ns2:PrincipalDomain>OID</ns2:PrincipalDomain>
       <ns2:PrincipalName>56F33FEB-098A-1036-A651-00000A2A2656</ns2:PrincipalName>
   </ns2:Principal>
   </ns2:PolicyEntry>
       <ns2:Property PropertyName="isCertified">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string">false</ns2:PropertyValue>
       </ns2:Property>
       <ns2:Property PropertyName="encryptionAlgorithm">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string">AES128</ns2:PropertyValue>
       </ns2:Property>
       <ns2:Property PropertyName="AccessDeniedErrorMessage">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string"></ns2:PropertyValue>
       </ns2:Property>
   <ns2:PolicyEntry>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.onlineOpen" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.copy" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.offlineOpen" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.accessible" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.editNotes" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.edit" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.fillAndSign" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.printHigh" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.printLow" Access="ALLOW"/>
   ```

   Naast het direct verwijderen van gegevens uit de `EdcPolicyXmlEntity` er zijn nog twee manieren waarop u dit kunt bereiken :

   **Beheerconsole gebruiken**

   1. Meld u als beheerder aan bij de Forms JEE-beheerconsole op https://[*server*]:[*poort*]/adminui.
   1. Navigeren naar **[!UICONTROL Services > Document Security > Policy Sets]**.
   1. Open een beleidsset en verwijder de gebruiker uit het beleid.

   **Webpagina voor documentbeveiliging gebruiken**

   Gebruikers met documentbeveiliging die gemachtigd zijn om persoonlijke beleidsregels te maken, kunnen gebruikersgegevens uit hun beleid verwijderen. Daartoe:

   1. Gebruikers met een persoonlijk beleid kunnen zich aanmelden bij hun webpagina voor documentbeveiliging op https://[*server*]:[*poort*]/dec.
   1. Navigeren naar **[!UICONTROL Services > Document Security > My Policies]**.
   1. Open een beleid en verwijder de gebruiker uit het beleid.

   >[!NOTE]
   >
   >Beheerders kunnen gebruikersgegevens zoeken, benaderen en verwijderen uit het persoonlijke beleid van andere gebruikers in **[!UICONTROL Services > Document Security > My Policies]** met beheerconsole.

1. Verwijder de gegevens voor de hoofd-id uit de gebruikersbeheerdatabase. Zie voor meer informatie [Forms-gebruikersbeheer | Gebruikersgegevens verwerken](/help/forms/using/user-management-handling-user-data.md).
1. Start de AEM Forms-server.
