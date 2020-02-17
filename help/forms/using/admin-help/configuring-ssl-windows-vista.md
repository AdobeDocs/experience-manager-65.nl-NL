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

---


# SSL configureren onder Windows Vista {#configuring-ssl-on-windows-vista}

Om SSL op Windows Vista™ te vormen, hebt u een SSL certificaat met sleutels van RSA voor authentificatie nodig. U kunt het Java-sleutelgereedschap gebruiken om het certificaat te maken.

>[!NOTE]
>
>Windows Vista werkt niet met DSA-toetsen.

U kunt keytool uitvoeren met één opdracht die alle informatie bevat die nodig is om het certificaat en sleutelarchief te maken.

**Een SSL-certificaat maken**

1. Navigeer naar *`[JAVA HOME]`*/bin in een opdrachtprompt en typ de volgende opdracht om het certificaat en sleutelarchief te maken:

   `keytool -genkey -keyalg RSA -dname "CN=`*Hostnaam *`, OU=`*Groepsnaam* `, O=`*bedrijfsnaam *`,L=`*City Name* `, S=`*State *`, C=`** `" -alias`**`-keypass``key`** ** `-keystore`**country code&quot;LC Cert&quot;_wachtwoordkeystorename`.keystore`

   >[!NOTE]
   >
   >Vervang deze door de map waarin de JDK is geïnstalleerd en vervang de cursieve tekst door waarden die overeenkomen met de omgeving. *`[JAVA_HOME]`*

1. Typ `changeit` het wachtwoord. Dit wachtwoord is de standaardinstelling voor een Java-installatie en de systeembeheerder kan deze hebben gewijzigd.

