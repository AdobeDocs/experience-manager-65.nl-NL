---
title: '"DB2-database: Een proces wekelijks uitvoeren"'
seo-title: '"DB2-database: Een proces wekelijks uitvoeren"'
description: Zie hoe u de prestaties van uw AEM formulieren DB2-database kunt verbeteren.
seo-description: Zie hoe u de prestaties van uw AEM formulieren DB2-database kunt verbeteren.
uuid: 36070087-c250-41df-a841-aa922e777697
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: fc0e8183-5d50-4fc0-997a-5f3168ba0d70
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# DB2-database: Een proces wekelijks uitvoeren{#db-database-running-a-process-weekly}

Als de database van AEM-formulieren DB2 langzaam begint te lopen, kunt u de prestaties verbeteren door het volgende proces wekelijks uit te voeren:

1. Start DB2 Control Center:

   (Windows) Selecteer Start > Programma&#39;s > IBM DB2 > Algemene beheertools > Control Center.

   (Linux en UNIX) Typ de `db2jcc` opdracht bij een opdrachtprompt.

1. Klik in de objectstructuur van het DB2 Control Center op Alle databases.
1. Klik op de database die u voor AEM-formulieren hebt gemaakt en klik op de map Tables.
1. Selecteer alle gegevensbestandlijsten in de inhoudruit, klik hen met de rechtermuisknop aan en selecteer de Statistieken van de Looppas.
1. Ga naar Statistieken > Indexstatistieken.
1. Selecteer Statistieken verzamelen voor alle indexen, selecteer Statistieken verzamelen voor indexen met Uitgebreide Gedetailleerde Statistieken, en klik dan O.K.

Er verschijnt een bericht wanneer het proces is voltooid. Sluit het bericht.
