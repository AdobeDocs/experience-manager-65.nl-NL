---
title: SSL configureren onder Windows Vista
seo-title: Configuring SSL on Windows Vista
description: Leer hoe te om SSL op Windows Vista te vormen.
seo-description: Learn how to configure SSL on Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 36c4300d-7a44-41f4-b294-06f32bb01686
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# SSL configureren onder Windows Vista {#configuring-ssl-on-windows-vista}

Om SSL op Windows Vista™ te vormen, hebt u een SSL certificaat met sleutels van RSA voor authentificatie nodig. U kunt het Java-sleutelgereedschap gebruiken om het certificaat te maken.

>[!NOTE]
>
>Windows Vista werkt niet met DSA-toetsen.

U kunt keytool uitvoeren met één opdracht die alle informatie bevat die nodig is om het certificaat en sleutelarchief te maken.

**Een SSL-certificaat maken**

1. In een bevelherinnering, navigeer aan *`[JAVA HOME]`*/bin en typ de volgende opdracht om het certificaat en sleutelarchief te maken:

   `keytool -genkey -keyalg RSA -dname "CN=`*Hostnaam* `, OU=`*Groepsnaam* `, O=`*Bedrijfsnaam* `,L=`*Plaats* `, S=`*Staat* `, C=`*Landcode* `" -alias`*&quot;LC Cert&quot;* `-keypass` `key`*_* *password* `-keystore`*sleutelbestandsnaam* `.keystore`

   >[!NOTE]
   >
   >Vervangen *`[JAVA_HOME]`met de directory waarin de JDK is geïnstalleerd, en vervangt u de cursieve tekst door waarden die overeenkomen met uw omgeving.*

1. Type `changeit` als het wachtwoord. Dit wachtwoord is de standaardinstelling voor een Java-installatie en de systeembeheerder kan deze hebben gewijzigd.
