---
title: Persoonlijke mappen om elementen te delen
description: Leer hoe u een persoonlijke map maakt in het dialoogvenster [!DNL Adobe Experience Manager Assets] en deelt het met andere gebruikers en wijst verschillende voorrechten aan hen toe.
contentOwner: AG
role: User
feature: Collaboration
exl-id: c1aece06-7c1c-43a0-bea0-6f11ecda7e68
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 1%

---

# Persoonlijke map in [!DNL Adobe Experience Manager Assets] {#private-folder}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/private-folder.html?lang=en) |
| AEM 6,5 | Dit artikel |

U kunt een privémap maken in het dialoogvenster [!DNL Adobe Experience Manager Assets] -gebruikersinterface die exclusief voor u beschikbaar is. U kunt deze persoonlijke map delen met andere gebruikers en deze gebruikers verschillende rechten geven. Op basis van het machtigingsniveau dat u toewijst, kunnen gebruikers verschillende taken op de map uitvoeren, bijvoorbeeld de elementen in de map weergeven of de elementen bewerken.

>[!NOTE]
>
>De privé omslag heeft minstens één lid met de rol van de Eigenaar.

## Maken en delen van persoonlijke mappen {#create-share-private-folder}

Persoonlijke map maken en delen:

1. In de [!DNL Assets] console, klik **[!UICONTROL Create]** op de werkbalk en kies vervolgens **[!UICONTROL Folder]** in het menu.

   ![Map met elementen maken](assets/Create-folder.png)

1. In de **[!UICONTROL Create Folder]** voert u een titel en naam (optioneel) voor de map in en selecteert u **[!UICONTROL Private]** -optie.

1. Klik op **[!UICONTROL Create]**. Er wordt een persoonlijke map gemaakt.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Als u de map wilt delen met andere gebruikers en de bijbehorende rechten wilt toewijzen, selecteert u de map en klikt u op **[!UICONTROL Properties]** op de werkbalk.

   ![info, optie](assets/do-not-localize/info-circle-icon.png)

   >[!NOTE]
   >
   >De map is pas zichtbaar voor andere gebruikers als u deze deelt.

1. In de **[!UICONTROL Folder Properties]** pagina, selecteert u een gebruiker in het **[!UICONTROL Add User]** een rol toewijzen aan de gebruiker in uw persoonlijke map en klikken **[!UICONTROL Add]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >U kunt verschillende rollen toewijzen, zoals `Editor`, `Owner`, of `Viewer` aan de gebruiker met wie u de omslag deelt. Als u een `Owner` rol voor de gebruiker, heeft de gebruiker `Editor` rechten voor de map. Bovendien kan de gebruiker de map met anderen delen. Als u een `Editor` als rol, kan de gebruiker de middelen in uw privé omslag uitgeven. Als u een viewerrol toewijst, kan de gebruiker alleen de elementen in uw persoonlijke map bekijken.

   >[!NOTE]
   >
   >De privé omslag heeft minstens één lid met `Owner` rol. Daarom kan de beheerder niet alle eigenaarleden uit een privé omslag verwijderen. Nochtans, om de bestaande eigenaars (en beheerder zelf) uit de privé omslag te verwijderen moet de beheerder een andere gebruiker als eigenaar toevoegen.

1. Klik op **[!UICONTROL Save]**. Afhankelijk van de rol die u toewijst, wordt aan de gebruiker een reeks rechten toegewezen aan uw persoonlijke map wanneer de gebruiker zich aanmeldt bij [!DNL Assets].
1. Klikken **[!UICONTROL Ok]** om het bevestigingsbericht te sluiten.
1. De gebruiker met wie u de map deelt, ontvangt een melding voor delen. Aanmelden bij [!DNL Assets] met de referenties van de gebruiker om het bericht weer te geven.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Klikken [!UICONTROL Notifications] om een lijst met kennisgevingen te openen.

   ![Lijst van kennisgevingen](assets/Assets-Notification.png)

1. Klik op de vermelding voor de privémap die door de beheerder wordt gedeeld om de map te openen.

>[!NOTE]
>
>Als u een persoonlijke map wilt maken, hebt u Lezen en Wijzigen nodig [toegangsbeheermachtigingen](/help/sites-administering/security.md#permissions-in-aem) in de bovenliggende map waarin u een privémap wilt maken. Als u geen beheerder bent, worden deze machtigingen standaard niet voor u ingeschakeld `/content/dam`. In dit geval moet u eerst deze machtigingen voor uw gebruikers-id/groep verkrijgen voordat u probeert persoonlijke mappen te maken.

## Verwijderen van persoonlijke map {#delete-private-folder}

U kunt een map verwijderen door de map te selecteren en [!UICONTROL Delete] in het bovenste menu of met de Backspace-toets op het toetsenbord.

![Optie verwijderen in bovenste menu](assets/delete-option.png)

>[!CAUTION]
>
>Als u een privémap uit CRXDE Lite verwijdert, blijven er overbodige gebruikersgroepen over in de opslagplaats.

>[!NOTE]
>
>Als u een map verwijdert met de bovenstaande methode uit de gebruikersinterface, worden ook de bijbehorende gebruikersgroepen verwijderd.
>
>De bestaande overbodige, ongebruikte en automatisch gegenereerde gebruikersgroepen kunnen echter uit de opslagplaats worden verwijderd met `clean` methode in JMX in de auteurinstantie (`http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets`).
