# 🚀 Vibe Coding Websites - Lead Generation Framework

**Automatisierte Website-Modernisierung für lokale Unternehmen in Kärnten**

---

## 📋 Über das Projekt

Systematisches Framework für die Akquise und Modernisierung veralteter Websites mit authentischem Branding und direkter Lead-Generierung. Speziell entwickelt für lokale Unternehmen in Kärnten (Ferienwohnungen, Hotels, Restaurants, Handwerk).

### 🎯 Hauptziele
- **Lead Discovery:** Automatisierte Suche nach modernisierungsbedürftigen Websites
- **Authentic Modernization:** 1:1 Übernahme bestehender Inhalte mit modernem Design
- **Azure Deployment:** Professionelle Cloud-Hosting Lösung
- **Customer Acquisition:** Personalisierte Anschreiben mit Live-Demos

---

## 🏗️ Projekt-Struktur

```
vibe-coding-websites/
├── casa-nonna/                 # ✅ LIVE: Casa Nonna Ferienwohnung
│   ├── index.html             # Moderne Website (Tailwind CSS)
│   ├── AZURE_DEPLOYMENT.md    # Live Azure SWA Deployment
│   ├── customer_screens/      # Screenshots für Kundenpräsentation
│   └── lead_materials/        # Personalisierte Anschreiben
├── fewo-weinleiten-modern/    # Ferienwohnung Weinleiten Modernisierung
└── leads/                     # Lead Research & Documentation
    └── results.md             # Dokumentierte Leads aus Brave Search
```

---

## 🛠️ Technologie-Stack

### Frontend Development
- **HTML5/CSS3/JavaScript** - Moderne Web-Standards
- **Tailwind CSS** - Utility-First CSS Framework
- **Responsive Design** - Mobile-First Approach

### Automation & Research
- **Brave Search API** - Lead Discovery & Business Research
- **Playwright Browser** - Automated Testing & Screenshots
- **GitHub API** - Repository Management

### Cloud Deployment
- **Azure Static Web Apps** - Hosting & CDN
- **Azure CLI** - Deployment Automation
- **SWA CLI** - Static Web Apps Deployment Tool

---

## 🎯 Live Projekte

### ✅ Casa Nonna - Ferienwohnung Klagenfurt
- **Status:** LIVE & DEPLOYED
- **URL:** https://purple-beach-0d9260303-preview.westeurope.1.azurestaticapps.net
- **Features:** Mobile-optimiert, moderne Galerie, Direct-Booking Integration
- **Lead Status:** Customer Materials Ready

### 🚧 Fewo Weinleiten - Millstätter See
- **Status:** Development Phase
- **Features:** Authentic Design, Responsive Layout, Image Gallery

---

## 📊 Lead Generation Workflow

### Phase 1: Lead Research
```javascript
// Brave Search für veraltete Websites
const searchQueries = [
    "Ferienwohnung Kärnten site:*.at -booking.com",
    "Restaurant Kärnten site:*.at -lieferando.de",
    "Handwerk site:*.at -willhaben.at"
];
```

### Phase 2: Website Modernization
- **Authentische Content-Extraktion** mit Playwright
- **Modern UI/UX** mit Tailwind CSS
- **Mobile-First** Responsive Design
- **Performance Optimization**

### Phase 3: Azure Deployment
```bash
# Azure Static Web App Creation
az staticwebapp create \
    --name "[client-name]-modern" \
    --resource-group "vibe-coding-websites-rg" \
    --location "West Europe"
```

### Phase 4: Customer Outreach
- **Personalisierte E-Mails** mit lokalem Bezug (St. Veit an der Glan)
- **Live Demo URLs** als Proof-of-Concept
- **Professional Screenshots** für Anhänge
- **Follow-up Strategie** für Conversion

---

## 🎨 Design Philosophy

### Authenticity First
- **Original Content Preservation** - Keine Änderung bestehender Texte
- **Brand Color Extraction** - Übernahme der Firmenfarben
- **Local Credibility** - Kärnten-spezifische Ansprache

### Modern Standards
- **Mobile Optimization** - 60%+ Traffic kommt von mobilen Geräten
- **Fast Loading** - Azure CDN für optimale Performance
- **SEO Ready** - Strukturierte Daten und Meta-Tags
- **Accessible Design** - WCAG-konforme Umsetzung

---

## 📈 Business Impact

### Für Kunden
- **Professional Online Presence** - Vertrauenswürdige Website
- **Higher Conversion Rates** - Bessere User Experience
- **Mobile Reach** - Optimiert für Smartphone-Nutzer
- **Search Visibility** - SEO-optimierte Struktur

### Für Lead Generation
- **Proof-of-Concept** - Live Demos für sofortige Überzeugung
- **Local Authenticity** - Glaubwürdige Ansprache aus St. Veit
- **Portfolio Growth** - Referenz-Projekte für weitere Akquise
- **Scalable Process** - Wiederverwendbares Framework

---

## 🚀 Quick Start

### 1. Projekt klonen
```bash
git clone https://github.com/fellnerd/vibe-coding-websites.git
cd vibe-coding-websites
```

### 2. Casa Nonna lokal testen
```bash
cd casa-nonna
python3 -m http.server 8081
# → http://localhost:8081
```

### 3. Lead Research starten
- Brave Search API für neue Targets
- Playwright für Website-Analyse
- Customer Materials erstellen

---

## 📞 Kontakt & Support

**Daniel Fellner**  
- **Location:** St. Veit an der Glan, Kärnten
- **Specialization:** Website-Modernisierung für lokale Unternehmen
- **GitHub:** [@fellnerd](https://github.com/fellnerd)

---

## 📄 Lizenz

Dieses Projekt ist für kommerzielle Lead-Generation entwickelt. Alle Kundenprojekte bleiben Eigentum der jeweiligen Unternehmen.

---

**🎯 Ready für die nächste Website-Modernisierung!**