---
title: Hoofdweergave voor beheer van machtigingen
seo-title: Hoofdweergave voor beheer van machtigingen
description: Leer over de nieuwe interface van de Aanraking UI die toestemmingenbeheer vergemakkelijkt.
seo-description: Leer over de nieuwe interface van de Aanraking UI die toestemmingenbeheer vergemakkelijkt.
uuid: 16c5889a-60dd-4b66-bbc4-74fbdb5fc32f
contentOwner: sarchiz
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
discoiquuid: db8665fa-353f-45c2-8e37-169d5c1df873
docset: aem65
translation-type: tm+mt
source-git-commit: a156e09e77951041dce017f2f78069bc050b6bdb
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 1%

---


# Hoofdweergave voor machtigingenbeheer{#principal-view-for-permissions-management}

## Overzicht {#overview}

AEM 6.5 introduceert het Beheer van Toestemmingen voor Gebruikers en Groepen. De belangrijkste functionaliteit blijft het zelfde als klassieke UI, maar is gebruikersvriendelijker en efficiënter.

## Het gebruik {#how-to-use}

### Toegang tot de interface {#accessing-the-ui}

Het nieuwe op UI gebaseerde toestemmingenbeheer wordt betreden door de kaart van Toestemmingen onder Veiligheid zoals hieronder getoond:

![](assets/screen_shot_2019-03-17at63333pm.png)

De nieuwe mening maakt het gemakkelijker om de volledige reeks voorrechten en beperkingen voor een bepaald hoofd op alle wegen te bekijken waar de Toestemmingen uitdrukkelijk zijn verleend. Hierdoor is het niet nodig om naar

CRXDE om geavanceerde voorrechten en beperkingen te beheren. Het is in dezelfde visie geconsolideerd. De mening blijft aan de Groep &quot;iedereen&quot;in gebreke.

![](assets/unu-1.png)

Er is een filter dat de gebruiker toestaat om het type van hoofdrolspelers te selecteren om **Users**, **Groepen**, of **allen** en onderzoek naar om het even welke principal **te bekijken.**.

![](assets/image2019-3-20_23-52-51.png)

### Machtigingen weergeven voor een principal {#viewing-permissions-for-a-principal}

In het linkerframe kunnen gebruikers omlaag schuiven om een hoofd te zoeken of naar een groep of een gebruiker te zoeken op basis van het geselecteerde filter, zoals hieronder wordt getoond:

![](assets/doi-1.png)

Als u op de naam klikt, worden de toegewezen machtigingen aan de rechterkant weergegeven. Het toestemmingenvenster toont de lijst van de Ingangen van het Toegangsbeheer op specifieke wegen samen met gevormde beperkingen.

![](assets/trei-1.png)

### Nieuw Toegang tot toegangsbeheer toevoegen voor Opdrachtgever {#adding-new-access-control-entry-for-a-principal}

De nieuwe toestemmingen kunnen worden toegevoegd door een nieuwe Toegang toe te voegen die Ingang controleert door de Add knoop van ACE te klikken.

![](assets/patru.png)

Dit brengt het hieronder getoonde venster omhoog, is de volgende stap een weg te kiezen waar de toestemming moet worden gevormd.

![](assets/cinci-1.png)

Hier selecteren wij een weg waar wij een toestemming voor **dam-users** willen vormen:

![](assets/sase-1.png)

Nadat het pad is geselecteerd, gaat de workflow terug naar dit scherm, waar de gebruiker een of meer rechten kan selecteren uit de beschikbare naamruimten (zoals `jcr`, `rep` of `crx`), zoals hieronder wordt weergegeven.

U kunt rechten toevoegen door te zoeken in het tekstveld en vervolgens te selecteren in de lijst.

>[!NOTE]
>
>Zie [deze pagina](/help/sites-administering/user-group-ac-admin.md#access-right-management) voor een volledige lijst met rechten en beschrijvingen.

![](assets/image2019-3-21_0-5-47.png) ![](assets/image2019-3-21_0-6-53.png)

Nadat de lijst met bevoegdheden is geselecteerd, kan de gebruiker het machtigingstype kiezen: Weigeren of Toestaan, zoals hieronder wordt weergegeven.

![](assets/screen_shot_2019-03-17at63938pm.png) ![](assets/screen_shot_2019-03-17at63947pm.png)

### Beperkingen {#using-restrictions} gebruiken

Naast een lijst met bevoegdheden en het machtigingstype op een bepaald pad, kunt u in dit scherm ook beperkingen toevoegen voor fijnkorrelig toegangsbeheer, zoals hieronder wordt getoond:

![](assets/image2019-3-21_1-4-14.png)

>[!NOTE]
>
>Voor meer informatie over wat elke beperking betekent, gelieve [deze pagina](/help/sites-administering/user-group-ac-admin.md#restrictions) te raadplegen.

U kunt beperkingen toevoegen zoals hieronder wordt weergegeven door het type beperking te kiezen, de waarde in te voeren en op het pictogram **+** te drukken. ![](assets/sapte-1.png) ![](assets/opt-1.png)

Het nieuwe ACE wordt weerspiegeld in de Lijst van het Toegangsbeheer zoals hieronder getoond. Merk op dat `jcr:write` een aggregaatvoorrecht is dat `jcr:removeNode` omvat die hierboven werd toegevoegd, maar hieronder niet als zijn behandeld onder `jcr:write` wordt getoond.

### ACE&#39;s bewerken {#editing-aces}

De Ingangen van het Toegangsbeheer kunnen worden uitgegeven door een hoofd te selecteren en ACE te kiezen die u wilt uitgeven.

Hier kunt u bijvoorbeeld de onderstaande vermelding voor **dam-users** bewerken door op het potloodpictogram aan de rechterkant te klikken:

![](assets/image2019-3-21_0-35-39.png)

Het bewerkingsscherm wordt weergegeven met de geconfigureerde ACE&#39;s die vooraf zijn geselecteerd. U kunt deze verwijderen door op het kruispictogram naast de ACE&#39;s te klikken of u kunt nieuwe bevoegdheden toevoegen voor het opgegeven pad, zoals hieronder wordt weergegeven.

![](assets/noua-1.png)

Hier voegen wij `addChildNodes` voorrecht voor **dam-users** op de bepaalde weg toe.

![](assets/image2019-3-21_0-45-35.png)

De veranderingen kunnen worden bewaard door **sparen** knoop op hoogste recht te klikken, en de veranderingen zullen in de nieuwe toestemmingen voor **dam-gebruikers **zoals hieronder getoond weerspiegelen:

![](assets/zece-1.png)

### ACE&#39;s {#deleting-aces} verwijderen

De Ingangen van het Toegangsbeheer kunnen worden geschrapt om alle toestemmingen te verwijderen die aan een hoofd op een specifieke weg worden gegeven. Het pictogram X naast ACE kan worden gebruikt om het te schrappen zoals hieronder getoond:

![](assets/image2019-3-21_0-53-19.png) ![](assets/unspe.png)

### Klassieke UI Privilege Combinaties {#classic-ui-privilege-combinations}

Merk op dat de nieuwe toestemmingenUI uitdrukkelijk de basisreeks voorrechten in plaats van vooraf bepaalde combinaties gebruikt die niet echt de nauwkeurige onderliggende voorrechten weerspiegelden die werden verleend.

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

