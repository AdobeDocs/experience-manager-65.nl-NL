---
title: Hoofdweergave voor beheer van machtigingen
description: Leer over de nieuwe interface van de Aanraking UI die toestemmingenbeheer vergemakkelijkt.
contentOwner: sarchiz
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
docset: aem65
exl-id: 4ce19c95-32cb-4bb8-9d6f-a5bc08a3688d
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 6f3c4f4aa4183552492c6ce5039816896bd67495
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---


# Hoofdweergave voor beheer van machtigingen{#principal-view-for-permissions-management}

## Overzicht {#overview}

AEM 6.5 introduceert het Beheer van Toestemmingen voor Gebruikers en Groepen. De belangrijkste functionaliteit blijft het zelfde als klassieke UI, maar is gebruikersvriendelijker en efficiënter.

## Hoe wordt het gebruikt {#how-to-use}

### De interface openen {#accessing-the-ui}

Het nieuwe op UI-Gebaseerde toestemmingenbeheer wordt betreden door de kaart van Toestemmingen onder Veiligheid zoals hieronder getoond:

![&#x200B; UI van het Beheer van Toestemmingen &#x200B;](assets/screen_shot_2019-03-17at63333pm.png)

De nieuwe mening maakt het gemakkelijker om de volledige reeks voorrechten en beperkingen voor een bepaald hoofd op alle wegen te bekijken waar de Toestemmingen uitdrukkelijk zijn verleend. Hierdoor is het niet nodig om naar

CRXDE om geavanceerde voorrechten en beperkingen te beheren. Het is in dezelfde visie geconsolideerd. De mening blijft aan de Groep &quot;iedereen&quot;in gebreke.

![&#x200B; Mening van &quot;iedereen&quot;groep &#x200B;](assets/unu-1.png)

Er is een filter dat de gebruiker toestaat om het type van hoofden te selecteren om **Gebruikers** te bekijken, **Groepen**, of **allen** en onderzoek naar om het even welk hoofd **.**

![&#x200B; Onderzoek naar types van Belangrijkste &#x200B;](assets/image2019-3-20_23-52-51.png)

### Machtigingen weergeven voor een principal {#viewing-permissions-for-a-principal}

In het linkerframe kunnen gebruikers omlaag schuiven om een hoofd te zoeken of naar een groep of een gebruiker te zoeken op basis van het geselecteerde filter, zoals hieronder wordt getoond:

![&#x200B; Toestemmingen van de Mening voor een Hoofd &#x200B;](assets/doi-1.png)

Als u op de naam klikt, worden aan de rechterkant de toegewezen machtigingen weergegeven. Het toestemmingenvenster toont de lijst van de Ingangen van het Toegangsbeheer op specifieke wegen samen met gevormde beperkingen.

![&#x200B; ACL van de Mening Lijst &#x200B;](assets/trei-1.png)

### Het toevoegen van nieuw Ingang van het Toegangsbeheer voor Principal {#adding-new-access-control-entry-for-a-principal}

De nieuwe toestemmingen kunnen worden toegevoegd door een Toegang toe te voegen die ingaat. Klik eenvoudig toevoegen ACE knoop.

![&#x200B; voeg nieuwe ACL voor Principal &#x200B;](assets/patru.png) toe

Dit brengt het hieronder getoonde venster omhoog, is de volgende stap een weg te kiezen waar de toestemming moet worden gevormd.

![&#x200B; vorm toestemmingenweg &#x200B;](assets/cinci-1.png)

Hier, wordt een weg geselecteerd waar u een toestemming voor **dam-gebruikers** kunt vormen:

![&#x200B; de configuratie van het Voorbeeld voor dam-gebruikers &#x200B;](assets/sase-1.png)

Nadat het pad is geselecteerd, gaat de workflow terug naar dit scherm, waar de gebruiker een of meer rechten kan selecteren uit de beschikbare naamruimten (zoals `jcr` , `rep` of `crx` ), zoals hieronder wordt weergegeven.

U kunt rechten toevoegen door te zoeken in het tekstveld en vervolgens te selecteren in de lijst.

>[!NOTE]
>
>Voor een volledige lijst van voorrechten en beschrijvingen, zie [&#x200B; Gebruiker, Groep, en het Beleid van de Rechten van de Toegang &#x200B;](/help/sites-administering/user-group-ac-admin.md#access-right-management).

![&#x200B; toestemming van het Onderzoek voor een bepaalde weg.](assets/image2019-3-21_0-5-47.png) ![&#x200B; voeg Nieuwe Ingang voor &quot;dam-gebruikers&quot;zoals aangetoond door een weg toe die in verticale kolommen wordt geselecteerd.](assets/image2019-3-21_0-6-53.png)

Nadat de lijst met bevoegdheden is geselecteerd, kan de gebruiker het machtigingstype Weigeren of Toestaan kiezen, zoals hieronder wordt weergegeven.

![&#x200B; Uitgezochte toestemming &#x200B;](assets/screen_shot_2019-03-17at63938pm.png) ![&#x200B; Uitgezochte toestemming &#x200B;](assets/screen_shot_2019-03-17at63947pm.png)

### Beperkingen gebruiken {#using-restrictions}

Naast de lijst met bevoegdheden en het machtigingstype op een bepaald pad, kunt u met dit scherm ook beperkingen voor fijnkorrelig toegangsbeheer toevoegen, zoals hieronder wordt getoond:

![&#x200B; voeg beperkingen &#x200B;](assets/image2019-3-21_1-4-14.png) toe

>[!NOTE]
>
>Voor meer informatie over wat elke beperking betekent, zie [&#x200B; de Documentatie van Jackrabbit Oak &#x200B;](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html).

U kunt beperkingen toevoegen zoals hieronder wordt weergegeven door het type beperking te kiezen, de waarde in te voeren en op het pictogram **+** te klikken.

![&#x200B; voeg het beperkingstype &#x200B;](assets/sapte-1.png) ![&#x200B; toe het beperkingstype &#x200B;](assets/opt-1.png)

Het nieuwe ACE wordt weerspiegeld in de Lijst van het Toegangsbeheer zoals hieronder getoond. `jcr:write` is een geaggregeerde bevoegdheid die `jcr:removeNode` bevat die hierboven is toegevoegd, maar die hieronder niet wordt weergegeven als een bevoegdheid die onder `jcr:write` valt.

### ACE&#39;s bewerken {#editing-aces}

De Ingangen van het Toegangsbeheer kunnen worden uitgegeven door een hoofd te selecteren en ACE te kiezen die u wilt uitgeven.

Bijvoorbeeld, hier kunt u de hieronder ingang voor **dam-gebruikers** uitgeven door het potloodpictogram op het recht te klikken:

![&#x200B; voeg beperking &#x200B;](assets/image2019-3-21_0-35-39.png) toe

Het bewerkingsscherm wordt weergegeven met de geconfigureerde ACE&#39;s die vooraf zijn geselecteerd. U kunt deze verwijderen door op het kruispictogram naast de ACE&#39;s te klikken of u kunt nieuwe bevoegdheden toevoegen voor het opgegeven pad, zoals hieronder wordt weergegeven.

![&#x200B; geef ingang &#x200B;](assets/noua-1.png) uit

Hier wordt het `addChildNodes` voorrecht toegevoegd voor **dam-gebruikers** op de bepaalde weg.

![&#x200B; voeg voorrecht &#x200B;](assets/image2019-3-21_0-45-35.png) toe

De veranderingen kunnen worden bewaard door **te klikken sparen** knoop op bovenkant recht, en de veranderingen worden weerspiegeld in de nieuwe toestemmingen voor **dam-gebruikers** zoals hieronder getoond:

![&#x200B; sparen veranderingen &#x200B;](assets/zece-1.png)

### ACE&#39;s verwijderen {#deleting-aces}

De Ingangen van het Toegangsbeheer kunnen worden geschrapt om alle toestemmingen te verwijderen die aan een hoofd op een specifieke weg worden gegeven. Het pictogram X naast ACE kan worden gebruikt om het te schrappen zoals hieronder getoond:

![&#x200B; Schrap ACEs &#x200B;](assets/image2019-3-21_0-53-19.png) ![&#x200B; ACEs &#x200B;](assets/unspe.png)

### Klassieke UI Privilege-combinaties {#classic-ui-privilege-combinations}

De nieuwe toestemmingenUI gebruikt uitdrukkelijk de basisreeks voorrechten in plaats van vooraf bepaalde combinaties die niet echt de nauwkeurige onderliggende voorrechten weerspiegelen die werden verleend.

Het veroorzaakte verwarring over wat precies wordt gevormd. De volgende lijst maakt een lijst van de afbeelding tussen de voorrechtcombinaties van Klassieke UI aan de daadwerkelijke voorrechten die hen vormen:

<table>
 <tbody>
  <tr>
   <th>Klassieke UI Privilege-combinaties</th>
   <th>Rechten UI-bevoegdheid</th>
  </tr>
  <tr>
   <td>Lezen</td>
   <td><code>jcr:read</code></td>
  </tr>
  <tr>
   <td>Wijzigen</td>
   <td><p><code>jcr:modifyProperties</code></p> <p><code>jcr:lockManagement</code></p> <p><code>jcr:versionManagement</code></p> </td>
  </tr>
  <tr>
   <td>Maken</td>
   <td><p><code>jcr:addChildNodes</code></p> <p><code>jcr:nodeTypeManagement</code></p> </td>
  </tr>
  <tr>
   <td>Verwijderen</td>
   <td><p><code>jcr:removeNode</code></p> <p><code>jcr:removeChildNodes</code></p> </td>
  </tr>
  <tr>
   <td>ACL lezen</td>
   <td><code>jcr:readAccessControl</code></td>
  </tr>
  <tr>
   <td>ACL bewerken</td>
   <td><code>jcr:modifyAccessControl</code></td>
  </tr>
  <tr>
   <td>Repliceren</td>
   <td><code>crx:replicate</code></td>
  </tr>
 </tbody>
</table>
