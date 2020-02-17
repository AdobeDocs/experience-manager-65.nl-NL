---
title: HSM-referenties beheren
seo-title: HSM-referenties beheren
description: Leer hoe u HSM-referenties beheert.
seo-description: Leer hoe u HSM-referenties beheert.
uuid: 30ddcd4a-f771-44d5-bdef-4826adcd0c44
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e5f17ba8-8aab-4449-811a-20ad33de1c6f
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# HSM-referenties beheren {#managing-hsm-credentials}

Via de pagina Betrouwbaarheidsopslagbeheer kunt u aanmeldingsgegevens voor de Hardware Security Module (HSM) beheren. Een HSM is een derdeapparaat PKCS#11 dat u kunt gebruiken om privé sleutels veilig te produceren en op te slaan. De HSM beschermt fysiek de toegang tot en het gebruik van de persoonlijke sleutels.

De clientsoftware is verplicht te communiceren met de HSM. De HSM-clientsoftware moet op dezelfde computer zijn geïnstalleerd en geconfigureerd als AEM-formulieren.

AEM-formulieren Digitale handtekeningen kunnen referenties gebruiken die zijn opgeslagen op een HSM om digitale handtekeningen op de server toe te passen. Volg de instructies in deze sectie om een alias voor elke HSM-referentie te maken die Digital Signatures zal gebruiken. De alias bevat alle parameters die door de HSM worden vereist.

>[!NOTE]
>
>Nadat u de HSM-configuratie hebt gewijzigd, start u de AEM-formulierserver opnieuw.

## Een alias maken voor een HSM-referentie wanneer het HSM-apparaat online is {#create-an-alias-for-an-hsm-credential-when-the-hsm-device-is-online}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > HSM-referenties en klik vervolgens op Toevoegen.
1. Typ in het vak Profielnaam een tekenreeks die wordt gebruikt om de alias aan te duiden. Deze waarde wordt gebruikt als een eigenschap voor bepaalde bewerkingen met digitale handtekeningen, zoals de bewerking Handtekeningveld ondertekenen.
1. Typ in het vak PKCS11-bibliotheek het volledig gekwalificeerde pad van uw HSM-clientbibliotheek op de server. Bijvoorbeeld, `c:\Program Files\LunaSA\cryptoki.dll`. In een gegroepeerde omgeving moet dit pad identiek zijn voor alle servers in de cluster.
1. Klik op HSM-connectiviteit testen. Als AEM-formulieren verbinding kunnen maken met het HSM-apparaat, wordt een bericht weergegeven met de mededeling dat de HSM beschikbaar is. Klik op Volgende.
1. Gebruik of de Symbolische Naam, identiteitskaart van de Slot, of Index van de Lijst van de Slot om te identificeren waar de geloofsbrieven op HSM worden opgeslagen.

   * **** Tokennaam: Komt overeen met de naam van de te gebruiken HSM-partitie (bijvoorbeeld HSMPART1).
   * **** Groef-id: De sleuf-id is een sleuf-id van het gegevenstype long.
   * **** Slot List Index: Als u Slot List Index selecteert, stelt u Slot Info in op een geheel getal dat overeenkomt met de sleuf. Dit is een op 0-gebaseerde index, zo betekent het dat als de cliënt met de verdeling HSMPART1 eerst wordt geregistreerd, HSMPART1 zal worden doorverwezen naar het gebruiken van waarde SlotListIndex 0.

1. Typ in het vak Symbolische punt het wachtwoord dat is vereist voor toegang tot de HSM-toets en klik op Volgende.
1. Selecteer een referentie in het vak Referenties. Klik op Opslaan.

## Een alias maken voor een HSM-referentie wanneer het HSM-apparaat offline is {#create-an-alias-for-an-hsm-credential-when-the-hsm-device-is-offline}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > HSM-referenties en klik vervolgens op Toevoegen.
1. Typ in het vak Profielnaam een tekenreeks die wordt gebruikt om de alias aan te duiden. Deze waarde wordt gebruikt als een eigenschap voor bepaalde bewerkingen met digitale handtekeningen, zoals de bewerking Handtekeningveld ondertekenen.
1. Typ in het vak PKCS11-bibliotheek het volledig gekwalificeerde pad van uw HSM-clientbibliotheek op de server. Bijvoorbeeld, `c:\Program Files\LunaSA\cryptoki.dll`. In een gegroepeerde omgeving moet dit pad identiek zijn voor alle servers in de cluster.
1. Schakel het selectievakje Offline profiel maken in. Klik op Volgende.
1. Selecteer in de lijst HSM-apparaat de fabrikant van het HSM-apparaat waar de referentie is opgeslagen.
1. Selecteer in de lijst Slot-type de optie Groef-id, Slot-index of Token-naam en geef een waarde op in het vak Slot-info. AEM-formulieren gebruiken deze instellingen om te bepalen waar de referenties worden opgeslagen op de HSM.

   * **** Tokennaam: Komt overeen met een verdelingsnaam (bijvoorbeeld, HSMPART1).
   * **** Groef-id: De sleuf-id is een geheel getal dat overeenkomt met de sleuf en dat op zijn beurt weer overeenkomt met een partitie. De client (formulierserver) is bijvoorbeeld eerst geregistreerd bij de HSMPART1-partitie. Dit brengt groef 1 aan de verdeling HSMPART1, voor deze cliënt in kaart. Omdat HSMPART1 de eerste geregistreerde verdeling is, is identiteitskaart van de Slot 1 en u zou Informatie van de Slot aan 1 plaatsen.

      De sleuf-id wordt per client ingesteld. Als u een tweede machine aan een verschillende verdeling (bijvoorbeeld, HSMPART2 op het zelfde apparaat HSM) registreerde, dan zou groef 1 met de verdeling HSMPART2 voor die cliënt worden geassocieerd.

   * **** Slot-index: Als u Slot Index selecteert, plaats de Info van de Slot aan een geheel dat aan de groef beantwoordt. Dit is een op 0 gebaseerde index, zo betekent het dat als de cliënt met de verdeling HSMPART1 eerst wordt geregistreerd, groef 1 aan HSMPART1 voor deze cliënt in kaart wordt gebracht. Omdat HSMPART1 de eerste geregistreerde verdeling is, is de Index van de Slot 0.

1. Selecteer een van deze opties en geef het pad op:

   * **Certificaat**: (Niet vereist als het gebruiken van SHA1) klik doorbladeren en van de weg naar de openbare sleutel voor de referentie de plaats bepalen u gebruikt.
   * **** Certificaat SHA1: (Niet vereist als u een fysiek certificaat gebruikt) Typ SHA1-waarde (miniafdruk) van het bestand met de openbare sleutel (.cer) voor de referentie die u gebruikt. Zorg ervoor dat er geen spaties worden gebruikt in de SHA1-waarde.

1. Typ in het vak Wachtwoord het wachtwoord dat is vereist voor toegang tot de HSM-sleutel voor de opgegeven sleufgegevens en klik op Opslaan.

## Eigenschappen van HSM-referentie voor aliassen weergeven {#view-hsm-credential-alias-properties}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidswinkelbeheer > HSM-referenties.
1. Klik op de aliasnaam van de referentie-alias om de eigenschappen weer te geven en klik vervolgens op OK.

## Controleer de status van een HSM-referentie {#check-the-status-of-an-hsm-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidswinkelbeheer > HSM-referenties.
1. Klik op het selectievakje naast de referentie die u wilt controleren en klik op Status controleren.

De kolom Status geeft de huidige status van de referentie aan. Bij een fout wordt een rode X weergegeven in de kolom Status. Houd de muis boven de X om knopinfo weer te geven die de oorzaak van de fout bevat.

## Eigenschappen van HSM-referentie-aliassen bijwerken {#update-hsm-credential-alias-properties}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidswinkelbeheer > HSM-referenties.
1. Klik op de aliasnaam van de referentie-alias.
1. Klik op Referentie bijwerken en werk de instellingen naar wens bij.

## Alle HSM-verbindingen herstellen {#reset-all-hsm-connections}

Herstel de open verbindingen aan een apparaat HSM na om het even welke verstoring aan de netwerkzitting tussen de vormenserver en het apparaat HSM. Bijvoorbeeld, kunnen de onderbrekingen gebeuren toe te schrijven aan een netwerkstroomonderbreking of het apparaat HSM dat offline voor een softwareupdate wordt genomen. Na een onderbreking, zijn de bestaande verbindingen stabiel en om het even welke ondertekenende verzoeken tegen die verbindingen ontbreken. Met de optie Alle HSM-verbindingen herstellen wist u de oude verbindingen.

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidswinkelbeheer > HSM-referenties.
1. Klik op Alle HSM-verbindingen herstellen.

## Een HSM-referentie-alias verwijderen {#delete-an-hsm-credential-alias}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidswinkelbeheer > HSM-referenties.
1. Selecteer de controledozen voor de geloofsbrieven HSM u wilt schrappen, Schrapping klikken, en dan O.K. klikken.

## Externe HSM-ondersteuning configureren {#configure-remote-hsm-support}

AEM-formulieren gebruiken een op webservices gebaseerd IPC/RPC-mechanisme. Met dit mechanisme kunnen AEM-formulieren een HSM gebruiken die op een externe computer is geïnstalleerd. Als u deze functionaliteit wilt gebruiken, installeert u de webservice op de externe computer waarop de HSM is geïnstalleerd. Zie het [Vormen steun HSM voor AEM vormen ES gebruikend Zon JDK op Vensters met 64 bits](https://kb2.adobe.com/cps/808/cpsid_80835.html)platform voor meer informatie.

Dit mechanisme ondersteunt het online maken van HSM-profielen of statuscontroles niet. Er zijn echter twee manieren om HSM-profielen te maken en statuscontroles uit te voeren:

* Maak een clientreferentie voor AEM-formulieren door deze door te geven in het certificaat van de ondertekenaar. Volg de stappen in het [Vormen van steun HSM voor vormen ES AEM gebruikend Zon JDK op het platform](https://kb2.adobe.com/cps/808/cpsid_80835.html)met 64 bits van Vensters. De locatie van de webservice wordt doorgegeven als een referentie-eigenschap. Offline HSM-profielen die zijn gemaakt met behulp van certificaatmodule of SHA-1-hexadecimale certificaat worden ook ondersteund. Als u echter een upgrade naar AEM-formulieren hebt uitgevoerd vanaf een eerdere versie van AEM-formulieren, brengt u wijzigingen aan op de client, omdat de referentie gegevens van het certificaat en de webservice bevat.
* De plaats van de Dienst van het Web wordt gespecificeerd in de beleidsconsole voor de dienst van de Handtekening. (Zie Instellingen [van de](/help/forms/using/admin-help/configure-service-settings.md#signature-service-settings)handtekeningenservice.) Hier droeg de client alleen de alias van het HSM-profiel in de vertrouwde opslag. U kunt deze optie naadloos gebruiken zonder wijzigingen op de client, zelfs als u een upgrade naar AEM-formulieren hebt uitgevoerd vanaf een eerdere versie van AEM-formulieren. Deze optie ondersteunt geen HSM-profielen die gebruikmaken van certificaat SHA-1.

