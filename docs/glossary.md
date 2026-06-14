---
layout: default
title: Glossary
nav_order: 8
permalink: /glossary/
---

# Glossary: Ensembl, Galaxy, AI, Prompt Engineering & RAG

A reference glossary spanning genome resources, workflow platforms, and the
generative-AI concepts used to build training and analysis tools around them.

---

## 1. Ensembl

**Ensembl** — A genome browser and annotation database jointly run by EMBL-EBI
and the Wellcome Sanger Institute, providing gene sets, variation, comparative
genomics and regulatory data across vertebrate genomes.

**Ensembl Genomes** — A sister project extending the Ensembl platform to
non-vertebrate taxa, divided into Ensembl Plants, Fungi, Metazoa, Protists and
Bacteria. *Ensembl Plants* hosts *Oryza sativa* and other crop genomes.

**Assembly** — A specific reconstructed version of a genome sequence (e.g.
GRCh38, IRGSP-1.0 for rice). Annotations are tied to an assembly version.

**Gene annotation / gene set** — The catalogue of genes, transcripts and their
structures predicted or curated for an assembly, released as the "Ensembl gene
set."

**Stable ID** — A persistent identifier for a feature: `ENSG` (gene), `ENST`
(transcript), `ENSP` (protein). Species-specific prefixes exist (e.g. `OS` for
rice in Ensembl Plants).

**BioMart** — A data-mining interface for bulk querying and exporting Ensembl
data by filters and attributes without writing code.

**VEP (Variant Effect Predictor)** — A tool that annotates variants with their
predicted consequences on genes, transcripts and proteins (e.g. missense,
stop-gained), plus regulatory and population-frequency context.

**Compara** — The comparative-genomics database providing gene trees,
homology relationships and whole-genome alignments across species.

**Homologue** — A gene related to another by common ancestry; split into
**orthologues** (related by speciation, across species) and **paralogues**
(related by duplication, often within a species).

**Gene tree** — A phylogenetic tree representing the evolutionary history of a
gene family, used to infer orthology and paralogy.

**Regulatory Build** — Ensembl's genome-wide annotation of regulatory features
(promoters, enhancers, transcription-factor binding sites) derived from
epigenomic data.

**Variation database** — The component storing known sequence variants (SNVs,
indels, structural variants) and their population frequencies.

**GTF / GFF** — Tab-delimited text formats describing gene and feature
coordinates; the standard way Ensembl annotation is exported for pipelines.

**REST API** — Ensembl's programmatic interface for retrieving sequences,
features and annotations over HTTP, suitable for scripting and automation.

---

## 2. Galaxy Workbench

**Galaxy** — An open-source, web-based platform for accessible, reproducible
data-intensive bioinformatics, letting users run tools and pipelines without
command-line access.

**Galaxy instance** — A deployed Galaxy server. Public examples include
usegalaxy.org (US), usegalaxy.eu (Europe) and usegalaxy.org.au; institutions
also run private instances.

**History** — A user's working record of datasets and the operations applied to
them, forming an auditable analysis session.

**Dataset** — Any input, intermediate or output file tracked within a Galaxy
history, with associated metadata and provenance.

**Dataset collection** — A structured group of datasets (e.g. a list of
samples, or paired reads) processed together as a single logical unit.

**Tool** — A wrapped command-line program exposed in Galaxy through a graphical
form for setting parameters.

**Tool wrapper** — The XML definition that maps a command-line tool's inputs,
parameters and outputs into Galaxy's interface.

**Tool Shed** — Galaxy's app store for discovering and installing community-
contributed tools and dependencies into an instance.

**Workflow** — A saved, reusable chain of tools that connects outputs to
inputs, enabling automated, repeatable multi-step analyses.

**Invocation** — A single execution run of a workflow, recording the inputs,
parameters and resulting datasets.

**Job** — The unit of computation Galaxy dispatches to a backend (local,
cluster or cloud) when a tool runs.

**Interactive tools** — Live environments such as Jupyter or RStudio launched
inside Galaxy for exploratory analysis alongside standard tools.

**Provenance / reproducibility** — Galaxy's automatic capture of every tool,
version, parameter and dataset so an analysis can be rerun or shared exactly.

**Conda / BioConda integration** — The dependency-resolution system Galaxy uses
to install reproducible tool environments.

**Galaxy Training Network (GTN)** — A community-maintained collection of
hands-on tutorials and training materials built on Galaxy.

---

## 3. Genome Annotation & Sequence Characterization

### Structural annotation

**Genome annotation** — The process of identifying functional elements in a
genome and describing what and where they are. It splits into *structural*
annotation (locating features) and *functional* annotation (assigning roles).

**Structural annotation** — Determining the location and architecture of
features such as genes, exons, introns and untranslated regions along the
sequence.

**Gene prediction (gene calling)** — Computationally identifying gene locations
and structures, either *ab initio* (from sequence signals alone) or
*evidence-based* (guided by RNA-seq, ESTs or protein alignments).

**Ab initio prediction** — Gene prediction from intrinsic sequence features
(codon usage, splice signals) using trained models such as AUGUSTUS or GeneMark.

**Evidence-based / homology-based annotation** — Predicting gene models by
aligning external evidence — transcripts, proteins from related species — to the
genome.

**Annotation pipeline** — An integrated workflow (e.g. MAKER, BRAKER) that
combines repeat masking, evidence alignment and gene predictors into consensus
gene models.

**Gene model** — The defined structure of a gene: its exons, introns, coding
sequence and untranslated regions, including alternative transcripts.

**ORF (open reading frame)** — A stretch of sequence between a start and stop
codon with the potential to encode a protein.

**CDS (coding sequence)** — The portion of a transcript that is translated into
protein, excluding untranslated regions.

**Exon / Intron** — Exons are sequence segments retained in the mature
transcript; introns are removed by splicing.

**UTR (untranslated region)** — Transcribed but non-coding regions flanking the
CDS (5′ and 3′ UTRs) that influence regulation and stability.

**Splice site** — The sequence boundary (canonically GT…AG) marking where
introns are removed and exons joined.

**Repeat masking** — Identifying and flagging repetitive sequence (e.g. with
RepeatMasker) before gene prediction; *soft masking* lowercases repeats while
*hard masking* replaces them with Ns.

**Transposable element** — A mobile, often repetitive DNA sequence; abundant in
plant genomes and a major focus of repeat annotation.

**ncRNA annotation** — Identifying non-coding RNAs such as rRNA, tRNA, miRNA and
lncRNA, often with specialised tools (e.g. tRNAscan-SE, Infernal/Rfam).

**Pseudogene** — A sequence resembling a functional gene but disabled by
mutations; flagged during annotation to avoid false gene calls.

**Annotation transfer / liftover** — Projecting annotations from one assembly or
species onto another via alignment or synteny, useful for newly assembled
genomes.

**Synteny** — Conservation of gene order and content across genomes, used to
support annotation transfer and comparative analysis.

**GFF3** — The standard hierarchical text format for representing structural
annotation (gene → mRNA → exon/CDS) with coordinates and attributes.

### Functional annotation & sequence characterization

**Functional annotation** — Assigning biological meaning to features —
molecular function, biological process, pathways — typically by transferring
information from characterised homologues.

**Homology search** — Finding similar sequences in databases (e.g. BLAST,
DIAMOND, MMseqs2) to infer function or evolutionary relationship.

**Sequence alignment** — Arranging sequences to maximise correspondence;
*pairwise* compares two, *multiple sequence alignment (MSA)* compares many to
reveal conserved positions.

**Profile HMM (Hidden Markov Model)** — A statistical model of a sequence family
capturing position-specific conservation, used to detect distant homologs and
domains.

**Protein domain** — A distinct, often independently folding functional unit
within a protein; conserved domains are strong functional clues.

**Motif** — A short, recurring sequence pattern associated with a function, such
as a binding site or catalytic site.

**InterPro / InterProScan** — A resource (and its scanning tool) that
integrates multiple signature databases (Pfam, PROSITE, etc.) to assign domains
and functional sites.

**Pfam** — A widely used database of protein families represented as profile
HMMs.

**Gene Ontology (GO)** — A controlled vocabulary describing gene products across
three aspects: molecular function, biological process and cellular component.

**KEGG / pathway annotation** — Mapping genes to metabolic and signalling
pathways using resources such as KEGG.

**EC number** — A four-part Enzyme Commission identifier classifying an enzyme
by the reaction it catalyses.

**Signal peptide / transmembrane prediction** — Identifying localisation and
membrane-spanning features from sequence (e.g. SignalP, TMHMM/DeepTMHMM),
relevant to characterising proteins like ER-localised receptors.

**BUSCO** — A completeness assessment that checks for expected single-copy
orthologues to gauge how complete an assembly or annotation is.

**GC content** — The proportion of guanine and cytosine bases in a sequence; a
basic compositional descriptor used in characterization and quality checks.

**k-mer** — A substring of length *k*; k-mer frequencies underpin many
assembly, classification and characterization methods.

**Codon usage** — The relative frequency of synonymous codons in coding
sequence, used in gene prediction and expression analysis.

**Annotation evidence / confidence** — Metadata indicating how a feature was
supported (experimental, computational, homology), important for judging
reliability of a gene model.

## 4. Artificial Intelligence (Core ML Concepts)

**Artificial Intelligence (AI)** — The broad field of building systems that
perform tasks normally requiring human intelligence, such as reasoning,
perception or language understanding.

**Machine learning (ML)** — A subset of AI where systems learn patterns from
data rather than being explicitly programmed with rules.

**Deep learning** — ML using multi-layered neural networks to learn
hierarchical representations directly from raw data.

**Neural network** — A model of interconnected nodes ("neurons") organised in
layers, whose connection strengths (weights) are adjusted during training.

**Parameters / weights** — The learned numerical values inside a model that
encode what it has learned; modern LLMs have billions of them.

**Training / pretraining** — The process of fitting model parameters to data.
*Pretraining* builds general capability on large corpora before any task-
specific adaptation.

**Fine-tuning** — Further training of a pretrained model on a narrower dataset
to specialise it for a task or domain (e.g. adapting a genomics model to rice).

**Inference** — Using a trained model to generate predictions or outputs on new
inputs, as opposed to training it.

**Supervised vs. unsupervised learning** — Supervised learning uses labelled
examples; unsupervised learning finds structure in unlabelled data.

**Large language model (LLM)** — A neural network trained on vast text to
predict and generate language, capable of summarising, reasoning and answering
questions.

**Transformer** — The neural-network architecture underlying modern LLMs, built
around an attention mechanism that weighs the relevance of different parts of
the input.

**Foundation model** — A large, general-purpose model pretrained on broad data
that can be adapted to many downstream tasks.

**Token** — The unit of text a model processes (a word, sub-word or character
fragment); models read and generate text one token at a time.

**Embedding** — A numerical vector representing the meaning of a token,
sentence or document, where similar items sit close together in vector space.

**Context window** — The maximum amount of text (in tokens) a model can
consider at once, including both the prompt and its response.

**Hallucination** — A confident but factually incorrect or fabricated model
output, a key risk to mitigate in scientific applications.

**Multimodal** — A model able to process more than one data type, e.g. text and
images together.

**Agent / agentic AI** — An AI system that plans and takes multi-step actions
toward a goal, often calling external tools, with optional human-in-the-loop
oversight.

---

## 5. Prompt Engineering

**Prompt** — The input text given to a model that frames the task and provides
any instructions, context or examples.

**Prompt engineering** — The practice of designing and refining prompts to
elicit accurate, reliable and well-formatted model outputs.

**System prompt** — A high-level instruction that sets a model's role,
constraints and behaviour for an entire session, separate from user messages.

**Zero-shot prompting** — Asking a model to perform a task with no worked
examples, relying solely on instructions.

**Few-shot prompting** — Providing a handful of example input–output pairs in
the prompt to demonstrate the desired behaviour.

**In-context learning** — A model's ability to adapt to a task purely from
examples and instructions in the prompt, without updating its weights.

**Chain-of-thought** — Prompting a model to reason step by step before
answering, which improves performance on multi-step problems.

**Role / persona prompting** — Instructing the model to adopt a specific
viewpoint or expertise (e.g. "act as a genomics curator") to shape its tone and
focus.

**Prompt template** — A reusable, parameterised prompt structure with slots for
variable inputs, enabling consistent automated use.

**Structured output** — Constraining a model to return a defined format such as
JSON or a table, so its output can be parsed programmatically.

**Temperature** — A setting controlling output randomness; lower values give
deterministic, focused responses, higher values give more varied ones.

**Prompt chaining** — Breaking a complex task into a sequence of prompts where
each step's output feeds the next.

**Guardrails** — Rules, filters or constraints applied to inputs and outputs to
keep model behaviour safe, on-topic and reliable.

**Prompt injection** — A security attack where malicious instructions hidden in
user input or external content try to override the intended prompt; a key
concern when models read untrusted data.

---

## 6. Retrieval-Augmented Generation (RAG)

**Retrieval-augmented generation (RAG)** — An architecture that retrieves
relevant documents from an external knowledge source and supplies them to an
LLM as context, grounding its answers in specific, up-to-date material.

**Knowledge base** — The curated collection of documents (papers, protocols,
annotations) that a RAG system retrieves from.

**Chunking** — Splitting source documents into smaller passages so they can be
embedded, indexed and retrieved at a useful granularity.

**Embedding model** — A model that converts text chunks and queries into
vectors for similarity comparison; distinct from the generation LLM.

**Vector database** — A store optimised for indexing embeddings and performing
fast nearest-neighbour similarity search (e.g. FAISS, Chroma, Pinecone,
Weaviate).

**Indexing** — Preprocessing the knowledge base into embeddings and data
structures so retrieval is efficient at query time.

**Semantic search** — Retrieval based on meaning via embedding similarity,
rather than exact keyword matching.

**Top-k retrieval** — Returning the *k* most relevant chunks for a query to
pass into the model's context.

**Hybrid search** — Combining dense (embedding-based) retrieval with sparse
keyword methods such as BM25 to improve recall and precision.

**Re-ranking** — A second-pass step that reorders retrieved candidates by
relevance, often with a more accurate but costlier model.

**Grounding** — Tying a model's response to retrieved evidence so claims are
traceable to source documents, reducing hallucination.

**Context augmentation** — Injecting retrieved passages into the prompt so the
model generates an answer informed by them.

**Citation / attribution** — Linking parts of a generated answer back to the
specific source passages that support them, important for scientific trust.

