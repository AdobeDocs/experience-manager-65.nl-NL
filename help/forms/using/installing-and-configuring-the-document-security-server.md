---
title: De documentbeveiligingsserver installeren en configureren
description: Met documentbeveiliging kunt u alle gegevens die u in een ondersteunde indeling hebt opgeslagen, veilig verspreiden. Alleen gemachtigde gebruikers hebben toegang tot beveiligde documenten.
contentOwner: khsingh
role: Admin
exl-id: 4a4bad4a-3e68-43cb-b55c-03b509a5d304
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication,Document Security
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# De documentbeveiligingsserver installeren en configureren {#installing-and-configuring-the-document-security-server}

Met documentbeveiliging kunt u alle gegevens die u in een ondersteunde indeling hebt opgeslagen, veilig verspreiden. Alleen gemachtigde gebruikers hebben toegang tot beveiligde documenten.

Met de beveiliging van Adobe Experience Manager Forms-documenten kunt u ervoor zorgen dat alleen geautoriseerde gebruikers uw documenten kunnen gebruiken. Met documentbeveiliging kunt u veilig alle informatie verspreiden die u in een ondersteunde indeling hebt opgeslagen. Ondersteunde bestandsindelingen zijn onder andere PDF (Portable Document Format) en Microsoft Word-, Excel- en PowerPoint-bestanden.

U kunt documenten beschermen door beleid te gebruiken. De vertrouwelijkheidsmontages u in een beleid specificeert bepalen hoe een ontvanger een document kan gebruiken waarop u het beleid toepast. U kunt bijvoorbeeld opgeven of ontvangers tekst kunnen afdrukken of kopiëren, tekst kunnen bewerken of handtekeningen en opmerkingen kunnen toevoegen aan beveiligde documenten.

Het beleid wordt opgeslagen op de server van de Veiligheid van het Document; u past het beleid op documenten door uw cliënttoepassing toe. Wanneer u een beleid op een document toepast, beschermen de vertrouwelijkheidsmontages die in het beleid worden gespecificeerd de informatie die het document bevat. U kunt het document dat met een beleid is beveiligd, verspreiden onder ontvangers die door het beleid zijn gemachtigd.

Documentbeveiliging biedt ook clients, viewers en indexeerders om documenten te beveiligen, beveiligde documenten weer te geven en beveiligde documenten te indexeren. Voor gedetailleerde informatie over documentveiligheid, zie [ over documentveiligheid ](/help/forms/using/admin-help/document-security.md).

## Implementatietopologie  {#deployment-topology}

De beveiligingsmogelijkheden voor documenten zijn alleen beschikbaar in AEM Forms op JEE. U hebt één instantie van AEM Forms op JEE nodig. Indien nodig kunt u ook een cluster of farm van AEM Forms-servers maken. De volgende topologie is indicatieve topologie om het vermogen van de documentveiligheid in werking te stellen. Voor gedetailleerde informatie over de topologie, zie [ Architectuur en plaatsingstopologieën voor AEM Forms ](aem-forms-architecture-deployment.md).

<!--fix above link-->

![ de topologie van de de veiligheidsserver van het Document ](do-not-localize/document-security-server_topology.png)

In het volgende diagram ziet u de typische architectuur voor AEM Forms Document Security:

![ de veiligheid typische milieu van het Document ](do-not-localize/document-security-typical-environment.png)

## AEM Forms installeren op JEE {#installing-aem-forms-on-jee}

Voer de volgende stappen uit om AEM Forms op JEE te installeren en te configureren:

1. Download AEM 6.5 Forms op de installateur van JEE van de [ Vergunnende Website van de Adobe (LWS) ](https://licensing.adobe.com/). U hebt een geldig onderhouds- en ondersteuningscontract nodig om het installatieprogramma te downloaden.
1. Lees [ AEM Forms op JEE Ondersteunde documenten van Platforms ](/help/forms/using/aem-forms-jee-supported-platforms.md) en zorg ervoor dat de software, de hardware, de werkende systemen, toepassingsserver, gegevensbestanden, JDKs, en andere infrastructuur klaar hebben om AEM Forms op JEE te installeren.
1. (De niet-Turnkey installaties slechts) lezen [ Voorbereidend om één enkele server van AEM Forms ](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_64) of [ Voorbereidend om de servercluster van AEM Forms ](https://www.adobe.com/go/learn_aemforms_prepareInstallcluster_64) te installeren en uw milieu klaar te maken om AEM Forms op JEE te installeren en te vormen.
1. Kies afhankelijk van uw omgeving en toepassingsserver een van de volgende documenten en volg de instructies om de installatie te voltooien

   * [ het installeren van en het opstellen van AEM Forms op JEE gebruikend turnkey JBoss ](https://www.adobe.com/go/learn_aemforms_installTurnkey_64)
   * [ Installerend en plaatsend AEM Forms op JEE voor JBoss ](https://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [ Installerend en plaatsend AEM Forms op JEE voor WebLogic ](https://www.adobe.com/go/learn_aemforms_installWebLogic_64)
   * [ Installerend en het opstellen van AEM Forms op JEE voor WebSphere ](https://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [ Vormend AEM Forms op JEE op cluster JBoss ](https://www.adobe.com/go/learn_aemforms_clusterJBoss_64)
   * [ Vormend AEM Forms op JEE op cluster WebLogic ](https://www.adobe.com/go/learn_aemforms_clusterWebLogic_64)
   * [ Vormend AEM Forms op JEE op cluster WebSphere ](https://www.adobe.com/go/learn_aemforms_clusterWebSphere_64)

   >[!NOTE]
   >
   >Selecteer de optie Documentbeveiliging in het selectiescherm Module van AEM Forms in JEE Configuration Manager. Voor de optie Documentbeveiliging hoeft u geen andere module te selecteren.

## Volgende stappen {#next-steps}

* [Client- en serveropties configureren](/help/forms/using/admin-help/configuring-client-server-options.md)
* [Beleid maken en beheren](/help/forms/using/admin-help/creating-policies.md)
* [Beleidssets maken en beheren](/help/forms/using/admin-help/creating-policy-sets.md)
