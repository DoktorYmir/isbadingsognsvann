# 🏊 Sognsvann Badetemperatur

Nettside som estimerer og visualiserer vanntemperaturen i Sognsvann gjennom høst, vinter og vår.

🌐 **Live side:** [sognsvann.netlify.app](https://sognsvann.netlify.app)

---

## Hva gjør siden?

- Viser **estimert vanntemperatur i dag og om en uke**, basert på værmeldingen fra Yr.no
- Bruker en **termodynamisk modell** der vanntemperaturen gradvis tilpasser seg lufttemperaturen:
  
  > Ny VannTemp = Gammel VannTemp + 0,12 × (LuftTemp − Gammel VannTemp)

- Henter **7-dagersprognose** med værikon basert på dagstimer (kl. 8–18) fra Meteorologisk Institutts API
- Viser en **graf** med egne målinger fra 2026 sammenlignet med referansedata fra 2025
- Grafen dekker perioden **1. august – 31. juli** med sesong-etikettene Høst / Vinter / Vår

---

## Filer i repoet

| Fil | Beskrivelse |
|-----|-------------|
| `index.html` | Hele nettsiden (selvinneholdt, ingen bygg-steg nødvendig) |
| `2026vanntemp.csv` | Egne målinger av vanntemperatur i 2026 |
| `README.md` | Denne filen |

---

## Legge til nye målinger

Åpne `2026vanntemp.csv` og legg til en ny linje på formatet:

```
DD.MM.ÅÅÅÅ;temperatur
```

Eksempel:
```
25.10.2026;9
01.11.2026;7
```

Klikk **Commit changes** — Netlify oppdaterer nettsiden automatisk innen ca. 1 minutt.

---

## Teknisk

- **Værdata:** [Meteorologisk Institutt / Yr.no](https://api.met.no) — locationforecast 2.0
- **Graf:** [Chart.js 4.4](https://www.chartjs.org/)
- **Hosting:** [Netlify](https://netlify.com) (gratis)
- Ingen server, ingen database, ingen bygg-steg — kun én HTML-fil
- Fungerer i alle moderne nettlesere

---

## Datakilder

- **Referansedata 2025:** Egne målinger ved Sognsvann, interpolert
- **Værprognose:** Hentet live fra `api.met.no` via CORS-proxy
- **Startverdi for prognosen:** Siste rad i `2026vanntemp.csv`

---

*Laget for personlig bruk. Temperaturestimatene er modellberegninger og ikke offisielle målinger.*
