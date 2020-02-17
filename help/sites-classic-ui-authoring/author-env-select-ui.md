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

---


# Gebruikersinterface selecteren{#selecting-your-ui}

Aangezien de interface met aanraakbediening de klassieke interface vervangt, moet de gebruiker of beheerder van de AEM-instantie een actief besluit nemen om de klassieke UI te blijven gebruiken. Omdat klassieke UI niet meer wordt gehandhaafd, is er geen manier voor de auteursgebruiker eenvoudig om van klassieke UI aan het equivalent in aan aanraking-toegelaten UI over te schakelen.

Voor het gemak waarmee gebruikers kunnen ontwerpen, maakt de interface met aanraakbediening het mogelijk om indien nodig over te schakelen op de klassieke interface. Zie de [Uw interface](/help/sites-authoring/select-ui.md) selecteren in de standaarddocumentatie voor ontwerpen voor meer informatie.

>[!NOTE]
>
>Instanties die zijn bijgewerkt vanaf een vorige versie behouden de klassieke interface voor het ontwerpen van pagina&#39;s.
>
>Na verbetering, zal de paginascreatie niet automatisch geschakeld worden aan aanraking-toegelaten UI, maar u kunt dit vormen[gebruikend de configuratie](/help/sites-deploying/configuring-osgi.md) OSGi van de **Dienst** van de Wijze van de Authoring UI van WCM (de `AuthoringUIMode` dienst). Zie [UI-overschrijvingen voor de Editor](#uioverridesfortheeditor).

## De standaardinterface voor uw instantie configureren {#configuring-the-default-ui-for-your-instance}

Een systeembeheerder kan UI vormen die bij opstarten en login door [Wortel Toewijzing](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping)te gebruiken wordt gezien.

Dit kan door gebruikersgebreken of zittingsmontages worden met voeten getreden.
