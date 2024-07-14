---
title: Documentbeveiliging | Gebruikersgegevens verwerken
description: Leer hoe u met AEM Forms Document Security gebruikersgegevens en gegevensopslag kunt beheren en gebruikersgegevens kunt openen, verwijderen en exporteren.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
exl-id: 00c01a12-1180-4f35-9179-461bf177c787
solution: Experience Manager, Experience Manager Forms
feature: Document Security,Adaptive Forms
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 0%

---

# Documentbeveiliging | Gebruikersgegevens verwerken {#document-security-handling-user-data}

Met de beveiliging van AEM Forms-documenten kunt u vooraf gedefinieerde beveiligingsinstellingen maken, opslaan en toepassen op uw documenten. Hiermee zorgt u ervoor dat alleen geautoriseerde gebruikers de documenten kunnen gebruiken. U kunt documenten beschermen door beleid te gebruiken. Een beleid is een inzameling van informatie die veiligheidsmontages en een lijst van erkende gebruikers omvat. U kunt een beleid op één of meerdere documenten toepassen en gebruikers machtigen die in het gebruikersbeheer van AEM Forms JEE worden toegevoegd.

<!-- Fix broken link For more information about how document security works, see AEM Forms JEE administration help. -->

## Gebruikersgegevens en gegevensopslag {#user-data-and-data-stores}

Met documentbeveiliging worden beleidsregels en gegevens met betrekking tot beveiligde documenten, waaronder gebruikersgegevens, opgeslagen in een database, zoals Mijn SQL, Oracle, MS® SQL Server en IBM® DB2®. Bovendien de gegevens voor geautoriseerde gebruikers in een beleid in opslag in gebruikersbeheer. Voor informatie over gegevens die in gebruikersbeheer worden opgeslagen, zie [ Forms Gebruikersbeheer: Behandelend gebruikersgegevens ](/help/forms/using/user-management-handling-user-data.md).

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
   <td>Hiermee worden XML-bestanden opgeslagen voor actief beleid. Een beleid XML <sup> </sup> bevat verwijzingen naar belangrijkste IDs van gebruikers verbonden aan het beleid. Beleid-XML wordt opgeslagen als een object Blob.</td>
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

Om gebruikersgegevens uit een gegevensbestand uit te voeren of te schrappen, moet u met het gegevensbestand verbinden gebruikend een gegevensbestandcliënt en te weten komen belangrijkste identiteitskaart die op sommige persoonlijk identificeerbare informatie van de gebruiker wordt gebaseerd. Als u bijvoorbeeld de hoofd-id van een gebruiker wilt ophalen met een aanmeldings-id, voert u de volgende opdracht `select` uit op de database.

Vervang de `<user_login_id>` in de opdracht `select` door de aanmeldings-id van de gebruiker wiens hoofd-id u wilt ophalen uit de databasetabel van `EdcPrincipalUserEntity` .

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Zodra u de belangrijkste identiteitskaart kent, kunt u de gebruikersgegevens uitvoeren of schrappen.

### Gebruikersgegevens exporteren {#export-user-data}

Voer de volgende databaseopdrachten uit, zodat u gebruikersgegevens voor een hoofd-id uit databasetabellen kunt exporteren. Vervang `<principal_id>` in de opdracht `select` door de hoofd-id van de gebruiker wiens gegevens u wilt exporteren.

>[!NOTE]
>
>De volgende opdrachten gebruiken databasetabelnamen in My SQL- en IBM® DB2®-databases. Wanneer u deze opdrachten uitvoert op Oracle- en MS® SQL-databases, vervangt u `EdcPolicySetPrincipalEntity` door `EdcPolicySetPrincipalEnt` in de opdrachten.

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
>Om gegevens van de `EdcAuditEntity` lijst uit te voeren, gebruik [ EventManager.exportEvents ](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/programlc/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) API die [ EventSearchFilter ](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/programlc/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) als parameter neemt om controlegegevens uit te voeren die op `principalId` worden gebaseerd, `policyId`, of `licenseId`.

Om volledige gegevens over een gebruiker in het systeem te krijgen, moet u tot gegevens van het gebruikersbeheergegevensbestand toegang hebben en uitvoeren. Voor meer informatie, zie [ Forms gebruikersbeheer: Behandelend gebruikersgegevens ](/help/forms/using/user-management-handling-user-data.md).

### Gebruikersgegevens verwijderen {#delete-user-data}

Ga als volgt te werk om documentbeveiligingsgegevens voor een hoofd-id uit databasetabellen te verwijderen.

1. Sluit de AEM Forms-server af.
1. Voer de volgende databaseopdrachten uit, zodat u gegevens voor de hoofd-id uit databasetabellen kunt verwijderen voor documentbeveiliging. Vervang `<principal_id>` in de opdracht `Delete` door de hoofd-id van de gebruiker wiens gegevens u wilt verwijderen.

   ```sql
   Delete from EdcPrincipalKeyEntity where principalid = '<principal_id>';
   
   Delete from EdcMyPolicyListEntity where principalId = '<principal_id>';
   
   Delete from edcpolicyarchiveentity where policyownerId = '<principal_id>';
   
   Delete from edcpolicysetprincipalentity where principalId = '<principal_id>';
   
   Delete from edcinviteduserentity where principalId = '<principal_id>';
   ```

   >[!NOTE]
   >
   >Om gegevens van de `EdcAuditEntity` lijst te schrappen, gebruik [ EventManager.deleteEvents ](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/programlc/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) API die [ EventSearchFilter ](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/programlc/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) als parameter neemt om controlegegevens te schrappen die op `principalId` worden gebaseerd, `policyId`, of `licenseId`.

1. XML-bestanden met actief en gearchiveerd beleid worden opgeslagen in respectievelijk de databasetabellen `EdcPolicyXmlEntity` en `EdcPolicyArchiveEntity` . Ga als volgt te werk om gegevens voor een gebruiker uit deze tabellen te verwijderen:

   1. Open de XML-blob van elke rij in de tabel `EdcPolicyXMLEntity` of `EdcPolicyArchiveEntity` en extraheer het XML-bestand. Het XML-bestand is vergelijkbaar met het onderstaande bestand.
   1. Bewerk het XML-bestand zodat u de blob voor de hoofd-id kunt verwijderen.
   1. Herhaal stap 1 en 2 voor het andere bestand.

   >[!NOTE]
   >
   >Verwijder de volledige blob binnen de tag `Principal` voor een hoofd-id of de beleids-XML wordt mogelijk beschadigd of onbruikbaar.

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

   Naast het rechtstreeks verwijderen van gegevens uit de tabel `EdcPolicyXmlEntity` zijn er nog twee andere manieren waarop u dit kunt bereiken:

   **Gebruikend beleidsconsole**

   1. Als beheerder, login aan de het beleidsconsole van Forms JEE in https:// [*server*]:[*haven*]/adminui.
   1. Navigeer naar **[!UICONTROL Services > Document Security > Policy Sets]** .
   1. Open een beleidsset en verwijder de gebruiker uit het beleid.

   **Gebruikend Web-pagina van de documentveiligheid**

   Gebruikers met documentbeveiliging die gemachtigd zijn om persoonlijke beleidsregels te maken, kunnen gebruikersgegevens uit hun beleid verwijderen. Daartoe:

   1. De gebruikers die persoonlijk beleidslogin aan hun Web-pagina van de documentveiligheid in https:// [*server*] hebben:[*haven*]/edc.
   1. Navigeer naar **[!UICONTROL Services > Document Security > My Policies]** .
   1. Open een beleid en verwijder de gebruiker uit het beleid.

   >[!NOTE]
   >
   >Beheerders kunnen met behulp van beheerconsole gebruikersgegevens zoeken in, benaderen uit en verwijderen uit persoonlijke beleidsregels van andere gebruikers in **[!UICONTROL Services > Document Security > My Policies]** .

1. Verwijder de gegevens voor de hoofd-id uit de gebruikersbeheerdatabase. Voor gedetailleerde stappen, zie [ het Gebruikersbeheer van Forms | Behandeling van gebruikersgegevens ](/help/forms/using/user-management-handling-user-data.md).
1. Start de AEM Forms-server.
