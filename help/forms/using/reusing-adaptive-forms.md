---
title: Aangepaste formulieren opnieuw gebruiken
seo-title: Reusing adaptive forms
description: U kunt een bestaand adaptief formulier opnieuw gebruiken om nieuwe adaptieve formulieren te maken.
seo-description: You can reuse an existing adaptive form to create new adaptive forms.
uuid: f1d0fb70-e255-4dd9-8e6d-fd65eaf2e81a
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: ef564750-f107-41cb-887e-fc6d22b7d32e
feature: Adaptive Forms
exl-id: d8ee4e82-3137-430e-aa47-b00191f2729c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Aangepaste formulieren opnieuw gebruiken {#reusing-adaptive-forms}

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
   >Alle geselecteerde elementen moeten adaptieve formulieren zijn, omdat kopieer- en plakfuncties alleen worden ondersteund voor adaptieve formulieren. Alle geselecteerde elementen moeten in dezelfde map aanwezig zijn.

   Nadat u de elementen hebt geselecteerd, klikt u op de kopie ![aem6forms_copy](assets/aem6forms_copy.png) op de werkbalk om het geselecteerde aangepaste formulier te kopiëren.

### Een adaptief formulier plakken {#paste-an-adaptive-form}

Wanneer u op de kopieeractie klikt, wordt de selectiemodus automatisch verlaten en wordt de plakbewerking ![aem6forms_paste](assets/aem6forms_paste.png) zichtbaar. Ga nu naar het gewenste mappad en klik op Plakken ![aem6forms_paste](assets/aem6forms_paste.png) pictogram om het gekopieerde adaptieve formulier te plakken.

Als u plakt in dezelfde map of een ander bestand met dezelfde knooppuntnaam (waarmee het bestand is opgeslagen in de CRX-opslagruimte) bestaat in deze doelmap, wordt 1 toegevoegd aan het achtervoegsel (myaf wordt bijvoorbeeld myaf1 en als myaf1 op dezelfde locatie bestaat, wordt myaf myaf2. Alle andere eigenschappen blijven hetzelfde als het oorspronkelijke adaptieve formulier.

Nadat u op de plakbewerking hebt geklikt ![aem6forms_paste](assets/aem6forms_paste.png) pictogram, wordt het opnieuw verborgen. In één keer kunt u slechts één keer plakken. Als u opnieuw een kopie van hetzelfde element wilt maken, kopieert u het opnieuw.

### Inhoud van nieuw adaptief formulier wijzigen {#change-contents-of-new-adaptive-form}

De inhoud van een geplakte adaptieve formulieren kan op de volgende manieren worden gewijzigd, zodat deze verschilt van het gekopieerde formulier:

1. **Eigenschappen van metagegevens wijzigen:**

   U kunt de eigenschappen van metagegevens van het adaptieve formulier wijzigen, bijvoorbeeld de titel en beschrijving. Zie voor meer informatie over eigenschappen van metagegevens en hoe deze kunnen worden gewijzigd [Formuliermetagegevens beheren](/help/forms/using/manage-form-metadata.md)

1. **XFA/XSD wijzigen voor adaptieve Forms op basis van XFA/XSD:**

   U kunt de XFA/XSD wijzigen die in adaptieve formulieren wordt gebruikt. Zie voor meer informatie over het wijzigen van deze adaptieve formulieren [Metagegevens van formulieren beheren](/help/forms/using/manage-form-metadata.md)

1. **Opnieuw publiceren:**

   Het geplakte element verschilt van het gekopieerde element. U kunt de presentatie publiceren als een nieuw element, zodat deze beschikbaar is voor eindgebruikers. Als u wilt weten hoe u een element publiceert, raadpleegt u [Formulieren publiceren en verwijderen](/help/forms/using/publishing-unpublishing-forms.md)
