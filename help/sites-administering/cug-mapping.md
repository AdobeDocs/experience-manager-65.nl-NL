---
title: Toewijzing van aangepaste gebruikersgroepen in AEM 6.5
description: Leer hoe de Toewijzing van de Gebruikersgroep van de Douane in Adobe Experience Manager werkt.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 661602eb-a117-454d-93d3-a079584f7a5d
feature: Security
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Toewijzing van aangepaste gebruikersgroepen in AEM 6.5 {#custom-user-group-mapping-in-aem}

## Vergelijking van JCR-inhoud met betrekking tot CUG (aangepaste gebruikersgroep) {#comparison-of-jcr-content-related-to-cug}

<table>
 <tbody>
  <tr>
   <td><strong>Oudere AEM</strong></td>
   <td><strong>AEM 6,5</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td><p>Eigenschap: cq:cugEnabled</p> <p>Type knooppunt declareren: N.v.t., resteigenschap</p> </td>
   <td><p>Autorisatie:</p> <p>Node: rep:cugPolicy of node type rep:CugPolicy</p> <p>Type knooppunt declareren: rep:CugMixin</p> <p> </p> <p> </p> <p> </p> Verificatie:</p> <p>Mixintype: graniet:AuthenticationRequired</p> </td>
   <td><p>Om leestoegang te beperken, wordt een specifiek beleid van de CUG toegepast op de doelknoop.</p> <p>NOTA: Het beleid kan slechts op de gevormde gesteunde wegen worden toegepast.</p> <p>Nodes met name rep:cugPolicy en type rep:CugPolicy zijn beschermd en kunnen niet worden geschreven gebruikend regelmatige vraag JCR API; gebruik in plaats daarvan het beheer van de toegangscontrole JCR.</p> <p>Zie <a href="https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html">deze pagina</a> voor meer informatie.</p> <p>Om authentificatievereiste op een knoop af te dwingen, is het voldoende om mixintype granite toe te voegen:AuthenticationRequired.</p> <p>NOTA: Slechts gerespecteerd onder de gevormde gesteunde wegen.</p> </td>
  </tr>
  <tr>
   <td><p>Eigenschap: cq:cugPrincipals</p> <p>Type knooppunt declareren: NA, resteigenschap</p> </td>
   <td><p>Eigenschap: rep:principalNames</p> <p>Type knooppunt declareren: rep:CugPolicy</p> </td>
   <td><p>De eigenschap die de namen bevat van de hoofden die de inhoud onder de beperkte CUG mogen lezen, is beveiligd en kan niet worden geschreven met behulp van reguliere JCR API-aanroepen. Gebruik in plaats daarvan het JCR-toegangsbeheer.</p> <p>Zie <a href="https://jackrabbit.apache.org/api/2.12/org/apache/jackrabbit/api/security/authorization/PrincipalSetPolicy.html">deze pagina</a> voor meer informatie over de uitvoering.</p> </td>
  </tr>
  <tr>
   <td><p>Eigenschap: cq:cugLoginPage</p> <p>Type knooppunt declareren: NA, resteigenschap</p> </td>
   <td><p>Eigenschap: graniet:loginPath (optioneel)</p> <p>Notititietype declareren: graniet:AuthenticationRequired</p> </td>
   <td><p>Een JCR-knooppunt waarvoor het mixinetype granite:AuthenticationRequired is gedefinieerd, kan optioneel een alternatief aanmeldingspad definiëren.</p> <p>NOTA: Slechts gerespecteerd onder de gevormde gesteunde wegen.</p> </td>
  </tr>
  <tr>
   <td><p>Eigenschap: cq:cugReal</p> <p>Type knooppunt declareren: NA, resteigenschap</p> </td>
   <td>NA</td>
   <td>Niet meer ondersteund met de nieuwe implementatie.</td>
  </tr>
 </tbody>
</table>

## Vergelijking van OSGi Services {#comparison-of-osgi-services}

**Oudere AEM**

Label: ondersteuning voor gesloten gebruikersgroep (CUG) bij Adobe Granite

Naam: com.day.cq.auth.impl.CugSupportImpl

**AEM 6,5**

* Label: Apache Jackrabbit Oak CUG Configuration

  Naam: org.apache.jackrabbit.oak.spi.security.authentication.cug.impl.CugConfiguration

  ConfigurationPolicy = REQUIRED

* Label: Apache Jackrabbit Oak CUG Exclusive List

  Naam: org.apache.jackrabbit.oak.spi.security.authentication.cug.impl.CugExcludeImpl

  ConfigurationPolicy = REQUIRED

* Naam: com.adobe.granite.auth.requirements.impl.RequirementService
* Label: Adobe graniet-verificatie vereist en Aanmeldingspad-handler

  Naam: com.adobe.granite.auth.requirements.impl.DefaultRequirementHandler

  ConfigurationPolicy = REQUIRED

**Opmerkingen**

* Configuratie van de CUG-autorisatie en inschakelen/uitschakelen van de evaluatie.
Dienst om uitsluitingslijsten van principes te configureren die niet door de CUG-autorisatie moeten worden beïnvloed.

  >[!NOTE]
  > 
  >Als de `CugExcludeImpl` is niet geconfigureerd, `CugConfiguration` wordt de standaardwaarde hersteld.

  Het is mogelijk om een aangepaste CugExclude-implementatie aan te sluiten als er speciale behoeften zijn.

* De component OSGi die LoginPathProvider uitvoert die een passende login weg aan LoginSelectorHandler blootstelt. Het heeft een verplichte verwijzing naar een RequirementHandler die wordt gebruikt om de waarnemer te registreren die aan veranderde auteisen luistert die in de inhoud door middel van graniet worden opgeslagen:AuthenticationRequired mixin type.
* De component OSGi die RequirementHandler uitvoert die SlingAuthenticator over veranderingen in authrequirements op de hoogte brengt.

  Aangezien het configuratiebeleid voor deze component VEREIST is, wordt het slechts geactiveerd als een reeks gesteunde wegen wordt gespecificeerd.

  Het toelaten van de dienst lanceert RequirementService.

<!-- nested tables not supported - text above is the table>
<table>
 <tbody>
  <tr>
   <td><strong>Older AEM Versions</strong></td>
   <td><strong>AEM 6.5</strong></td>
   <td><strong>Comments</strong></td>
  </tr>
  <tr>
   <td><p>Label: Adobe Granite Closed User Group (CUG) Support</p> <p>Name: com.day.cq.auth.impl.CugSupportImpl</p> </td>
   <td><p>Label: Apache Jackrabbit Oak CUG Configuration</p> <p>Name: org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration</p> <p>ConfigurationPolicy = REQUIRED</p> </td>
    <td><p>Label: Apache Jackrabbit Oak CUG Exclude List</p> <p>Name: org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl</p> <p>ConfigurationPolicy = REQUIRED</p> <p> </p> <p> </p> <p> </p> <p> </p> </td>
      </tr>
      <tr>
       <td>Name: com.adobe.granite.auth.requirement.impl.RequirementService</td>
      </tr>
      <tr>
       <td><p>Label: Adobe Granite Authentication Requirement and Login Path Handler</p> <p>Name: com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler</p> <p>ConfigurationPolicy = REQUIRED</p> </td>
      </tr>
     </tbody>
    </table> </td>
   <td>
     <tbody>
      <tr>
       <td>Configuration of the CUG authorization and enable/disable the evaluation.</td>
      </tr>
      <tr>
       <td><p>Service to configure exclusion list of principals which should not be affected by the CUG authorization.</p> <p>NOTE: If the CugExcludeImpl is not configured, the CugConfiguration will fall back to the default.</p> <p>It is possible to plug a custom CugExclude implementation if there are special needs.</p> </td>
      </tr>
      <tr>
       <td>OSGi component implementing LoginPathProvider that exposes a matching login path to the LoginSelectorHandler. It has a mandatory reference to a RequirementHandler which is used to register the observer that listens to changed auth requirements stored in the content by the means of the granite:AuthenticationRequired mixin type. </td>
      </tr>
      <tr>
       <td><p>OSGi component implementing RequirementHandler that notifies the SlingAuthenticator about changes to authrequirements.</p> <p>As configuration policy for this component is REQUIRE it will only be activated if a set of supported paths is specified.</p> <p>Enabling the service will launch the RequirementService.</p> </td>
      </tr>
     </tbody>
     </td>
  </tr>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->
