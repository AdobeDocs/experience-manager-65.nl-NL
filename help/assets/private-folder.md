---
title: Persoonlijke mappen om elementen te delen
description: Leer hoe te om een privé omslag in  [!DNL Adobe Experience Manager Assets] te creëren en het met andere gebruikers te delen en verschillende voorrechten aan hen toe te wijzen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ce43c49f8f7d4509e414554b8f4eba368ff66e95
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 0%

---


# Persoonlijke map in [!DNL Adobe Experience Manager Assets] {#private-folder}

U kunt een privé omslag in [!DNL Adobe Experience Manager Assets] gebruikersinterface tot stand brengen die exclusief aan u beschikbaar is. U kunt deze persoonlijke map delen met andere gebruikers en deze gebruikers verschillende rechten geven. Op basis van het machtigingsniveau dat u toewijst, kunnen gebruikers verschillende taken op de map uitvoeren, bijvoorbeeld de middelen in de map weergeven of de elementen bewerken.

>[!NOTE]
>
>De privé omslag heeft minstens één lid met de rol van de Eigenaar.

## Maken en delen van privémappen {#create-share-private-folder}

Persoonlijke map maken en delen:

1. Klik in de [!DNL Assets]-console op **[!UICONTROL Create]** op de werkbalk en kies **[!UICONTROL Folder]** in het menu.

   ![Map met elementen maken](assets/Create-folder.png)

1. Voer in het dialoogvenster **[!UICONTROL Create Folder]** een titel en naam (optioneel) voor de map in en selecteer de optie **[!UICONTROL Private]**.

1. Klik op **[!UICONTROL Create]**. Er wordt een persoonlijke map gemaakt.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Als u de map wilt delen met andere gebruikers en de gebruikers rechten wilt toewijzen, selecteert u de map en klikt u op **[!UICONTROL Properties]** op de werkbalk.

   ![info, optie](assets/do-not-localize/info-circle-icon.png)

   >[!NOTE]
   >
   >De map is pas zichtbaar voor andere gebruikers als u deze deelt.

1. Selecteer op de pagina **[!UICONTROL Folder Properties]** een gebruiker in de lijst **[!UICONTROL Add User]**, wijs een rol toe aan de gebruiker in uw persoonlijke map en klik op **[!UICONTROL Add]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >U kunt verschillende rollen, zoals `Editor`, `Owner`, of `Viewer` aan de gebruiker toewijzen met wie u de omslag deelt. Als u een `Owner` rol aan de gebruiker toewijst, heeft de gebruiker `Editor` voorrechten op de omslag. Bovendien kan de gebruiker de map met anderen delen. Als u een rol `Editor` toewijst, kan de gebruiker de activa in uw privé omslag uitgeven. Als u een viewerrol toewijst, kan de gebruiker alleen de elementen in uw persoonlijke map bekijken.

   >[!NOTE]
   >
   >De privé omslag heeft minstens één lid met `Owner` rol. Daarom kan de beheerder niet alle eigenaarleden uit een privé omslag verwijderen. Nochtans, om de bestaande eigenaars (en beheerder zelf) uit de privé omslag te verwijderen moet de beheerder een andere gebruiker als eigenaar toevoegen.

1. Klik op **[!UICONTROL Save]**. Afhankelijk van de rol die u toewijst, wordt aan de gebruiker een reeks rechten toegewezen aan uw persoonlijke map wanneer de gebruiker zich aanmeldt bij [!DNL Assets].
1. Klik **[!UICONTROL Ok]** om het bevestigingsbericht te sluiten.
1. De gebruiker met wie u de map deelt, ontvangt een melding voor delen. Meld u aan bij [!DNL Assets] met de referenties van de gebruiker om het bericht weer te geven.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Klik op [!UICONTROL Notifications] om een lijst met meldingen te openen.

   ![Lijst van kennisgevingen](assets/Assets-Notification.png)

1. Klik op de vermelding voor de privémap die door de beheerder wordt gedeeld om de map te openen.

>[!NOTE]
>
>Om een privé omslag tot stand te brengen, vereist u Gelezen en wijzigt [toegangsbeheertoestemmingen](/help/sites-administering/security.md#permissions-in-aem) op de ouderomslag waaronder u een privé omslag wilt tot stand brengen. Als u geen beheerder bent, worden deze toestemmingen niet toegelaten voor u door gebrek op `/content/dam`. In dit geval moet u eerst deze machtigingen voor uw gebruikers-id/groep verkrijgen voordat u probeert persoonlijke mappen te maken.

## Verwijderen van privémap {#delete-private-folder}

U kunt een map verwijderen door de map te selecteren en de optie [!UICONTROL Delete] in het bovenste menu te selecteren of door de Backspace-toets op het toetsenbord te gebruiken.

![Optie verwijderen in bovenste menu](assets/delete-option.png)

>[!CAUTION]
>
>Als u een privémap uit CRXDE Lite verwijdert, blijven er overbodige gebruikersgroepen over in de opslagplaats.

>[!NOTE]
>
>Als u een map verwijdert met de bovenstaande methode uit de gebruikersinterface, worden ook de bijbehorende gebruikersgroepen verwijderd.
>
>De bestaande redundante, ongebruikte en automatisch gegenereerde gebruikersgroepen kunnen echter uit de opslagplaats worden verwijderd met de methode `clean` in JMX in de auteurinstantie (`http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets`).
