---
title: De volgorde van de evaluatie voor verificatie wijzigen
seo-title: De volgorde van de evaluatie voor verificatie wijzigen
description: U kunt de volgorde wijzigen waarin AEM formulieren meerdere verificatieproviders evalueren.
seo-description: U kunt de volgorde wijzigen waarin AEM formulieren meerdere verificatieproviders evalueren.
uuid: c2693e5b-cf09-4bb8-815a-2b20ebf6eea0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5434df9c-ecf6-450a-aa7e-d9ab69b66fe6
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# De volgorde van de evaluatie voor verificatie wijzigen {#change-the-order-of-evaluation-for-authentication}

Als u meerdere verificatieproviders hebt geconfigureerd, kunt u de volgorde wijzigen waarin AEM formulieren deze evalueren voor verificatie. De orde van de authentificatieleveranciers die in het config.xml- dossier worden vermeld bepaalt de orde van evaluatie voor authentificatie.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden importeren en exporteren.
1. Als u de huidige configuratie-instelling naar een bestand wilt exporteren, klikt u op Exporteren en slaat u het configuratiebestand op een andere locatie op.
1. Zoek het volgende knooppunt in het bestand:

   ```xml
    <node name="AuthSchemes">
        <map />
            <node name="CertificateAuth">
                <map>
                    <entry key="order" value="3" />
                    <entry key="name" value="edc.server.auth.scheme.certificate" />
                </map>
        </node>
        <node name="Kerberos">
            <map>
                <entry key="kerberosSPN" value="defaultSPN" />
                <entry key="order" value="1" />
                <entry key="name" value="edc.server.auth.scheme.kerberos" />
            </map>
    </node>
   ```

   Bewerk in `<entry key="order" value="3" />` de waarde voor elk knooppunt om de volgorde van de verificatiebeoordeling in te stellen.

1. Als u het bijgewerkte bestand wilt importeren, klikt u in Gebruikersbeheer op Configuratie > Configuratiebestanden importeren en exporteren.
1. Klik op Bladeren om het bestand te zoeken, klik op Importeren en klik vervolgens op OK.

