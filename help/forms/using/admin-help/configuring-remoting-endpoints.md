---
title: Het vormen het Verwijderen eindpunten
description: Leer hoe te om remoting eindpunten te vormen. In dit document wordt uitgelegd hoe u toepassingen die zijn gemaakt met Flex, kunt laten gebruiken om de service aan te roepen met de functie AEM formulieren verwijderen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 891d7d75-555a-46c6-a8a0-d5238b48bc79
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---

# Het vormen het Verwijderen eindpunten {#configuring-remoting-endpoints}

Met een extern eindpunt kan een toepassing die met Flex is gebouwd, de service aanroepen met (Verouderd voor AEM formulieren) AEM formulieren Remoting. Een remoting eindpunt wordt automatisch gecreeerd voor elke geactiveerde dienst. Een bestemming van Flex die de zelfde naam zoals het eindpunt heeft wordt gecreeerd, en de cliënten van Flex kunnen verre voorwerpen tot stand brengen die aan deze bestemming richten om verrichtingen op de relevante dienst aan te halen.

## Instellingen voor eindpunten verwijderen {#remoting-endpoint-settings}

**Flex Client Authentication Method:** Bepaalt het type van reactie dat de server terug naar de cliënt verzendt wanneer de aangehaalde dienst toegelaten veiligheid is, steunt de aangehaalde verrichting geen anonieme aanroepen, en de cliënt gaat of in geen of ongeldige geloofsbrieven over.
