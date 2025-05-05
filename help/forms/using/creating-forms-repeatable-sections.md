---
title: Formulieren maken met herhaalbare secties
description: Herhalbare secties zijn deelvensters die dynamisch aan een formulier kunnen worden toegevoegd of eruit kunnen worden verwijderd.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 01724ca0-6901-45e7-b045-f44814ed574e
feature: Adaptive Forms,Foundation Components
exl-id: f2abae0a-f7fd-4a39-bd8c-03492ce06fe9
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 0%

---

# Formulieren maken met herhaalbare secties {#creating-forms-with-repeatable-sections}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

Herhaalbare secties zijn deelvensters die dynamisch aan een formulier kunnen worden toegevoegd of eruit kunnen worden verwijderd.

Tijdens het aanvragen van een baan verschaft de werkzoekende bijvoorbeeld eerdere werkgelegenheidsgegevens, zoals bedrijfsnaam, rol, project en andere informatie. De informatie van alle werkgevers vereist verschillende, maar gelijksoortige rubrieken. In een dergelijk scenario voorziet het formulier voor de arbeidsvoorziening in een sectie van de werkgever en biedt het ook de mogelijkheid om dynamisch meer van dergelijke secties toe te voegen. Deze secties, die dynamisch worden toegevoegd, worden genoemd Herhalbare secties.

U kunt een van de volgende methoden gebruiken om herhaalbare deelvensters te maken:

## Instance Manager gebruiken via scripts  {#using-instance-manager-via-scripts-nbsp}

1. Op uitgeeft wijze, selecteer een paneel, dan uitgezochte ![ cmp ](assets/cmppr.png). In sidebar, onder Eigenschappen, laat **toe om Comité te herhalen**. Geef waarden op voor de velden **[!UICONTROL Maximum]** en **[!UICONTROL Minimum]** .

   In het veld Maximaal wordt het maximale aantal keer opgegeven dat een deelvenster op de pagina kan worden weergegeven. U kunt -1 opgeven in het veld Maximum aantal om het deelvenster een oneindig aantal keren weer te geven.

   Met het veld Minimaal geeft u op hoe vaak het aantal keer dat een deelvenster wordt weergegeven op het formulier. Als u het veld Minimum aantal op nul instelt, kunt u later alle instanties via scripts verwijderen nadat de vertoning is voltooid.

   >[!NOTE]
   >
   >Als u een niet-herhaalbaar deelvenster wilt maken, stelt u de waarde van het veld Maximaal en Minimaal in op 1. De accordeonlay-out ondersteunt geen -1 in het veld Maximum aantal. U kunt een hoog getal opgeven om een oneindige waarde op te geven.

1. Het bovenliggende element van het deelvenster, dat moet worden herhaald, moet knoppen voor toevoegen en verwijderen bevatten om instanties van de herhaalbare deelvensters te beheren. Voer de volgende stappen uit om knoppen in te voegen in het bovenliggende element en om scripts in de knoppen in te schakelen:

   1. Sleep vanuit het zijpaneel een knopcomponent naar het bovenliggende element van het deelvenster. Selecteer de component en selecteer ![ uitgeven-regels ](assets/edit-rules.png). De regels van de knoop open in de regelredacteur.
   1. In het venster van de Redacteur van de Regel, leidt de klik **&#x200B;**&#x200B;tot.

      Selecteer **Visuele Redacteur** in de rij van Objecten en van Functies van de Vorm.

      1. In het regelgebied, onder WANNEER, wordt de uitgezochte staat **geklikt**.
      1. Onder DAN:

         * Om toe te voegen voeg paneelknoop toe, **voeg Instantie** toe, en belemmering-daling het paneel gebruikend ![ toe knevel-zij-paneel ](assets/toggle-side-panel.png) of selecteer het gebruikend **voorwerp van de Daling of selecteer hier.**
         * Om tot een schrappingspaneelknoop te leiden, verwijder **Instantie**, en sleep-daling het paneel gebruikend ![ knevel-zij-paneel ](assets/toggle-side-panel.png) of selecteer het gebruikend **voorwerp van de Daling of selecteer hier.**

      Selecteer **Redacteur van de Code** in de rij van Objecten en van Functies van de Vorm. Klik **uitgeven Regels** en in het codegebied:

      * Als u een knop in het deelvenster Toevoegen wilt maken, geeft u `this.panel.instanceManager.addInstance()` op
      * Als u een knop in het deelvenster Verwijderen wilt maken, geeft u op `this.panel.instanceManager.removeInstance(this.panel.instanceIndex)`

      Klik **Gedaan**.

      >[!NOTE]
      >
      >Als een veld tot een herhaalbaar deelvenster behoort, kunt u het veld niet rechtstreeks openen met de naam ervan in uw scripts. Als u toegang wilt krijgen tot het veld, geeft u met de API `instances` in `InstanceManager` de herhaalbare instantie op waartoe het veld behoort. De syntaxis voor het gebruik van de `instances` API in `InstanceManager` is:
      >
      >
      >`<panelName>.instanceManager.instances[<instanceNumber>].<fieldname>`
      >
      >
      >U maakt bijvoorbeeld een adaptief formulier met een herhaalbaar deelvenster met een tekstvak. Wanneer u het formulier vooraf invult met drie herhaalbare tekstvakken, hebt u de xml hieronder nodig:
      >
      >
      >`<panel1><textbox1>AA1</panel1></textbox1>`
      >
      >
      >`<panel1><textbox1>AA2</panel1></textbox1>`
      >
      >
      >`<panel1><textbox1>AA3</panel1></textbox1>`
      >
      >
      >Als u AA1-gegevens wilt lezen, geeft u:
      >
      >
      >`Panel1.instanceManager.instances[0].textbox.value`
      >
      >
      >Als u AA2-gegevens wilt lezen, geeft u:
      >
      >
      >`Panel1.instanceManager.instances[1].textbox.value`
      >
      >
      >Voor meer informatie, zie: Klasse: InstanceManager#instances in [ AEM Forms Java API verwijzing ](https://adobe.com/go/learn_aemforms_documentation_63).

      >[!NOTE]
      >
      >Wanneer alle instanties van een deelvenster uit een adaptief formulier zijn verwijderd en u een instantie van het verwijderde deelvenster wilt toevoegen, gebruikt u de syntaxis _panelName om het Instance Manager van het deelvenster vast te leggen en gebruikt u de API van Instance Manager addInstance om de verwijderde instantie toe te voegen. Bijvoorbeeld _panelName.addInstance(). Er wordt een instantie van het verwijderde deelvenster toegevoegd.

## De accordeonlay-out gebruiken voor het bovenliggende deelvenster   {#using-the-accordion-layout-for-the-parent-panel-nbsp}

Een deelvenster heeft verschillende lay-outopties. De optie Layout voor accordeonontwerp biedt geen ondersteuning voor herhaalbare deelvensters. Voer de volgende stappen uit naar het herhaalbare deelvenster met de optie Layout voor accordeonontwerp:

1. Op de ouder van paneel dat moet worden herhaald, uitgezochte ![ cmp ](assets/cmppr.png). U kunt de eigenschappen in de zijbalk zien. In de **drop-down Lay-out**, uitgezochte **Accordeon**.
1. Voor een paneel, dat moet worden herhaald, selecteer ![ cmp ](assets/cmppr.png). U kunt de deelvenstereigenschappen in de zijbalk zien. Laat het **Van het Comité Herhaalbare** tabel maken, en specificeer waarde voor **Maximum** en **Minimum** gebieden.

   Nu, kunt u plus (+) gebruiken en ( ![ schrappen-paneel ](assets/delete-panel.png)) knopen schrappen om de panelen toe te voegen en te verwijderen.

## Herhalende subformulieren gebruiken vanuit formuliersjabloon (XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

Herhalbaar subformulier is vergelijkbaar met de herhaalbare deelvensters in Adaptief Forms. Voer in AEM Forms Designer de volgende stappen uit om een herhalend subformulier te maken:

1. Selecteer in het palet Hiërarchie het bovenliggende subformulier van het subformulier dat u wilt herhalen.
1. Klik in het palet Object op het tabblad Subformulier en selecteer Overlopen in de lijst Inhoud.
1. Selecteer het subformulier dat u wilt herhalen.
1. Klik in het palet Object op het tabblad Subformulier en selecteer Geplaatst of Overlopen in de lijst Inhoud.
1. Klik op het tabblad Binding en selecteer Subformulier herhalen voor elk gegevensitem.
1. Als u het minimale aantal herhalingen wilt opgeven, selecteert u Min. aantal en typt u een getal in het bijbehorende vak. Als deze optie is ingesteld op 0 en er geen gegevens zijn opgegeven voor de objecten in het subformulier bij het samenvoegen van gegevens, wordt het subformulier niet geplaatst wanneer het formulier wordt gegenereerd.
1. Als u het maximale aantal herhalingen van subformulieren wilt opgeven, selecteert u Max en typt u een getal in het bijbehorende vak. Als u geen waarde opgeeft in het vak Max, is het aantal herhalingen van het subformulier onbeperkt.
1. Als u een ingesteld aantal herhalingen van subformulieren wilt opgeven, ongeacht de hoeveelheid gegevens, selecteert u Eerste telling en typt u een getal in het bijbehorende vak. Als u deze optie selecteert en er geen gegevens beschikbaar zijn of er minder gegevensitems zijn dan de opgegeven waarde bij Eerste telling, worden lege exemplaren van het subformulier nog steeds op het formulier geplaatst.
1. Voeg twee knoppen toe aan het bovenliggende subformulier: een voor het toevoegen van een exemplaar en een andere voor het verwijderen van exemplaren van herhaalbare subformulieren. Voor gedetailleerde stappen, zie [ een actie ](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2) bouwen.
1. Koppel nu de formuliersjabloon aan het adaptieve formulier. Voor gedetailleerde stappen, zie [ een adaptieve vorm creëren die op een malplaatje ](/help/forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-a-template) wordt gebaseerd.
1. Gebruik de knoppen die u in stap 9 hebt gemaakt om subformulieren toe te voegen en te verwijderen.

ZIP-bestand dat is gekoppeld, bevat een voorbeeld van een herhaalbaar subformulier.

[Bestand ophalen](assets/samplerepeatablesubform.zip)

## Herhalingsinstellingen van een XML-schema (XSD) gebruiken {#using-repeat-settings-of-an-xml-schema-xsd-br}

U kunt herhaalbare panelen van een Schema van XML en van het minOccurs &amp; maxOccurs bezit van om het even welk complex typeelement tot stand brengen. Voor gedetailleerde informatie over het Schema van XML, zie [ adaptieve vormen creëren gebruikend het Schema van XML als Model van de Vorm ](/help/forms/using/adaptive-form-xml-schema-form-model.md).

In de volgende code, gebruikt het `SampleType` paneel minOccours &amp; maxOccurs bezit.

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
                <xs:element name="assignmentStartDate" type="xs:date"/>
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
>Voor een niet-harmonische indeling gebruikt u adaptieve componenten van een formulierknop om instanties toe te voegen en te verwijderen.
