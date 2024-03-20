---
title: Aangepaste formulieren opnieuw gebruiken
description: U kunt een bestaand adaptief formulier opnieuw gebruiken om nieuwe adaptieve formulieren te maken.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: ef564750-f107-41cb-887e-fc6d22b7d32e
feature: Adaptive Forms, Foundation Components
exl-id: d8ee4e82-3137-430e-aa47-b00191f2729c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 1%

---

# Aangepaste formulieren opnieuw gebruiken {#reusing-adaptive-forms}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/manage-metadata/reusing-adaptive-forms.html) |
| AEM 6,5 | Dit artikel |

## Inleiding {#introduction}

Als u bepaalde eigenschappen van een bestaand adaptief formulier wilt gebruiken om een nieuw formulier te genereren, kunt u gewoon de functie Kopiëren en plakken gebruiken. Bovendien kunt u het nieuwe aangepaste formulier op het gewenste mappad plakken. Alle metagegevenseigenschappen worden gerepliceerd en de XFA- en XSD-waarden voor op XFA en XSD gebaseerde adaptieve formulieren worden ook gekopieerd.

>[!NOTE]
>
>De status en de revisiedetails worden niet gekopieerd. Als uw adaptieve formulier bijvoorbeeld wordt gepubliceerd en u het kopieert, is het geplakte adaptieve formulier in ongepubliceerde staat. Op dezelfde manier geldt dat als een gekopieerd actief wordt gecontroleerd, het geplakte actief niet onder dezelfde revisie valt.

### Een adaptief formulier kopiëren {#copy-an-adaptive-form}

Kopieer een adaptief formulier op een van de volgende manieren:

1. Klikken op kopiëren ![aem6forms_copy](assets/aem6forms_copy.png) pictogram van Snelle acties.

   >[!NOTE]
   >
   >Snelle acties zijn de actiepunten die over een duimnagel worden getoond wanneer de muiswijzer.

1. Selecteer het adaptieve formulier. Het selectieproces is anders voor verschillende weergaven.

   Ga in de kaartweergave naar de selectiemodus door op de selectie te klikken ![aem6forms_check-circle](assets/aem6forms_check-circle.png) en klik op alle aangepaste formulieren die u wilt kopiëren.

   Als u in de lijstweergave werkt, klikt u op de selectievakjes van alle adaptieve formulieren om deze te selecteren.

   >[!NOTE]
   >
   >Alle geselecteerde elementen moeten adaptieve formulieren zijn, omdat de functie Kopiëren en plakken alleen wordt ondersteund voor adaptieve formulieren. Alle geselecteerde elementen moeten in dezelfde map aanwezig zijn.

   Klik op de kopie nadat u de elementen hebt geselecteerd ![aem6forms_copy](assets/aem6forms_copy.png) op de werkbalk om het geselecteerde aangepaste formulier te kopiëren.

### Een adaptief formulier plakken {#paste-an-adaptive-form}

Wanneer u op de kopieeractie klikt, wordt de selectiemodus automatisch verlaten en wordt de plakbewerking ![aem6forms_paste](assets/aem6forms_paste.png) zichtbaar. Ga nu naar het gewenste mappad en klik op Plakken ![aem6forms_paste](assets/aem6forms_paste.png) pictogram om het gekopieerde adaptieve formulier te plakken.

Als u plakt in dezelfde map of een ander bestand met dezelfde knooppuntnaam (waarmee het bestand is opgeslagen in de CRX-opslagruimte) bestaat in deze doelmap, wordt 1 toegevoegd aan het achtervoegsel (myaf wordt bijvoorbeeld myaf1 en als myaf1 op dezelfde locatie bestaat, wordt myaf myaf2. Alle andere eigenschappen blijven hetzelfde als het oorspronkelijke adaptieve formulier.

Na het klikken op de plakbewerking ![aem6forms_paste](assets/aem6forms_paste.png) pictogram, wordt het opnieuw verborgen. U kunt tegelijkertijd slechts één keer plakken. Als u opnieuw een kopie van hetzelfde element wilt maken, kopieert u het opnieuw.

### Inhoud van nieuw adaptief formulier wijzigen {#change-contents-of-new-adaptive-form}

De inhoud van een geplakte adaptieve formulieren kan op de volgende manieren worden gewijzigd, zodat deze verschilt van het gekopieerde formulier:

1. **Eigenschappen van metagegevens wijzigen:**

   U kunt de eigenschappen van metagegevens van het adaptieve formulier wijzigen, bijvoorbeeld de titel en beschrijving. Zie voor meer informatie over eigenschappen van metagegevens en hoe deze kunnen worden gewijzigd [Formuliermetagegevens beheren](/help/forms/using/manage-form-metadata.md)

1. **XFA/XSD wijzigen voor adaptieve Forms op basis van XFA/XSD:**

   U kunt de XFA/XSD wijzigen die in adaptieve formulieren wordt gebruikt. Als u wilt weten hoe deze adaptieve formulieren kunnen worden gewijzigd, gaat u naar [Metagegevens van formulieren beheren](/help/forms/using/manage-form-metadata.md)

1. **Opnieuw publiceren:**

   Het geplakte element verschilt van het gekopieerde element. U kunt de presentatie publiceren als een nieuw element, zodat deze beschikbaar is voor eindgebruikers. Als u wilt weten hoe u een element publiceert, raadpleegt u [Formulieren publiceren en verwijderen](/help/forms/using/publishing-unpublishing-forms.md)
