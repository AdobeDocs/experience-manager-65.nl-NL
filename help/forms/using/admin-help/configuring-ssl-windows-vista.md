---
title: SSL configureren onder Windows Vista
seo-title: SSL configureren onder Windows Vista
description: Leer hoe te om SSL op Windows Vista te vormen.
seo-description: Leer hoe te om SSL op Windows Vista te vormen.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
translation-type: tm+mt
source-git-commit: d3719a9ce2fbb066f99445475af8e1f1e7476f4e
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# SSL configureren op Windows Vista {#configuring-ssl-on-windows-vista}

Om SSL op Windows Vista™ te vormen, hebt u een SSL certificaat met sleutels van RSA voor authentificatie nodig. U kunt het Java-sleutelgereedschap gebruiken om het certificaat te maken.

>[!NOTE]
>
>Windows Vista werkt niet met DSA-toetsen.

U kunt keytool uitvoeren met één opdracht die alle informatie bevat die nodig is om het certificaat en sleutelarchief te maken.

**Een SSL-certificaat maken**

1. In een bevelherinnering, navigeer aan *`[JAVA HOME]`*/bin en typ het volgende bevel om het certificaat en keystore tot stand te brengen:

   `keytool -genkey -keyalg RSA -dname "CN=`*Host* `, OU=`*NameGroup* `, O=`*NameCompany* `,L=`*NameCity* `, S=`** `, C=`*NameStateCountry Code* `" -alias`*&quot;LC Cert&quot;* `-keypass` `key`*_* ** `-keystore`*passwordKeystorename* `.keystore`

   >[!NOTE]
   >
   >Vervang *`[JAVA_HOME]`door de map waarin de JDK is geïnstalleerd en vervang de cursieve tekst door waarden die overeenkomen met uw omgeving.*

1. Typ `changeit` als wachtwoord. Dit wachtwoord is de standaardinstelling voor een Java-installatie en de systeembeheerder kan deze hebben gewijzigd.

