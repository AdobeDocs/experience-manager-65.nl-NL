---
title: Externe functies in Expression Builder
description: Met Expression Builder in Correspondence Management kunt u expressies en externe functies maken.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: b41af9fe-c698-44b3-9ac6-97d42cdc02d4
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---

# Externe functies in Expression Builder{#remote-functions-in-expression-builder}

Met de expressiebouwer kunt u expressies of voorwaarden maken waarmee berekeningen worden uitgevoerd op gegevenswaarden die worden geleverd door het gegevenswoordenboek of door eindgebruikers. Het Beheer van de correspondentie gebruikt het resultaat van de uitdrukkingsevaluatie om activa zoals tekst, beelden, lijsten, en voorwaarden te selecteren en hen op te nemen in de correspondentie zoals vereist.

## Expressies en externe functies maken met expressiebuilder {#creating-expressions-and-remote-functions-with-expression-builder}

De expressiebouwer gebruikt intern JSP EL-bibliotheken, zodat de expressie voldoet aan de JSPEL-syntaxis. Voor meer informatie, zie [ uitdrukkingen van het Voorbeeld ](#exampleexpressions).

![ Bouwer van de Uitdrukking ](assets/expressionbuilder.png)

### Operatoren {#operators}

De operatoren die beschikbaar zijn voor gebruik in expressies zijn beschikbaar in de bovenste balk van de expressiebouwer.

### Voorbeeldexpressies {#exampleexpressions}

Hier zijn een paar algemeen gebruikte JSP EL voorbeelden die u in uw oplossing van het Beheer van de Correspondentie kunt gebruiken:

* Twee getallen toevoegen: ${number1 + number 
* Twee tekenreeksen aaneenschakelen: ${str1} $ {str2}
* Twee getallen vergelijken: ${age &lt; 18}

U kunt meer informatie in de [ JSP EL specificatie ](https://download.oracle.com/otn-pub/jcp/jsp-2.1-fr-spec-oth-JSpec/jsp-2_1-fr-spec-el.pdf) vinden. De client-side expressiemanager biedt geen ondersteuning voor bepaalde variabelen en functies in de JSP EL-specificatie, met name:

* Indexen en kaartsleutels voor verzamelingen (met de notatie [] ) worden niet ondersteund in variabelenamen voor expressies die op de client worden geëvalueerd.
* Hieronder ziet u de parametertypen of retourneringstypen van functies die in expressies worden gebruikt:

   * java.lang.String
   * java.lang.Character
   * Char
   * java.lang.Boolean
   * Boolean
   * java.lang.Integer
   * Int
   * java.util.list
   * java.lang.Short
   * Kort
   * java.lang.Byte
   * byte
   * java.lang.Double
   * Dubbel
   * java.lang.Long
   * Lang
   * java.lang.Float
   * Float
   * java.util.Calendar
   * java.util.Date
   * java.util.List

### Externe functie {#remote-function}

Externe functies bieden de mogelijkheid om aangepaste logica in expressies te gebruiken. U kunt aangepaste logica schrijven voor gebruik in expressie als een methode in Java en dezelfde functie kan worden gebruikt in expressies. Beschikbare externe functies worden weergegeven onder het tabblad &quot;Externe functies&quot; aan de linkerkant van de Expressieeditor.

![ remotefunction ](assets/remotefunction.png)

#### Aangepaste externe functies toevoegen {#adding-custom-remote-functions}

U kunt een aangepaste bundel maken om uw eigen externe functies te exporteren voor gebruik in expressies. Als u een aangepaste bundel wilt maken om uw eigen externe functies te exporteren, voert u de volgende taken uit. Het toont aan hoe te om een douanefunctie te schrijven die zijn inputkoord met hoofdletters maakt.

1. Bepaal een interface voor de dienst OSGi die methodes bevat die voor gebruik door de Manager van de Uitdrukking worden uitgevoerd.
1. Declareer methodes op interface A en annoteer hen met de @ServiceMethod annotation (com.adobe.exm.expeval.ServiceMethod). Expression Manager negeert methoden zonder annotatie. De annotatie ServiceMethod heeft de volgende facultatieve attributen die ook kunnen worden gespecificeerd:

   1. **Toegelaten**: Bepaalt als deze methode wordt toegelaten. Expressiebeheer negeert uitgeschakelde methoden.
   1. **familyId**: Specificeert de familie van de methode (groep). Als dit leeg is, gaat Expression Manager ervan uit dat de methode tot de standaardfamilie behoort. Er is geen register van families (behalve het standaardregister) waaruit functies worden gekozen. De Manager van de uitdrukking leidt dynamisch tot de registratie door een vereniging van alle familie IDs te nemen die door alle functies wordt gespecificeerd die door de diverse bundels worden uitgevoerd. Zorg ervoor dat de id die ze hier opgeven redelijk leesbaar is, aangezien deze ook wordt weergegeven in de gebruikersinterface voor het schrijven van expressies.
   1. **displayName**: Een mens-leesbare naam voor de functie. Deze naam wordt gebruikt voor weergavedoeleinden in de ontwerpgebruikersinterface. Als dit leeg is, wordt in Expression Manager een standaardnaam samengesteld met het voorvoegsel en de lokale naam van de functie.
   1. **Beschrijving**: Een uitgebreide beschrijving voor de functie. Deze beschrijving wordt gebruikt voor weergavedoeleinden in de ontwerpgebruikersinterface. Als dit leeg is, wordt in Expression Manager een standaardbeschrijving gemaakt met het voorvoegsel en de lokale naam van de functie.

   ```java
   package mergeandfuse.com;
   import com.adobe.exm.expeval.ServiceMethod;
   
   public interface RemoteFunction {
    @ServiceMethod(enabled=true,displayName="Returns_all_caps",description="Function to convert to all CAPS", familyId="remote")
    public String toAllCaps(String name);
   
   }
   ```

   De parameters van de methoden kunnen optioneel ook worden geannoteerd met de annotatie @ServiceMethodParameter (com.adobe.exm.expeval.ServiceMethodParameter). Deze annotatie wordt alleen gebruikt voor het opgeven van namen en beschrijvingen van methodeparameters voor gebruik in de ontwerpgebruikersinterface. Zorg ervoor dat de parameters en de terugkeer-waarden van de interfacemethodes tot één van de volgende types behoren:

   * java.lang.String
   * java.lang.Character
   * Char
   * java.lang.Boolean
   * Boolean
   * java.lang.Integer
   * Int
   * java.lang.Short
   * Kort
   * java.lang.Byte
   * byte
   * java.lang.Double
   * Dubbel
   * java.lang.Long
   * Lang
   * java.lang.Float
   * Float
   * java.util.Calendar
   * java.util.Date
   * java.util.List

1. Bepaal de implementatie van de interface, vorm het als dienst OSGI en bepaal de volgende de diensteigenschappen:

```jsp
@org.apache.felix.scr.annotations.Properties({
  @org.apache.felix.scr.annotations.Property(name = "connectors.jsoninvoker", boolValue = true),
  @org.apache.felix.scr.annotations.Property(name = "connectors.jsoninvoker.alias", value = "<service_id>"),
  @org.apache.felix.scr.annotations.Property(name = "exm.service", boolValue = true)})
```

Het item exm.service=true instrueert Expression Manager dat de service externe functies bevat die geschikt zijn voor gebruik in expressies. De waarde &lt;service_id> moet een geldige Java-id zijn (alfanumeriek,$, _ zonder andere speciale tekens). Deze waarde, voorafgegaan door het trefwoord REMOTE_, vormt het voorvoegsel dat in expressies wordt gebruikt. Bijvoorbeeld, kan een interface met een geannoteerde methodebar () en de dienst identiteitskaart foo in de de diensteigenschappen, binnen uitdrukkingen worden van verwijzingen voorzien gebruikend REMOTE_foo:bar ().

```java
package mergeandfuse.com;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

@Component(metatype = true, immediate = true, label = "RemoteFunctionImpl")
@Service(value = RemoteFunction.class)
@org.apache.felix.scr.annotations.Properties({
  @org.apache.felix.scr.annotations.Property(name = "connectors.jsoninvoker", boolValue = true),
  @org.apache.felix.scr.annotations.Property(name = "connectors.jsoninvoker.alias", value = "test1"),
  @org.apache.felix.scr.annotations.Property(name = "exm.service", boolValue = true)})
public class RemoteFuntionImpl implements RemoteFunction {

 @Override
 public String toAllCaps(String name) {
  System.out.println("######Got######"+name);
  
  return name.toUpperCase();
 }
 
}
```

Hieronder vindt u voorbeeldarchieven die moeten worden gebruikt:

* **GoodFunctions.jar.zip** is het jar dossier met bundel die een steekproef verre functiedefinitie bevat. Download het bestand GoodFunctions.jar.zip en decomprimeer het bestand om het jar-bestand op te halen.
* **GoodFunctions.zip** is het pakket van broncode voor het bepalen van een douane verre functie en het creëren van een bundel voor het.

GoodFunctions.jar.zip

[Bestand ophalen](assets/goodfunctions.jar.zip)

GoodFunctions.zip

[Bestand ophalen](assets/goodfunctions.zip)
