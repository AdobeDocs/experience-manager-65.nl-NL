---
title: Aangepaste opslag voor concepten en verzendingscomponenten
seo-title: Custom storage for drafts and submissions component
description: Zie hoe u de opslag van gebruikersgegevens voor concepten en verzendingen kunt aanpassen.
seo-description: See how to customize the storage of user data for drafts and submissions.
uuid: ac2e80ee-a9c7-44e6-801e-fe5a840cb7f8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 154255e7-468a-42e6-a33d-eee691cf854d
feature: Forms Portal
exl-id: b1300eeb-2653-4bb5-b2fd-88048c9c43b9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Aangepaste opslag voor concepten en verzendingscomponenten {#custom-storage-for-drafts-and-submissions-component}

## Overzicht {#overview}

Met AEM Forms kunt u een formulier opslaan als concept. Met de conceptfunctionaliteit kunt u een formulier bijhouden dat u later vanaf elk apparaat kunt invullen en verzenden.

Standaard slaat AEM Forms de gebruikersgegevens die aan het concept en de verzending van een formulier zijn gekoppeld op in het dialoogvenster `/content/forms/fp` op de instantie Publish. Daarnaast bieden de AEM Forms-portalcomponenten gegevensservices waarmee u de implementatie van het opslaan van gebruikersgegevens voor concepten en verzendingen kunt aanpassen. U kunt bijvoorbeeld gebruikersgegevens opslaan in een gegevensopslag.

## Vereisten  {#prerequisites}

* Inschakelen [componenten van Forms Portal](/help/forms/using/enabling-forms-portal-components.md)
* Een [pagina Formulierportal](/help/forms/using/creating-form-portal-page.md)
* Inschakelen [adaptieve formulieren voor formulierportal](/help/forms/using/draft-submission-component.md)
* Meer informatie [implementatiedetails van aangepaste opslag](/help/forms/using/draft-submission-component.md#customizing-the-storage)

## Conceptgegevensservice {#draft-data-service}

Als u de opslag van gebruikersgegevens voor concepten wilt aanpassen, moet u alle methoden van het dialoogvenster `DraftDataService` interface. In de volgende voorbeeldcode worden de methoden en argumenten beschreven.

```java
/**
 * DraftDataService service will get/delete/save user data (attachments and form data) filled with a draft instance of Form
 */

public interface DraftDataService {

    /**
     * To save/modify user data for this userDataID, it will be null in case of creation
     * @param draftDataID: unique identifier associated with the form data
     * @param formName: name of the form whose draft is being saved
     * @param formData: user data associated with this draft
     * @return userdataID corresponding to which user data has been stored and which can be used later to retrieve this user data
     * @throws FormsPortalException
     */
    public String saveData (String draftDataID, String formName, String formData) throws FormsPortalException;

    /**
     * Returns the user data stored against the ID passed as the argument
     * @param userDataID: unique data id for user data associated with a draft
     * @return user data associated with this data ID
     * @throws FormsPortalException
     */

    public byte[] getData (String userDataID) throws FormsPortalException;

    /**
     * To delete data associated with this draft
     * @param userDataID: unique data id for data associated with a draft
     * @return status of delete operation on data associated with this draft
     * @throws FormsPortalException
     */

    public boolean deleteData (String userDataID) throws FormsPortalException;

    /**
     * Saves the attachment for current form instance
     * @param attachmentsBytes: byte array of the attachment to be saved
     * @return unique id (attachmentID) for the attachment just saved (so that it could be retrieved later)
     * @throws FormsPortalException
     */
    public String saveAttachment (byte[] attachmentBytes) throws FormsPortalException;

    /**
     * To delete an attachment
     * @param attachmentID: unique id for this attachment
     * @return status of delete operation performed on attachment corresponding to this attachment ID
     * @throws FormsPortalException
     */
    public boolean deleteAttachment (String attachmentID) throws FormsPortalException;

    /**
     * To get attachment bytes
     * @param attachmentID: unique id for this attachment
     * @return data corresponding to this attachmentID
     * @throws FormsPortalException
     */
    public byte[] getAttachment (String attachmentID) throws FormsPortalException;
}
```

>[!NOTE]
>
>De minimumwaarde voor de lengte van het veld concept-id is 26 tekens. Adobe raadt u aan de lengte van de concept-id in te stellen op 26 of meer tekens.

## Verzendgegevensservice {#submission-data-service}

Als u de opslag van gebruikersgegevens voor verzending wilt aanpassen, moet u alle methoden van het dialoogvenster `SubmitDataService` interface. In de volgende voorbeeldcode worden de methoden en argumenten beschreven.

```java
/**
 * SubmitDataService service will get/delete/submit user data (attachments and form data) filled with a submission of Form
 */
public interface SubmitDataService {

    /**
     * Submits the user data passed in argument map
     * @param userDataID, unique identifier associated with this user data
     * @param formName, name of the form whose draft is being submitted
     * @param formData, user data associated with this submission
     * @return userdataID, corresponding to which the user data has been stored and which can be used later to retrieve this data
     * @throws FormsPortalException
     */
    public String saveData (String userDataID, String formName, String formData) throws FormsPortalException;

    /**
     * Submits the user data provided as byte array
     * @param id
     * @param data
     * @return id corresponding to saved data
     * @throws FormsPortalException
     */
    public String saveData (String id, byte[] data) throws FormsPortalException;

    /** Submits the user data provided as byte array asynchronously for the user name provided in the options map
     * @param data data to be saved in bytes
     * @param options map containing options that affect this save
     * @return id of the saved data instance
     */
    public String saveDataAsynchronusly(byte[] data, Map<String, Object> options) throws FormsPortalException;

    /**
     * Gets the user data stored against the ID passed as argument
     * @param userDataID: unique id associated with this user data for this submission
     * @return user data associated with this submission
     * @throws FormsPortalException
     */
    public byte[] getData(String userDataID) throws FormsPortalException;

    /**
     * Deletes user data stored against the userDataID
     * @param userDataID: unique id associated with this user data for this submission
     * @return status of the delete operation on this submission
     * @throws FormsPortalException
     */

    public boolean deleteData(String userDataID) throws FormsPortalException;

    /**
     * Submits the attachment bytes passed as argument
     * @param attachmentsBytes: would expect byte array of the attachment for this submission
     * @return attachmentID for the attachment just saved (so that it could be retrieved later)
     * @throws FormsPortalException
     */
    public String saveAttachment(byte[] attachmentBytes) throws FormsPortalException;

    /** Submits the attachment bytes passed as argument asynchronously for the user id provided in options map.
     * @param attachmentBytes would expect byte array of the attachment for this submission
     * @param options map containing options that affect this save
     * @return attachmentID for the attachment just saved (so that it could be retrieved later)
     * @throws FormsPortalException
     */
    public String saveAttachmentAsynchronously(byte[] attachmentBytes, Map<String, Object> options) throws FormsPortalException;

    /**
     * To delete an attachment
     * @param attachmentID: Unique id for this attachment
     * @return status of delete operation performed on attachment corresponding to this attachment ID
     * @throws FormsPortalException
     */
    public boolean deleteAttachment (String attachmentID) throws FormsPortalException;

    /**
     * To get attachment bytes
     * @param attachmentID: unique id for this attachment
     * @return data corresponding to this attachmentID
     * @throws FormsPortalException
     */
    public byte[] getAttachment (String attachmentID) throws FormsPortalException;
}
```

Het portaal van Forms gebruikt universeel uniek herkenningsteken (UUID) concept om een unieke identiteitskaart voor elk ontwerp en voorgelegd vorm te produceren. U kunt ook een eigen unieke id genereren. U kunt de interface FPKeyGeneratorService uitvoeren, zijn methodes met voeten treden, en een douanelogica ontwikkelen om een douane unieke identiteitskaart voor elk ontwerp en voorgelegd vorm te produceren. Ook, plaats de dienstrang van de generatie van douaneID hoger dan 0. Het zorgt ervoor dat de douaneimplementatie in plaats van de standaardimplementatie wordt gebruikt.

```java
public interface FPKeyGeneratorService {
    /**
     * returns a unique id for draft and submission
     *
     * @param none
     * @return unique id in string format as per the implementation
     * @throws FormsPortalException
     */
    public String getUniqueId() throws FormsPortalException;
}
```

U kunt de onderstaande aantekening gebruiken om de servicerangschikking te verhogen voor aangepaste id&#39;s die met bovenstaande code zijn gegenereerd:

`@Properties(value = { @Property(name = "service.ranking", intValue = 15) } )`

Als u de bovenstaande annotatie wilt gebruiken, importeert u het volgende naar uw project:

```java
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
```
