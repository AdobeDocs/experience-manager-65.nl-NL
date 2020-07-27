---
title: Het wachtwoord voor LDAP-binding configureren
seo-title: Het wachtwoord voor LDAP-binding configureren
description: Leer hoe te om het bind wachtwoordgebied te vormen alvorens u het configuratiedossier in een ander systeem invoert.
seo-description: Leer hoe te om het bind wachtwoordgebied te vormen alvorens u het configuratiedossier in een ander systeem invoert.
uuid: 1ab1907c-8b55-4b6f-bd5b-49f22d78b8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 165b3950-b03f-4848-8361-ffb0a26d2658
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 3%

---


# Het wachtwoord voor LDAP-binding configureren{#configure-the-ldap-bind-password}

Om veiligheidsrisico&#39;s te vermijden, bindt het bind wachtwoordgebied in het uitgevoerde configuratiedossier (config.xml) niet wordt gevormd. Alvorens u het configuratiedossier in een ander systeem invoert, zorg ervoor dat u dit wachtwoord vormt. Dit wachtwoord negeert een bestaand wachtwoord dat in het gegevensbestand wordt opgeslagen. Een null-wachtwoord negeert een bestaande wachtwoordwaarde die niet gelijk is aan null.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden importeren en exporteren.
1. Als u de huidige configuratie-instelling naar een bestand wilt exporteren, klikt u op Exporteren en slaat u het configuratiebestand op een andere locatie op.
1. Ga in het bestand naar `Domains` > *[Uw domeinnaam]* > `DirectoryConfigs` > `LDAPGroupConfig` knooppunt. Hier volgt een voorbeeld:

   ```xml
    <node name="LDAPGroupConfig">
        <map>
            <entry key="bindanonymously" value="false" />
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />
            <entry key="batchSize" value="200" />
            <entry key="binduser" value="cn=Directory Manager" />
            <entry key="bindpassword" value="" />
        </map>
   ```

   Typ een waarde voor de wijzigingen `bindpassword` en sla deze op.

1. Ga in het bestand naar `Domains` > *[Uw domeinnaam]* > `DirectoryConfigs` > `LDAPGroupConfig` > `LDAPUserConfig` knooppunt. Hier volgt een voorbeeld:

   ```xml
    <node name="LDAPUserConfig">
        <map>
            <entry key="bindanonymously" value="false" />
            <entry key="batchSize" value="200" />
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />
            <entry key="bindpassword" value="" />
            <entry key="binduser" value="cn=Directory Manager" />
        </map>
   ```

   Typ een waarde voor de wijzigingen `bindpassword` en sla deze op.

1. Als u het bijgewerkte bestand wilt importeren, klikt u in Gebruikersbeheer op Configuratie > Configuratiebestanden importeren en exporteren.
1. Klik op Bladeren om het bestand te zoeken, klik op Importeren en klik vervolgens op OK.

