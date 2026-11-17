# Seeing Through Green: replication code

## Contents

`code/` holds the scripts:

- `04_agreement.py`: inter-annotator agreement
- `06_gold_standard.py`: resolve labels, apply design weights
- `07_metriche.py`: weighted precision, recall, F1, bootstrap CIs
- `26_universo_granted.py`: granted universe, final flags, reweighting, classifier comparison tables
- `32_descrittive_csv.py`: descriptive statistics, appendix tables and figures
- `12_sensitivity.py`: sensitivity of the vocabulary
- `17_provenienza_prestazione.py`: per-expression precision
- `18_scomposizione_cpc.py`: false positives by technological subclass
- `27_combinazioni.py`: combinations of the three classifiers
- `33_cella_solo_testo.py`: patents retrieved only by the text-based classifier
- `34_robustezza_annotatori.py`: robustness of the results to leaving out one annotator
- `36_citazioni_gold.py`: citations of classified green patents, population and gold standard
- `37_tabella4_citazioni.py`: citation regressions
- `22_diagnostica_bert.py`: matching and metrics for the unscreened expansions (imported by 41)
- `41_bert_.py`: Word2Vec against BERT for Patents
- `10_bert_espansione.py`: BERT expansion; matching functions used by the others
- `15_w2v_grezzo.py`: unscreened Word2Vec expansion

`10` needs a GPU and the BERT for Patents model; `15` needs the Word2Vec
model trained on green patents. Their outputs are read by `22` and `41`.

`run_all.py` runs the other scripts in order. Set `BASE` at the top of it, and
at the top of each script, to the folder that holds `data/` and `results/`.

`environment.txt` lists the Python version and the packages the code imports.

`MANIFEST.sha256` holds the checksums. Verify with:

    sha256sum -c MANIFEST.sha256

## Data

The code reads the patent corpus and the gold standard, which are built on
PATSTAT text and identifiers and cannot be redistributed. The vocabulary is the
one printed in Tables A1 to A3 of the paper; the scripts read it from
`data/parquet/vocabolario.tsv`.
