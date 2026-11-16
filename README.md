# Punti nascita – dataviz Radar QN

| Dataviz | Cartella | Dati |
|---|---|---|
| Meno nascite, meno ospedali (parti e punti nascita 2010-2025) | `parti-punti-nascita/` | `data/parti-punti-nascita.csv` |

**Fonte**: ministero della Salute, Rapporto CeDAP 2024 e 2025, tabella 1 ("Stato della rilevazione CeDAP").

**Trasformazioni**
- "Punti nascita" = colonna "Strutture ospedaliere che hanno inviato i dati CeDAP" (il rapporto stesso parla di "347 punti nascita" per il 2025).
- "Parti" = colonna "Schede CeDAP pervenute" (una scheda per parto).
- Serie limitata al 2010-2025 (dal 2008 tutte le 21 Regioni/P.A. inviano i dati).
- 2017: il file Excel del Ministero (2025) riporta 397 strutture, entrambi i rapporti PDF 399. Usato 399, segnalato nel CSV e nel tooltip.
- Calcolati nella pagina: variazioni 2010-2025, parti medi per punto nascita, calo massimo in due anni (annotazione).

Per aggiornare il grafico basta modificare il CSV.
