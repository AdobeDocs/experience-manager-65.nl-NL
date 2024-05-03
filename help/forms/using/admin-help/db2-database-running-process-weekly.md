---
title: "DB2&reg; database: een proces wekelijks uitvoeren"
description: Leer hoe u de prestaties van uw AEM Forms DB2&reg; database kunt verbeteren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: ca2cfe35-b602-4ef8-b4e3-af846105d4de
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# DB2®-database: wekelijks een proces uitvoeren{#db-database-running-a-process-weekly}

Als uw AEM Forms DB2®-database langzaam begint te werken, kunt u de prestaties verbeteren door het volgende proces wekelijks uit te voeren:

1. Start DB2® Control Center:

   (Windows) Selecteer Start > Programma&#39;s > IBM® DB2® > Algemene beheertools > Control Center.

   (Linux® en UNIX®) Typ de opdracht `db2jcc` gebruiken.

1. Klik in de objectstructuur van het DB2® Control Center op Alle databases.
1. Klik op de database die u voor AEM Forms hebt gemaakt en klik op de map Tables.
1. Selecteer alle databasetabellen in het inhoudsvenster, klik met de rechtermuisknop op de tabellen en selecteer vervolgens Statistieken uitvoeren.
1. Ga naar Statistieken > Indexstatistieken.
1. Selecteer Statistieken verzamelen voor alle indexen, selecteer Statistieken verzamelen voor indexen met uitgebreide Gedetailleerde Statistieken, en klik dan O.K.

Er verschijnt een bericht wanneer het proces is voltooid. Sluit het bericht.
