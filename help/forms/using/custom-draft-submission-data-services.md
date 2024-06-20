---
title: Services voor ontwerp- en verzendgegevens aanpassen
description: AEM Forms slaat standaard concept- en verzonden adaptieve formulieren op in een standaardknooppunt van het Publish-exemplaar. U kunt echter de services voor concepten en verzendgegevens van AEM Forms configureren om de opslag van concepten en verzonden adaptieve formulieren aan te passen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
exl-id: ed10ef8c-7b9c-43cf-bea8-7cf9742a8cac
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Services voor ontwerp- en verzendgegevens aanpassen {#customizing-draft-and-submission-data-services}

## Overzicht {#overview}

Met AEM Forms kunnen gebruikers een adaptief formulier opslaan als concept. De conceptfunctionaliteit biedt gebruikers de mogelijkheid om een formulier in uitvoering te onderhouden. Vervolgens kan een gebruiker het formulier op elk gewenst moment vanaf elk apparaat invullen en verzenden.

AEM Forms slaat standaard gebruikersgegevens op die zijn gekoppeld aan het concept en de verzending op het Publish-exemplaar in de `/content/forms/fp` knooppunt.

AEM Forms Portal-componenten bieden echter gegevensservices waarmee u de implementatie van het opslaan van gebruikersgegevens voor concepten en verzendingen kunt aanpassen. U kunt de gegevens bijvoorbeeld opslaan in een gegevensopslagruimte die momenteel in uw organisatie is geïmplementeerd.

Als u de opslag van gebruikersgegevens wilt aanpassen, moet u de [Conceptgegevens](/help/forms/using/custom-draft-submission-data-services.md#p-draft-data-service-p) en [Indieningsgegevens](/help/forms/using/custom-draft-submission-data-services.md#p-submission-data-service-p) diensten.

## Vereisten {#prerequisites}

* Inschakelen [Forms Portal-componenten](/help/forms/using/enabling-forms-portal-components.md)
* Een [Forms Portal-pagina](/help/forms/using/creating-form-portal-page.md)
* Inschakelen [adaptieve formulieren voor Forms Portal](/help/forms/using/draft-submission-component.md)
* Meer informatie [implementatiedetails van aangepaste opslag](/help/forms/using/draft-submission-component.md#customizing-the-storage)

## Conceptgegevensservice {#draft-data-service}

Als u de opslag van gebruikersconceptgegevens wilt aanpassen, moet u een implementatie opgeven voor alle methoden van het dialoogvenster `DraftAFDataService` interface.

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
  * @param draftUserDataMap contains Form Data (key - "guideState"), Adaptive Form Name (Key - "guideName"), and Draft DataID (Key - "userDataID") if there is update
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

Als u de opslag van gegevens over het verzenden van gebruikers wilt aanpassen, moet u een implementatie voor alle methoden van het dialoogvenster `SubmittedAFDataService` interface.

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
