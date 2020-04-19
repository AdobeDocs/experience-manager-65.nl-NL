---
title: Documentbeveiliging| Gebruikersgegevens verwerken
seo-title: Documentbeveiliging| Gebruikersgegevens verwerken
description: 'null'
seo-description: 'null'
uuid: 1624a465-8b0c-4347-a53f-1118bfa6e18f
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 898268cb-4426-421f-8f63-d75bd85cb57f
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Documentbeveiliging| Gebruikersgegevens verwerken {#document-security-handling-user-data}

Met de beveiliging van AEM Forms-documenten kunt u vooraf gedefinieerde beveiligingsinstellingen maken, opslaan en toepassen op uw documenten. Hiermee zorgt u ervoor dat alleen geautoriseerde gebruikers de documenten kunnen gebruiken. U kunt documenten beschermen door beleid te gebruiken. Een beleid is een inzameling van informatie die veiligheidsmontages en een lijst van erkende gebruikers omvat. U kunt een beleid toepassen op een of meer documenten en gebruikers autoriseren die zijn toegevoegd aan het gebruikersbeheer van AEM Forms JEE.

<!-- Fix broken link For more information about how document security works, see AEM Forms JEE administration help. -->

## Gebruikersgegevens en gegevensopslag {#user-data-and-data-stores}

Met documentbeveiliging worden beleidsregels en gegevens met betrekking tot beveiligde documenten, waaronder gebruikersgegevens, opgeslagen in een database, zoals My Sql, Oracle, MS SQL Server en IBM DB2. Bovendien de gegevens voor geautoriseerde gebruikers in een beleid in opslag in gebruikersbeheer. Voor informatie over gegevens die in gebruikersbeheer worden opgeslagen, zie het Beheer van de Gebruiker van [Formulieren: Gebruikersgegevens](/help/forms/using/user-management-handling-user-data.md)verwerken.

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
   <td>Hiermee wordt informatie over controlegebeurtenissen opgeslagen, zoals gebruikersgebeurtenissen, documentgebeurtenissen en beleidsgebeurtenissen.</td>
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
   <td>Hiermee worden XML-bestanden opgeslagen voor actief beleid. Een beleid XML<sup> </sup>bevat verwijzingen naar belangrijkste IDs van gebruikers verbonden aan het beleid. Beleid-XML wordt opgeslagen als een object Blob.</td>
  </tr>
  <tr>
   <td><code>EdcPolicyArchiveEntity</code></td>
   <td>Hiermee wordt informatie over gearchiveerd beleid opgeslagen. Een gearchiveerd beleid bevat zijn beleid-XML die als voorwerp van de Blob wordt opgeslagen.</td>
  </tr>
  <tr>
   <td><p><code>EdcPolicySetPrincipalEntity</code></p> <p><code>EdcPolicySetPrincipalEnt</code> (Oracle- en MS SQL-databases)</p> </td>
   <td>Hiermee wordt de koppeling tussen de beleidsset en de gebruikers opgeslagen.</td>
  </tr>
  <tr>
   <td><code>EdcInvitedUserEntity</code></td>
   <td>Hiermee worden gegevens over uitgenodigde gebruiker opgeslagen.</td>
  </tr>
 </tbody>
</table>

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

U kunt documentbeveiligingsgegevens voor gebruikers in de databases openen en exporteren en indien nodig permanent verwijderen.

Om gebruikersgegevens uit een gegevensbestand uit te voeren of te schrappen, moet u met het gegevensbestand verbinden gebruikend een gegevensbestandcliënt en te weten komen belangrijkste identiteitskaart die op sommige persoonlijk identificeerbare informatie van de gebruiker wordt gebaseerd. Bijvoorbeeld, om belangrijkste identiteitskaart van een gebruiker terug te winnen die een login identiteitskaart gebruikt, stel het volgende `select` bevel op het gegevensbestand in werking.

In het `select` bevel, vervang `<user_login_id>` met login identiteitskaart van de gebruiker de waarvan belangrijkste identiteitskaart u van de `EdcPrincipalUserEntity` gegevensbestandlijst wilt terugwinnen.

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Zodra u de belangrijkste identiteitskaart kent, kunt u de gebruikersgegevens uitvoeren of schrappen.

### Gebruikersgegevens exporteren {#export-user-data}

Voer de volgende databaseopdrachten uit om gebruikersgegevens voor een hoofd-id uit databasetabellen te exporteren. In het `select` bevel, vervang `<principal_id>` met belangrijkste identiteitskaart van de gebruiker de waarvan gegevens u wilt uitvoeren.

>[!NOTE]
>
>De volgende bevelen gebruiken de namen van de gegevensbestandlijst in Mijn SQL en de gegevensbestanden van IBM DB2. Wanneer u deze opdrachten uitvoert op Oracle- en MS SQL-databases, vervangt u deze door `EdcPolicySetPrincipalEntity` `EdcPolicySetPrincipalEnt` de opdrachten.

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
>Om gegevens uit de `EdcAuditEntity` lijst uit te voeren, gebruik [EventManager.exportEvents](https://helpx.adobe.com/experience-manager/6-5/forms/programlc/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) API die [EventSearchFilter](https://helpx.adobe.com/experience-manager/6-5/forms/programlc/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) als parameter neemt om controlegegevens uit te voeren die op `principalId`, `policyId`of `licenseId`worden gebaseerd.

Om volledige gegevens over een gebruiker in het systeem te krijgen, moet u tot gegevens van het gebruikersbeheergegevensbestand toegang hebben en uitvoeren. Zie [Formuliergebruikersbeheer voor meer informatie: Gebruikersgegevens](/help/forms/using/user-management-handling-user-data.md)verwerken.

### Gebruikersgegevens verwijderen {#delete-user-data}

Ga als volgt te werk om documentbeveiligingsgegevens voor een hoofd-id uit databasetabellen te verwijderen.

1. Sluit de AEM Forms-server af.
1. Voer de volgende databaseopdrachten uit om gegevens voor de hoofd-id te verwijderen uit databasetabellen voor documentbeveiliging. In het `Delete` bevel, vervang `<principal_id>` met belangrijkste identiteitskaart van de gebruiker de waarvan gegevens u wilt schrappen.

   ```sql
   Delete from EdcPrincipalKeyEntity where principalid = '<principal_id>';
   
   Delete from EdcMyPolicyListEntity where principalId = '<principal_id>';
   
   Delete from edcpolicyarchiveentity where policyownerId = '<principal_id>';
   
   Delete from edcpolicysetprincipalentity where principalId = '<principal_id>';
   
   Delete from edcinviteduserentity where principalId = '<principal_id>';
   ```

   >[!NOTE]
   >
   >Om gegevens uit de `EdcAuditEntity` lijst te schrappen, gebruik [EventManager.deleteEvents](https://helpx.adobe.com/experience-manager/6-5/forms/programlc/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) API die [EventSearchFilter](https://helpx.adobe.com/experience-manager/6-5/forms/programlc/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) als parameter neemt om controlegegevens te schrappen die op `principalId`, `policyId`of worden gebaseerd `licenseId`.

1. De actieve en gearchiveerde dossiers van beleidXML worden opgeslagen in de `EdcPolicyXmlEntity` en `EdcPolicyArchiveEntity` gegevensbestandlijsten, respectievelijk. Ga als volgt te werk om gegevens voor een gebruiker uit deze tabellen te verwijderen:

   1. Open de XML-blob van elke rij in de `EdcPolicyXMLEntity` of `EdcPolicyArchiveEntity` tabel en extraheer het XML-bestand. Het XML-bestand is vergelijkbaar met het onderstaande bestand.
   1. Bewerk het XML-bestand om de blob voor de hoofd-id te verwijderen.
   1. Herhaal stap 1 en 2 voor het andere bestand.
   >[!NOTE]
   >
   >U moet de volledige blob binnen de `Principal` tag voor een hoofd-id verwijderen, anders wordt de beleid-XML mogelijk beschadigd of onbruikbaar.

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

   Naast het direct verwijderen van gegevens uit de `EdcPolicyXmlEntity` tabel zijn er nog twee manieren waarop u dit kunt bereiken:

   **Beheerconsole gebruiken**

   1. Meld u als beheerder aan bij de Forms JEE-beheerconsole op https://[*server*]:[*port*]/adminui.
   1. Ga naar **[!UICONTROL Services > Documentbeveiliging > Beleidssets]**.
   1. Open een beleidsset en verwijder de gebruiker uit het beleid.
   **Webpagina voor documentbeveiliging gebruiken**

   Gebruikers met documentbeveiliging die gemachtigd zijn om persoonlijke beleidsregels te maken, kunnen gebruikersgegevens uit hun beleid verwijderen. Daartoe:

   1. Gebruikers met een persoonlijk beleid melden zich aan op de webpagina voor documentbeveiliging op https://[*server*]:[*poort*]/edc.
   1. Ga naar **[!UICONTROL Services > Documentbeveiliging > Mijn beleid]**.
   1. Open een beleid en verwijder de gebruiker uit het beleid.
   >[!NOTE]
   >
   >Beheerders kunnen met behulp van beheerconsole zoeken naar gebruikersgegevens in, toegang krijgen tot en verwijderen uit persoonlijke beleidsregels van andere gebruikers in **[!UICONTROL Services > Documentbeveiliging > Mijn beleid]** .

1. Verwijder de gegevens voor de hoofd-id uit de gebruikersbeheerdatabase. Voor gedetailleerde stappen, zie het Beheer van de Gebruiker van [Formulieren| Gebruikersgegevens](/help/forms/using/user-management-handling-user-data.md)verwerken.
1. Start de AEM Forms-server.

