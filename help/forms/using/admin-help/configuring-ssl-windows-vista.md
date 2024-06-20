---
title: SSL configureren onder Windows Vista
description: Leer hoe te om SSL op Windows Vista te vormen. Gebruik en voer het Java Keytool uit om het SSL-certificaat te genereren met RSA-sleutels voor de verificatie.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 36c4300d-7a44-41f4-b294-06f32bb01686
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# SSL configureren onder Windows Vista {#configuring-ssl-on-windows-vista}

Om SSL op Windows Vista™ te vormen, hebt u een SSL certificaat met sleutels van RSA voor authentificatie nodig. U kunt het Java-sleutelgereedschap gebruiken om het certificaat te maken.

>[!NOTE]
>
>Windows Vista werkt niet met DSA-toetsen.

U kunt keytool uitvoeren met één opdracht die alle informatie bevat die nodig is om het certificaat en sleutelarchief te maken.

**Een SSL-certificaat maken**

1. Navigeer naar een opdrachtprompt *`[JAVA HOME]`*/bin en typ de volgende opdracht om het certificaat en sleutelarchief te maken:

   `keytool -genkey -keyalg RSA -dname "CN=`*Hostnaam* `, OU=`*Groepsnaam* `, O=`*Bedrijfsnaam* `,L=`*Plaats* `, S=`*Staat* `, C=`*Landcode* `" -alias`*&quot;LC Cert&quot;* `-keypass` `key`*_* *password* `-keystore`*sleutelbestandsnaam* `.keystore`

   >[!NOTE]
   >
   >Vervangen *`[JAVA_HOME]`met de directory waarin de JDK is geïnstalleerd, en vervangt u de cursieve tekst door waarden die overeenkomen met uw omgeving.*

1. Type `changeit` als het wachtwoord. Dit wachtwoord is de standaardinstelling voor een Java-installatie en de systeembeheerder kan deze hebben gewijzigd.
