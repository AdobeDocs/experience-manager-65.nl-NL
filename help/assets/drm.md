---
title: Digital Rights Management van activa
description: Leer hoe u de status van verlopen van middelen en informatie over gelicentieerde middelen beheert in [!DNL Experience Manager].
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
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/drm.html?lang=en) |
| AEM 6,5 | Dit artikel |

Digitale middelen zijn vaak gekoppeld aan een licentie die de gebruiksvoorwaarden en -duur bepaalt. Omdat [!DNL Adobe Experience Manager Assets] is volledig geïntegreerd met de [!DNL Experience Manager] -platform, kunt u informatie over het verlopen van bedrijfsmiddelen en de status van bedrijfsmiddelen efficiënt beheren. U kunt ook licentiegegevens aan elementen koppelen.

## Vervaldatum van element {#asset-expiration}

Vervaldatum van activa is een effectieve manier om de licentievereisten voor activa af te dwingen. Het zorgt ervoor dat het gepubliceerde element niet gepubliceerd wordt wanneer het vervalt, wat de mogelijkheid van schending van de licentie afsluit. Een gebruiker zonder beheerdersmachtigingen kan een verlopen middel niet bewerken, kopiëren, verplaatsen, publiceren en downloaden.

U kunt de vervalstatus van een element weergeven in het dialoogvenster [!DNL Assets] in zowel de kaart- als lijstweergaven.

![expired_flag_list](assets/expired_flag_list.png)

*Afbeelding: in de lijstweergave [!UICONTROL Status] de kolom toont [!UICONTROL Expired] banner.*

U kunt de vervalstatus van een element weergeven in het dialoogvenster [!UICONTROL Timeline] in linkerspoor.

![chlimage_1-144](assets/chlimage_1-144.png)

>[!NOTE]
>
>De vervaldatum van een element wordt anders weergegeven voor gebruikers in verschillende tijdzones.

U kunt ook de vervalstatus van elementen weergeven in het dialoogvenster **[!UICONTROL References]** spoorwegen. Het beheert activa vervalstatussen en verhoudingen tussen samengestelde activa en referenced subassets, inzamelingen, en projecten.

1. Navigeer naar het element waarvan u de verwijzing naar webpagina&#39;s en samengestelde elementen wilt weergeven.
1. Selecteer het element en open **[!UICONTROL References]** in linkerspoor. Voor verlopen elementen [!UICONTROL References] spoorstaaf geeft de verloopstatus weer **[!UICONTROL Asset is Expired]** bovenaan.

   ![chlimage_1-147](assets/chlimage_1-147.png)

   Als het element verlopen is, worden de [!UICONTROL References] spoorstaaf geeft de status **[!UICONTROL Asset has Expired Sub-Assets]**.

   ![chlimage_1-148](assets/chlimage_1-148.png)

### Zoeken in verlopen elementen {#search-expired-assets}

In het deelvenster Zoeken kunt u zoeken naar verlopen elementen, waaronder verlopen subelementen.

1. In de [!DNL Assets] console, klik **[!UICONTROL Search]** in de werkbalk om het vak Onderzoek weer te geven.

1. Selecteer met de cursor in het vak Onderzoek de optie `Enter` om de pagina met zoekresultaten weer te geven.
1. Open het zoekpaneel in de linkerspoorstaaf. Klik op de knop **[!UICONTROL Expiry Status]** om het uit te breiden.

   ![chlimage_1-152](assets/chlimage_1-152.png)

1. Kies **[!UICONTROL Expired]**. Alleen de verlopen elementen worden weergegeven nadat de zoekresultaten zijn gefilterd.

Wanneer u **[!UICONTROL Expired]** de [!DNL Assets] De console toont slechts de verlopen activa en de subassets die door samengestelde activa van verwijzingen worden voorzien. De samengestelde elementen die verwijzen naar verlopen subelementen worden niet direct weergegeven nadat de subelementen verlopen zijn. In plaats daarvan worden ze weergegeven na [!DNL Experience Manager] ontdekt dat zij verlopen subassets van verwijzingen voorzien de volgende tijd de planner loopt.

Als u de vervaldatum van een gepubliceerd element aan een datum vroeger dan de huidige plannercyclus wijzigt, ontdekt het programma nog dit element als verlopen activa in de volgende tijd het loopt en wijst dienovereenkomstig op status.

Bovendien als een glitch of een fout de planner verhindert verlopen activa in de huidige cyclus te ontdekken, onderzoekt de planner deze activa in de volgende cyclus opnieuw en ontdekt hun verlopen status.

Om het [!DNL Assets] console om de verwijzende samengestelde activa samen met de verlopen subassets te tonen, vorm en **[!UICONTROL Adobe CQ DAM Expiry Notification]** workflow in [!DNL Experience Manager] Configuratiebeheer.

1. Openen [!DNL Experience Manager] Configuratiebeheer.
1. Kies **[!UICONTROL Adobe CQ DAM Expiry Notification]**. Standaard, **[!UICONTROL Time based Scheduler]** is geselecteerd, die een taak plant om op een bepaald tijdstip te controleren of een element verlopen subassets heeft. Nadat de taak is voltooid, worden elementen waarvan de subelementen zijn verlopen en waarnaar wordt verwezen, weergegeven als verlopen in de zoekresultaten.

1. Als u de taak periodiek wilt uitvoeren, wist u het veld **[!UICONTROL Time Based Scheduler Rule]** en wijzigt u de tijd in seconden in het veld **[!UICONTROL Periodic Scheduler]**. De voorbeeldexpressie `0 0 0 * * ?` wordt de taak om 00 uur gestart.
1. Selecteren **[!UICONTROL send email]** om e-mails te ontvangen wanneer een middel verloopt.

   >[!NOTE]
   >
   >Alleen de maker van het actief (de persoon die een bepaald actief uploadt naar [!DNL Assets]) ontvangt een e-mail wanneer het middel vervalt. Zie [hoe te om e-mailbericht te vormen](/help/sites-administering/notification.md) voor meer informatie over het configureren van e-mailmeldingen in het algemeen [!DNL Experience Manager] niveau.

1. In de **[!UICONTROL Prior notification in seconds]** geeft u de tijd in seconden op voordat een element vervalt wanneer u een melding over de vervaldatum wilt ontvangen. De makers van bedrijfsmiddelen ontvangen een bericht vóór het verstrijken van het element om aan te geven dat het element op het punt staat na de opgegeven tijd te verlopen. Nadat het element is verlopen, ontvangt u een ander bericht waarin de vervaldatum wordt bevestigd. Bovendien worden de verlopen activa gedeactiveerd.

1. Klik op **[!UICONTROL Save]**.

## Elementstatussen {#asset-states}

De [!DNL Assets] De console kan diverse staten voor activa tonen. Afhankelijk van de huidige status van een bepaald element wordt in de kaartweergave een label weergegeven dat de status beschrijft, bijvoorbeeld Verlopen, Gepubliceerd, Goedgekeurd, Afgewezen enzovoort.

1. In de [!DNL Assets] -interface selecteert u een element.
1. Klik op **[!UICONTROL Publish]** op de werkbalk. Als u niet ziet **Publiceren** klikt u op de werkbalk op **[!UICONTROL More]** op de werkbalk en zoek **[!UICONTROL Publish]** ![publicatieoptie](assets/do-not-localize/publish-globe.png) -optie.
1. Kies **[!UICONTROL Publish]** in het menu en sluit vervolgens het bevestigingsvenster.
1. Sluit de selectiemodus. De publicatiestatus voor het element wordt onder aan de elementminiatuur weergegeven in de kaartweergave. In de lijstmening, toont de Gepubliceerde kolom de tijd toen de activa werd gepubliceerd.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. Als u de pagina met elementdetails wilt weergeven, gaat u naar [!DNL Assets] interface, selecteer een element en klik op **[!UICONTROL Properties]** ![weergave-eigenschappen](assets/do-not-localize/info-circle-icon.png).

1. In de [!UICONTROL Advanced] een vervaldatum voor het element in te stellen vanaf de **[!UICONTROL Expires]** veld.

   ![de vervaldatum en tijd van het element instellen in het veld Verlopen](assets/asset-properties-advanced-tab.png)

   *Afbeelding: [!UICONTROL Advanced] tab in element [!UICONTROL Properties] pagina voor instellen van verlopen van elementen.*

1. Klikken **[!UICONTROL Save]** en klik vervolgens op **[!UICONTROL Close]** om de Asset-console weer te geven.
1. De publicatiestatus voor het element geeft aan dat de status is verlopen onder aan de elementminiatuur in de kaartweergave. In de lijstweergave wordt de status van het element weergegeven als **[!UICONTROL Expired]**.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. In de [!DNL Assets] Selecteer een map en maak een revisietaak in de map.
1. Reviseer en keur de elementen in de revisietaak goed/verwerp deze en klik op **[!UICONTROL Complete]**.
1. Navigeer naar de map waarvoor u de revisietaak hebt gemaakt. De status voor de middelen die u hebt goedgekeurd/geweigerd, wordt onderaan weergegeven in de kaartweergave. In de lijstweergave worden de goedkeuringsstatus en de vervalstatus weergegeven in de desbetreffende kolommen.

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. Als u wilt zoeken naar elementen op basis van hun status, klikt u op **[!UICONTROL Search]** ![zoekoptie](assets/do-not-localize/search_icon.png) om de zoekbalk weer te geven.
1. Selecteren `Return` en klik op [!DNL Experience Manager] om het zoekvenster weer te geven.
1. Klik in het deelvenster Zoeken op **[!UICONTROL Publish Status]** en selecteert u **[!UICONTROL Published]** om te zoeken naar gepubliceerde elementen in [!DNL Assets].

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Klikken **[!UICONTROL Approval Status]** en klik op de gewenste optie om te zoeken naar goedgekeurde of geweigerde elementen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Als u naar assets wilt zoeken op basis van hun vervalstatus, selecteert u **[!UICONTROL Expiry Status]** in het deelvenster Zoeken en kiest u de juiste optie.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. U kunt ook naar elementen zoeken op basis van een combinatie van statussen onder verschillende zoekfacetten. U kunt bijvoorbeeld zoeken naar gepubliceerde elementen die zijn goedgekeurd in een overzichtstaak en die nog niet zijn verlopen door de juiste opties te selecteren in de zoekfacetten.

   ![chlimage_1-166](assets/chlimage_1-166.png)

## Digital Rights Management in [!DNL Assets] {#digital-rights-management-in-assets-1}

Deze functie dwingt de acceptatie van de licentieovereenkomst af voordat u een licentie-asset kunt downloaden van [!DNL Adobe Experience Manager Assets].

Als u een beveiligd element selecteert en klikt op **[!UICONTROL Download]**, wordt u omgeleid naar een licentiepagina om de licentieovereenkomst te accepteren. Als u de licentieovereenkomst niet accepteert, **[!UICONTROL Download]** is niet beschikbaar.

Als de selectie meerdere beveiligde elementen bevat, selecteert u één element tegelijk, accepteert u de licentieovereenkomst en gaat u verder met het downloaden van het element.

Een actief wordt als beschermd beschouwd indien aan een van deze voorwaarden is voldaan:

* De eigenschap voor metagegevens van het element `xmpRights:WebStatement` verwijst naar het pad van de pagina die de licentieovereenkomst voor het element bevat.
* De waarde van de eigenschap voor metagegevens van het element `adobe_dam:restrictions` is een ruwe HTML die de licentieovereenkomst specificeert.

>[!NOTE]
>
>De locatie `/etc/dam/drm/licenses` gebruikt voor de opslag van licenties in eerdere versies van [!DNL Experience Manager] is vervangen.
>
>Als u licentiepagina&#39;s maakt of wijzigt, of deze van vorige [!DNL Experience Manager] releases, raadt Adobe u aan deze onder te slaan `/apps/settings/dam/drm/licenses` of `/conf/&ast;/settings/dam/drm/licenses`.

### DRM-beveiligde bestanden downloaden {#downloading-drm-assets}

1. Selecteer in de kaartweergave de elementen die u wilt downloaden en klik op **[!UICONTROL Download]**.
1. Selecteer op de pagina **[!UICONTROL Copyright Management]** de asset die u uit de lijst wilt downloaden.
1. In de [!UICONTROL License] deelvenster, kiest u **[!UICONTROL Agree]**. Naast het element wordt een vinkje weergegeven. Klik op de knop **[!UICONTROL Download]** -optie.

   >[!NOTE]
   >
   >De **[!UICONTROL Download]** is alleen ingeschakeld als u akkoord gaat met de licentieovereenkomst voor een beveiligd element. Als uw selectie echter zowel beveiligde als niet-beveiligde elementen bevat, worden alleen de beveiligde elementen weergegeven in het deelvenster en in het dialoogvenster **[!UICONTROL Download]** is ingeschakeld om de niet-beveiligde elementen te downloaden. Als u tegelijkertijd licentieovereenkomsten voor meerdere beveiligde assets wilt accepteren, selecteert u de assets in de lijst en vervolgens kiest u **[!UICONTROL Agree]**.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Klik op **[!UICONTROL Download]** om het element of de uitvoeringen te downloaden.
