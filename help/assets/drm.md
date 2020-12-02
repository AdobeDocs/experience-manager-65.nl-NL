---
title: Digital Rights Management van activa
description: Leer hoe u de verloopstatussen van elementen en informatie voor gelicentieerde middelen beheert in [!DNL Experience Manager].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 97d3edf155ddeabf3f39139c9079621c3627820b
workflow-type: tm+mt
source-wordcount: '1322'
ht-degree: 5%

---


# Digital Rights Management voor elementen {#digital-rights-management-in-assets}

Digitale middelen zijn vaak gekoppeld aan een licentie die de gebruiksvoorwaarden en -duur bepaalt. Omdat [!DNL Adobe Experience Manager Assets] volledig geïntegreerd is met het [!DNL Experience Manager]-platform, kunt u op efficiënte wijze informatie over de vervaldatum van bedrijfsmiddelen en de status van bedrijfsmiddelen beheren. U kunt ook licentiegegevens aan elementen koppelen.

## Vervaldatum van element {#asset-expiration}

Vervaldatum van activa is een effectieve manier om licentievereisten voor activa af te dwingen. Het zorgt ervoor dat het gepubliceerde element niet gepubliceerd wordt wanneer het vervalt, wat de mogelijkheid van schending van de licentie afsluit. Een gebruiker zonder beheerdersmachtigingen kan een verlopen middel niet bewerken, kopiëren, verplaatsen, publiceren en downloaden.

U kunt de vervalstatus van een middel in de [!DNL Assets] console in zowel de kaart als lijstmeningen bekijken.

![expired_flag_list](assets/expired_flag_list.png)

*Afbeelding: In de lijstweergave geeft de  [!UICONTROL Status] kolom de  [!UICONTROL Expired] banner weer.*

U kunt de vervalstatus van een element in [!UICONTROL Timeline] in linkerspoor bekijken.

![chlimage_1-144](assets/chlimage_1-144.png)

>[!NOTE]
>
>De vervaldatum van een element wordt anders weergegeven voor gebruikers in verschillende tijdzones.

U kunt de vervalstatus van activa in **[!UICONTROL References]** spoorlijn ook bekijken. Het beheert activa vervalstatussen en verhoudingen tussen samengestelde activa en referenced subassets, inzamelingen, en projecten.

1. Navigeer naar het element waarvan u de verwijzing naar webpagina&#39;s en samengestelde elementen wilt weergeven.
1. Selecteer het element en open **[!UICONTROL References]** in linkerspoor. Voor verlopen elementen wordt de vervalstatus **[!UICONTROL Asset is Expired]** bovenaan weergegeven in de [!UICONTROL References]-rail.

   ![chlimage_1-147](assets/chlimage_1-147.png)

   Als het element verlopen subassets heeft, wordt de status **[!UICONTROL Asset has Expired Sub-Assets]** weergegeven in de [!UICONTROL References]-rail.

   ![chlimage_1-148](assets/chlimage_1-148.png)

### Zoeken in verlopen elementen {#search-expired-assets}

In het deelvenster Zoeken kunt u zoeken naar verlopen elementen, waaronder verlopen subelementen.

1. Klik in de [!DNL Assets]-console op **[!UICONTROL Search]** in de werkbalk om het vak Onderzoek weer te geven.

1. Met de curseur in het vakje van het Onderzoek, druk de Enter sleutel om de pagina van onderzoeksresultaten te tonen.
1. Open het zoekpaneel in de linkerspoorstaaf. Klik op de optie **[!UICONTROL Expiry Status]** om deze uit te vouwen.

   ![chlimage_1-152](assets/chlimage_1-152.png)

1. Choose **[!UICONTROL Expired]**. Alleen de verlopen elementen worden weergegeven nadat de zoekresultaten zijn gefilterd.

Als u de optie **[!UICONTROL Expired]** kiest, worden in de [!DNL Assets]-console alleen de verlopen elementen en subelementen weergegeven waarnaar wordt verwezen door samengestelde elementen. De samengestelde elementen die verwijzen naar verlopen subelementen worden niet direct weergegeven nadat de subelementen verlopen zijn. In plaats daarvan, worden zij getoond nadat [!DNL Experience Manager] ontdekt dat zij verlopen subassets van verwijzingen voorzien de volgende tijd de planner loopt.

Als u de vervaldatum van een gepubliceerd element aan een datum vroeger dan de huidige plannercyclus wijzigt, ontdekt het programma nog dit element als verlopen activa in de volgende tijd het loopt en wijst dienovereenkomstig op status.

Bovendien als een glitch of een fout de planner verhindert verlopen activa in de huidige cyclus te ontdekken, onderzoekt de planner deze activa in de volgende cyclus opnieuw en ontdekt hun verlopen status.

Om [!DNL Assets] console toe te laten om de verwijzende samengestelde activa samen met de verlopen subassets te tonen, vorm een **[!UICONTROL Adobe CQ DAM Expiry Notification]** werkschema in [!DNL Experience Manager] de Manager van de Configuratie.

1. Open [!DNL Experience Manager] Configuratiebeheer.
1. Kies **[!UICONTROL Adobe CQ DAM Expiry Notification]**. Standaard is **[!UICONTROL Time based Scheduler]** geselecteerd, die een taak plant om op een bepaald tijdstip te controleren of een element verlopen subassets heeft. Nadat de taak is voltooid, worden elementen waarvan de subelementen zijn verlopen en waarnaar wordt verwezen, weergegeven als verlopen in de zoekresultaten.

1. Als u de taak periodiek wilt uitvoeren, wist u het veld **[!UICONTROL Time Based Scheduler Rule]** en wijzigt u de tijd in seconden in het veld **[!UICONTROL Periodic Scheduler]**. De voorbeeldexpressie `0 0 0 &ast; &ast; ?` activeert de taak bijvoorbeeld op 00 uur.
1. Selecteer **[!UICONTROL send email]** om e-mails te ontvangen wanneer een element vervalt.

   >[!NOTE]
   >
   >Alleen de maker van het element (de persoon die een bepaald element uploadt naar [!DNL Assets]) ontvangt een e-mail wanneer het element vervalt. Zie [E-mailmelding configureren](/help/sites-administering/notification.md) voor meer informatie over het configureren van e-mailmeldingen op het algemene niveau [!DNL Experience Manager].

1. Geef in het veld **[!UICONTROL Prior notification in seconds]** de tijd op in seconden voordat een element vervalt wanneer u een melding over de vervaldatum wilt ontvangen. De makers van bedrijfsmiddelen ontvangen een bericht vóór het verstrijken van het element om aan te geven dat het element op het punt staat na de opgegeven tijd te verlopen. Nadat het element is verlopen, ontvangt u een ander bericht waarin de vervaldatum wordt bevestigd. Bovendien worden de verlopen activa gedeactiveerd.

1. Klik op **[!UICONTROL Save]**.

## Elementstatussen {#asset-states}

De [!DNL Assets] console kan diverse staten voor activa tonen. Afhankelijk van de huidige status van een bepaald element wordt in de kaartweergave een label weergegeven dat de status beschrijft, bijvoorbeeld Verlopen, Gepubliceerd, Goedgekeurd, Afgewezen enzovoort.

1. Selecteer een element in de gebruikersinterface [!DNL Assets].
1. Klik op **[!UICONTROL Publish]** op de werkbalk. Als u **Publish** op de toolbar niet ziet, klik **[!UICONTROL More]** op de toolbar en bepaal de plaats **[!UICONTROL Publish]** ![publicatieoptie](assets/do-not-localize/publish-globe.png) optie.
1. Kies **[!UICONTROL Publish]** in het menu en sluit vervolgens het bevestigingsvenster.
1. Sluit de selectiemodus. De publicatiestatus voor het element wordt onder aan de elementminiatuur weergegeven in de kaartweergave. In de lijstmening, toont de Gepubliceerde kolom de tijd toen de activa werd gepubliceerd.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. Als u de pagina met elementdetails wilt weergeven, selecteert u een element in de interface [!DNL Assets] en klikt u op **[!UICONTROL Properties]** ![eigenschappen weergeven](assets/do-not-localize/info-circle-icon.png).

1. Stel op het tabblad [!UICONTROL Advanced] een vervaldatum voor het element in in het veld **[!UICONTROL Expires]**.

   ![de vervaldatum en tijd van het element instellen in het veld Verlopen](assets/asset-properties-advanced-tab.png)

   *Afbeelding:  [!UICONTROL Advanced] op de  [!UICONTROL Properties] elementpagina om de vervaldatum van elementen in te stellen.*

1. Klik **[!UICONTROL Save]** en klik dan **[!UICONTROL Close]** om de console van Activa te tonen.
1. De publicatiestatus voor het element geeft aan dat de status is verlopen onder aan de elementminiatuur in de kaartweergave. In de lijstweergave wordt de status van het element weergegeven als **[!UICONTROL Expired]**.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. Selecteer in de [!DNL Assets]-console een map en maak een revisietaak in de map.
1. Reviseer, keur/verwerp de activa in de overzichtstaak en klik **[!UICONTROL Complete]**.
1. Navigeer naar de map waarvoor u de revisietaak hebt gemaakt. De status voor de middelen die u hebt goedgekeurd/geweigerd, wordt onderaan weergegeven in de kaartweergave. In de lijstweergave worden de goedkeuringsstatus en de vervalstatus weergegeven in de desbetreffende kolommen.

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. Als u wilt zoeken naar elementen op basis van hun status, klikt u op **[!UICONTROL Search]** ![zoekoptie](assets/do-not-localize/search_icon.png) om de zoekbalk weer te geven.
1. Druk op Enter en klik op [!DNL Experience Manager] om het deelvenster Zoeken weer te geven.
1. Klik in het zoekvenster op **[!UICONTROL Publish Status]** en selecteer **[!UICONTROL Published]** om te zoeken naar gepubliceerde elementen in [!DNL Assets].

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Klik **[!UICONTROL Approval Status]** en klik de aangewezen optie om naar goedgekeurde of verworpen activa te zoeken.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Als u naar assets wilt zoeken op basis van hun vervalstatus, selecteert u **[!UICONTROL Expiry Status]** in het deelvenster Zoeken en kiest u de juiste optie.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. U kunt ook naar elementen zoeken op basis van een combinatie van statussen onder verschillende zoekfacetten. U kunt bijvoorbeeld zoeken naar gepubliceerde elementen die zijn goedgekeurd in een overzichtstaak en die nog niet zijn verlopen door de juiste opties te selecteren in de zoekfacetten.

   ![chlimage_1-166](assets/chlimage_1-166.png)

## Digital Rights Management in [!DNL Assets] {#digital-rights-management-in-assets-1}

Deze functie dwingt de acceptatie van de licentieovereenkomst af voordat u een onder licentie gegeven element kunt downloaden van [!DNL Adobe Experience Manager Assets].

Als u een beveiligd element selecteert en op **[!UICONTROL Download]** klikt, wordt u omgeleid naar een licentiepagina om de licentieovereenkomst te accepteren. Als u de licentieovereenkomst niet accepteert, is de optie **[!UICONTROL Download]** niet beschikbaar.

Als de selectie meerdere beveiligde elementen bevat, selecteert u één element tegelijk, accepteert u de licentieovereenkomst en gaat u verder met het downloaden van het element.

Een actief wordt als beschermd beschouwd indien aan een van deze voorwaarden is voldaan:

* De eigenschap voor metagegevens van het element `xmpRights:WebStatement` verwijst naar het pad van de pagina die de licentieovereenkomst voor het element bevat.
* De waarde van de eigenschap voor metagegevens van het element `adobe_dam:restrictions` is een onbewerkte HTML die de licentieovereenkomst opgeeft.

>[!NOTE]
>
>De locatie `/etc/dam/drm/licenses` die wordt gebruikt voor het opslaan van licenties in eerdere versies van [!DNL Experience Manager] is afgekeurd.
>
>Als u licentiepagina&#39;s maakt of wijzigt of deze van vorige [!DNL Experience Manager]-releases poort, raadt Adobe u aan deze pagina&#39;s op te slaan onder `/apps/settings/dam/drm/licenses` of `/conf/&ast;/settings/dam/drm/licenses`.

### Met DRM beveiligde middelen downloaden {#downloading-drm-assets}

1. Selecteer in de kaartweergave de elementen die u wilt downloaden en klik op **[!UICONTROL Download]**.
1. Selecteer op de pagina **[!UICONTROL Copyright Management]** de asset die u uit de lijst wilt downloaden.
1. Kies **[!UICONTROL Agree]** in het deelvenster [!UICONTROL License]. Naast het element wordt een vinkje weergegeven. Klik op de optie **[!UICONTROL Download]**.

   >[!NOTE]
   >
   >De optie **[!UICONTROL Download]** is alleen ingeschakeld als u akkoord gaat met de licentieovereenkomst voor een beveiligd element. Als uw selectie echter zowel beveiligde als niet-beveiligde elementen bevat, worden alleen de beveiligde elementen weergegeven in het deelvenster en wordt de optie **[!UICONTROL Download]** ingeschakeld om de niet-beveiligde elementen te downloaden. Als u tegelijkertijd licentieovereenkomsten voor meerdere beveiligde assets wilt accepteren, selecteert u de assets in de lijst en vervolgens kiest u **[!UICONTROL Agree]**.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Klik in het dialoogvenster op **[!UICONTROL Download]** om het element of de uitvoeringen te downloaden.
