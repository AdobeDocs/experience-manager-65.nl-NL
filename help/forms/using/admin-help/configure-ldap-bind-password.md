---
title: Het LDAP-wachtwoord voor binden configureren
description: Leer hoe te om het bind wachtwoordgebied te vormen alvorens u het configuratiedossier in een ander systeem invoert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: c72794f5-8767-409e-a1df-91a8fdc54d18
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Het LDAP-wachtwoord voor binden configureren{#configure-the-ldap-bind-password}

Om veiligheidsrisico&#39;s te vermijden, bindt het bind wachtwoordgebied in het uitgevoerde configuratiedossier (config.xml) niet wordt gevormd. Alvorens u het configuratiedossier in een ander systeem invoert, zorg ervoor dat u dit wachtwoord vormt. Dit wachtwoord negeert een bestaand wachtwoord dat in het gegevensbestand wordt opgeslagen. Een null-wachtwoord negeert een bestaande wachtwoordwaarde die niet gelijk is aan null.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden importeren en exporteren.
1. Als u de huidige configuratie-instelling naar een bestand wilt exporteren, klikt u op Exporteren en slaat u het configuratiebestand op een andere locatie op.
1. Zoek in het bestand de locatie `Domains` > *[Uw domeinnaam]* > `DirectoryConfigs` > `LDAPGroupConfig` knooppunt. Hier volgt een voorbeeld:

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

   Typ een waarde voor `bindpassword` en sla uw wijzigingen op.

1. Zoek in het bestand de locatie `Domains` > *[Uw domeinnaam]* > `DirectoryConfigs` > `LDAPGroupConfig` > `LDAPUserConfig` knooppunt. Hier volgt een voorbeeld:

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

   Typ een waarde voor `bindpassword` en sla uw wijzigingen op.

1. Als u het bijgewerkte bestand wilt importeren, klikt u in Gebruikersbeheer op Configuratie > Configuratiebestanden importeren en exporteren.
1. Klik op Bladeren om het bestand te zoeken, klik op Importeren en klik vervolgens op OK.
