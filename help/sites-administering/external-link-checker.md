---
title: De externe koppelingencontrole
seo-title: De externe koppelingencontrole
description: Meer informatie over de External Link Checker in AEM.
seo-description: Meer informatie over de External Link Checker in AEM.
uuid: 09160594-e45f-4604-8b36-f14b148b9f63
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: d1ccd194-8549-4188-8932-7136be1e88a2
docset: aem65
translation-type: tm+mt
source-git-commit: 0a94bf49a7136c5831c42eb274d07517c12014ec

---


# De externe koppelingencontrole{#the-external-link-checker}

Een externe koppelingencontrole wordt verstrekt binnen AEM. De koppelingencontrole:

* scant alle inhoudspagina&#39;s
* genereert een lijst met alle geldige en ongeldige koppelingen
* Hiermee worden ongeldige koppelingen op de afzonderlijke inhoudspagina&#39;s gemarkeerd als verbroken

## Externe koppelingen valideren {#how-to-validate-external-links}

De externe koppelingencontrole gebruiken:

1. Gebruikend **Navigatie**, uitgezochte **Hulpmiddelen**, dan **Plaatsen**.
1. Selecteer **Externe koppelingencontrole**. Er wordt een lijst met alle externe koppelingen gegenereerd.
1. Valideer een specifieke koppeling door deze te selecteren in de lijst en vervolgens te klikken op **Controleren**:

   ![](assets/telc-01.png)

   Informatie wordt weergegeven:

   * **Status** van de koppeling
   * **URL**
   * **Referenter**
   * tijd sinds de koppeling voor het **laatst is gecontroleerd** (gevalideerd)
   * De **laatste status** die is geretourneerd

   * tijd sinds de koppeling voor het **laatst beschikbaar was**
   * tijd sinds de koppeling voor **laatst geopend is**

1. Ongeldige koppelingen op de afzonderlijke inhoudspagina&#39;s worden weergegeven als verbroken:

   ![](assets/chlimage_1-143.png)