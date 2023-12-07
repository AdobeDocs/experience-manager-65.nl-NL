---
title: Formulieren en gerelateerde bronnen verwijderen
description: Hoe te om een vorm of een activa in AEM Forms te schrappen en het effect op referenced en verwijzende activa en XFA vormen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
role: Admin
exl-id: b31f9f56-dd33-4478-ad34-01ac7d5a1b40
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Formulieren en gerelateerde bronnen verwijderen {#deleting-forms-and-related-resources}

U kunt de formulieren en elementen verwijderen om deze elementen uit de gegevensopslagruimte te verwijderen. De verwijderbewerking werkt op alle elementtypen en mappen.

Als u een element verwijdert uit de instantie Auteur, wordt het element ook verwijderd uit de instantie Publiceren. AEM Forms-server bestaat uit auteur- en publicatieinstanties. De instantie Auteur is bedoeld voor het maken en beheren van formulieren en bronnen. De instantie Publiceren bevat de gepubliceerde formulierelementen en verwante bronnen die beschikbaar zijn voor eindgebruikers.

## Een formulier verwijderen {#how-to-delete-a-form}

1. Meld u aan bij de gebruikersinterface van AEM Forms via `https://[hostname]:'port'/aem/forms.html.`
1. Navigeer naar en selecteer het formulier dat u wilt verwijderen. Klik op Verwijderen ![aem6forms_delete2](assets/aem6forms_delete2.png) op de werkbalk en bevestig de verwijderingsbewerking.

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

In AEM Forms kan naar een XFA-formuliersjabloon worden verwezen door een adaptief formulier of een andere XFA-formuliersjabloon. Ook, kan een malplaatje naar een middel of een ander malplaatje verwijzen XFA.

Het is niet raadzaam een XFA-formulier te verwijderen waarnaar wordt verwezen door een adaptief formulier, omdat het het adaptieve formulier kan beschadigen. Wanneer een adaptief formulier verwijst naar een XFA-formulier, zijn de velden gebonden. Na XFA-verwijdering kan het aangepaste formulier zijn velden niet synchroniseren met de XFA-velden en wordt een foutbericht voor dergelijke velden weergegeven. Voor meer informatie over het effect van referenced XFA schrapping en over vuile AFs, zie [XFA-formulieren waarnaar wordt verwezen bijwerken](/help/forms/using/get-xdp-pdf-documents-aem.md#p-updating-referenced-xfa-forms-p).

Als u een dergelijk XFA-formulier wilt verwijderen, werkt u het aangepaste formulier bij en verwijdert u de bindingen met de XFA-velden.
