# GitHub Copilot Instructions - Lead Generation & Website Modernization Framework

## 🎯 Hauptziel: Automatisierte Lead-Generierung durch Website-Modernisierung
Systematische Akquise und Modernisierung veralteter Websites mit authentischem Branding, personalisierten Anschreiben und Azure-Deployment.

## 📧 PHASE 4: Personalisiertes Anschreiben-System

### Optimiertes E-Mail Template (Final Version)
```markdown
**Betreff:** Familie sucht [DIENSTLEISTUNG] [REGION] - Website-Feedback inklusive 😊

Hallo!

Mein Name ist Daniel, ich wohne in St. Veit an der Glan und arbeite nebenbei als Webentwickler und unterstütze mitunter Unternehmen bei der Modernisierung ihrer Webseite.

Wir waren eigentlich auf der Suche nach [SPEZIFISCHE_SUCHE] - [PERSÖNLICHER_BEZUG]. Bei der Recherche bin ich auf Ihre Webseite gestoßen und [SPEZIFISCHES_KOMPLIMENT]!

Beim Durchstöbern Ihrer Website ist mir allerdings aufgefallen, dass [KONKRETE_BEOBACHTUNG]. Besonders am Handy war es [SPEZIFISCHES_PROBLEM].

Da ich beruflich öfter mit Websites zu tun habe, ist mir das aufgefallen - wahrscheinlich geht es anderen potenziellen [ZIELGRUPPE] genauso, und das wäre schade, weil Sie wirklich [STÄRKE_HERVORHEBEN] haben.

Aus purem Interesse habe ich mir erlaubt, ein paar Bilder zu erstellen, die zeigen, wie Ihre Website mit einer moderneren Aufmachung aussehen könnte. Alle Ihre Texte und Bilder habe ich dabei so gelassen wie sie sind.

Ich hänge einfach mal zwei Bilder an - vielleicht interessiert es Sie ja. Falls nicht, ist das auch völlig in Ordnung - ich wollte Ihnen nur eine kleine Anregung geben, weil ich finde, dass [LOKALER_BEZUG] mehr Aufmerksamkeit verdient hat.

Falls Sie uns noch eine Empfehlung haben: [BRANCHENSPEZIFISCHE_FRAGE]?

Liebe Grüße aus St. Veit,  
Daniel Fellner

P.S.: Falls Sie Interesse an den Bildern haben oder Fragen dazu, können Sie mir gerne schreiben. Ansonsten einfach ignorieren - kein Problem! 😊
```

### Tonalität & Stil-Guidelines

#### ✅ VERWENDEN:
- **Authentischer Familienbezug:** "meine Frau und ich", "unser kleiner Sohn"
- **Lokale Glaubwürdigkeit:** "St. Veit an der Glan", regionale Bezüge
- **Selbstbewusste Expertise:** "unterstütze Unternehmen bei der Modernisierung"
- **Konkrete Beobachtungen:** "am Handy schwierig zu navigieren"
- **Positive Verstärkung:** "tolles Angebot", "traumhafte Lage"
- **Unaufdringlicher CTA:** "vielleicht interessiert es Sie ja"

#### ❌ VERMEIDEN:
- **Defensive Sprache:** "Keine Sorge", "nur aus Neugier"
- **Zu verkäuferisch:** "günstige Preise", "sofortiges Angebot"
- **Spam-Indikatoren:** "KOSTENLOS", "JETZT", Ausrufezeichen-Ketten
- **Übertreibungen:** "revolutionär", "einzigartig in ganz Österreich"
- **Formelle Anrede:** "Sehr geehrte Damen und Herren"

### E-Mail Template für Lead Generation mit personalisierten Anschreiben und Azure-Deployment.

## 📊 PHASE 1: Lead Research & Targeting

### Zielgruppen-Identifikation
**Primäre Targets:**
- Ferienwohnungen & Hotels (hohe Priorität für Webauftritt)
- Restaurants & Gastronomiebetriebe
- Handwerksbetriebe & lokale Dienstleister
- Medizinische Praxen & Kliniken
- Einzelhandel & E-Commerce

### Website-Research mit Brave Search & Playwright
```javascript
// 1. Brave Search für Lead-Discovery
const braveSearchQueries = [
    "Ferienwohnung Kärnten site:*.at -booking.com -airbnb.com",
    "Hotel Österreich site:*.at -booking.com -trivago.com",
    "Restaurant Kärnten site:*.at -lieferando.de -mjam.net",
    "Handwerk site:*.at -willhaben.at",
    "Zahnarzt Praxis site:*.at -docfinder.at"
];

// 2. Erweiterte Suche für spezifische Regionen
const regionalSearches = [
    "Ferienwohnung St. Veit an der Glan",
    "Hotel Millstätter See",
    "Restaurant Villach", 
    "Handwerker Klagenfurt"
];

// 3. Veraltete Website-Indikatoren
const outdatedIndicators = [
    "erstellt 2018" OR "copyright 2019" OR "letzte Aktualisierung 2020",
    "Flash" OR "Internet Explorer" OR "optimiert für",
    "Webmaster" OR "Homepage erstellt mit" OR "kostenlose Homepage"
];
```

### Brave Search Integration
```javascript
// Brave Web Search für Lead-Discovery
const searchForOutdatedWebsites = async (industry, region) => {
    const query = `${industry} ${region} site:*.at -booking.com -airbnb.com`;
    const results = await braveWebSearch({
        query: query,
        country: "AT",
        freshness: "py", // Letztes Jahr für aktuelle aber veraltete Sites
        count: 20
    });
    
    return results.filter(result => 
        isOutdatedWebsite(result.url) && 
        hasBusinessPotential(result.description)
    );
};
```

### Qualifikationskriterien
- Website älter als 3-5 Jahre (erkennbar an Design/Technologie)
- Schlechte Mobile-Optimierung
- Veraltete Navigation/UX
- Fehlende moderne Features (Online-Buchung, etc.)
- Aber: Aktives Geschäft mit Potenzial

### Lead-Dokumentation in results.md
Alle gefundenen Leads werden strukturiert in `leads/results.md` dokumentiert:

```markdown
# Lead-Discovery Ergebnisse

## Ferienwohnungen & Hotels

### [BETRIEBSNAME]
- **URL:** https://example.at
- **Kontakt:** +43 123 456789
- **Ort:** Millstätter See, Kärnten
- **E-Mail:** info@example.at
- **Ansprechpartner:** Max Mustermann
- **Auffälligkeiten:** 
  - Copyright 2019, nicht mobile-optimiert
  - Veraltetes Design, keine Online-Buchung
  - Potenzial: Premium-Lage, gute Bewertungen
```

## 📊 PHASE 2: Datenextraktion mit Brave Search & Playwright

### Lead-Validierung mit Brave Search
```javascript
// Geschäfts-Informationen recherchieren
const validateBusinessLead = async (businessName, location) => {
    const queries = [
        `"${businessName}" ${location} Bewertungen`,
        `"${businessName}" ${location} Öffnungszeiten`,
        `"${businessName}" ${location} Kontakt`
    ];
    
    for (const query of queries) {
        const results = await braveWebSearch({
            query: query,
            country: "AT",
            count: 5
        });
        
        // Validiere ob Geschäft aktiv und seriös ist
        const hasRecentActivity = results.some(r => 
            r.description.includes("2024") || 
            r.description.includes("geöffnet")
        );
    }
};
```

### Kontaktdaten-Extraktion mit Playwright
```javascript
// Playwright-Script für Datenextraktion
const extractContactData = {
    impressum: 'a[href*="impressum"], a[href*="kontakt"]',
    email: 'a[href^="mailto:"]',
    phone: 'a[href^="tel:"]',
    businessName: 'h1, .company-name, #company',
    address: '.address, .kontakt address',
    owner: '.inhaber, .geschäftsführer'
};
```

### Content-Extraktion für Authentizität
- Haupttexte und Beschreibungen
- Bilder und visuelle Elemente
- Dienstleistungen/Angebote
- Besonderheiten und USPs
- Branding-Farben und Schriften

## 🚀 PHASE 3: Projekt-Setup & Modernisierung

### Automatisches Projekt-Setup
```bash
mkdir "projects/[business-name]-modern"
mkdir "projects/[business-name]-modern/images"
mkdir "projects/[business-name]-modern/customer_screens"
mkdir "projects/[business-name]-modern/lead_materials"
```

## 📋 Workflow: Research → Extract → Modern → Contact

### Phase 1: Lead Research & Data Extraction
- Automatisierte Suche nach veralteten Websites in Zielzielgruppen
- Playwright-basierte Extraktion von Kontakt- und Businessdaten
- Qualifikation der Leads nach Modernisierungspotenzial
- Sammlung authentischer Inhalte für Modernisierung

### Phase 2: Authentische Modernisierung
- Projekt-Setup mit extrahierten Daten
- 1:1 Übernahme authentischer Texte und Inhalte
- Moderne UI/UX mit Tailwind CSS
- Fokus auf Startseite als Demo-Showcase

### Phase 3: Screenshot-Dokumentation
- 3-4 professionelle Screenshots für Kundenpräsentation
- Desktop und Mobile Views
- Vergleich Alt vs. Neu (optional)

### Phase 4: Personalisiertes Anschreiben
- Standort-basierte Personalisierung (St. Veit an der Glan)
- Authentische Ansprache als lokaler Webentwickler
- Konkrete Verbesserungsvorschläge
- Screenshots als Proof-of-Concept beilegen

### Phase 2: Projekt Setup
```bash
mkdir "projects/[business-name]-modern"
mkdir "projects/[business-name]-modern/images"
mkdir "projects/[business-name]-modern/customer_screens"
mkdir "projects/[business-name]-modern/lead_materials"
```

### Automatische Content-Integration
```javascript
// Extrahierte Daten in Template einsetzen
const modernizeWebsite = {
    businessName: extractedData.businessName,
    owner: extractedData.owner,
    description: extractedData.description,
    services: extractedData.services,
    images: extractedData.images,
    branding: {
        colors: extractedData.colors,
        fonts: extractedData.fonts
    }
};
```

### Phase 3: Modernes HTML Template mit authentischen Daten
```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[CLIENT NAME] - Modernisiert</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'brand-primary': '#EXTRACTED_COLOR_1',
                        'brand-secondary': '#EXTRACTED_COLOR_2'
                    }
                }
            }
        }
    </script>
</head>
<body class="font-sans">
    <nav class="fixed top-0 w-full bg-white/95 backdrop-blur shadow z-50">
        <div class="container mx-auto px-4 py-4 flex justify-between items-center">
            <img src="images/authentic-logo.png" 
                 alt="[CLIENT NAME]" 
                 class="h-12"
                 onerror="this.style.display='none'; this.nextElementSibling.style.display='block';">
            <div class="hidden text-2xl font-bold text-brand-primary">[CLIENT NAME]</div>
        </div>
    </nav>
    
    <section id="home" class="min-h-screen flex items-center justify-center">
        <div class="text-center">
            <h1 class="text-4xl md:text-6xl font-bold mb-6 fade-on-scroll">
                [AUTHENTIC TITLE]
            </h1>
            <p class="text-xl mb-8 fade-on-scroll">
                [AUTHENTIC DESCRIPTION]
            </p>
        </div>
    </section>
</body>
</html>
```

## 📧 PHASE 4: Personalisiertes Anschreiben-System

### Branchenspezifische Variablen-Sets

#### Ferienwohnungen & Hotels:
```javascript
{
    DIENSTLEISTUNG: "Ferienwohnung" / "Ferienhaus" / "Hotel",
    REGION: "Millstätter See" / "Kärnten" / "Wörthersee",
    SPEZIFISCHE_SUCHE: "einer schönen Ferienwohnung am Millstätter See für meine Frau und mich mit unserem kleinen Sohn",
    PERSÖNLICHER_BEZUG: "wir lieben die Gegend und möchten gerne ein paar Tage dort verbringen",
    SPEZIFISCHES_KOMPLIMENT: "die Lage Ihrer Wohnungen klingt wirklich traumhaft",
    KONKRETE_BEOBACHTUNG: "es etwas schwierig war, alle Informationen zu finden, die wir brauchen",
    SPEZIFISCHES_PROBLEM: "nicht so einfach zu navigieren, und ich musste ziemlich hin- und herscrollen",
    ZIELGRUPPE: "Gästen",
    STÄRKE_HERVORHEBEN: "ein tolles Angebot",
    LOKALER_BEZUG: "Ihre traumhafte Lage am Millstätter See",
    BRANCHENSPEZIFISCHE_FRAGE: "Haben Sie Tipps für familienfreundliche Aktivitäten in der Nähe"
}
```

#### Restaurants & Gastronomie:
```javascript
{
    DIENSTLEISTUNG: "Restaurant" / "Gasthaus" / "Pizzeria",
    SPEZIFISCHE_SUCHE: "einem gemütlichen Restaurant für einen besonderen Anlass mit der Familie",
    PERSÖNLICHER_BEZUG: "wir feiern bald unseren Hochzeitstag",
    SPEZIFISCHES_KOMPLIMENT: "Ihre Speisekarte hört sich wirklich interessant an",
    KONKRETE_BEOBACHTUNG: "dass die Speisekarte am Handy nicht gut lesbar war",
    BRANCHENSPEZIFISCHE_FRAGE: "Haben Sie auch einen ruhigen Bereich für Familien mit Kindern"
}
```

#### Handwerk & Dienstleister:
```javascript
{
    DIENSTLEISTUNG: "Handwerker" / "Installateur" / "Maler",
    SPEZIFISCHE_SUCHE: "einem zuverlässigen [HANDWERK] für unser Haus",
    PERSÖNLICHER_BEZUG: "wir renovieren gerade unser Eigenheim",
    KONKRETE_BEOBACHTUNG: "dass es schwer war, konkrete Preise oder Referenzen zu finden",
    BRANCHENSPEZIFISCHE_FRAGE: "Haben Sie Erfahrung mit älteren Häusern aus den 80er Jahren"
}
```

### Anschreiben Best Practices

#### Timing & Versendung:
- **Beste Zeiten:** Dienstag-Donnerstag, 9-11 Uhr
- **Max. Anzahl:** 5-10 personalisierte Mails pro Tag
- **Response-Zeit:** 3-5 Werktage warten vor Follow-up

#### Anhänge & Format:
- **2 Screenshots:** Desktop + Mobile Ansicht
- **Dateigröße:** Max. 2MB pro Bild
- **Format:** PNG oder JPEG
- **Benennung:** [business-name]-modern-desktop.png

#### A/B Test Varianten:
- **Betreff A:** "Familie sucht [DIENSTLEISTUNG] [REGION] - Website-Feedback inklusive 😊"
- **Betreff B:** "[REGION] Buchung + kleine Website-Beobachtung"
- **Betreff C:** "Anfrage [BUSINESS_NAME] - mit kleinem Feedback 😊"

### Personalisierungs-Variablen
```javascript
const emailPersonalization = {
    BUSINESS_NAME: extractedData.businessName,
    ANSPRECHPERSON: extractedData.owner || "Inhaber/in",
    NACHNAME: extractedData.ownerLastName,
    BRANCHE: detectIndustry(extractedData.content), // "Ferienvermietung", "Gastronomie", etc.
    SPEZIFISCHE_ERWÄHNUNG: generateSpecificMention(industry), // "bei Ihnen ein Ferienhaus"
    KONKRETE_BEOBACHTUNG: generateObservation(websiteAnalysis)
};
```

## 📸 Screenshot-System für Kundenpräsentationen

### Screenshot-Modus aktivieren
```javascript
// URL Parameter: ?screenshot=1 deaktiviert Animationen
const urlParams = new URLSearchParams(window.location.search);
const screenshotMode = urlParams.get('screenshot') === '1';

if (screenshotMode) {
    document.querySelectorAll('.fade-on-scroll').forEach(el => {
        el.style.opacity = '1';
        el.style.transform = 'none';
    });
}
```

### Screenshots erstellen
```bash
# Desktop (1200x700)
playwright-cli screenshot "file://$(pwd)/index.html?screenshot=1" \
    --viewport-size=1200,700 \
    --output="customer_screens/01_desktop_overview.png"

# Mobile (390x844)
playwright-cli screenshot "file://$(pwd)/index.html?screenshot=1" \
    --viewport-size=390,844 \
    --output="customer_screens/02_mobile_overview.png"
```

## 🔄 Zwei-Runden Optimierung

### Runde 1: Funktionalität
- Mobile Navigation testen
- Kontaktformular validieren
- Responsive Breakpoints prüfen
- Performance-Check (Lighthouse)

### Runde 2: User Experience
- Animation-Timing optimieren
- Screenshot-Modus finalisieren
- Cross-Browser Testing
- Kundenpräsentation vorbereiten

## ☁️ Azure Static Web Apps Deployment

### Voraussetzungen
- ✅ **Resource Group bereits vorhanden:** `vibe-coding-websites-rg`
- ✅ **Azure CLI installiert und eingeloggt**
- ✅ **SWA CLI installiert:** `npm install -g @azure/static-web-apps-cli`

### Website Deployment (Direkt in existierende Resource Group)
```bash
# Static Web App erstellen (Resource Group bereits vorhanden)
az staticwebapp create \
    --name "[client-name]-modern" \
    --resource-group "vibe-coding-websites-rg" \
    --location "West Europe" \
    --sku "Free"

# Deployment Token abrufen
az staticwebapp secrets list \
    --name "[client-name]-modern" \
    --resource-group "vibe-coding-websites-rg" \
    --query "properties.apiKey" -o tsv

# Build-Ordner vorbereiten
mkdir -p dist
cp index.html dist/
cp -r images dist/
cp staticwebapp.config.json dist/

# Website deployen
swa deploy dist --deployment-token "YOUR_DEPLOYMENT_TOKEN"
```

### Beispiel: Casa Nonna Deployment
- **Resource Group:** `vibe-coding-websites-rg` ✅
- **App Name:** `casa-nonna-modern` ✅  
- **Live URL:** https://purple-beach-0d9260303-preview.westeurope.1.azurestaticapps.net ✅

## 🔄 Zwei-Runden Optimierung

### Runde 1: Funktionalität
- Mobile Navigation testen
- Kontaktformular validieren
- Responsive Breakpoints prüfen
- Performance-Check (Lighthouse)

### Runde 2: User Experience
- Animation-Timing optimieren
- Screenshot-Modus finalisieren
- Cross-Browser Testing
- Kundenpräsentation vorbereiten

## 🚀 Deployment Checkliste

### Pre-Deployment
- [ ] Authentische Inhalte integriert
- [ ] Screenshots erstellt
- [ ] Mobile + Desktop getestet
- [ ] Performance >90 (Lighthouse)

### Azure Deployment
- [ ] Resource Group verfügbar
- [ ] Static Web App erstellt
- [ ] Deployment erfolgreich
- [ ] Live-URL funktional

Diese Instructions sind ready-to-use für jede Website-Modernisierung! 🎯