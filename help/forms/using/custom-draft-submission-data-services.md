---
title: Services voor ontwerp- en verzendgegevens aanpassen
seo-title: Services voor ontwerp- en verzendgegevens aanpassen
description: AEM Forms slaat standaard concept- en verzonden adaptieve formulieren op in een standaardknooppunt in de instantie Publiceren. U kunt echter de services voor concepten en verzendgegevens van AEM Forms configureren om de opslag van concepten en verzonden adaptieve formulieren aan te passen.
seo-description: AEM Forms slaat standaard concept- en verzonden adaptieve formulieren op in een standaardknooppunt in de instantie Publiceren. U kunt echter de services voor concepten en verzendgegevens van AEM Forms configureren om de opslag van concepten en verzonden adaptieve formulieren aan te passen.
uuid: c3ec1708-3b11-4142-93f0-1cffb6643f34
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 602fd6a9-9a65-411c-8475-a4082a3fdee0
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---


# Services {#customizing-draft-and-submission-data-services} voor conceptgegevens en verzendgegevens aanpassen

## Overzicht {#overview}

Met AEM Forms kunnen gebruikers een adaptief formulier opslaan als concept. De conceptfunctionaliteit biedt gebruikers de mogelijkheid om een formulier in uitvoering te onderhouden. Vervolgens kan een gebruiker het formulier op elk gewenst moment vanaf elk apparaat invullen en verzenden.

Standaard slaat AEM Forms de gebruikersgegevens die aan het concept en de verzending zijn gekoppeld op de instantie Publiceren op in het knooppunt `/content/forms/fp`.

AEM Forms Portal-componenten bieden echter gegevensservices waarmee u de implementatie van het opslaan van gebruikersgegevens voor concepten en verzendingen kunt aanpassen. U kunt de gegevens bijvoorbeeld opslaan in een gegevensopslagruimte die momenteel in uw organisatie is geïmplementeerd.

Als u de opslag van gebruikersgegevens wilt aanpassen, moet u de services [Conceptgegevens](/help/forms/using/custom-draft-submission-data-services.md#p-draft-data-service-p) en [Verzendgegevens](/help/forms/using/custom-draft-submission-data-services.md#p-submission-data-service-p) implementeren.

## Vereisten {#prerequisites}

* [Forms-poortcomponenten inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* Een [pagina voor een formulierportal maken](/help/forms/using/creating-form-portal-page.md)
* [Aangepaste formulieren inschakelen voor formulierportal](/help/forms/using/draft-submission-component.md)
* Meer informatie over [implementatiedetails van aangepaste opslag](/help/forms/using/draft-submission-component.md#customizing-the-storage)

## Conceptgegevensservice {#draft-data-service}

Als u de opslag van gebruikersconceptgegevens wilt aanpassen, moet u een implementatie voor alle methoden van de `DraftAFDataService`-interface bieden.

Een beschrijving van de methodes en hun argumenten worden verstrekt in het volgende codevoorbeeld van de interface:

```java
public interface DraftAFDataService {

 /**
  * Deletes the user data stored against the ID passed as the argument
  *
  * @param draftDataID
  * @return status for the just occurred delete draft UserData operation
  * @throws FormsPortalException
  */
 public Boolean deleteAFDraftUserData (String draftDataID) throws FormsPortalException;

 /**
  * Saves user data provided in the argument map
  *
  * @param draftUserDataMap contains Form Data (key - "guideState"), Adaptive Form Name (Key - "guideName"), and Draft DataID (Key - "userDataID") in case of update
  * @return userData ID would be returned which needs to be saved in metadata node
  * @throws FormsPortalException
  */
 public String saveAFUserData (Map<String, Object> draftUserDataMap) throws FormsPortalException;

 /**
  * Gets the user data stored against the ID passed as the argument
  *
  * @param Draft DataID
  * @return guideState (which would then be populated in adaptive form to reload the draft) which is stored against draftDataID
  * @throws FormsPortalException
  */
 public byte[] getAFDraftUserData(String draftDataID) throws FormsPortalException;

 /**
  * Saves the attachments for current adaptive form instance
  *
  * @param attachmentsBytes would expect byte array of the attachment to be saved
  * @return id for the attachment just saved (so that it could be retrieved later)
  * @throws FormsPortalException
  */
 public String saveAttachments(byte[] attachmentBytes) throws FormsPortalException;
}
```

## Verzendgegevensservice {#submission-data-service}

Om de opslag van de gegevens van de gebruikersvoorlegging aan te passen, moet u implementatie voor alle methodes van de `SubmittedAFDataService` interface verstrekken.

Een beschrijving van de methodes en hun argumenten worden verstrekt in het volgende codevoorbeeld van de interface:

```java
public interface SubmittedAFDataService {

 /**
  * Submits the user data passed in argument map
  *
  * @param submittedAFUserdataMap contains Form Data (key - "guideState"), Adaptive Form Name (Key - "guideName"), and Draft DataID (Key - "userDataID")
  * @return userData ID is returned that needs to be saved in the metadata node
  * @throws FormsPortalException
  */
 public String submitAFUserData (Map<String, Object> submittedAFUserdataMap) throws FormsPortalException;

 /**
  * Gets the user data stored against the ID passed as argument
  *
  * @param submitDataID
  * @return guideState which would be used to open DOR
  * @throws FormsPortalException
  */
 public byte[] getSubmittedAFUSerData(String submitDataID) throws FormsPortalException;

 /**
  * Deletes user data stored against the ID passed as argument
  *
  * @param Submit DataID
  * @return status of the delete operation on Submitted User data
  * @throws FormsPortalException
  */

 public Boolean deleteSubmittedAFUserData(String submitDataID) throws FormsPortalException;

 /**
  * Submits the attachment bytes passed as argument
  *
  * @param attachmentsBytes would expect byte array of the attachment to be saved
  * @return id for the attachment just saved (so that it could be retrieved later)
  * @throws FormsPortalException
  */
 public String submitAttachments(Object attachmentBytes) throws FormsPortalException;

}
```

