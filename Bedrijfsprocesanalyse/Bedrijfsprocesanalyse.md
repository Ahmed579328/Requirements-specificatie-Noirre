# Bedrijfsprocessanalyse — Mobiele Applicatie The Chocolate Firm

**Ist · Soll · Knelpunten · Gap-analyse · SIPOC**

| | |
|---|---|
| **Document** | Bedrijfsprocessanalyse |
| **Proces** | Klantbeleving via mobiele applicatie |
| **Versie** | 1.0 — Definitief concept |
| **Methode** | SIPOC + Ist/Soll + Knelpunten + Gap |

---

## 1. Procesafbakening & Scope

Het te analyseren proces betreft de klantbeleving en serviceverlening van The Chocolate Firm richting haar klanten. Dit proces loopt van het moment dat een klant een product aankoopt tot en met het moment dat de klant volledig bediend wordt: productinformatie raadplegen, bestellingen plaatsen, klachten indienen, gepersonaliseerde aanbevelingen ontvangen en deelnemen aan de community.

| | |
|---|---|
| **Proceseigenaar** | Product Owner / MT The Chocolate Firm |
| **Processtart** | Klant koopt een chocoladeproduct en wil informatie, service of ondersteuning |
| **Proceseinde** | Klant heeft inzicht in productinfo, ontvangt service en is betrokken bij de merkbeleving |
| **In scope** | Productregistratie, notificaties, contentbibliotheek, bestellen, klachtenafhandeling, AI-chatbot, personalisatie, community, winkelzoeker, events, privacy & beveiliging |
| **Buiten scope** | Interne ERP-invoer, HR-processen, facturatiebeheer, BI-rapportage voor medewerkers |
| **Betrokken systemen** | Odoo ERP, Odoo CRM, BI-tool, CMS, geolocatie API, AI-module, notificatieservice |

---

## 2. SIPOC — Huidige Situatie (Ist)

| S — Suppliers | I — Inputs | P — Process | O — Outputs | C — Customers |
|---|---|---|---|---|
| Odoo ERP | Klantaankopen (kassabon, batchnummer) | 1. Klant zoekt productinfo op via website of verpakking | Statische productinformatie (PDF, website) | Klanten (B2C) |
| Odoo CRM | Klachten via e-mail of telefoon | 2. Klant belt of mailt klantenservice met vragen of klachten | E-mailbevestiging klacht | B2B-klanten |
| Klantenservice | Vragen via e-mail of telefoon | 3. Medewerker zoekt handmatig info op in ERP en reageert | Telefonische toelichting | Klantenservicemedewerkers |
| Marketingafdeling | Promotiemateriaal (PDF, bulk-e-mail) | 4. Medewerker registreert klacht handmatig in CRM | Promotie-e-mails (bulk, niet gepersonaliseerd) | |
| Verkoopafdeling | Bestellingen via telefoon of e-mail | 5. Verkoopmedewerker verwerkt bestelling handmatig in ERP | | |

---

## 3. Ist — Huidige Situatie

### 3.1 Procesverloop

| # | Processtap | Beschrijving (Ist) | Actor | Systeem/Tool | Frequentie |
|---|---|---|---|---|---|
| 1 | Productinfo opzoeken | Klant zoekt informatie op via de website, verpakking of belt de klantenservice. Er is geen centraal digitaal klantplatform. | Klant / klantenservicemedewerker | Website, telefoon | Per behoefte |
| 2 | Klacht melden | Klant stuurt een e-mail of belt de klantenservice. Medewerker registreert de klacht handmatig in het CRM-systeem. | Klant / klantenservicemedewerker | E-mail, telefoon, Odoo CRM | Per klacht |
| 3 | Bestelling plaatsen | B2B-klant belt of mailt een verkoopmedewerker. De order wordt handmatig ingevoerd in Odoo ERP. | B2B-klant / verkoopmedewerker | Telefoon, e-mail, Odoo ERP | Per bestelling |
| 4 | Promoties ontvangen | Marketing verstuurt bulk-e-mails zonder koppeling aan aankoophistorie of persoonlijke voorkeuren. | Marketingafdeling | E-mailclient | Periodiek |
| 5 | Evenementaanmelding | Klant belt of mailt om zich in te schrijven voor een workshop of proeverij. Bevestiging wordt per e-mail verstuurd. | Klant / medewerker | Telefoon, e-mail | Per event |

### 3.2 Doorlooptijd Ist

| Stap | Minimale tijd | Maximale tijd | Opmerking |
|---|---|---|---|
| Productinfo opzoeken | 5 min | 30+ min | Afhankelijk van beschikbaarheid klantenservicemedewerker |
| Klacht registreren en beantwoorden | 15 min | 2 uur | Volledig handmatige verwerking, geen automatisering |
| Bestelling invoeren (B2B) | 10 min | 1 uur | Afhankelijk van beschikbaarheid verkoopmedewerker |
| Evenementaanmelding verwerken | 10 min | 30 min | Handmatige registratie en bevestiging per e-mail |
| **Totale servicecyclus per klantcontact** | **30 min** | **3+ uur** | Per interactie, per medewerker |

---

## 4. Knelpunten

| # | Knelpunt | Beschrijving | Categorie | Impact |
|---|---|---|---|---|
| K1 | Geen centraal klantplatform | Klanten hebben geen digitaal platform. Alle interacties verlopen via telefoon, e-mail of website zonder integratie tussen systemen. | Proces | Hoge werkdruk klantenservice, trage afhandeling, geen schaalbaarheid |
| K2 | Geen productregistratie mogelijk | Klanten kunnen aangekochte producten niet registreren. Er is geen inzicht in houdbaarheid, allergenen of herkomst via een digitaal kanaal. | Data | Gemiste klantenservice, hogere klachtkans bij verlopen producten |
| K3 | Geen gepersonaliseerde communicatie | Marketing verstuurt bulk-e-mails zonder koppeling aan aankoophistorie. Klanten ontvangen irrelevante informatie. | Marketing | Lage klantbetrokkenheid, hoog afmeldpercentage |
| K4 | Handmatige klachtenverwerking | Klachten worden handmatig geregistreerd en opgevolgd. De klant heeft geen statusinzage en er is geen automatische probleemherkenning. | Efficiency | Lange doorlooptijd, lage klanttevredenheid |
| K5 | Geen 24/7 klantenservice | Klantenservice is alleen bereikbaar tijdens openingstijden. Buiten kantooruren zijn klanten volledig op zichzelf aangewezen. | Service | Klantfrustatie, gemiste vragen en klachten buiten openingstijden |
| K6 | Geen community of betrokkenheid | Er is geen platform waar klanten recepten kunnen delen, smaakervaringen uitwisselen of deelnemen aan challenges. | Klantloyaliteit | Lage herhaalaankopen, beperkte merkbinding |
| K7 | Geen digitale besteloptie | B2B-klanten zijn afhankelijk van verkoopmedewerkers voor bestellingen. Self-service is niet mogelijk. | Efficiency | Vertraging bij bestellingen, onnodige druk op verkoopteam |
| K8 | Geen inzicht in herkomst en duurzaamheid | Klanten kunnen de herkomstreis van hun product niet digitaal volgen. Duurzaamheidsinformatie is niet centraal beschikbaar. | Transparantie | Gemiste differentiatie op duurzaamheid, minder klantvertrouwen |

---

## 5. SIPOC — Gewenste Situatie (Soll)

| S — Suppliers | I — Inputs | P — Process | O — Outputs | C — Customers |
|---|---|---|---|---|
| Odoo ERP (API) | QR-code scan of batchnummer | 1. Klant registreert product via app (QR of handmatig) | Persoonlijk productdashboard | Klanten (B2C) |
| Odoo CRM (API) | Klantprofiel en aankoophistorie | 2. App haalt productdata op via Odoo ERP-API | Pushnotificaties (houdbaarheid, releases, duurzaamheid) | B2B-klanten |
| CMS | Content (recepten, video's, tutorials) | 3. Klant raadpleegt digitale productkaart en contentbibliotheek | Digitale productkaarten en gepersonaliseerde recepten | Klantenservice (minder belasting) |
| AI-module | Chatbotinteracties en CRM-profiel | 4. Klant bestelt product of dient klacht in via app | Orderbevestiging en real-time klachtstatus | Productontwikkeling |
| Geolocatie API | Locatiedata klant | 5. AI-chatbot beantwoordt vragen 24/7 op basis van CRM-profiel | Gepersonaliseerde productaanbevelingen | Marketing |
| Notificatieservice | Eventdata en productreleases | 6. App toont gepersonaliseerde aanbevelingen en exclusieve aanbiedingen | Community-interacties en gamificationbadges | |
| BI-tool | Geanonimiseerde gebruiksdata | 7. Klant neemt deel aan community, events en Cocoa Journey Tracking | Winkelzoeker en eventoverzicht | |

---

## 6. Soll — Gewenste Situatie

### 6.1 Procesverloop

| # | Processtap | Beschrijving (Soll) | Actor | Systeem/Tool | Doorlooptijd |
|---|---|---|---|---|---|
| 1 | Productregistratie | Klant scant QR-code of voert batchnummer in. App haalt productdata op via Odoo ERP en toont persoonlijk dashboard met houdbaarheid, allergenen en herkomst. | Klant | Mobiele app, Odoo ERP | < 1 min |
| 2 | Notificaties ontvangen | App stuurt automatisch pushnotificaties bij naderende houdbaarheidsdatum, nieuwe productreleases en seizoensproducten op basis van ERP-data. | Systeem (automatisch) | Notificatieservice, Odoo ERP | Automatisch |
| 3 | Productinfo raadplegen | Klant opent digitale productkaart of doorzoekt de contentbibliotheek op allergenen, herkomst, recepten of video's. Zoekresultaat verschijnt binnen 2 seconden. | Klant | Mobiele app, CMS | < 1 min |
| 4 | Bestelling plaatsen | Klant bestelt product direct via de app. Bestelling wordt verwerkt in Odoo ERP. Klant ontvangt bevestiging en kan bestelstatus volgen in de app. | Klant | Mobiele app, Odoo ERP | < 3 min |
| 5 | Klacht indienen | Klant dient klacht in via een formulier met foto- of video-bijlage. App herkent automatisch veelvoorkomende problemen en biedt direct een oplossing of registreert de melding voor verdere afhandeling. | Klant | Mobiele app, Odoo CRM | < 5 min |
| 6 | AI-chatbot raadplegen | Klant stelt een vraag aan de AI-chatbot (24/7 beschikbaar). Chatbot geeft gepersonaliseerd antwoord op basis van CRM-profiel. Bij complexe vragen: doorverwijzing naar live medewerker of terugbelverzoek. | Klant / AI-module | Mobiele app, Odoo CRM | < 2 min |
| 7 | Aanbevelingen ontvangen | App toont gepersonaliseerde productaanbevelingen op basis van aankoophistorie en BI-data. Klant ontvangt early-access tot limited editions en exclusieve app-aanbiedingen. | Systeem (automatisch) | Mobiele app, BI-tool, Odoo CRM | Automatisch |
| 8 | Community en events | Klant deelt recept, verdient badges, schrijft zich in voor een event. Bevestiging en herinnering worden automatisch verstuurd. | Klant | Mobiele app, CMS | < 2 min |

### 6.2 Doorlooptijd Soll (verwacht)

| Stap | Ist (gemiddeld) | Soll (verwacht) | Verbetering |
|---|---|---|---|
| Productinfo raadplegen | 5–30 min | < 1 min | Direct beschikbaar, geen medewerker nodig |
| Klacht indienen en registreren | 15 min–2 uur | < 5 min | Automatische herkenning en registratie via app |
| Bestelling plaatsen (B2B) | 10 min–1 uur | < 3 min | Self-service via app met directe ERP-koppeling |
| Gepersonaliseerde communicatie | Niet mogelijk | Automatisch | Op basis van aankoophistorie, CRM en BI-data |
| Evenementaanmelding | 10–30 min | < 2 min | Directe inschrijving via app, automatische bevestiging |
| **Totale servicecyclus per klantcontact** | **30 min–3+ uur** | **< 10 min** | **~85% reductie in handmatige afhandeling** |

---

## 7. Gap-analyse

| Dimensie | Ist (nu) | Soll (gewenst) | Prioriteit | Actie om gap te dichten |
|---|---|---|---|---|
| Klantplatform | Geen digitaal platform; alle contact via telefoon of e-mail | Centrale mobiele app als primair klantkanaal voor alle diensten | Kritiek | Ontwikkel en lanceer mobiele applicatie voor iOS en Android |
| Productregistratie | Niet mogelijk; geen koppeling met klantprofiel | QR-scan of batchnummer; persoonlijk dashboard met productdetails | Kritiek | Bouw registratieflow met Odoo ERP-koppeling en dashboardweergave |
| Notificaties | Geen automatische meldingen aan klant | Pushnotificaties op basis van ERP-data (houdbaarheid, releases, duurzaamheid) | Kritiek | Implementeer notificatieservice gekoppeld aan Odoo ERP |
| Klachtenafhandeling | Handmatig via e-mail of telefoon; geen statusinzage voor klant | In-app formulier met automatische probleemherkenning en statusinzage | Hoog | Bouw klachtenmodule met Odoo CRM-koppeling en trackingfunctie |
| Klantenservice | Alleen bereikbaar tijdens openingstijden | AI-chatbot 24/7 beschikbaar, aangevuld met live chat tijdens openingstijden | Hoog | Integreer AI-module gekoppeld aan CRM-profiel |
| Personalisatie | Bulk-e-mails zonder relevantie voor de klant | Gepersonaliseerde aanbevelingen op basis van aankoophistorie en BI-data | Hoog | Koppel BI-tool en Odoo CRM aan aanbevelingsengine in de app |
| Duurzaamheid & herkomst | Niet digitaal beschikbaar voor de klant | Cocoa Journey Tracking via interactieve tijdlijn per geregistreerd product | Hoog | Bouw herkomstmodule met koppeling aan Odoo ERP en productiesysteem |
| Community & betrokkenheid | Geen platform voor klantinteractie | Communityforum met gamification (badges, punten, challenges) | Middel | Ontwikkel communitymodule binnen de app |
| Self-service bestellen | Alleen via verkoopmedewerker (B2B) | Directe bestelling via app gekoppeld aan Odoo ERP met ordertracking | Middel | Bouw bestelmodule met ERP-integratie |
| Privacy & beveiliging | Geen 2FA, geen in-app privacybeheer voor klant | 2FA verplicht, AVG-conform, end-to-end encryptie, transparant privacybeleid | Middel | Implementeer authenticatieservice en privacyinstellingen in de app |

### 7.1 Prioriteitenlegenda

| Prioriteit | Betekenis | Gaps |
|---|---|---|
| Kritiek | Direct aanpakken — blokkeert go-live | Klantplatform, Productregistratie, Notificaties |
| Hoog | Aanpakken in fase 1–2 | Klachtenafhandeling, Klantenservice, Personalisatie, Duurzaamheid & herkomst |
| Middel | Aanpakken in fase 2–3 | Community, Self-service bestellen, Privacy & beveiliging |

---

## 8. Conclusie

De gap-analyse toont aan dat het huidige klantproces structureel tekortschiet op drie kritieke dimensies: **er is geen centraal digitaal klantplatform**, **productregistratie is niet mogelijk** en **klanten ontvangen geen automatische notificaties**. Deze drie gaps blokkeren een succesvolle go-live en moeten als eerste worden aangepakt.

De overige gaps (klachtenafhandeling, personalisatie, duurzaamheid, community) zijn oplosbaar binnen de kaders van de mobiele applicatie, mits de implementatie gefaseerd wordt uitgevoerd en eindgebruikers vroeg worden betrokken bij het ontwerp en de testfase.

De verwachte reductie van **~85% in handmatige klantafhandeling per servicecyclus** rechtvaardigt de investering, ook bij een gefaseerde uitrol.

---

## Bronvermelding

### Opdracht & Casus

- Hogeschool Utrecht. (2026). *Pakket/leverancier selectie & Implementatieplan*. Canvas HU. https://canvas.hu.nl/courses/50249/pages/pakket-slash-leverancier-selectie-and-implementatieplan

### Interview

- Manager IT & Financiën, The Chocolate Firm. (2026, 17 april). *Interview behoefteanalyse mobiele applicatie* [Persoonlijk interview]. Hogeschool Utrecht.

### Requirements

- Hogeschool Utrecht. (2026). *Requirements specificatie casus — Mobiele applicatie voor de Chocolate Firm*. Canvas HU.
