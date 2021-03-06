---
title: Taakvariabelen ophalen in Summiere URL
seo-title: Taakvariabelen ophalen in Summiere URL
description: Hoe te om de informatie over een taak te hergebruiken en een Samenvatting URL te produceren om een taak samen te vatten of te beschrijven.
seo-description: Hoe te om de informatie over een taak te hergebruiken en een Samenvatting URL te produceren om een taak samen te vatten of te beschrijven.
uuid: 9eab3a6a-a99a-40ae-b483-33ec7d21c5b6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 6dc31bec-b02d-47db-a4f4-be8c14c5619e
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---


# Taakvariabelen ophalen in overzicht-URL {#getting-task-variables-in-summary-url}

Op de overzichtspagina wordt informatie over taken weergegeven. In dit artikel wordt beschreven hoe u taakgerelateerde informatie in de overzichtspagina kunt hergebruiken.

In deze voorbeeldorganisatie dient een medewerker een formulier voor een verlofaanvraag in. Het aanvraagformulier gaat vervolgens ter goedkeuring naar de manager van de werknemer.

1. Maak een voorbeeld van een HTML-renderer (html.esp) voor het TypeResponse **Employees/PtoApplication**.

   De renderer gaat ervan uit dat de volgende eigenschappen op het knooppunt moeten worden ingesteld:

   * naam
   * leegmaken
   * reason
   * duration

   >[!NOTE]
   >
   >Deze renderer is de sjabloon voor de overzichtspagina.

   De volgende voorbeeldcode voor deze renderer is opgenomen in:

   `apps/Employees/PtoApplication/html.esp`

   ```html
   <html>
     <body>
       <table>
       <tbody>
       <tr>
           <td>
               <h3>Employee Name: <%= currentNode.ename %></h3>
               <h3>Employee ID: <%= currentNode.eid %></h3>
               <h3>Leave duration: <%= currentNode.duration %> days</h3>
               <h3>Reason: <%= currentNode.reason %></h3>
           </td>
       </tr>
       </tbody>
       </table>
     </body>
   </html>
   ```

1. Pas het orkest aan om de vier eigenschappen uit de ingediende formuliergegevens te halen. Na dit creeer een knoop in CRX van type **Employees/PtoApplication**, met de bevolkte eigenschappen.

   1. Creeer een proces **creeer PTO samenvatting** en gebruik dit als subprocess v????r **Assign Taak** verrichting in uw orchestratie.
   1. Definieer **employeeNaam**, **employeeID**, **ptoReason**, **totalDays** en **nodeName** als invoervariabelen in uw nieuwe proces. Deze variabelen worden doorgegeven als verzonden formuliergegevens.

      Definieer ook een uitvoervariabele **ptoNodePath** die wordt gebruikt tijdens het instellen van de samenvatting-URL.

   1. In **creeer PTO summiere** proces, gebruik **vastgestelde waarde** component om de inputdetails in een **nodeProperty** (**nodeProps**) kaart te plaatsen.

      De sleutels in deze kaart zouden het zelfde moeten zijn als de sleutels die in uw renderer van HTML in de vorige stap worden bepaald.

      Voeg ook een **sling:resourceType** sleutel met waarde **Employees/PtoApplication** in de kaart toe.

   1. Gebruik het subproces **storeContent** van de **ContentRepositoryConnector** dienst in **creeer PTO summiere** proces. Met dit subproces wordt een CRX-knooppunt gemaakt.

      Er zijn drie invoervariabelen voor nodig:

      * **Pad naar** map: Het pad waar het nieuwe CRX-knooppunt wordt gemaakt. Stel het pad in als **/content**.
      * **Node name**: Wijs de input variable nodeName aan dit gebied toe. Dit is een unieke tekenreeks met een knooppuntnaam.
      * **Type** knooppunt: Definieer het type als  **niet:ongestructureerd**. De uitvoer van dit proces is nodePath. Het nodePath is het CRX-pad van het nieuwe knooppunt. De nodePath zou de definitieve output van het **creeer PTO** overzichtsproces zijn.
   1. Geef de ingediende formuliergegevens (**employeeName**, **employeeID**, **ptoReason** en **totalDays**) door als invoer voor het nieuwe proces **PTO-overzicht** maken. Neem de uitvoer als **ptoSummaryNodePath**.


1. Definieer de samenvatting-URL als een XPath-expressie die de serverdetails bevat, samen met **ptoSummaryNodePath**.

   XPath: `concat('https://[*server*]:[*port*]/lc',/process_data/@ptoSummaryNodePath,'.html')`.

Wanneer u een taak opent in de AEM Forms-werkruimte, krijgt de summiere URL toegang tot het CRX-knooppunt en geeft de HTML-renderer het overzicht weer.

De overzichtslay-out kan worden gewijzigd zonder het proces te wijzigen. De HTML-renderer geeft het overzicht op de juiste wijze weer.
