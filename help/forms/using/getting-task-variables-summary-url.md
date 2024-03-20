---
title: Taakvariabelen ophalen in Summiere URL
description: Hoe te om de informatie over een taak te hergebruiken en een Samenvatting URL te produceren om een taak samen te vatten of te beschrijven.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: b5e27b54-d141-48dd-a4ed-dd0a691319a5
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Taakvariabelen ophalen in Summiere URL {#getting-task-variables-in-summary-url}

Op de overzichtspagina wordt informatie over taken weergegeven. In dit artikel wordt beschreven hoe u taakgerelateerde informatie in de overzichtspagina kunt hergebruiken.

In deze voorbeeldorganisatie dient een medewerker een formulier voor een verlofaanvraag in. Het aanvraagformulier gaat vervolgens ter goedkeuring naar de manager van de werknemer.

1. Een voorbeeld van een HTML-renderer (html.esp) maken voor ArraftType **Werknemers/PtoApplication**.

   De renderer gaat ervan uit dat de volgende eigenschappen op het knooppunt moeten worden ingesteld:

   * naam
   * leegmaken
   * reden
   * duur

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

1. Pas het orkest aan om de vier eigenschappen uit de ingediende formuliergegevens te halen. Hierna maakt u een knooppunt in CRX van het type **Werknemers/PtoApplication**, met de eigenschappen gevuld.

   1. Een proces maken **PTO-overzicht maken** en gebruik dit als een subproces vóór de **Taak toewijzen** in uw orkest.
   1. Definiëren **employeeName**, **employeeID**, **ptoReason**, **totalDays**, en **nodeName** als invoervariabelen in uw nieuwe proces. Deze variabelen worden doorgegeven als verzonden formuliergegevens.

      Ook een uitvoervariabele definiëren **ptoNodePath** wordt gebruikt bij het instellen van de samenvatting-URL.

   1. In de **PTO-overzicht maken** proces gebruiken **waarde instellen** om de invoerdetails in een **nodeProperty**(**nodeProps**) kaart.

      De sleutels in deze kaart zouden het zelfde moeten zijn als de sleutels die in uw renderer van HTML in de vorige stap worden bepaald.

      Voeg ook een **sling:resourceType** key with value **Werknemers/PtoApplication** op de kaart.

   1. Het subproces gebruiken **storeContent** van de **ContentRepositoryConnector** in de **PTO-overzicht maken** proces. Dit subproces leidt tot een knoop CRX.

      Er zijn drie invoervariabelen voor nodig:

      * **Mappad**: Het pad waar het nieuwe CRX-knooppunt wordt gemaakt. Pad instellen als **/content**.
      * **Knooppuntnaam**: Wijs de invoervariabele nodeName aan dit veld toe. Dit is een unieke tekenreeks met een knooppuntnaam.
      * **Knooppunttype**: Definieer het type als **nt:ongestructureerd**. De uitvoer van dit proces is nodePath. Het nodePath is het CRX-pad van het nieuwe knooppunt. De nodePath zou de definitieve output van zijn **PTO maken** samenvattingsproces.

   1. De verzonden formuliergegevens doorgeven (**employeeName**, **employeeID**, **ptoReason**, en **totalDays**) als input voor het nieuwe proces **PTO-overzicht maken**. De uitvoer als volgt instellen **ptoSummaryNodePath**.

1. De samenvatting-URL definiëren als een XPath-expressie die de serverdetails bevat, samen met **ptoSummaryNodePath**.

   XPath: `concat('https://[*server*]:[*port*]/lc',/process_data/@ptoSummaryNodePath,'.html')`.

Wanneer u een taak opent in de AEM Forms-werkruimte, krijgt de summiere URL toegang tot het CRX-knooppunt en geeft de HTML-renderer het overzicht weer.

De overzichtslay-out kan worden gewijzigd zonder het proces te wijzigen. De HTML renderer geeft het overzicht correct weer.
