---
title: Services voor ontwerp- en verzendgegevens aanpassen
description: AEM Forms slaat standaard concept- en verzonden adaptieve formulieren op in een standaardknooppunt van het Publish-exemplaar. U kunt echter de services voor concepten en verzendgegevens van AEM Forms configureren om de opslag van concepten en verzonden adaptieve formulieren aan te passen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
exl-id: ed10ef8c-7b9c-43cf-bea8-7cf9742a8cac
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
source-git-commit: 8a77756e8ba771c8de9950c2323bef8f23cc59b4
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Services voor ontwerp- en verzendgegevens aanpassen {#customizing-draft-and-submission-data-services}

## Overzicht {#overview}

Met AEM Forms kunnen gebruikers een adaptief formulier opslaan als concept. De conceptfunctionaliteit biedt gebruikers de mogelijkheid om een formulier in uitvoering te onderhouden. Vervolgens kan een gebruiker het formulier op elk gewenst moment vanaf elk apparaat invullen en verzenden.

AEM Forms slaat standaard gebruikersgegevens op die zijn gekoppeld aan het concept en verzending op de Publish-instantie in het knooppunt `/content/forms/fp` .

AEM Forms Portal-componenten bieden echter gegevensservices waarmee u de implementatie van het opslaan van gebruikersgegevens voor concepten en verzendingen kunt aanpassen. U kunt de gegevens bijvoorbeeld opslaan in een gegevensopslagruimte die momenteel in uw organisatie is geïmplementeerd.

Om de opslag van gebruikersgegevens aan te passen, moet u de [ Gegevens van het Ontwerp ](/help/forms/using/custom-draft-submission-data-services.md#p-draft-data-service-p) uitvoeren en [ de diensten van de Gegevens van de Verzending ](/help/forms/using/custom-draft-submission-data-services.md#p-submission-data-service-p).

## Vereisten {#prerequisites}

* Laat [ Forms Portal componenten ](/help/forms/using/enabling-forms-portal-components.md) toe
* Creeer a [ de Portaalpagina van Forms ](/help/forms/using/creating-form-portal-page.md)
* Laat [ adaptieve vormen voor Forms Portal ](/help/forms/using/draft-submission-component.md) toe
* Leer [ implementatiedetails van douaneopslag ](/help/forms/using/draft-submission-component.md#customizing-the-storage)

## Conceptgegevensservice {#draft-data-service}

Als u de opslag van gebruikersconceptgegevens wilt aanpassen, moet u een implementatie opgeven voor alle methoden van de interface `DraftAFDataService` .

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

Als u de opslag van verzonden gegevens door gebruikers wilt aanpassen, moet u een implementatie voor alle methoden van de interface `SubmittedAFDataService` opgeven.

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
