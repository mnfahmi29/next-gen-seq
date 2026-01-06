**⚠️⚠️Desclaimer: due to my new step in Github, I will post my code as soon as possible⚠️⚠️**  
# 🧬 NGS Ubuntu Python Pipeline

Reproducible, modular Python-based workflows for **Next-Generation Sequencing (NGS)** analysis on **Ubuntu**, covering quality control, alignment, variant processing, annotation, and downstream biological interpretation (e.g. pathway analysis).

This repository is designed as a **research-grade toolkit** rather than a monolithic black-box pipeline: each step is explicit, inspectable, and independently runnable.

---

## 🎯 Scope & Philosophy

This repo prioritizes:

- **Transparency** — every step is readable and modifiable
- **Modularity** — QC, alignment, variants, and pathway analysis are separable
- **Reproducibility** — fixed environments, deterministic outputs
- **Clinical realism** — designed around real NGS workflows (WES/WGS, tumor studies)

> This repository is intended for **research and educational use**, not as a validated clinical diagnostic pipeline.

---

## 📁 Repository Structure

```

next-gen-seq/  
│  
├── README.md  
├── environment/  
│   ├── environment.yml          # Conda environment  
│   └── requirements.txt         # Pip fallback  
│  
├── data/  
│   ├── raw/                     # FASTQ / BAM / VCF (gitignored)  
│   ├── reference/               # Genome references (paths only)  
│   └── testdata/                # Tiny example files (optional)  
│  
├── src/  
│   ├── 01_qc/                   # FASTQ/BAM quality control  
│   ├── 02_alignment/            # BWA / STAR alignment  
│   ├── 03_postprocess/          # Sorting, duplication, metrics  
│   ├── 04_variant_calling/      # Variant calling  
│   ├── 05_annotation/           # VEP / ANNOVAR  
│   └── 06_pathway_analysis/     # Gene set & enrichment analysis  
│  
├── configs/  
│   └── config.yaml              # Central configuration  
│  
├── results/  
│   ├── qc/  
│   ├── alignment/  
│   ├── variants/  
│   └── reports/  
│  
├── scripts/  
    └── run_pipeline.sh          # Pipeline runner  

````

---

## 🖥️ System Requirements

- **OS**: Ubuntu 20.04+ (tested)
- **Python**: ≥ 3.10
- **Package manager**: Conda / Mamba recommended
- **External tools** (installed separately):
  - FastQC, MultiQC
  - BWA / STAR
  - Samtools
  - GATK / bcftools (optional)
  - ANNOVAR / VEP (optional)

> External tools are **not bundled** and must be available in `$PATH`.

---

## 🧪 Environment Setup
-will be released soon

---

## ⚙️ Configuration

All paths and parameters are defined in:

```
configs/config.yaml
```

Typical fields include:

* input FASTQ / BAM directories
* reference genome paths
* output directories
* number of threads
* analysis toggles (e.g. germline vs somatic)

**No hard-coded paths** should remain in scripts.

---

## ▶️ Running the Pipeline

Example (end-to-end):

```bash
bash scripts/run_pipeline.sh --config configs/config.yaml
```

Or run modules individually:

```bash
python src/01_qc/run_fastqc.py
python src/02_alignment/run_bwa.py
python src/06_pathway_analysis/enrichment.py
```

Each module writes outputs to a **predictable subfolder** under `results/`.

---

## 📤 Inputs & 📥 Outputs

### Inputs

* FASTQ / BAM / VCF files (not tracked in git)
* Reference genome files (paths only)
* Optional clinical or cohort metadata

### Outputs

* QC reports (FastQC / MultiQC)
* Aligned BAM files + metrics
* Variant tables (VCF / TSV)
* Gene lists & pathway enrichment results
* Figures and summary tables

---

## 🔒 Data & Privacy Policy

This repository **does NOT contain**:

* Raw sequencing data
* Identifiable sample information
* Clinical records

Users are responsible for:

* Mounting local data securely
* Complying with institutional and ethical guidelines

---

## 🧠 Intended Use Cases

* Academic NGS analysis (WES / WGS)
* Tumor cohort comparison
* Variant filtering & annotation
* Downstream pathway analysis
* Methodological prototyping

---

## 🚧 Project Status

* ✔ Core workflows exist (Ubuntu-tested)
* 🚧 Ongoing refactoring into modular structure
* 🚧 Documentation and tests in progress

This repo is **actively developed** and evolves as new analyses are added.

---

## 📚 Citation & Attribution

If you use this repository in academic work, please cite:

> Fahmi MN. *NGS Ubuntu Python Pipeline*. GitHub repository.

A `CITATION.cff` file will be added in a future release.

---

## 🧩 Future Extensions

* Snakemake / Nextflow wrapper
* Containerized execution
* More robust logging & resume logic
* Integration with methylation & RNA-seq pipelines

---

## 📬 Contact

For questions or collaboration ideas, please open an issue.

---

## 👤 Author

**Muhammad Nur Fahmi, MD**

---

**Disclaimer:**
This software is provided for research purposes only and is **not validated for clinical decision-making**.

---

