---
tags:
  - biologi
  - bioinformatika
  - komputasi
  - data-biologi
created: 2026-08-20
aliases: [bioinformatics, bioinformatika, computational-biology]
---

# Bioinformatika

Bioinformatika adalah ilmu yang menggunakan metode komputasi dan matematika untuk menganalisis data biologi, terutama data sekuens genetik, struktur protein, dan data omics. Ini adalah bidang interdisipliner antara biologi, ilmu komputer, statistika, dan matematika.

## Sejarah Singkat

- **1960-an** — Penciptaan database sekuens protein (dayhoff, atlas protein)
- **1977** — Frederick Sanger mengembangkan metode sekuensing DNA
- **1990-an** — Proyek Genom Manusia membutuhkan tools komputasi
- **2003** — Proyek Genom Manusia selesai
- **2010-an** — Next-generation sequencing (NGS) menghasilkan data dalam jumlah masif
- **2020-an** — AI/ML dalam prediksi struktur protein (AlphaFold)

## Jenis Data Biologi

### Genomik
- **Sekuens DNA** — Urutan basa nitrogen (A, T, G, C)
- **Genom** — Seluruh sekuens DNA suatu organisme
- **Transkriptom** — Kumpulan semua mRNA yang diekspresikan
- **Proteom** — Kumpulan semua protein
- **Metabolom** — Kumpulan semua metabolit

### Data Struktural
- **Struktur protein** — Koordinat atom dari kristalografi sinar-X, cryo-EM, NMR
- **Database:** PDB (Protein Data Bank)

## Tools & Database Penting

### Database Utama
| Database | Isi | URL |
| --- | --- | --- |
| GenBank | Sekuens DNA & RNA | ncbi.nlm.nih.gov/genbank |
| UniProt | Protein | uniprot.org |
| PDB | Struktur protein | rcsb.org |
| Ensembl | Genom vertebrata | ensembl.org |
| KEGG | Jalur metabolisme | genome.jp/kegg |
| Pfam | Domain protein | pfam.xfam.org |

### Tools Analisis
| Tool | Fungsi |
| --- | --- |
| BLAST | Pencarian sekuens mirip (sequence alignment) |
| Clustal Omega | Multiple sequence alignment |
| MUSCLE | Multiple sequence alignment |
| RAxML | Filogenetik berbasis maximum likelihood |
| HMMER | Pencarian domain protein (hidden Markov model) |
| GROMACS | Simulasi dinamika molekuler |
| AlphaFold | Prediksi struktur protein (AI/ML) |
| BWA/Bowtie | Mapping sekuens ke referensi |

### Pemrograman dalam Bioinformatika
- **Python** — Paling populer (Biopython, pandas, scikit-learn)
- **R** — Statistika dan visualisasi (Bioconductor)
- **Perl** — Analisis teks sekuens (historical)
- **Bash/Unix** — Pipeline sekuensing (awk, grep, sed)

## Analisis Sekuens

### Sequence Alignment
- **Pairwise alignment** — Membandingkan 2 sekuens (BLAST)
- **Multiple alignment** — Membandingkan banyak sekuens (Clustal, MUSCLE)
- **Scoring matrix:** BLOSUM62 (protein), PAM (protein), match/mismatch (DNA)

### BLAST (Basic Local Alignment Search Tool)
- Mencari sekuens mirip di database
- Parameter penting:
  - **E-value** — Jumlah kecocokan acak yang diharapkan (lebih kecil = lebih signifikan)
  - **Bit score** — Skor kecocokan (lebih tinggi = lebih mirip)
  - **Identity** — Persentase kecocokan basa/asam amino

### Pemetaan Gen (Gene Mapping)
- **Linkage mapping** — Peta berdasarkan frekuensi rekombinasi
- **Physical mapping** — Peta berdasarkan jarak fisik (bp)
- **QTL mapping** — Mengidentifikasi lokus yang mempengaruhi sifat kuantitatif

## Filogenetika Komputasional

### Membangun Pohon Filogenetik
1. **Penyelarasan sekuens** (alignment)
2. **Pemilihan model evolusi** (JC69, GTR, WAG)
3. **Pembangunan pohon** (Neighbor-Joining, Maximum Likelihood, Bayesian)
4. **Penilaian kepercayaan** (bootstrap, posterior probability)

### Interpretasi
- **Clade** — Kelompok monofiletik (spesies yang berbagi nenek moyang bersama)
- **Sister group** — Dua clade yang paling dekat
- **Outgroup** — Spesies referensi untuk menentukan arah evolusi

## Next-Generation Sequencing (NGS)

### Tipe NGS
| Platform | Tipe | Output |
| --- | --- | --- |
| Illumina | Short-read (150-300 bp) | Tinggi akurasi, murah per read |
| PacBio | Long-read (10-100 kb) | Berguna untuk genome assembly |
| Oxford Nanopore | Ultra-long-read (>100 kb) | Portable, real-time sequencing |

### Pipeline Analisis NGS
1. Quality control (FastQC)
2. Trimming adapter (Trimmomatic)
3. Mapping ke referensi (BWA, STAR)
4. Variant calling (GATK)
5. Annotation (ANNOVAR, SnpEff)
6. Interpretasi

## Metagenomik
- Sekuensing DNA langsung dari sampel lingkungan (tanah, laut, usus)
- Tidak perlu kultur → mendeteksi organisme yang tidak bisa dikultur
- **16S rRNA sequencing** — Identifikasi bakteri
- **Shotgun metagenomics** — Sekuensi seluruh genom dari komunitas

## Kecerdasan Buatan dalam Biologi

### AlphaFold (DeepMind)
- **AlphaFold2** — Memprediksi struktur protein dari sekuens saja
- Akurasi mendekati eksperimen laboratorium
- Database: AlphaFold DB (200+ juta struktur)

### Aplikasi AI Lainnya
- **DeepVariant** — Variant calling menggunakan deep learning
- **Drug discovery** — Prediksi interaksi obat-target
- **Single-cell analysis** — Pengelompokan sel berdasarkan ekspresi gen
- **Cancer genomics** — Identifikasi mutasi driver

## Topik Terkait
- [[Biologi]]
- [[Genetika]]
- [[Biologi Molekuler]]
- [[Bioteknologi]]
