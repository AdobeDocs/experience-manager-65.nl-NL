---
title: Formulieren en gerelateerde bronnen verwijderen
seo-title: Formulieren en gerelateerde bronnen verwijderen
description: Hoe te om een vorm of een activa in Vormen AEM te schrappen en het effect op referenced en verwijzende activa en XFA vormen.
seo-description: Hoe te om een vorm of een activa in Vormen AEM te schrappen en het effect op referenced en verwijzende activa en XFA vormen.
uuid: df522b87-59d8-4678-922d-c9aab82b1381
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: c8519eec-f841-4867-baa9-a9e03042755e
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Formulieren en gerelateerde bronnen verwijderen {#deleting-forms-and-related-resources}

U kunt de formulieren en elementen verwijderen om deze elementen uit de gegevensopslagruimte te verwijderen. De verwijderbewerking werkt op alle elementtypen en mappen.

Als u een element verwijdert uit de instantie Auteur, wordt het element ook verwijderd uit de instantie Publiceren. De AEM Forms-server bestaat uit instanties van Auteurs en Publiceren. De instantie Auteur is bedoeld voor het maken en beheren van formulierelementen en -bronnen. De instantie Publiceren bevat de gepubliceerde formulierelementen en verwante bronnen die beschikbaar zijn voor eindgebruikers.

## Een formulier verwijderen {#how-to-delete-a-form}

1. Meld u aan bij de gebruikersinterface van AEM Forms via `https://[hostname]:'port'/aem/forms.html.`
1. Navigeer naar en selecteer het formulier dat u wilt verwijderen. Klik op ![Aem6forms_delete2](assets/aem6forms_delete2.png) verwijderen op de werkbalk en bevestig de verwijderbewerking.

   >[!NOTE]
   >
   >Er kan slechts één formulier tegelijk worden verwijderd. Verwijder meerdere formulieren afzonderlijk of verwijder de bovenliggende map.

1. Voordat u een element verwijdert, controleert AEM Forms op referenties en vraagt het om een expliciete bevestiging. Klik op Verwijderen forceren als u het element wilt verwijderen, ongeacht de relatiestatus.

   >[!NOTE]
   >
   >Als u een element verwijdert waarnaar wordt verwezen door andere elementen, kunnen er functionele problemen optreden.

   >[!NOTE]
   >
   >Als het geselecteerde element een map is en het element een dergelijk element in de hiërarchie bevat, verwijdert u afzonderlijke elementen of verwijdert u de volledige map.

## Effect van het verwijderen van een XFA-formulier waarnaar wordt verwezen {#impact-of-deleting-a-referenced-xfa-form}

In AEM Forms kan een XFA-formuliersjabloon worden doorgestuurd door een adaptief formulier of een andere XFA-formuliersjabloon. Ook, kan een malplaatje naar een middel of een ander malplaatje verwijzen XFA.

Het is niet raadzaam een XFA-formulier te verwijderen waarnaar wordt verwezen door een adaptief formulier, omdat het het adaptieve formulier kan beschadigen. Wanneer een adaptief formulier verwijst naar een XFA-formulier, zijn de velden gebonden. Na XFA-verwijdering kan het aangepaste formulier zijn velden niet synchroniseren met de XFA-velden en wordt een foutbericht voor dergelijke velden weergegeven. Zie [XFA-formulieren](/help/forms/using/get-xdp-pdf-documents-aem.md#p-updating-referenced-xfa-forms-p)bijwerken voor meer informatie over de gevolgen van XFA-verwijdering waarnaar wordt verwezen en over vieze AF&#39;s.

Als u een dergelijk XFA-formulier wilt verwijderen, werkt u het aangepaste formulier bij en verwijdert u de bindingen met de XFA-velden.
