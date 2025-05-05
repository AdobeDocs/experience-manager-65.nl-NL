---
title: Hoe te om Aangepast Forms tot stand te brengen gebruikend het Schema van XML?
description: Leer hoe u het XML-schema als formuliermodel in een adaptief formulier gebruikt. U kunt bestaande XSD-sjablonen toepassen om adaptieve formulieren te maken en schemaelementen van XSD naar het aangepaste formulier te slepen. Dig dieper in met een voorbeeld van een XML-schema, voeg speciale eigenschappen toe aan velden die gebruikmaken van het XML-schema en beperkt acceptabele waarden voor een adaptieve formuliercomponent.
feature: Adaptive Forms,Foundation Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 35d5859f-54c4-4d14-9c64-0d9291ef9029
solution: Experience Manager, Experience Manager Forms
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---

# Aangepaste formulieren maken met XML-schema {#creating-adaptive-forms-using-xml-schema}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Vereisten {#prerequisites}

Wanneer u een adaptief formulier maakt met een XML-schema als formuliermodel, hebt u basiskennis van XML-schema&#39;s nodig. Bovendien wordt aangeraden de volgende inhoud vóór dit artikel te lezen.

* [Een adaptief formulier maken](creating-adaptive-form.md)
* [ schema van XML ](https://www.w3.org/TR/xmlschema-2/)

## Een XML-schema gebruiken als formuliermodel {#using-an-xml-schema-as-form-model}

[!DNL Experience Manager Forms] ondersteunt het maken van een adaptief formulier met een bestaand XML-schema als formuliermodel. Dit schema van XML vertegenwoordigt de structuur waarin de gegevens door het achterste deelsysteem in uw organisatie worden geproduceerd of worden verbruikt.

De belangrijkste kenmerken van het gebruik van een XML-schema zijn:

* De structuur van de XSD wordt weergegeven als een structuur op het tabblad Inhoudszoeker in de ontwerpmodus voor een adaptief formulier. U kunt een element slepen van de XSD-hiërarchie naar het aangepaste formulier.
* U kunt het formulier vooraf invullen met een XML-bestand dat compatibel is met het bijbehorende schema.
* Bij verzending worden de gegevens die de gebruiker heeft ingevoerd, verzonden als XML die op het bijbehorende schema wordt uitgelijnd.

Een XML-schema bestaat uit eenvoudige en complexe elementtypen. De elementen hebben attributen die regels aan het element toevoegen. Wanneer deze elementen en kenmerken naar een adaptief formulier worden gesleept, worden ze automatisch toegewezen aan de bijbehorende adaptieve formuliercomponent.

Deze toewijzing van XML-elementen met adaptieve formuliercomponenten is als volgt:

<table>
 <tbody>
  <tr>
   <th><strong>XML-element of -kenmerk </strong></th>
   <th><strong>Aangepast formulieronderdeel</strong></th>
  </tr>
  <tr>
   <td><code>xs:string</code></td>
   <td>Tekstvak</td>
  </tr>
  <tr>
   <td><code>xs:boolean</code></td>
   <td>Selectievakje</td>
  </tr>
  <tr>
   <td>
    <ul>
     <li><code>xs:unsignedInt</code></li>
     <li><code>xs:xs:int</code></li>
     <li><code class="code">xs:decimal
        </code></li>
     <li>Alle typen numerieke waarden</li>
    </ul> </td>
   <td>Numeriek vak</td>
  </tr>
  <tr>
   <td><code>xs:date</code></td>
   <td>Datumkiezer</td>
  </tr>
  <tr>
   <td><code class="code">xs:enumeration
      </code></td>
   <td>Vervolgkeuzelijst</td>
  </tr>
  <tr>
   <td>Elk complex-type element</td>
   <td>Deelvenster</td>
  </tr>
 </tbody>
</table>

## Voorbeeld-XML-schema {#sample-xml-schema}

Hier is een voorbeeld van een XML-schema.

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="https://adobe.com/sample.xsd"
                    xmlns="https://adobe.com/sample.xsd"
                    xmlns:xs="https://www.w3.org/2001/XMLSchema"
                >

        <xs:element name="sample" type="SampleType"/>

        <xs:complexType name="SampleType">
            <xs:sequence>
                <xs:element name="leaderName" type="xs:string" default="Enter Name"/>
                <xs:element name="assignmentStartBirth" type="xs:date"/>
                <xs:element name="gender" type="GenderEnum"/>
                <xs:element name="noOfProjectsAssigned" type="IntType"/>
                <xs:element name="assignmentDetails" type="AssignmentDetails"
                                            minOccurs="0" maxOccurs="10"/>
            </xs:sequence>
        </xs:complexType>

        <xs:complexType name="AssignmentDetails">
            <xs:attribute name="name" type="xs:string" use="required"/>
            <xs:attribute name="durationOfAssignment" type="xs:unsignedInt" use="required"/>
            <xs:attribute name="numberOfMentees" type="xs:unsignedInt" use="required"/>
             <xs:attribute name="descriptionOfAssignment" type="xs:string" use="required"/>
             <xs:attribute name="financeRelatedProject" type="xs:boolean"/>
       </xs:complexType>
  <xs:simpleType name="IntType">
            <xs:restriction base="xs:int">
            </xs:restriction>
        </xs:simpleType>
  <xs:simpleType name="GenderEnum">
            <xs:restriction base="xs:string">
                <xs:enumeration value="Female"/>
                <xs:enumeration value="Male"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:schema>
```

>[!NOTE]
>
>Zorg ervoor dat uw XML-schema slechts één hoofdelement heeft. Een XML-schema met meer dan één hoofdelement wordt niet ondersteund.

## Speciale eigenschappen aan velden toevoegen met XML-schema {#adding-special-properties-to-fields-using-xml-schema}

U kunt de volgende kenmerken toevoegen aan elementen van een XML-schema om speciale eigenschappen toe te voegen aan de velden van het gekoppelde adaptieve formulier.

<table>
 <tbody>
  <tr>
   <th><strong>Schema, eigenschap</strong></th>
   <th><strong>Gebruik in adaptieve vorm</strong></th>
   <th><strong>Ondersteund in </strong></th>
  </tr>
  <tr>
   <td><code>use=required </code></td>
   <td>Merkt een verplicht gebied <br /> </td>
   <td>Kenmerk</td>
  </tr>
  <tr>
   <td><code>default="default value"</code></td>
   <td>Hiermee wordt een standaardwaarde toegevoegd</td>
   <td>Element en kenmerk</td>
  </tr>
  <tr>
   <td><code>minOccurs="3"</code></td>
   <td><p>Geeft minimale voorvallen op</p> <p>(Voor herhaalbare subformulieren (complexe typen))</p> </td>
   <td>Element (complex type)</td>
  </tr>
  <tr>
   <td><code class="code">maxOccurs="10"
      </code></td>
   <td><p>Hiermee worden de maximale voorvallen opgegeven</p> <p>(Voor herhaalbare subformulieren (complexe typen))</p> </td>
   <td>Element (complex type)</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Wanneer u een schema-element naar een adaptief formulier sleept, wordt een standaardbijschrift gegenereerd door:
>
>* Het eerste teken van de elementnaam omzetten in hoofdletters
>* Witruimte invoegen bij grenzen van camelhoofdletters.
>
>Als u bijvoorbeeld het schema-element `userFirstName` toevoegt, wordt het bijschrift dat in het adaptieve formulier wordt gegenereerd, ingesteld op `User First Name` .

## Acceptabele waarden voor een adaptieve formuliercomponent beperken {#limit-acceptable-values-for-an-adaptive-form-component}

U kunt de volgende beperkingen toevoegen aan elementen van het XML-schema om de waarden te beperken die acceptabel zijn voor een adaptieve formuliercomponent:

<table>
 <tbody>
  <tr>
   <td><p><strong> Schema, eigenschap</strong></p> </td>
   <td><p><strong>Gegevenstype</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
   <td><p><strong>Component</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>totalDigits</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee wordt het maximale aantal cijfers opgegeven dat in een component is toegestaan. Het opgegeven aantal cijfers moet groter zijn dan nul.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>maximum</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee geeft u de bovengrens voor numerieke waarden en datums op. Standaard wordt de maximumwaarde opgenomen.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap <br /> </li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minimum</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee geeft u de ondergrens voor numerieke waarden en datums op. Standaard wordt de minimumwaarde opgenomen.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap</li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMaximum</code></p> </td>
   <td><p>Boolean</p> </td>
   <td><p>Indien waar (true), moet de numerieke waarde of datum die in de component van het formulier is opgegeven, kleiner zijn dan de numerieke waarde of datum die voor de eigenschap maximum is opgegeven.</p> <p>Indien onwaar, moet de numerieke waarde of datum die in de component van de vorm wordt gespecificeerd minder dan of gelijk aan de numerieke waarde of de datum zijn die voor het maximumbezit wordt gespecificeerd.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap</li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMinimum</code></p> </td>
   <td><p>Boolean</p> </td>
   <td><p>Indien waar (true), moet de numerieke waarde of datum die in de component van het formulier is opgegeven, groter zijn dan de numerieke waarde of datum die voor de eigenschap minimum is opgegeven.</p> <p>Indien onwaar, moet de numerieke waarde of datum die in de component van de vorm wordt gespecificeerd groter zijn dan of gelijk aan de numerieke waarde of de datum die voor het minimumbezit wordt gespecificeerd.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap</li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minLength</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee wordt het minimale aantal tekens opgegeven dat in een component is toegestaan. De minimumlengte moet gelijk zijn aan of groter zijn dan nul.</p> </td>
   <td>
    <ul>
     <li>Tekstvak</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>maxLength</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee wordt het maximale aantal tekens opgegeven dat in een component is toegestaan. De maximumlengte moet groter zijn dan nul.</p> </td>
   <td>
    <ul>
     <li>Tekstvak</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>length</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee wordt het exacte aantal tekens opgegeven dat in een component is toegestaan. De lengte moet gelijk zijn aan of groter zijn dan nul.</p> </td>
   <td>
    <ul>
     <li>Tekstvak</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>fractionDigits</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee wordt het maximale aantal decimalen opgegeven dat in een component is toegestaan. De fractionDigits moet gelijk zijn aan of groter dan nul.</p> </td>
   <td>
    <ul>
     <li> Numeriek vak met gegevenstype zwevend of decimaal</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>pattern</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee geeft u de volgorde van de tekens op. Een component accepteert de tekens als de tekens overeenkomen met het opgegeven patroon.</p> <p>De eigenschap pattern verwijst naar het validatiepatroon van de overeenkomstige adaptieve formuliercomponent.</p> </td>
   <td>
    <ul>
     <li>Alle componenten voor adaptieve formulieren die zijn toegewezen aan een XSD-schema </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Veelgestelde vragen {#frequently-asked-questions}

**hoe ik weet welk element in de boom met welk element van XML wordt geassocieerd?**

Wanneer u dubbelklikt op een element in de Inhoudszoeker, wordt in een pop-upvenster een veldnaam en een eigenschap met de naam `bindRef` weergegeven. Deze eigenschap wijst het structuurelement toe aan het element of kenmerk in het schema.

![ het bindref gebied van A van een het schemaelement van XML ](assets/dblclick.png)

<code> bindRef</code> in het veld wordt de koppeling weergegeven tussen een structuurelement en een element of kenmerk in een schema.

>[!NOTE]
>
>Attributen hebben een `@` symbool in hun `bindRef` waarde om hen van elementen te onderscheiden. Bijvoorbeeld `/config/projectDetails/@duration` .

**waarom ik niet individuele elementen van een subformulier (structuur die van om het even welk complex type wordt geproduceerd) voor herhaalbare subforms (minOccurs of maxOccurs waarden zijn groter dan 1) kan slepen?**

In een herhaalbaar subformulier moet u het subformulier Voltooien gebruiken. Als u alleen selectieve velden wilt, gebruikt u de volledige structuur en verwijdert u de ongewenste velden.

**ik heb een lange complexe structuur in de Vinder van de Inhoud. Hoe kan ik een specifiek element vinden?**

U hebt twee opties:

* Door de boomstructuur schuiven
* Gebruik het vak Zoeken om een element te zoeken

**wat is een bindRef?**

A `bindRef` is de verbinding tussen een adaptieve formuliercomponent en een schema-element of -kenmerk. De waarde die wordt vastgelegd vanuit deze component of dit veld, wordt voorgeschreven in de `XPath` waar de waarde beschikbaar is in de uitvoer-XML. A `bindRef` wordt ook gebruikt wanneer het prepopuleren van een gebiedswaarde van vooraf ingevulde (vooraf ingevulde) XML.
