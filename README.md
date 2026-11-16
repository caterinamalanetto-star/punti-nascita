# Punti nascita – dataviz Radar QN

| Dataviz | Cartella | Dati |
|---|---|---|
| Meno nascite, meno ospedali (parti e punti nascita 2010-2025) | `parti-punti-nascita/` | `data/parti-punti-nascita.csv` |
| Dove non si nasce più (mappa dei tempi verso il punto nascita) | `mappa-punti-nascita/` | `data/tempi-comuni.csv`, `data/punti-nascita-2024.csv`, `data/comuni.json`, `data/regioni.json` |
| Quanto è lontano il primo parto (scenari e dieci territori) | `distanze-parto/` | `data/tempi-comuni.csv`, `data/territori.csv`, `data/punti-nascita-2024.csv` |
| Senza Nottola e Campostaggia (provincia di Siena) | `siena-nottola/` | `data/siena-nottola.csv` |
| Ogni ospedale un punto (punti nascita per parti e area interna) | `ospedali-punti-nascita/` | `data/punti-nascita-2024.csv`, `data/tempi-comuni.csv` |
| La sicurezza in cifre (terapia intensiva e pretermine per classe) | `sicurezza-punti-nascita/` | `data/sicurezza-classi.csv` (CeDAP 2025, tab. 6 e 9) |
| Quanti minuti, quante persone (curva dei residenti per minuti) | `minuti-persone/` | `data/curva-minuti.csv`, calcolato da `data/tempi-comuni.csv` |

## Fonti
- Ministero della Salute, Rapporti CeDAP 2024 e 2025, tab. 1 (serie 2010-2025).
- Agenas, Programma nazionale esiti: "Parti: volume di ricoveri" per struttura, 2024.
- Ministero della Salute, open data "Posti letto per stabilimento ospedaliero e disciplina" (disciplina 37, Ostetricia e ginecologia), 2010.
- Istat, Matrici delle distanze tra comuni (tempi di percorrenza), tutte le 20 Regioni.
- Istat, Confini delle unità amministrative al 1° gennaio 2026.
- Dipartimento per le politiche di coesione, Mappa Aree interne 2020 (classi e residenti al censimento 2020).

## Metodo
- **Punti nascita 2024**: strutture PNE con almeno 10 parti nell'anno (378 su 406; sotto i 10 sono nascite occasionali in ospedali senza maternità, criterio usato anche dal PNE).
- **Tempo**: per ogni comune, minimo tempo di percorrenza Istat (colonna TEP_TOT, minuti) verso un comune che ospita un punto nascita; 0 se il punto nascita è nel comune. I tempi sono tra i centri dei comuni: vicino alle grandi città la distanza reale può essere minore. Per le isole minori il tempo include il traghetto.
- **Scenario "soglia 500"**: restano solo le strutture con almeno 500 parti nel 2024 (soglia minima dell'accordo Stato-Regioni del 16 dicembre 2010).
- **2010**: comuni con un reparto di Ostetricia e ginecologia nel 2010. Non tutti facevano parti, quindi le distanze 2010 sono sottostimate.
- **Reparti chiusi**: comuni con un reparto di Ostetricia e ginecologia nel 2010 e senza punto nascita nel 2024 (`data/reparti-chiusi.csv`).
- Codici dei comuni riallineati ai confini 2026 (fusioni, nuove province sarde) per nome e Regione.
- 2017 (grafico 1): il file Excel del Ministero riporta 397 strutture, i rapporti PDF 399. Usato 399.
- Geometrie semplificate su una griglia di 400 metri.
- **Siena**: stesso calcolo per i 35 comuni della provincia togliendo i punti nascita di Montepulciano (Nottola) e Poggibonsi (Campostaggia); restano tutti gli altri, anche fuori regione (Orvieto, Arezzo).
- Grafico 1: la serie CeDAP conta le strutture ospedaliere (un'azienda con più sedi conta una volta): 347 strutture nel 2025 a fronte di 382 punti nascita.
- Nomi dei comuni e sigle delle province: elenco ufficiale Istat al 1° gennaio 2026 (comprese le nuove province sarde del 2025). Nomi delle strutture: quelli del PNE con maiuscole e accenti normalizzati; l'originale è nella colonna `Struttura (PNE)`.
