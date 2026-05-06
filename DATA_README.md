# Project 14 Data Setup

## Data Files Included

The essential data for Project 14 is packaged in `SDY212_data_essential.zip` (54 MB):

- **SDY212_WholeBlood_Microarray_update_11242014.389992.txt** (161 MB uncompressed)
  - Gene expression matrix (microarray signals)
  - 47,000+ probes × 92 samples
  
- **biosample.txt** (87 KB)
  - Maps biosamples to subjects and time points
  - Includes: SUBJECT_ACCESSION, STUDY_TIME_COLLECTED, descriptions
  
- **msb201315-s2_assessment.txt** (5 KB)
  - Subject-level metadata
  - Includes: age, gender, BMI, FLU_EVR (symptom status), vaccination history

## Gene Ontology (GO) Data

**Approach: Automatic Download (Option A)**

The notebook uses `gseapy` for pathway enrichment analysis, which automatically downloads GO databases from Enrichr on first use:

```python
import gseapy as gp
enrich = gp.enrichr(genes, gene_sets=['GO_Biological_Process_2021'])
```

**Requirements:**
- Internet connection during Step 7 (pathway enrichment)
- `gseapy` installed: `pip install gseapy`

**Advantages:**
- No extra files to manage
- Automatically uses latest GO/Enrichr database versions
- Standard bioinformatics workflow
- Locally cached after first download

## File Paths in Notebook

The notebook expects this structure:

```
Proj3_Group14_I320D_BiomedDataSci/
├── SDY212/
│   ├── ResultFiles/Illumina_BeadArray/
│   │   └── SDY212_WholeBlood_Microarray_update_11242014.389992.txt
│   ├── SDY212-DR58_Tab/Tab/
│   │   └── biosample.txt
│   └── StudyFiles/
│       └── msb201315-s2_assessment.txt
└── Project_14_GeneExpression_Analysis.ipynb
```

## To Share with Group Partner

1. Extract `SDY212_data_essential.zip`
2. Ensure project structure matches above
3. Run the notebook - gseapy will handle GO data automatically

## Notes

- Total uncompressed data: ~161 MB (mostly expression matrix)
- All paths are absolute in the notebook (update for your machine)
- GO data is auto-cached in `~/.cache/gseapy/` after first enrichment run
