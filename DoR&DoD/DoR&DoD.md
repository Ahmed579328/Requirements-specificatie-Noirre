# User Stories – Mobiele Applicatie voor The Chocolate Firm

## Definition of Ready (DoR)

Een user story mag pas de sprint in als aan **alle** onderstaande criteria is voldaan:

1. De user story is geschreven in het standaardformaat: *"Als [rol] wil ik [functionaliteit] zodat [waarde]."*
2. De acceptatiecriteria zijn concreet en toetsbaar geformuleerd (SMART).
3. De story is besproken met en begrepen door het hele team (refinement is gedaan).
4. De benodigde systeemkoppelingen zijn geïdentificeerd (bijv. welke Odoo-modules, CMS of externe diensten nodig zijn).
5. Afhankelijkheden met andere stories of systemen (Odoo ERP/CRM, BI-tool, notificatieservice) zijn in kaart gebracht en geborgd.
6. De story is ingeschat door het team (story points).
7. De story is klein genoeg om binnen één sprint af te ronden.
8. Eventueel benodigde wireframes, mock-ups of UX-definities zijn beschikbaar.
9. De betrokken stakeholder of product owner is beschikbaar voor vragen tijdens de sprint.

---

## Definition of Done (DoD)

Een user story is pas "Done" als aan **alle** onderstaande criteria is voldaan:

1. De functionaliteit voldoet aan alle geformuleerde acceptatiecriteria.
2. De code/configuratie is gereviewd door minimaal één ander teamlid (peer review).
3. De koppeling met het juiste bronsysteem (Odoo ERP, CRM, CMS of externe API) is werkend en gevalideerd op correctheid.
4. De functionaliteit is getest op zowel iOS als Android in de afgesproken testomgeving.
5. De oplossing is getest door een eindgebruiker (klant of medewerker van de betreffende afdeling).
6. Notificaties, koppelingen en berekeningen zijn uniform en komen overeen met de afgestemde definities.
7. De documentatie in GitHub (Markdown) is bijgewerkt: technische beschrijving, gebruikte koppelingen en eventuele configuratiestappen.
8. De oplossing werkt in de afgesproken omgeving (test- of acceptatieomgeving).
9. Eventuele bekende beperkingen of bugs zijn gedocumenteerd in de backlog.
10. De product owner heeft de story geaccepteerd na een demo.

---

## Story Point Referentie

| Punten | Omvang | Voorbeeld |
|--------|--------|-----------|
| 1–2    | Zeer klein, minimale complexiteit | Tekstaanpassing, notificatiefilter toevoegen |
| 3      | Klein, weinig onzekerheid | Eenvoudige productkaartweergave |
| 5      | Gemiddeld, bekende techniek | Scherm met één systeemkoppeling (ERP of CMS) |
| 8      | Groot, meerdere koppelingen of complexe logica | Productregistratie met QR-scan en dashboardkoppeling |
| 13     | Zeer groot, veel afhankelijkheden | Overkoepelende functionaliteit met meerdere systeemintegraties |

---

## User Stories

### Productregistratie & Dashboard

#### US-01 | Productregistratie via QR-code of batchnummer

> *Als klant wil ik mijn aangekochte chocoladeproducten registreren via een QR-code of batchnummer, zodat ik een persoonlijk overzicht heb van al mijn producten.*

**Acceptatiecriteria:**

- De klant kan een product registreren door een QR-code te scannen of handmatig een batchnummer, productcode of kassabon in te voeren.
- Na registratie verschijnt het product direct in het persoonlijk dashboard met aankoopdatum, houdbaarheid, allergeneninformatie, herkomst van de cacao, productspecificaties en certificeringen (bijv. Fairtrade of Rainforest Alliance).
- De registratie is gekoppeld aan Odoo ERP voor productvalidatie.
- De flow werkt op zowel iOS als Android.

**Databronnen:** Odoo ERP, mobiel platform
**Inschatting:** 8 story points

---

#### US-02 | Persoonlijk productdashboard

> *Als klant wil ik een overzicht zien van al mijn geregistreerde producten inclusief productdetails, zodat ik altijd actuele informatie over mijn aankopen bij de hand heb.*

**Acceptatiecriteria:**

- Het dashboard toont per geregistreerd product: aankoopdatum, houdbaarheid, allergeneninformatie, herkomst van de cacao, productspecificaties en certificeringen.
- Het dashboard laadt binnen 3 seconden bij een lijst van minimaal 50 producten.
- De klant kan producten filteren op categorie of aankoopdatum.
- Data wordt opgehaald uit Odoo ERP op basis van de productregistratie.

**Databronnen:** Odoo ERP
**Inschatting:** 5 story points

---

### Notificaties

#### US-03 | Automatische houdbaarheidsmeldingen

> *Als klant wil ik een pushnotificatie ontvangen wanneer een geregistreerd product bijna over de datum raakt, zodat ik geen product ongemerkt laat verlopen.*

**Acceptatiecriteria:**

- De app stuurt een pushnotificatie 7 dagen en 1 dag voor de houdbaarheidsdatum van een geregistreerd product.
- De notificatie bevat de productnaam en de exacte houdbaarheidsdatum.
- De klant kan notificatievoorkeuren instellen per productcategorie (aan/uit).
- Notificaties worden verstuurd ongeacht of de app op dat moment actief is.

**Databronnen:** Odoo ERP, notificatieservice
**Inschatting:** 5 story points

---

#### US-04 | Notificaties nieuwe producten en seizoensreleases

> *Als klant wil ik een melding ontvangen wanneer nieuwe smaakvarianten, limited editions of seizoensproducten beschikbaar komen, zodat ik als eerste op de hoogte ben.*

**Acceptatiecriteria:**

- De app stuurt een pushnotificatie bij nieuwe productreleases, inclusief ingrediënten, cacaopercentage, sensorische beschrijving en allergeneninformatie.
- B2B-klanten ontvangen aanvullend notificaties over wijzigingen in levertijden, voorraadstatus en productieplanning.
- De klant kan notificatievoorkeuren instellen per type (bijv. "alleen seizoenspakketten" of "alleen nieuwe smaken").
- De klant kan niet-storen periodes instellen voor notificaties.
- Notificaties zijn gekoppeld aan Odoo ERP voor actuele productdata.

**Databronnen:** Odoo ERP, notificatieservice
**Inschatting:** 5 story points

---

### Productinformatie & Content

#### US-05 | Digitale productkaarten en contentbibliotheek

> *Als klant wil ik digitale productkaarten en interactieve content kunnen raadplegen, zodat ik meer informatie heb over mijn chocoladeaankopen en nieuwe recepten kan ontdekken.*

**Acceptatiecriteria:**

- Per geregistreerd product is een digitale productkaart beschikbaar met specificaties, allergenen, herkomst en certificeringen.
- De bibliotheek bevat minimaal: interactieve tutorials, video's over chocoladeproductie ("van boon tot reep") en stap-voor-stap recepten.
- Alle video's zijn voorzien van ondertiteling.
- Content is beschikbaar in Nederlands, Engels, Frans en Duits en wordt gelokaliseerd per regio.
- De content wordt regelmatig bijgewerkt met nieuwe recepten, productreleases en achtergrondverhalen vanuit plantages en fabrieken.

**Databronnen:** CMS, Odoo ERP
**Inschatting:** 8 story points

---

#### US-06 | Zoekfunctie productinformatie

> *Als klant wil ik snel kunnen zoeken op smaken, allergenen, herkomst, kwaliteit en duurzaamheid, zodat ik direct antwoord vind op mijn vragen.*

**Acceptatiecriteria:**

- De zoekfunctie geeft resultaten binnen 2 seconden.
- Zoekresultaten zijn categoriseerbaar op type (product, recept, vraag).
- De zoekfunctie ondersteunt alle beschikbare talen van de app.
- Wanneer een zoekopdracht geen resultaten oplevert, verschijnt een doorverwijzing naar de AI-chatbot of klantenservice.

**Databronnen:** CMS, Odoo ERP
**Inschatting:** 5 story points

---

### Bestellen & Klachten

#### US-07 | Producten bestellen via de app

> *Als klant wil ik nieuwe producten direct via de app kunnen bestellen, zodat ik niet afhankelijk ben van verkoopmedewerkers of externe portals.*

**Acceptatiecriteria:**

- De klant kan producten zoeken, selecteren en bestellen binnen de app via een koppeling met Odoo ERP.
- De klant ontvangt een orderbevestiging via de app en per e-mail.
- De bestelstatus is traceerbaar in de app.
- B2B-klanten kunnen aanvullend de voorraadstatus en verwachte levertijd inzien voor het plaatsen van een bestelling.

**Databronnen:** Odoo ERP
**Inschatting:** 8 story points

---

#### US-08 | Klacht of retourmelding indienen

> *Als klant wil ik eenvoudig een klacht of retourmelding kunnen indienen inclusief foto's of video's, zodat mijn probleem snel en correct wordt afgehandeld.*

**Acceptatiecriteria:**

- De klant kan via een intuïtief formulier een klacht of retourmelding indienen met foto- of video-bijlage.
- De app herkent automatisch veelvoorkomende problemen, zoals smeltschade, breukschade of afwijkende structuur.
- Waar mogelijk biedt de app direct een oplossing of compensatie aan.
- De klant kan de status van de melding volgen in de app, met een notificatie bij elke belangrijke statuswijziging.

**Databronnen:** Odoo CRM, Odoo ERP
**Inschatting:** 8 story points

---

### Klantenservice & AI

#### US-09 | AI-chatbot klantenservice

> *Als klant wil ik 24/7 gebruik kunnen maken van een AI-gestuurde chatbot voor vragen over producten, allergenen, bestellingen en klachten, zodat ik altijd snel geholpen word.*

**Acceptatiecriteria:**

- De chatbot is 24/7 beschikbaar en beantwoordt veelgestelde vragen over productinformatie, allergenen, bestellingen, klachten en duurzaamheid.
- De chatbot is gekoppeld aan CRM-gegevens zodat antwoorden gepersonaliseerd kunnen worden.
- Bij complexere vragen kan de klant een live chat starten met een klantenservicemedewerker tijdens openingstijden, of een terugbelfunctie gebruiken.
- De chatbot ondersteunt alle beschikbare talen van de app.

**Databronnen:** Odoo CRM, AI-module
**Inschatting:** 13 story points

---

### Personalisatie & Aanbevelingen

#### US-10 | Gepersonaliseerde productaanbevelingen

> *Als klant wil ik aanbevelingen ontvangen op basis van mijn geregistreerde producten en aankoophistorie, zodat ik nieuwe producten ontdek die bij mijn voorkeuren passen.*

**Acceptatiecriteria:**

- De app toont aanbevelingen op basis van geregistreerde producten, aankoophistorie en gebruikersactiviteit, zoals nieuwe smaken, cadeauverpakkingen, proefboxen en accessoires.
- De app toont exclusieve aanbiedingen voor app-gebruikers en geeft early-access tot limited editions.
- De klant kan voorkeuren instellen voor het type promoties, zoals "alleen duurzame producten", "alleen nieuwe smaken" of "alleen seizoenspakketten".
- Aanbevelingen zijn gekoppeld aan de BI-tool voor klantgedragsdata.

**Databronnen:** Odoo CRM, Odoo ERP, BI-tool
**Inschatting:** 8 story points

---

### Community & Gamification

#### US-11 | Communityforum en gamification

> *Als klant wil ik recepten kunnen delen, smaakervaringen uitwisselen en deelnemen aan challenges, zodat ik betrokken blijf bij de merkbeleving van The Chocolate Firm.*

**Acceptatiecriteria:**

- De app bevat een communityforum waar klanten recepten, vragen en smaakervaringen kunnen delen en kunnen stemmen op nieuwe smaakideeën.
- Gamification-elementen zijn aanwezig: badges (bijv. "Master Taster", "Cocoa Explorer"), punten, challenges en seizoenswedstrijden.
- Forumcontent is modereerbaar door een beheerder.
- Participatie in de community wordt beloond met punten die zichtbaar zijn op het klantprofiel.

**Databronnen:** CMS, intern platform
**Inschatting:** 13 story points

---

### Winkelzoeker & Events

#### US-12 | Winkelzoeker op basis van locatie

> *Als klant wil ik via de app de dichtstbijzijnde verkooppunten vinden inclusief openingstijden en routebeschrijving, zodat ik weet waar ik producten kan kopen.*

**Acceptatiecriteria:**

- De winkelzoeker toont dichtstbijzijnde winkels, marktkramen, verkooppunten en deelnemende cafés op basis van geolocatie.
- Per locatie zijn openingstijden, contactgegevens en een routebeschrijving beschikbaar.
- De kaart laadt binnen 3 seconden na het openen van de functie.
- Locatiedata is actueel en beheersbaar via het CMS.

**Databronnen:** Geolocatie API, CMS
**Inschatting:** 5 story points

---

#### US-13 | Inschrijven voor events en workshops

> *Als klant wil ik mij via de app kunnen aanmelden voor workshops, proeverijen en fabrieksrondleidingen, zodat ik eenvoudig kan deelnemen aan evenementen van The Chocolate Firm.*

**Acceptatiecriteria:**

- De app toont een overzicht van beschikbare events, zoals workshops, proeverijen, plantagepresentaties, fabrieksrondleidingen en duurzaamheidsevents.
- De klant kan zich inschrijven en ontvangt een bevestiging en automatische herinnering via de app.
- Annuleren is mogelijk tot een instelbare termijn voor het event.
- Eventdata is beheersbaar via het CMS.

**Databronnen:** CMS, notificatieservice
**Inschatting:** 5 story points

---

### Privacy, Beveiliging & Toegankelijkheid

#### US-14 | AVG-conforme privacyinstellingen

> *Als klant wil ik zelf kunnen bepalen welke gegevens de app verzamelt en hoe deze worden gebruikt, zodat mijn privacy gewaarborgd is.*

**Acceptatiecriteria:**

- De app biedt uitgebreide privacy-instellingen waarmee de klant dataverwerking kan beheren.
- Bij het eerste gebruik en bij elke beleidswijziging informeert de app transparant over het privacybeleid en het gebruik van persoonsgegevens.
- Alle dataoverdracht is end-to-end versleuteld.
- De app voldoet aantoonbaar aan AVG/GDPR en alle relevante privacywetgeving.

**Databronnen:** Intern platform, juridisch kader
**Inschatting:** 8 story points

---

#### US-15 | Tweefactorauthenticatie

> *Als klant wil ik bij het inloggen gebruik kunnen maken van tweefactorauthenticatie, zodat mijn account beter beveiligd is.*

**Acceptatiecriteria:**

- Tweefactorauthenticatie is beschikbaar via sms of een authenticator-app.
- De klant kan 2FA activeren of deactiveren via de accountinstellingen.
- Bij inloggen op een nieuw apparaat is 2FA verplicht.
- De 2FA-flow werkt op zowel iOS als Android.

**Databronnen:** Intern platform, authenticatieservice
**Inschatting:** 5 story points

---

#### US-16 | Toegankelijkheidsinstellingen

> *Als klant wil ik de app kunnen gebruiken met toegankelijkheidsfuncties zoals een schermlezer en aanpasbare lettergrootte, zodat de app ook bruikbaar is voor klanten met een visuele beperking.*

**Acceptatiecriteria:**

- De app ondersteunt schermlezers voor slechtzienden op zowel iOS (VoiceOver) als Android (TalkBack).
- Lettergrootte en contrastinstellingen zijn aanpasbaar door de klant.
- Alle video's in de contentbibliotheek zijn voorzien van ondertiteling.
- De app biedt een lichte en donkere modus instelbaar via de persoonlijke instellingen.

**Databronnen:** Intern platform, CMS
**Inschatting:** 5 story points

---

### Instellingen & Analytics

#### US-17 | Notificatievoorkeuren en niet-storen periodes

> *Als klant wil ik mijn notificatievoorkeuren en niet-storen periodes kunnen instellen, zodat ik alleen meldingen ontvang die voor mij relevant zijn.*

**Acceptatiecriteria:**

- De klant kan per notificatietype aan- of uitzetten: productupdates, promoties, duurzaamheidsupdates, community-activiteiten en seizoensvents.
- De klant kan niet-storen periodes instellen waarbinnen geen notificaties worden verstuurd.
- Instellingen zijn direct van kracht na opslaan.
- Notificatievoorkeuren worden opgeslagen in het klantprofiel via Odoo CRM.

**Databronnen:** Odoo CRM, notificatieservice
**Inschatting:** 3 story points

---

#### US-18 | Geanonimiseerde data-analyse

> *Als productmanager wil ik geanonimiseerde gebruiksdata uit de app kunnen inzien via de BI-tool, zodat ik trends in smaakvoorkeuren, aankoopgedrag en community-betrokkenheid kan identificeren.*

**Acceptatiecriteria:**

- De app verzamelt geanonimiseerde data over gebruikersgedrag, smaakvoorkeuren, aankoopcycli en productfeedback.
- De data is beschikbaar in de BI-tool voor relevante afdelingen (productontwikkeling, marketing, kwaliteit).
- Gegevensverzameling voldoet aan AVG/GDPR; persoonlijke data wordt niet gedeeld zonder expliciete toestemming.
- De klant is via de privacyinstellingen op de hoogte van welke data wordt verzameld.

**Databronnen:** BI-tool, Odoo CRM, intern analyseplatform
**Inschatting:** 8 story points

---

### Unieke Functionaliteit

#### US-19 | Cocoa Journey Tracking — herkomst van jouw reep

> *Als klant wil ik de volledige herkomstreis van mijn chocoladereep kunnen volgen van plantage tot verpakking, zodat ik inzicht krijg in de duurzaamheid en transparantie achter mijn aankoop.*

**Acceptatiecriteria:**

- De klant kan via het geregistreerde product de herkomstreis inzien: land van herkomst, plantage, productiedatum, transportroute en certificeringen (bijv. Fairtrade, Rainforest Alliance).
- De herkomstreis wordt visueel gepresenteerd op een interactieve tijdlijn of kaart.
- Data is gekoppeld aan Odoo ERP en het productiesysteem via API.
- De functionaliteit is beschikbaar per geregistreerd product en sluit aan bij de duurzaamheidsstrategie van The Chocolate Firm.

**Databronnen:** Odoo ERP, productiesysteem (API)
**Inschatting:** 13 story points

---

## Bronvermelding

### Opdracht & Casus

- Hogeschool Utrecht. (2026). *Pakket/leverancier selectie & Implementatieplan*. Canvas HU. https://canvas.hu.nl/courses/50249/pages/pakket-slash-leverancier-selectie-and-implementatieplan

### Interview

- Manager IT & Financiën, The Chocolate Firm. (2026, 17 april). *Interview behoefteanalyse mobiele applicatie* [Persoonlijk interview]. Hogeschool Utrecht.

### Requirements

- Hogeschool Utrecht. (2026). *Requirements specificatie casus — Mobiele applicatie voor de Chocolate Firm*. Canvas HU.
