---
title: Gebruikersinterface selecteren
description: Voor het gemak waarmee gebruikers kunnen ontwerpen, maakt de interface met aanraakbediening het mogelijk om indien nodig over te schakelen op de klassieke interface.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 57d45b06-e76e-420c-8cd0-389bd9f811af
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Gebruikersinterface selecteren{#selecting-your-ui}

Aangezien de aanraking-toegelaten UI de klassieke UI vervangt, moet de gebruiker of de beheerder van de AEM instantie een actief besluit nemen om het gebruiken van klassieke UI voort te zetten. Omdat klassieke UI niet meer wordt gehandhaafd, is er geen manier voor de auteursgebruiker eenvoudig om van klassieke UI aan het equivalent in aan aanraking-toegelaten UI over te schakelen.

Voor het gemak waarmee gebruikers kunnen ontwerpen, maakt de interface met aanraakbediening het mogelijk om indien nodig over te schakelen op de klassieke interface. Zie [ Selecterend uw UI ](/help/sites-authoring/select-ui.md) in de standaardAuthoring documentatie voor details.

>[!NOTE]
>
>Instanties die zijn bijgewerkt vanaf een vorige versie behouden de klassieke interface voor het ontwerpen van pagina&#39;s.
>
>Na verbetering, zal de paginascreatie niet automatisch geschakeld worden aan aanraking-toegelaten UI, maar u kunt dit vormen gebruikend de [ configuratie OSGi ](/help/sites-deploying/configuring-osgi.md) van de **WCM Authoring UI van de Wijze van de Wijze** ( `AuthoringUIMode` dienst). Zie [ met voeten treedt UI voor de Redacteur ](#uioverridesfortheeditor).

## De standaardinterface voor uw instantie configureren {#configuring-the-default-ui-for-your-instance}

Een systeembeheerder kan UI vormen die bij opstarten en login door [ Toewijzing van de Wortel te gebruiken ](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping) wordt gezien.

Dit kan door gebruikersgebreken of zittingsmontages worden met voeten getreden.
