---
title: Gebruikersinterface selecteren
seo-title: Gebruikersinterface selecteren
description: Voor het gemak waarmee gebruikers kunnen ontwerpen, maakt de interface met aanraakbediening het mogelijk om indien nodig over te schakelen op de klassieke interface.
seo-description: Voor het gemak waarmee gebruikers kunnen ontwerpen, maakt de interface met aanraakbediening het mogelijk om indien nodig over te schakelen op de klassieke interface.
uuid: 755e513e-990c-4dba-8316-623f17bf5c33
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: dcac2a3a-3241-47de-96ce-982ab0bc05eb
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---


# Uw interface selecteren{#selecting-your-ui}

Aangezien de aanraking-toegelaten UI de klassieke UI vervangt, moet de gebruiker of de beheerder van de AEM instantie een actief besluit nemen om het gebruiken van klassieke UI voort te zetten. Omdat klassieke UI niet meer wordt gehandhaafd, is er geen manier voor de auteursgebruiker eenvoudig om van klassieke UI aan het equivalent in aan aanraking-toegelaten UI over te schakelen.

Voor het gemak waarmee gebruikers kunnen ontwerpen, maakt de interface met aanraakbediening het mogelijk om indien nodig over te schakelen op de klassieke interface. Zie [Uw UI](/help/sites-authoring/select-ui.md) in de standaardAuthoring documentatie voor details selecteren.

>[!NOTE]
>
>Instanties die zijn bijgewerkt vanaf een vorige versie behouden de klassieke interface voor het ontwerpen van pagina&#39;s.
>
>Na verbetering, zal de pagina authoring niet automatisch worden geschakeld op touch-enabled UI, maar u kunt dit vormen gebruikend [OSGi configuratie](/help/sites-deploying/configuring-osgi.md) van **WCM Authoring UI Mode Service** ( `AuthoringUIMode` dienst). Zie [UI-overschrijvingen voor de Editor](#uioverridesfortheeditor).

## Standaardinterface configureren voor uw instantie {#configuring-the-default-ui-for-your-instance}

Een systeembeheerder kan UI vormen die bij opstarten en login door [Toewijzing van de Wortel](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping) te gebruiken wordt gezien.

Dit kan door gebruikersgebreken of zittingsmontages worden met voeten getreden.
