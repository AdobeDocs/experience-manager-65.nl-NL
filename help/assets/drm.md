---
title: Digital Rights Management van activa
description: Leer hoe te om activa te beheren vervalst staten en informatie voor vergunning gegeven activa in  [!DNL Experience Manager].
contentOwner: AG
role: User, Admin
feature: DRM,Asset Management
exl-id: a49cfd25-e8d9-492f-be5e-acab0cf67a28
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1347'
ht-degree: 5%

---

# Digital Rights Management voor elementen {#digital-rights-management-in-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/drm.html?lang=en) |
| AEM 6,5 | Dit artikel |

Digitale middelen zijn vaak gekoppeld aan een licentie die de gebruiksvoorwaarden en -duur bepaalt. Omdat [!DNL Adobe Experience Manager Assets] volledig geïntegreerd is met het [!DNL Experience Manager] -platform, kunt u op efficiënte wijze informatie over het verlopen van elementen en de status van elementen beheren. U kunt ook licentiegegevens aan elementen koppelen.

## Vervaldatum van element {#asset-expiration}

Vervaldatum van activa is een effectieve manier om de licentievereisten voor activa af te dwingen. Het zorgt ervoor dat het gepubliceerde element niet gepubliceerd wordt wanneer het vervalt, wat de mogelijkheid van schending van de licentie afsluit. Een gebruiker zonder beheerdersmachtigingen kan een verlopen middel niet bewerken, kopiëren, verplaatsen, publiceren en downloaden.

U kunt de vervalstatus van een middel in de [!DNL Assets] console in zowel de kaart als lijstmeningen bekijken.

![ expired_flag_list ](assets/expired_flag_list.png)

*Cijfer: In lijstmening, toont de [!UICONTROL Status] kolom de [!UICONTROL Expired] banner.*

U kunt de vervalstatus van een element in [!UICONTROL Timeline] in linkerspoor bekijken.

![ chlimage_1-144 ](assets/chlimage_1-144.png)

>[!NOTE]
>
>De vervaldatum van een element wordt anders weergegeven voor gebruikers in verschillende tijdzones.

U kunt ook de vervalstatus van elementen bekijken in de **[!UICONTROL References]** -rail. Het beheert activa vervalstatussen en verhoudingen tussen samengestelde activa en referenced subassets, inzamelingen, en projecten.

1. Navigeer naar het element waarvan u de verwijzing naar webpagina&#39;s en samengestelde elementen wilt weergeven.
1. Selecteer het element en open **[!UICONTROL References]** in linkerraster. Voor verlopen elementen geeft de [!UICONTROL References] -rail de vervalstatus **[!UICONTROL Asset is Expired]** bovenaan weer.

   ![ chlimage_1-147 ](assets/chlimage_1-147.png)

   Als het element verlopen subassets heeft, geeft de [!UICONTROL References] -rail de status **[!UICONTROL Asset has Expired Sub-Assets]** weer.

   ![ chlimage_1-148 ](assets/chlimage_1-148.png)

### Zoeken in verlopen elementen {#search-expired-assets}

In het deelvenster Zoeken kunt u zoeken naar verlopen elementen, waaronder verlopen subelementen.

1. Klik in de [!DNL Assets] -console op de **[!UICONTROL Search]** -werkbalk om het vak Onderzoek weer te geven.

1. Selecteer met de cursor in het vak Onderzoek de `Enter` -toets om de pagina met zoekresultaten weer te geven.
1. Open het zoekpaneel in de linkerspoorstaaf. Klik op de optie **[!UICONTROL Expiry Status]** om deze uit te vouwen.

   ![ chlimage_1-152 ](assets/chlimage_1-152.png)

1. Kies **[!UICONTROL Expired]** . Alleen de verlopen elementen worden weergegeven nadat de zoekresultaten zijn gefilterd.

Wanneer u de optie **[!UICONTROL Expired]** kiest, worden in de [!DNL Assets] -console alleen de verlopen elementen en subelementen weergegeven waarnaar wordt verwezen door samengestelde elementen. De samengestelde elementen die verwijzen naar verlopen subelementen worden niet direct weergegeven nadat de subelementen verlopen zijn. In plaats daarvan, worden zij getoond nadat [!DNL Experience Manager] ontdekt dat zij verlopen subassets van verwijzingen voorzien de volgende tijd de planner loopt.

Als u de vervaldatum van een gepubliceerd element aan een datum vroeger dan de huidige plannercyclus wijzigt, ontdekt het programma nog dit element als verlopen activa in de volgende tijd het loopt en wijst dienovereenkomstig op status.

Bovendien als een glitch of een fout de planner verhindert verlopen activa in de huidige cyclus te ontdekken, onderzoekt de planner deze activa in de volgende cyclus opnieuw en ontdekt hun verlopen status.

Als u wilt dat de [!DNL Assets] -console de samengestelde middelen die naar verwijzen samen met de verlopen submiddelen weergeeft, configureert u een **[!UICONTROL Adobe CQ DAM Expiry Notification]** -workflow in [!DNL Experience Manager] Configuration Manager.

1. Open [!DNL Experience Manager] Configuration Manager.
1. Kies **[!UICONTROL Adobe CQ DAM Expiry Notification]** . Standaard is **[!UICONTROL Time based Scheduler]** geselecteerd. Hiermee wordt een taak gepland om op een bepaald tijdstip te controleren of een element verlopen subelementen heeft. Nadat de taak is voltooid, worden elementen waarvan de subelementen zijn verlopen en waarnaar wordt verwezen, weergegeven als verlopen in de zoekresultaten.

1. Als u de taak periodiek wilt uitvoeren, wist u het veld **[!UICONTROL Time Based Scheduler Rule]** en wijzigt u de tijd in seconden in het veld **[!UICONTROL Periodic Scheduler]**. De voorbeeldexpressie `0 0 0 * * ?` activeert de taak bijvoorbeeld op 00 uur.
1. Selecteer **[!UICONTROL send email]** om e-mails te ontvangen wanneer een element vervalt.

   >[!NOTE]
   >
   >Alleen de maker van het element (de persoon die een bepaald element uploadt naar [!DNL Assets] ) ontvangt een e-mail wanneer het element vervalt. Zie [ hoe te om e-mailbericht ](/help/sites-administering/notification.md) voor extra details te vormen rond het vormen van e-mailberichten op het algemene [!DNL Experience Manager] niveau.

1. Geef in het veld **[!UICONTROL Prior notification in seconds]** de tijd in seconden op voordat een element vervalt wanneer u een melding over de vervaldatum wilt ontvangen. De makers van bedrijfsmiddelen ontvangen een bericht vóór het verstrijken van het element om aan te geven dat het element op het punt staat na de opgegeven tijd te verlopen. Nadat het element is verlopen, ontvangt u een ander bericht waarin de vervaldatum wordt bevestigd. Bovendien worden de verlopen activa gedeactiveerd.

1. Klik op **[!UICONTROL Save]**.

## Elementstatussen {#asset-states}

De [!DNL Assets] -console kan verschillende statussen voor elementen weergeven. Afhankelijk van de huidige status van een bepaald element wordt in de kaartweergave een label weergegeven dat de status beschrijft, bijvoorbeeld Verlopen, Gepubliceerd, Goedgekeurd, Afgewezen enzovoort.

1. Selecteer een element in de gebruikersinterface van [!DNL Assets] .
1. Klik op **[!UICONTROL Publish]** op de werkbalk. Als u **Publish** op de toolbar niet ziet, klik **[!UICONTROL More]** op de toolbar en bepaal de plaats van **[!UICONTROL Publish]** ![ optie ](assets/do-not-localize/publish-globe.png) publiceren.
1. Kies **[!UICONTROL Publish]** in het menu en sluit vervolgens het bevestigingsvenster.
1. Sluit de selectiemodus. De publicatiestatus voor het element wordt onder aan de elementminiatuur weergegeven in de kaartweergave. In de lijstmening, toont de Gepubliceerde kolom de tijd toen de activa werd gepubliceerd.

   ![ chlimage_1-157 ](assets/chlimage_1-157.png)

1. Om zijn pagina van elementdetails, in de [!DNL Assets] interface te tonen, selecteer een activa en klik **[!UICONTROL Properties]** ![ meningseigenschappen ](assets/do-not-localize/info-circle-icon.png).

1. Stel op het tabblad [!UICONTROL Advanced] een vervaldatum voor het element in vanuit het veld **[!UICONTROL Expires]** .

   ![ vastgestelde datum en tijd van de activavervaldatum op Verloopt gebied ](assets/asset-properties-advanced-tab.png)

   *Cijfer: [!UICONTROL Advanced] lusje in activa [!UICONTROL Properties] pagina om activa te plaatsen vervallen.*

1. Klik op **[!UICONTROL Save]** en vervolgens op **[!UICONTROL Close]** om de Asset-console weer te geven.
1. De publicatiestatus voor het element geeft aan dat de status is verlopen onder aan de elementminiatuur in de kaartweergave. In de lijstweergave wordt de status van het element weergegeven als **[!UICONTROL Expired]** .

   ![ chlimage_1-160 ](assets/chlimage_1-160.png)

1. Selecteer in de [!DNL Assets] -console een map en maak een revisietaak in de map.
1. Reviseer, keur de elementen in de revisietaak goed of wijs deze af en klik op **[!UICONTROL Complete]** .
1. Navigeer naar de map waarvoor u de revisietaak hebt gemaakt. De status voor de middelen die u hebt goedgekeurd/geweigerd, wordt onderaan weergegeven in de kaartweergave. In de lijstweergave worden de goedkeuringsstatus en de vervalstatus weergegeven in de desbetreffende kolommen.

   ![ chlimage_1-161 ](assets/chlimage_1-161.png)

1. Om naar activa te zoeken die op hun status worden gebaseerd, klik **[!UICONTROL Search]** ![ onderzoeksoptie ](assets/do-not-localize/search_icon.png) om de bar van het Onderzoek te tonen.
1. Selecteer `Return` en klik op [!DNL Experience Manager] om het deelvenster Zoeken weer te geven.
1. Klik in het deelvenster Zoeken op **[!UICONTROL Publish Status]** en selecteer **[!UICONTROL Published]** om te zoeken naar gepubliceerde elementen in [!DNL Assets] .

   ![ chlimage_1-163 ](assets/chlimage_1-163.png)

1. Klik op **[!UICONTROL Approval Status]** en klik op de gewenste optie om te zoeken naar goedgekeurde of geweigerde elementen.

   ![ chlimage_1-164 ](assets/chlimage_1-164.png)

1. Als u naar assets wilt zoeken op basis van hun vervalstatus, selecteert u **[!UICONTROL Expiry Status]** in het deelvenster Zoeken en kiest u de juiste optie.

   ![ chlimage_1-165 ](assets/chlimage_1-165.png)

1. U kunt ook naar elementen zoeken op basis van een combinatie van statussen onder verschillende zoekfacetten. U kunt bijvoorbeeld zoeken naar gepubliceerde elementen die zijn goedgekeurd in een overzichtstaak en die nog niet zijn verlopen door de juiste opties te selecteren in de zoekfacetten.

   ![ chlimage_1-166 ](assets/chlimage_1-166.png)

## Digital Rights Management in [!DNL Assets] {#digital-rights-management-in-assets-1}

Deze functie dwingt de acceptatie van de licentieovereenkomst af voordat u een licentie-element kunt downloaden van [!DNL Adobe Experience Manager Assets] .

Als u een beveiligd element selecteert en op **[!UICONTROL Download]** klikt, wordt u omgeleid naar een licentiepagina om de licentieovereenkomst te accepteren. Als u de licentieovereenkomst niet accepteert, is de optie **[!UICONTROL Download]** niet beschikbaar.

Als de selectie meerdere beveiligde elementen bevat, selecteert u één element tegelijk, accepteert u de licentieovereenkomst en gaat u verder met het downloaden van het element.

Een actief wordt als beschermd beschouwd indien aan een van deze voorwaarden is voldaan:

* De eigenschap voor metagegevens van elementen `xmpRights:WebStatement` verwijst naar het pad van de pagina die de licentieovereenkomst voor het element bevat.
* De waarde van de eigenschap voor metagegevens van elementen `adobe_dam:restrictions` is een onbewerkte HTML die de licentieovereenkomst opgeeft.

>[!NOTE]
>
>De locatie `/etc/dam/drm/licenses` die wordt gebruikt voor het opslaan van licenties in eerdere versies van [!DNL Experience Manager] , is afgekeurd.
>
>Als u licentiepagina&#39;s maakt of wijzigt of deze van vorige [!DNL Experience Manager] -releases poort, raadt de Adobe u aan deze pagina&#39;s op te slaan onder `/apps/settings/dam/drm/licenses` of `/conf/&ast;/settings/dam/drm/licenses` .

### DRM-beveiligde bestanden downloaden {#downloading-drm-assets}

1. Selecteer in de kaartweergave de elementen die u wilt downloaden en klik op **[!UICONTROL Download]** .
1. Selecteer op de pagina **[!UICONTROL Copyright Management]** de asset die u uit de lijst wilt downloaden.
1. Kies **[!UICONTROL Agree]** in het deelvenster [!UICONTROL License] . Naast het element wordt een vinkje weergegeven. Klik op de optie **[!UICONTROL Download]** .

   >[!NOTE]
   >
   >De optie **[!UICONTROL Download]** wordt alleen ingeschakeld wanneer u akkoord gaat met de licentieovereenkomst voor een beveiligd element. Als uw selectie echter zowel beveiligde als niet-beveiligde elementen bevat, worden alleen de beveiligde elementen weergegeven in het deelvenster en wordt de optie **[!UICONTROL Download]** ingeschakeld om de niet-beveiligde elementen te downloaden. Als u tegelijkertijd licentieovereenkomsten voor meerdere beveiligde assets wilt accepteren, selecteert u de assets in de lijst en vervolgens kiest u **[!UICONTROL Agree]**.

   ![ chlimage_1-167 ](assets/chlimage_1-167.png)

1. Klik in het dialoogvenster op **[!UICONTROL Download]** om het element of de uitvoeringen te downloaden.
