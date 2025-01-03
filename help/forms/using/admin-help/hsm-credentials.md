---
title: HSM-referenties beheren
description: Leer hoe u HSM-referenties beheert. U kunt HSM beheren via de pagina Betrouwbaarheidswinkelbeheer. U kunt HSM-componenten weergeven, controleren, bijwerken, opnieuw instellen en verwijderen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: facbeab2-de95-4778-894c-faa771d3391e
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '1334'
ht-degree: 0%

---

# HSM-referenties beheren {#managing-hsm-credentials}

Via de pagina Betrouwbaarheidsopslagbeheer kunt u aanmeldingsgegevens voor de Hardware Security Module (HSM) beheren. Een HSM is een derdeapparaat PKCS#11 dat u kunt gebruiken om privé sleutels veilig te produceren en op te slaan. De HSM beschermt fysiek de toegang tot en het gebruik van de persoonlijke sleutels.

De clientsoftware is verplicht te communiceren met de HSM. De HSM-clientsoftware moet op dezelfde computer zijn geïnstalleerd en geconfigureerd als AEM.

AEM formulieren Digitale handtekeningen kunnen referenties gebruiken die op een HSM zijn opgeslagen om digitale handtekeningen op de server toe te passen. Volg de instructies in deze sectie om een alias voor elke HSM-referentie te maken die Digital Signatures zal gebruiken. De alias bevat alle parameters die door de HSM worden vereist.

>[!NOTE]
>
>Nadat u de HSM-configuratie hebt gewijzigd, start u de AEM Forms Server opnieuw.

## Een alias maken voor een HSM-referentie wanneer het HSM-apparaat online is {#create-an-alias-for-an-hsm-credential-when-the-hsm-device-is-online}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > HSM-referenties en klik vervolgens op Toevoegen.
1. Typ in het vak Profielnaam een tekenreeks die wordt gebruikt om de alias te identificeren. Deze waarde wordt gebruikt als een eigenschap voor bepaalde bewerkingen met digitale handtekeningen, zoals de bewerking Handtekeningveld ondertekenen.
1. Typ in het vak PKCS11-bibliotheek het volledig gekwalificeerde pad van de HSM-clientbibliotheek op de server. Bijvoorbeeld `c:\Program Files\LunaSA\cryptoki.dll` . In een gegroepeerde omgeving moet dit pad identiek zijn voor alle servers in de cluster.
1. Klik op HSM-connectiviteit testen. Als AEM formulieren verbinding kunnen maken met het HSM-apparaat, wordt een bericht weergegeven met de mededeling dat de HSM beschikbaar is. Klik op Volgende.
1. Gebruik of de Symbolische Naam, identiteitskaart van de Slot, of Index van de Lijst van de Slot om te identificeren waar de geloofsbrieven op HSM worden opgeslagen.

   * **Symbolische Naam:** beantwoordt aan de naam van de te gebruiken verdeling HSM (bijvoorbeeld, HSMPART1).
   * **Identiteitskaart van de Slot:** identiteitskaart van de Slot is een groef herkenningsteken van type lang gegevenstype.
   * **de Index van de Lijst van de Slot:** als u de Index van de Lijst van de Slot selecteert, plaats Info van de Slot aan een geheel dat aan de groef beantwoordt. Dit is een op 0-gebaseerde index, zo betekent het dat als de cliënt met de verdeling HSMPART1 eerst wordt geregistreerd, HSMPART1 zal worden doorverwezen naar het gebruiken van waarde SlotListIndex 0.

1. Typ in het vak Symbolische punt het wachtwoord dat is vereist voor toegang tot de HSM-toets en klik op Volgende.
1. Selecteer een referentie in het vak Referenties. Klik op Opslaan.

## Een alias maken voor een HSM-referentie wanneer het HSM-apparaat offline is {#create-an-alias-for-an-hsm-credential-when-the-hsm-device-is-offline}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > HSM-referenties en klik vervolgens op Toevoegen.
1. Typ in het vak Profielnaam een tekenreeks die wordt gebruikt om de alias te identificeren. Deze waarde wordt gebruikt als een eigenschap voor bepaalde bewerkingen met digitale handtekeningen, zoals de bewerking Handtekeningveld ondertekenen.
1. Typ in het vak PKCS11-bibliotheek het volledig gekwalificeerde pad van de HSM-clientbibliotheek op de server. Bijvoorbeeld `c:\Program Files\LunaSA\cryptoki.dll` . In een gegroepeerde omgeving moet dit pad identiek zijn voor alle servers in de cluster.
1. Schakel het selectievakje Offline profiel maken in. Klik op Volgende.
1. Selecteer in de lijst HSM-apparaat de fabrikant van het HSM-apparaat waar de referentie is opgeslagen.
1. Selecteer in de lijst Slot-type de optie Groef-id, Slot-index of Token-naam en geef een waarde op in het vak Slot-info. AEM formulieren gebruiken deze instellingen om te bepalen waar de referenties op de HSM worden opgeslagen.

   * **Symbolische Naam:** beantwoordt aan een verdelingsnaam (bijvoorbeeld, HSMPART1).
   * **identiteitskaart van de Slot:** identiteitskaart van de Slot is een geheel dat aan de groef beantwoordt, die beurtelings aan een verdeling beantwoordt. Bijvoorbeeld, de cliënt (de Server van Forms) die met de verdeling HSMPART1 eerst wordt geregistreerd. Dit brengt groef 1 aan de verdeling HSMPART1, voor deze cliënt in kaart. Omdat HSMPART1 de eerste geregistreerde verdeling is, is identiteitskaart van de Slot 1 en u zou Informatie van de Slot aan 1 plaatsen.

     De groef ID wordt geplaatst op een cliënt-door-cliënt basis. Als u een tweede machine aan een verschillende verdeling (bijvoorbeeld, HSMPART2 op het zelfde apparaat HSM) registreerde, dan zou groef 1 met de verdeling HSMPART2 voor die cliënt worden geassocieerd.

   * **Index van de Slot:** als u de Index van de Slot selecteert, plaats Info van de Slot aan een geheel dat aan de groef beantwoordt. Dit is een op 0 gebaseerde index, zo betekent het dat als de cliënt met de verdeling HSMPART1 eerst wordt geregistreerd, groef 1 aan HSMPART1 voor deze cliënt in kaart wordt gebracht. Omdat HSMPART1 de eerste geregistreerde verdeling is, is de Index van de Slot 0.

1. Selecteer een van deze opties en geef het pad op:

   * **Certificaat**: (Niet vereist als het gebruiken van SHA1) klik doorbladert en van de weg naar de openbare sleutel voor de referentie de plaats bepalen u gebruikt.
   * **Certificaat SHA1:** (Niet vereist als het gebruiken van een fysiek certificaat) waarde SHA1 van het Type (duimdruk) van het openbare zeer belangrijke (.cer) dossier voor referentie u gebruikt. Zorg ervoor dat er geen spaties worden gebruikt in de SHA1-waarde.

1. Typ in het vak Wachtwoord het wachtwoord dat is vereist voor toegang tot de HSM-sleutel voor de opgegeven sleufgegevens en klik op Opslaan.

## Eigenschappen van HSM-referentie weergeven {#view-hsm-credential-alias-properties}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidswinkelbeheer > HSM-referenties.
1. Klik op de aliasnaam van de referentie-alias om de eigenschappen weer te geven en klik vervolgens op OK.

## Controleer de status van een HSM-referentie {#check-the-status-of-an-hsm-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidswinkelbeheer > HSM-referenties.
1. Klik op het selectievakje naast de referentie die u wilt controleren en klik op Status controleren.

De kolom Status geeft de huidige status van de referentie aan. Als er een fout optreedt, wordt een rode X weergegeven in de kolom Status. Houd de muis boven de X om knopinfo weer te geven die de oorzaak van de fout bevat.

## Eigenschappen van HSM-referentie-aliassen bijwerken {#update-hsm-credential-alias-properties}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidswinkelbeheer > HSM-referenties.
1. Klik op de aliasnaam van de referentie-alias.
1. Klik op Referentie bijwerken en werk de instellingen naar wens bij.

## Alle HSM-verbindingen herstellen {#reset-all-hsm-connections}

Herstel de open verbindingen aan een apparaat HSM na om het even welke verstoring aan de netwerkzitting tussen de Server van Forms en het apparaat HSM. Bijvoorbeeld, kunnen de onderbrekingen gebeuren toe te schrijven aan een netwerkstroomonderbreking of het apparaat HSM dat offline voor een softwareupdate wordt genomen. Na een onderbreking, zijn de bestaande verbindingen stabiel en om het even welke ondertekenende verzoeken tegen die verbindingen ontbreken. Met de optie Alle HSM-verbindingen herstellen wist u de oude verbindingen.

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidswinkelbeheer > HSM-referenties.
1. Klik op Alle HSM-verbindingen herstellen.

## Een HSM-referentie-alias verwijderen {#delete-an-hsm-credential-alias}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidswinkelbeheer > HSM-referenties.
1. Selecteer de controledozen voor de geloofsbrieven HSM u wilt schrappen, Schrapping klikken, en dan O.K. klikken.

## Externe HSM-ondersteuning configureren {#configure-remote-hsm-support}

AEM vormen gebruiken een Web op diensten-Gebaseerd mechanisme IPC/RPC. Met dit mechanisme kunnen AEM formulieren een HSM gebruiken die op een externe computer is geïnstalleerd. Als u deze functionaliteit wilt gebruiken, installeert u de webservice op de externe computer waarop de HSM is geïnstalleerd. Zie [ Vormend steun HSM voor AEM vormen ES gebruikend Zon JDK op Vensters platform met 64 bits ](https://kb2.adobe.com/cps/808/cpsid_80835.html) voor meer informatie.

Dit mechanisme ondersteunt het online maken van HSM-profielen of statuscontroles niet. Er zijn echter twee manieren om HSM-profielen te maken en statuscontroles uit te voeren:

* Maak een clientreferentie voor AEM formulieren door deze door te geven in het certificaat van de ondertekenaar. Volg de stappen in [ Vormend steun HSM voor AEM vormen ES gebruikend Zon JDK op het platform met 64 bits van Vensters ](https://kb2.adobe.com/cps/808/cpsid_80835.html). De locatie van de webservice wordt doorgegeven als een referentie-eigenschap. Offline HSM-profielen die zijn gemaakt met behulp van certificaatmodule of SHA-1-hexadecimale certificaat worden ook ondersteund. Als u echter een upgrade hebt uitgevoerd naar AEM formulieren uit een eerdere versie van AEM formulieren, brengt u wijzigingen aan op de client omdat de referentie gegevens van het certificaat en de webservice heeft meegevoerd.
* De plaats van de Dienst van het Web wordt gespecificeerd in de beleidsconsole voor de dienst van de Handtekening. (Zie [ de dienstmontages van de Handtekening ](/help/forms/using/admin-help/configure-service-settings.md#signature-service-settings).) hier, droeg de cliënt slechts alias van het profiel HSM in de vertrouwensopslag. U kunt deze optie naadloos gebruiken zonder wijzigingen op de client, zelfs als u een upgrade hebt uitgevoerd naar AEM formulieren van een eerdere versie van AEM formulieren. Deze optie ondersteunt geen HSM-profielen die gebruikmaken van certificaat SHA-1.
