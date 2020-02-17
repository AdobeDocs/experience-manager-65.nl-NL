---
title: Formulieren maken met herhaalbare secties
seo-title: Formulieren maken met herhaalbare secties
description: Herhalbare secties zijn deelvensters die dynamisch aan een formulier kunnen worden toegevoegd of eruit kunnen worden verwijderd.
seo-description: Herhalbare secties zijn deelvensters die dynamisch aan een formulier kunnen worden toegevoegd of eruit kunnen worden verwijderd.
uuid: c3fa2aa4-a6b4-458e-8534-138e075290b1
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 01724ca0-6901-45e7-b045-f44814ed574e
translation-type: tm+mt
source-git-commit: 9d90bc5f77f827925e3e1ecd12d56a94a2bbae30

---


# Formulieren maken met herhaalbare secties {#creating-forms-with-repeatable-sections}

Herhaalbare secties zijn deelvensters die dynamisch aan een formulier kunnen worden toegevoegd of eruit kunnen worden verwijderd.

Tijdens het aanvragen van een baan verschaft de werkzoekende bijvoorbeeld eerdere werkgelegenheidsgegevens, zoals bedrijfsnaam, rol, project en andere informatie. De informatie van alle werkgevers vereist verschillende, maar gelijksoortige rubrieken. In een dergelijk scenario voorziet het formulier voor de arbeidsvoorziening in een sectie van de werkgever en biedt het ook de mogelijkheid om dynamisch meer van dergelijke secties toe te voegen. Deze secties, die dynamisch worden toegevoegd, worden genoemd Herhalbare secties.

U kunt een van de volgende methoden gebruiken om herhaalbare deelvensters te maken:

## Instance Manager gebruiken via scripts {#using-instance-manager-via-scripts-nbsp}

1. Selecteer in de bewerkingsmodus een deelvenster en tik vervolgens op ![cmp](assets/cmppr.png). Schakel in het zijpaneel onder Eigenschappen de optie Deelvenster **opnieuw** maken in. Geef waarden op voor de velden **[!UICONTROL Maximaal]** en **[!UICONTROL Minimaal]** .

   In het veld Maximaal wordt het maximale aantal keer opgegeven dat een deelvenster op de pagina kan worden weergegeven. U kunt -1 opgeven in het veld Maximum aantal om het deelvenster een oneindig aantal keren weer te geven.

   Met het veld Minimaal geeft u op hoe vaak het aantal keer dat een deelvenster wordt weergegeven op het formulier, minimaal moet zijn. Als u het veld Minimum aantal op nul instelt, kunt u later alle instanties via scripts verwijderen nadat de vertoning is voltooid.

   >[!NOTE]
   >
   >Als u een niet-herhaalbaar deelvenster wilt maken, stelt u de waarde van het veld Maximaal en Minimaal in op 1. De accordeonlay-out ondersteunt geen -1 in het veld Maximum aantal. U kunt een hoog getal opgeven om een oneindige waarde op te geven.

1. Het bovenliggende element van het deelvenster, dat moet worden herhaald, moet knoppen voor toevoegen en verwijderen bevatten om instanties van de herhaalbare deelvensters te beheren. Voer de volgende stappen uit om knoppen in te voegen in het bovenliggende element en om scripts in de knoppen in te schakelen:

   1. Sleep vanuit het zijpaneel een knopcomponent naar het bovenliggende element van het deelvenster. Selecteer de component en tik op ![bewerkingsregels](assets/edit-rules.png). De regels van de knoop open in de regelredacteur.
   1. Klik in het venster Regeleditor op **Maken**.

      Selecteer **Visuele editor** in de rij Formulierobjecten en -functies.

      1. In het regelgebied, onder WHEN, **wordt de uitgezochte staat geklikt**.
      1. Onder DAN:

         * Als u een knop in het deelvenster Toevoegen wilt maken, selecteert u **Instantie** toevoegen en sleept u het deelvenster met het ![schakelpaneel](assets/toggle-side-panel.png) . U kunt het deelvenster ook selecteren met het **object Drop of hier selecteren.**
         * Als u een knop in het deelvenster Verwijderen wilt maken, selecteert u Instantie **** verwijderen en sleept u het deelvenster met het ![deelvenster](assets/toggle-side-panel.png) en/of selecteert u het met het object **Drop of selecteert u hier naartoe.**
      Selecteer **Code-editor** in de rij Formulierobjecten en -functies. Klik op Regels **** bewerken en in het codegebied:

      * Als u een knop in het deelvenster Toevoegen wilt maken, geeft u `this.panel.instanceManager.addInstance()`
      * Als u een knop in het deelvenster Verwijderen wilt maken, geeft u `this.panel.instanceManager.removeInstance(this.panel.instanceIndex)`
      Klik op **Gereed**.

      >[!NOTE]
      >
      >Als een veld tot een herhaalbaar deelvenster behoort, kunt u het veld niet rechtstreeks openen met de naam ervan in uw scripts. Als u toegang wilt krijgen tot het veld, geeft u de herhaalbare instantie op waartoe het veld behoort met behulp van de `instances` API in `InstanceManager`. De syntaxis voor het gebruik van de `instances` API in `InstanceManager` is:
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
      >Als u AA1-gegevens wilt lezen, geeft u op:
      >
      >
      >`Panel1.instanceManager.instances[0].textbox.value`
      >
      >
      >Als u AA2-gegevens wilt lezen, geeft u op:
      >
      >
      >`Panel1.instanceManager.instances[1].textbox.value`
      >
      >
      > Zie voor meer informatie: Klasse: InstanceManager#instances in [AEM Forms Java API reference](https://adobe.com/go/learn_aemforms_documentation_63).

      >[!NOTE]
      >
      >Wanneer alle instanties van een deelvenster uit een adaptief formulier zijn verwijderd en u een instantie van het verwijderde deelvenster wilt toevoegen, gebruikt u de syntaxis _panelName om het Instance Manager van het deelvenster vast te leggen en gebruikt u de API van Instance Manager addInstance om de verwijderde instantie toe te voegen. Bijvoorbeeld _panelName.addInstance(). Er wordt een instantie van het verwijderde deelvenster toegevoegd.















## De accordeonlay-out gebruiken voor het bovenliggende deelvenster {#using-the-accordion-layout-for-the-parent-panel-nbsp}

Een deelvenster heeft verschillende layoutopties. De optie Layout voor accordeonontwerp heeft geen ondersteuning voor herhaalbare deelvensters. Voer de volgende stappen uit naar het herhaalbare deelvenster met de optie Layout voor accordeonontwerp:

1. Tik op ![cmp in het bovenliggende deelvenster dat u wilt herhalen](assets/cmppr.png). U kunt de eigenschappen in de zijbalk zien. Selecteer in de vervolgkeuzelijst **Lay-out** de optie **Accordeon**.
1. Tik in een deelvenster op ![cmp](assets/cmppr.png)dat moet worden herhaald. U kunt de deelvenstereigenschappen in de zijbalk zien. Schakel het tabblad **Deelvenster reproduceerbaar** maken in en geef waarde op voor de velden **Maximaal** en **Minimaal** .

   Nu kunt u de plus- (+) en verwijderknoppen ( ![delete-panel](assets/delete-panel.png)) gebruiken om deelvensters toe te voegen en te verwijderen.

## Herhalende subformulieren gebruiken vanuit formuliersjabloon (XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

Herhalbaar subformulier is vergelijkbaar met de herhaalbare deelvensters in Adaptieve formulieren. Voer in AEM Forms Designer de volgende stappen uit om een herhalend subformulier te maken:

1. Selecteer in het palet Hiërarchie het bovenliggende subformulier van het subformulier dat u wilt herhalen.
1. Klik in het palet Object op het tabblad Subformulier en selecteer Overlopen in de lijst Inhoud.
1. Selecteer het subformulier dat moet worden herhaald.
1. Klik in het palet Object op het tabblad Subformulier en selecteer Geplaatst of Overlopen in de lijst Inhoud.
1. Klik op het tabblad Binding en selecteer Subformulier herhalen voor elk gegevensitem.
1. Als u een minimumaantal herhalingen wilt opgeven, selecteert u Min. aantal en typt u een aantal in het bijbehorende vak. Als deze optie is ingesteld op 0 en er geen gegevens zijn opgegeven voor de objecten in het subformulier wanneer de gegevens worden samengevoegd, wordt het subformulier niet geplaatst wanneer het formulier wordt gegenereerd.
1. Als u een maximumaantal herhalingen van het subformulier wilt opgeven, selecteert u Max en typt u een aantal in het bijbehorende vak. Als u geen waarde opgeeft in het vak Max, is het aantal herhalingen van het subformulier onbeperkt.
1. Als u een setnummer van subformulierherhalingen wilt opgeven, ongeacht de hoeveelheid gegevens, selecteert u de optie Eerste telling en typt u een aantal in het bijbehorende vak. Als u deze optie selecteert en er geen gegevens beschikbaar zijn of er minder gegevensvermeldingen zijn dan opgegeven bij Eerste telling, worden lege exemplaren van het subformulier toch in het formulier geplaatst.
1. Voeg twee knoppen toe aan het bovenliggende subformulier: een voor het toevoegen van een exemplaar en een andere voor het verwijderen van exemplaren van herhaalbare subformulieren. Zie Een handeling [](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2)maken voor gedetailleerde stappen.
1. Koppel nu de formuliersjabloon aan het adaptieve formulier. Zie [Een adaptief formulier maken op basis van een sjabloon](/help/forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-a-template)voor gedetailleerde stappen.
1. Gebruik de knoppen die u in stap 9 hebt gemaakt om subformulieren toe te voegen en te verwijderen.

ZIP-bestand dat is gekoppeld, bevat een voorbeeld van een herhaalbaar subformulier.

[Bestand ophalen](assets/samplerepeatablesubform.zip)

## Herhalingsinstellingen van een XML-schema (XSD) gebruiken {#using-repeat-settings-of-an-xml-schema-xsd-br}

U kunt herhaalbare panelen van een Schema van XML en van het minOccurs &amp; maxOccurs bezit van om het even welk complex typeelement tot stand brengen. Zie Aangepaste formulieren [maken met XML-schema als formuliermodel](/help/forms/using/adaptive-form-xml-schema-form-model.md)voor meer informatie over XML-schema.

In de volgende code gebruikt het `SampleType`deelvenster de eigenschap minOccurs &amp; maxOccurs.

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
