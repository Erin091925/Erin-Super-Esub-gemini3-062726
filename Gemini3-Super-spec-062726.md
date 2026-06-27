# Technical Specification Document: Project Aetheris

## Agentic AI System for Medical Device Submission Review and Assessment

---

## 1. Executive Summary & System Overview

### 1.1 Document Purpose

This technical specification outlines the software architecture, engine design, data flows, and functional interfaces for **Project Aetheris**, an advanced, enterprise-grade agentic AI platform. Project Aetheris is engineered to automate, accelerate, and optimize the review of medical device regulatory submission materials (e.g., FDA 510(k), De Novo, or PMA dossiers). By combining localized document processing with highly adaptive large language model (LLM) orchestration, the system processes heterogeneous regulatory materials, iterates on regulatory skill sets, addresses compliance criteria, and compiles complete medical device review reports.

### 1.2 System Context

Regulatory submissions for medical devices frequently comprise hundreds or thousands of pages of unstructured, highly technical documentation. These dossiers span engineering specifications, clinical trial datasets, risk assessments ($ISO\ 14971$), and software validation files. Project Aetheris serves as an automated, interactive co-pilot for regulatory affairs (RA) professionals and internal reviewers. The system functions as an autonomous agentic framework that ingest files, executes flexible Optical Character Recognition (OCR), dynamically enhances its own rule books (`skill.md`), constructs exhaustive multi-dimensional questionnaires, and prints evaluation summaries using user-defined document definitions.

---

## 2. System Architecture & High-Level Design

### 2.1 Microservices and Component Topography

Project Aetheris utilizes a decoupled microservices architecture designed to run containerized execution environments over highly secure cloud infrastructures or on-premise air-gapped instances.

```
                                +-----------------------------------+
                                |         User Interface            |
                                |     (React / TailWind CSS)        |
                                +-----------------+-----------------+
                                                  | REST / WebSockets
                                                  v
+-------------------------------------------------+-------------------------------------------------+
|                                     Application Orchestration Layer                               |
+---------------------------------------------------------------------------------------------------+
|   +-----------------------+   +------------------------+   +-------------------+   +----------+   |
|   | Document Ingestion /  |   |   Dual-Engine OCR      |   |   Agent Logic &   |   | Export   |   |
|   | Processing Pipeline   |   |     Orchestrator       |   | Prompt Manager    |   | Engine   |   |
|   +-----------+-----------+   +-----------+------------+   +---------+---------+   +----+-----+   |
|               |                           |                          |                      |     |
+---------------|---------------------------|--------------------------|----------------------|-----+
                |                           |                          |                      |
                v                           v                          v                      v
    +-----------+-----------+   +-----------+------------+   +---------+---------+   +----+-----+
    |  PyMuPDF / PyPDF Engine|   | Local/LLM OCR Wrappers |   | Gemini 3.1 / LLM  |   | WeasyPrint/|
    |  & Trimming Sandbox   |   | (Tesseract, Paddle, etc) |   | Context Gateway   |   | Pandoc   |
    +-----------------------+   +------------------------+   +-------------------+   +----------+

```

* **User Interface (UI) Layer:** A responsive web application built with a modern frontend framework optimized for handling long markdown documents, real-time code rendering, and live text diffs.
* **Application Orchestration Layer (Backend API):** A Python-based backend utilizing asynchronous frameworks (FastAPI) to handle long-running background tasks, file management, and state transitions.
* **Agent Logic and Prompt Manager:** An advanced abstraction layer powered by structured runtime engines that manage conversation history, state storage, dynamic prompt injection, and multi-turn orchestration.
* **Asynchronous Task Queue (Celery/Redis):** Dedicated workers running decoupled workloads such as heavy file decoding, intensive local OCR extraction loops, and parallelized LLM text parsing.

### 2.2 System Core State Machine

The operation of the application follows a linear progressive state machine with back-propagation allowed at any historical junction. The global session tracking schema follows these primary states:

| State Identifier | State Name | Allowed Transitions | Data Dependency |
| --- | --- | --- | --- |
| `ST_INIT` | System Initialization | `ST_INGEST` | None |
| `ST_INGEST` | Material Ingestion & Trim | `ST_OCR_PROCESSING` | raw documents |
| `ST_OCR` | OCR Extraction Engine | `ST_SUMMARY_GEN` | trimmed document bytes |
| `ST_SUMMARY` | Narrative Transformation | `ST_SKILL_ALIGN` | unified ocr text payload |
| `ST_SKILL` | Skill Optimizing Pipeline | `ST_QA_GEN` | `skill.md` base + user prompt |
| `ST_QA` | Comprehensive Q&A Matrix | `ST_REPORT_COMPILE` | summarized text + finalized skill |
| `ST_REPORT` | Review Compilation & Export | `ST_INIT` (Reset) | interactive QA logs + documents |

---

## 3. Detailed Workflow & Feature Specifications

### 3.1 Phase 1: Ingestion & Document Manipulation (PDF Trimming)

The entry point of the platform handles heterogeneous ingestion profiles, accommodating Markdown (`.md`), Plain Text (`.txt`), Structured Objects (`.json`), and Portable Document Format (`.pdf`).

#### 3.1.1 Ingestion Specifications

* **File Size Matrix:** Individual file ceiling threshold at 50 MB for standard uploads; system handles batch directories up to 500 MB total aggregate context.
* **Validation Layer:** Enforces explicit file format inspections via magic-byte checking rather than file extension sniffing, insulating the application from malicious content injections.

#### 3.1.2 Advanced PDF Dissection and Trimming

Upon identification of a `.pdf` payload, the platform spawns a dedicated manipulation microservice:

1. **Exploratory Parsing:** The system evaluates the document using libraries like `PyMuPDF` (Fitz) or `PyPDF` to extract metadata, structural bookmarks, structural tags, and page counts.
2. **Visual Page Grid Generation:** The frontend renders a scalable grid of high-fidelity page previews (rasterized on-the-fly at 150 DPI into WebP structures via specialized background workers).
3. **Trimming Selector Control:** The user is provided an interactive target selection panel allowing custom array notation filtering (e.g., `1-15, 34, 50-89, -120` where negative values denote offsets from the document tail).
4. **Destructive Compilation Pipeline:** The system slices the original resource in memory based on the selected criteria, purging unselected pages, rebuilding the internal PDF cross-reference cross-tables (XREFs), and generating a streamlined document payload.
5. **Artifact Extraction:** The trimmed PDF asset is saved into an isolated object-store scratchpad, making it immediately available for standalone cryptographic validation hash creation (`SHA-256`) and client-side extraction downloading.

---

### 3.2 Phase 2: Dual-Engine OCR Framework (Python vs. LLM)

To ensure the processing of both clear digital texts and low-resolution scanned imagery, Project Aetheris incorporates a hybrid, dual-engine Optical Character Recognition ecosystem.

```
                     +---------------------------------------+
                     |        Trimmed PDF Document           |
                     +-------------------+-------------------+
                                         |
                                         v
                     +-------------------+-------------------+
                     |       User Engine Selection           |
                     +--------+---------------------+--------+
                              |                     |
             +----------------+                     +-----------------+
             | Python-Based Local OCR               | LLM-Based Native Multimodal OCR
             v                                      v
+------------+------------------------+   +--------+------------------------+
| Selectable Packages:                |   | Native Multimodal Core Engine   |
| 1. Tesseract OCR Engine            |   | Default: gemini-3.1-flash-lite  |
| 2. EasyOCR Engine                   |   | User Options: Pro / Custom Models|
| 3. PaddleOCR Engine                 |   +----------------+----------------+
+------------+------------------------+                    |
             |                                             | Apply High-Fidelity
             | Language Multi-Packs:                       | Extraction Prompt Template
             | English + Traditional Chinese               |
             +----------------+----------------------------+
                              |
                              v
            +-----------------+---------------------+
            | Unified JSON Character & Text Map     |
            +-----------------+---------------------+
                              |
                              v
            +-----------------+---------------------+
            |  Interactive Extraction Workspace UI   |
            +---------------------------------------+

```

#### 3.2.1 Option A: Localized Python-Based OCR Infrastructure

Engineered for strict data-residency compliance and predictable computing loops, this track provisions three optimized python bindings:

* **Tesseract OCR (`pytesseract`):** Optimized for structured, single-column textual data with linguistic modules configured for simultaneous character processing.
* **EasyOCR (`easyocr`):** End-to-end deep learning framework leveraging ResNet feature extraction pipelines and LSTM sequence modeling, ideal for complex spatial text arrangements.
* **PaddleOCR (`paddleocr`):** Ultra-high precision, industrial-grade PP-OCR pipeline configured explicitly to recognize dense layouts, technical schematics, and mixed language patterns.

The processing architecture handles complex linguistic profiles by pairing **Traditional Chinese (zh-tw)** and **English (en)**. Documents undergo automatic deskewing, binarization optimization via Adaptive Otsu Thresholding, and parallel layout analysis before text string translation.

#### 3.2.2 Option B: Native Multimodal LLM-Based OCR Engine

Leveraging advanced multi-modal spatial awareness, this track routes page payloads directly through an LLM layer.

* **Default Execution Base:** `gemini-3.1-flash-lite`. This model is optimized for low-latency, high-volume document ingestion pipelines, featuring a native 1-million-token context window that enables entire PDF files to be passed directly as visual/textual arrays without chunking bottlenecks.
* **Extensible Engine Selectors:** Users can scale operations up to frontier reasoning models (`gemini-3.5-flash`, `gemini-3.1-pro`) depending on data density or domain-specific complexity.
* **Custom Prompt Injection:** User interfaces provide an open engineering console allowing complete over-indexing of the system instruction.

##### Default Operational System Instruction for LLM-Based OCR:

```text
You are an advanced regulatory compliance document transcription engine specialized in high-fidelity medical device technical files. 
Your objective is to perform deep structural text extraction across all provided page images or document streams.

EXECUTIVE EXTRACTION LAWS:
1. Preserve structural placement: Maintain paragraph bounds, technical lists, numeric tables, data schematics, and tabular column structures using Markdown layouts.
2. Language Integrity: Transcribe mixed English and Traditional Chinese structures with high precision. Do not translate or cross-interpret words; transcribe verbatim.
3. Handle Artifacts: Extract form figures, checkboxes, approval stamps, signatures, and document metadata (e.g., document ID, revisions). If an element is a visual diagram, provide a descriptive tag: [Diagram: Description of visual system component].
4. No Editorial Noise: Output only the extracted textual data. Do not add introductory preambles or concluding explanations.

```

#### 3.2.3 Editing, Serialization, and Synchronization Workspace

The completed output from either tracking engine resolves into a uniform JSON schema containing page indexes, bounding coordinate mappings, and text values. This raw layer populates a split-screen **Interactive Extraction Workspace UI**:

* *Left Pane:* Text Editor with absolute line tracking and syntax highlighting.
* *Right Pane:* Visual high-resolution canvas matching extracted characters to the source document.
* *Export Framework:* Users can modify the raw output or download the full text array instantly as a single `.txt` string or a structured `.json` data tree.

---

### 3.3 Phase 3: Agentic Summary Transformation & Coral-Highlighting

Once text extraction is locked, an autonomous pipeline transforms unstructured text arrays into structured medical device regulatory submission summaries.

#### 3.3.1 Architectural Pipeline Execution

The transformation pipeline runs via an isolated processing agent that matches incoming content patterns against standard international classification frameworks (e.g., FDA 510(k) Substantial Equivalence structures, $ISO\ 13485$ Quality Management Systems, and $ISO\ 14971$ Risk Management Matrices).

The backend formats the final output into clean Markdown. Crucially, the transformation engine applies inline styling rules to render all identified core regulatory keywords, device names, critical values, and compliance status verdicts in **Coral Color (`#FF7F50`)**. To preserve clean markdown interpretation across multiple downstream compilers, keywords are wrapped in standard HTML tags: `<span style="color:#FF7F50;">[KEYWORD]</span>`.

#### 3.3.2 Regulatory Transformation Prompt Blueprint

```text
CONTEXT: You are a Lead Regulatory Engineering Analyst agent specialized in medical device regulatory dossiers (FDA 510(k), PMA, CE MDR).
TASK: Transform the provided raw OCR text compilation into an ultra-structured, highly polished submission summary document written in GitHub-Flavored Markdown.

STRUCTURAL TAXONOMY REQUIREMENTS:
Your summary must incorporate the following clear administrative layout sections:
1. ADMINISTRATIVE & IDENTIFICATION TRACKING
2. DEVICE DESCRIPTION & INTENDED USE
3. SUBSTANTIAL EQUIVALENCE (SE) MATRIX
4. BIOCOMPATIBILITY & MATERIAL SPECIFICATIONS
5. SOFTWARE VALIDATION, CYBERSECURITY & ELECTRICAL SAFETY
6. RISK MANAGEMENT & CLINICAL SUMMARY

CRITICAL INLINE CORAL HIGHLIGHTING RULES:
You must explicitly isolate and highlight key regulatory entities, metrics, compliance conclusions, standards identifiers, and device specifications by wrapping them EXACTLY in this HTML span syntax: <span style="color:#FF7F50;">**CRITICAL_TERM**</span>.

Target Entities for Coral Highlighting:
- Exact Device Brand Names and Manufacturer names (e.g., <span style="color:#FF7F50;">**AetherSurg Pulse-8**</span>)
- Regulatory pathways and submission tracking numbers (e.g., <span style="color:#FF7F50;">**510(k)**</span>, <span style="color:#FF7F50;">**K261234**</span>)
- Standard identification numbers (e.g., <span style="color:#FF7F50;">**ISO 13485**</span>, <span style="color:#FF7F50;">**IEC 60601-1**</span>)
- Specific test values, metrics, and thresholds (e.g., <span style="color:#FF7F50;">**99.4% Sensitivity**</span>, <span style="color:#FF7F50;">**IP22 Waterproof Rating**</span>)
- Definite compliance or risk metrics (e.g., <span style="color:#FF7F50;">**PASS**</span>, <span style="color:#FF7F50;">**COMPLIANT**</span>, <span style="color:#FF7F50;">**HIGH RISK**</span>)

Do not omit any section. Ensure the markdown formatting remains perfectly valid. Do not include markdown code block wraps (` ```markdown `) in your final response string.

```

#### 3.3.3 Summary Manipulation Workspace UI & Export Pipeline

The frontend provides a real-time Markdown editor featuring dual-pane interactive rendering. The rendering pipeline uses a sanitizer component to verify that `<span style="color:#FF7F50;">` styles execute securely without cross-site scripting risks.

```
+---------------------------------------------------------------------------------+
|                               SUMMARY WORKSPACE                                 |
+---------------------------------------------------+-----------------------------+
| ACTIONS: [Save] [Download Markdown] [Download PDF] [Download HTML]              |
+---------------------------------------------------+-----------------------------+
| EDITABLE MARKDOWN PANE                            | LIVE PREVIEW RENDERING PANE |
|                                                   |                             |
| ## 1. DEVICE IDENTIFICATION                       | ## 1. DEVICE IDENTIFICATION |
| The device under review is the                    | The device under review is  |
| <span style="color:#FF7F50;">                     | the **AetherSurg Pulse-8** |
| **AetherSurg Pulse-8**</span> manufactured        | manufactured by NeuroMed.   |
| by NeuroMed. It follows the                       | It follows the **510(k)** |
| <span style="color:#FF7F50;">                     | pathway under product code  |
| **510(k)**</span> pathway under                   | **DOG**.                    |
| product code <span style="color:#FF7F50;">        |                             |
| **DOG**</span>.                                   |                             |
+---------------------------------------------------+-----------------------------+

```

The user can modify the content directly or trigger multi-format rendering engines:

* **Markdown Target:** Plain document text streaming download.
* **HTML Target:** Wraps the body structure within a compliance-optimized stylesheet containing explicit typographical definitions:
```css
body { font-family: 'Helvetica Neue', Arial, sans-serif; line-height: 1.6; color: #333333; }
h1, h2, h3 { color: #1A365D; border-bottom: 1px solid #E2E8F0; padding-bottom: 4px; }
strong { font-weight: 600; }

```


* **PDF Target:** Processes the rendered HTML structure through a headless Chrome rendering pipeline or a specialized Python document service (e.g., `WeasyPrint` or `ReportLab`). This converts inline CSS color signatures directly into vector-embedded print documents, preventing any loss of color formatting.

---

### 3.4 Phase 4: Dynamic Prompt & Skill.md Iteration Pipeline

To support custom auditing guidelines, Project Aetheris uses a highly tailored instruction module known as the **Knowledge & Review Optimization Layer (`skill.md`)**. This file acts as the primary rulebook that guides the agent's review logic and verification criteria.

#### 3.4.1 Baseline Default `skill.md` Template Blueprint

```markdown
# MEDICAL DEVICE REVIEW REVIEWER EXPERT SKILL MATRIX (V1.0.0)

## 1. CORE OPERATIONAL FRAMEWORK
You evaluate submissions against international standards and safety protocols. Your analytical view matches strict regulatory audit parameters, focusing on consistency, verification, and data traceability.

## 2. REQUISITE EVALUATION CRITERIA
* **Completeness:** Verify every standard section matches file specifications.
* **Data Integrity:** Check that statistical clinical summaries match raw data metrics across all text tables.
* **Risk Profile Evaluation:** Confirm that identified hazards map to corresponding mitigation protocols in the software testing suites.
* **Biocompatibility Verification:** Check that all patient-contacting components match explicitly defined $ISO\ 10993-1$ endpoints.

## 3. AUDITING RULES & INSTRUCTIONAL CONSTRAINTS
* Do not assume verification tests passed unless explicit data results are presented.
* Flag any missing software validation plans, cyber security profiles, or software bills of materials (SBOM).
* Verify that internal software categorization rules match appropriate risk boundaries (e.g., FDA Level of Concern Major/Moderate/Minor or IEC 62304 Class A/B/C frameworks).

```

#### 3.4.2 Interactive Iteration and Refinement Engine

Users can paste customized variants, upload regional guidance documentation, or utilize the native blueprint. The interaction layer features a dynamic refinement interface powered by an underlying optimization loop:

```
[User Interface Console] ---> Inputs Iteration Target / Meta-Instructions
                                      |
                                      v
[Orchestrator] -------------> Fetches Current state of skill.md + User Directives
                                      |
                                      v
[LLM Optimizer Loop] --------> Compiles via Structured Feedback Model
                                      |
                                      v
[Structural Verification] ---> Validates against Regulatory Schema Rules
                                      |
                                      v
[Frontend Workspace] --------> Displays Updated skill.md via Visual Side-by-Side Diff View

```

1. The optimization loop uses `gemini-3.1-flash-lite` (or custom models like `gemini-3.1-pro`) to process the target `skill.md` alongside user modifications.
2. The engine runs a meta-evaluation prompt to systematically improve the file, expanding dense concepts, adding missing regulatory clauses, and ensuring clear instructional phrasing.
3. The updated file passes through structural verification to ensure no standard formatting tags were corrupted.
4. The frontend displays the revised version using an interactive, color-coded side-by-side diff view (Green additions, Red deletions), allowing users to review changes before finalizing the new version.

---

### 3.5 Phase 5: Autonomous 30-Question Assessment Generation & Interactive Human-in-the-Loop Modification

Once the `skill.md` file is finalized, the system switches to deep analysis mode. It runs an automated audit sequence that acts as an inner reasoning layer, evaluating the ingested document against the updated rules matrix.

#### 3.5.1 Algorithmic Question/Answer Strategy Optimization

The agent parses the internal document context against the rules defined in `skill.md`. It is programmatically required to extract **exactly 30 highly detailed, comprehensive review questions** along with corresponding analytical answers. This process uses an itemized parallelized generation script that divides the review requirements across 5 distinct clinical and technical assessment categories:

```
                  +-------------------------------------------------+
                  |      Finalized skill.md + Ingested Dossier      |
                  +------------------------+------------------------+
                                           |
                                           v
                  +-------------------------------------------------+
                  |      Autonomous Deep Auditing Agent Engine       |
                  +------------------------+------------------------+
                                           |
    +-----------------------+--------------+---------------+------------------------+
    |                       |                              |                        |
    v                       v                              v                        v
[Category A]            [Category B]                  [Category C]             [Category D]
Administrative &        Technical Specs               Risk & Hazard            Software, Cyber
Biocompatibility        & Verification                Mitigation               & Electronics
(Q1 - Q8)               (Q9 - Q15)                    (Q16 - Q22)              (Q23 - Q30)
    |                       |                              |                        |
    +-----------------------+--------------+---------------+------------------------+
                                           |
                                           v
                  +-------------------------------------------------+
                  |   Consolidated 30-Question Matrix JSON Object   |
                  +------------------------+------------------------+
                                           |
                                           v
                  +-------------------------------------------------+
                  |   Interactive Real-Time Modification Board UI   |
                  +-------------------------------------------------+

```

#### 3.5.2 Complete Questionnaire Prompt Template

```text
CONTEXT: You are an Expert Regulatory Review Auditor serving on an international medical device assessment board.
DATA REPOSITORIES:
- Global System Knowledge Foundation: [skill.md content]
- Source Device Submission Dossier: [Target OCR Extracted text summary]

TASK: Generate EXACTLY 30 complex, highly critical review questions and their corresponding, evidence-backed answers based on the provided submission text.

GENRES AND DISTRIBUTION COMPLIANCE:
You must balance the 30 questions evenly across the following specific architectural categories:
- Category 1: Administrative Integrity, Indication Nuances, and Biocompatibility Evaluation (Questions 1-8)
- Category 2: Physical & Technical Performance Specifications, Verification Bench Diagnostics (Questions 9-15)
- Category 3: Hazard Localization, ISO 14971 Risk Analysis, and Mitigation Completeness (Questions 16-22)
- Category 4: Software Lifecycles, IEC 62304 Architecture, Cybersecurity Architecture, and Electrical Safety Compliance (Questions 23-30)

ANSWER VALIDATION REQUIREMENTS:
Each answer must be extensive, technical, objective, and reference precise data points from the source text. 
If specific information is missing or not included in the source dossier, state clearly: "CRITICAL GAPS OBSERVED: The submission file fails to present this data segment." Do not create fake metrics.

OUTPUT FORMAT TYPE:
Your response must conform to a single structured JSON array containing exactly 30 entries. Do not wrap the JSON in markdown markers.
[
  {
    "id": 1,
    "category": "Biocompatibility Evaluation",
    "question": "What explicitly are the validation details for...",
    "answer": "The validation testing documented on page 4 notes..."
  }
]

```

#### 3.5.3 Interactive Real-Time Modification Board UI

The generated JSON array parses into an interactive web interface. Each question card functions as a distinct modular component:

```
===================================================================================
QUESTION ASSESSMENT INTERACTIVE BOARD
===================================================================================
[Category: Software Lifecycles]  Card ID: #24 status: [Requires Review]
Question: Describe the device cybersecurity profile and patch deployment pipeline.
-----------------------------------------------------------------------------------
System Generated Answer:
The system file maps software updates to an automated deployment pipeline. However, 
the documentation does not include a Software Bill of Materials (SBOM) listing third-party 
vulnerabilities, which presents a security gap.

[ User Modification Console Workspace Editor - Live Override ]
User Input: Update: The vendor added the SBOM via Appendix G-4, which details 12 open-source components with no unmitigated CVEs.
-----------------------------------------------------------------------------------
[Button: Re-Verify via Agent]   [Button: Freeze & Lock Answer]
===================================================================================

```

Users can modify answers, override data fields, or flag items for real-time verification. When a user updates a field, the local system state synchronizes instantly, updating the background context cache for the final report compilation phase.

---

### 3.6 Phase 6: Full Review Report Compilation & Multi-Format Export

The final phase consolidates all processed data to compile a comprehensive, audit-ready Medical Device Review Report.

#### 3.6.1 Data Consolidation Flow

The report compilation agent aggregates three data layers: the extraction summary, the finalized `skill.md` parameters, and the validated 30-question interactive matrix.

```
+-----------------------------------+
|     Phase 3 Summary Payload       |
+-----------------+-----------------+
                  |
                  +---> [Report Compiling Agent] <--- [Phase 4 Final skill.md]
                  | font-size, layout rules
                  |
+-----------------+-----------------+
|  Phase 5 Validated QA Matrix Log  |
+-----------------------------------+

```

#### 3.6.2 Corporate Regulatory Report Stylesheet Template

The system processes the compiled data through a structured HTML/Markdown template designed to match standard corporate and regulatory reporting layouts.

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<style>
    @page { size: letter; margin: 1in; @bottom-right { content: "Page " counter(page) " of " counter(pages); font-size: 9pt; font-family: Arial, sans-serif; } }
    body { font-family: 'Segoe UI', Arial, sans-serif; color: #2D3748; line-height: 1.5; margin: 0; padding: 0; }
    .header-container { border-bottom: 3px solid #1A365D; padding-bottom: 12px; margin-bottom: 30px; }
    .report-title { font-size: 26pt; font-weight: 700; color: #1A365D; margin: 0; }
    .metadata-box { background-color: #F7FAFC; border: 1px solid #E2E8F0; padding: 15px; border-radius: 6px; margin-bottom: 25px; display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
    .meta-label { font-weight: bold; color: #4A5568; }
    h2 { font-size: 18pt; color: #2B6CB0; border-bottom: 2px solid #E2E8F0; padding-bottom: 6px; margin-top: 35px; page-break-after: avoid; }
    h3 { font-size: 14pt; color: #2C5282; margin-top: 20px; page-break-after: avoid; }
    .qa-block { background-color: #FFFFFF; border-left: 4px solid #4299E1; padding: 10px 15px; margin: 15px 0; box-shadow: 0 1px 3px rgba(0,0,0,0.05); page-break-inside: avoid; }
    .question-text { font-weight: 600; color: #2B6CB0; margin-bottom: 6px; }
    .answer-text { color: #2D3748; text-align: justify; }
    .coral-highlight { color: #FF7F50; font-weight: bold; }
    .gap-alert { background-color: #FFF5F5; border: 1px solid #FEB2B2; padding: 10px; border-radius: 4px; color: #C53030; font-weight: 500; margin-top: 8px; }
</style>
<title>Medical Device Regulatory Assessment Report</title>
</head>
<body>

<div class="header-container">
    <h1 class="report-title">MEDICAL DEVICE REGULATORY ASSESSMENT REPORT</h1>
    <div style="font-size: 10pt; color: #718096; margin-top: 5px;">AUTOMATED AGENTIC COMPLIANCE AUDIT ENGINE</div>
</div>

<div class="metadata-box">
    <div><span class="meta-label">Evaluation Date:</span> [Insert Current System Timestamp]</div>
    <div><span class="meta-label">Orchestration Base:</span> Gemini Core Production Layer</div>
    <div><span class="meta-label">Document Hash:</span> SHA-256 System Ingestion Signature</div>
    <div><span class="meta-label">Compliance Target:</span> Skill Matrix Architecture V1.0.0</div>
</div>

<h2>1. EXECUTIVE OVERVIEW & CONSOLIDATED ANALYSIS</h2>
<div>[The system automatically generates a cohesive introductory analysis based on the extracted data, identifying key product configurations and safety considerations.]</div>

<h2>2. STRATEGIC REGULATORY QUESTIONS MATRIX</h2>
<div class="qa-block">
    <div class="question-text">Q[Index]: [System Question Data Slot]</div>
    <div class="answer-text">[System Answer Data Slot with inline highlights if relevant]</div>
</div>

<h2>3. SYSTEM-WIDE DEFICIENCY & COMPLIANCE FINDINGS</h2>
<div>[The system auto-compiles all flagged compliance gaps into an actionable, itemized table.]</div>

</body>
</html>

```

#### 3.6.3 Final Report Multi-Format Export Drivers

The finalized report can be modified through an integrated preview window and exported into four distinct file formats:

1. **Markdown (`.md`):** High-portability text standard that converts HTML span styles back into clean, readable text tags.
2. **JSON Framework (`.json`):** A machine-readable format that stores the structured data sections, metadata hashes, and question arrays for integration into enterprise audit platforms.
3. **HTML Asset (`.html`):** A standalone web file with embedded styles, enabling responsive offline viewing across various enterprise environments.
4. **PDF Document (`.pdf`):** A print-ready document processed through a server-side rendering pipeline (e.g., WeasyPrint or headless Chromium), ensuring exact pagination, running headers, and consistent color presentation.

---

## 4. Three Advanced "Wow" AI Engineering Features

To elevate Project Aetheris beyond standard retrieval-augmented pipelines, three advanced agentic components are integrated directly into the system's core architecture.

```
                    +------------------------------------------+
                    |      PROJECT AETHERIS CORE PLATFORM      |
                    +--------------------+---------------------+
                                         |
         +-------------------------------+-------------------------------+
         |                               |                               |
         v                               v                               v
+--------+---------------+      +--------+---------------+      +--------+---------------+
|  FEATURE 1:            |      |  FEATURE 2:            |      |  FEATURE 3:            |
|  Cross-Dossier         |      |  Contradiction Vector  |      |  Self-Correcting       |
|  Precedent Analyzer    |      |  Triangulation Loop    |      |  Regulatory Agent      |
+--------+---------------+      +--------+---------------+      +--------+---------------+
         |                               |                               |
         v                               v                               v
Compares input against          Scans and flags internal        Autonomously tests and
historical FDA predicates       discrepancies between           refines prompts via
and clearance metrics           text blocks & appendices        multi-turn diagnostics

```

---

### 4.1 Feature 1: Automated Cross-Dossier Precedent Analyzer & Substantial Equivalence Predictor

This module goes beyond simple text processing by systematically comparing the uploaded document against historical regulatory data.

* **Mechanism:** When a user uploads a device dossier, the agent extracts structural parameters such as raw dimensions, energy outputs, software classifications, and intended clinical environments. It then runs parallel search queries across a localized repository of cleared device metadata (e.g., historical FDA 510(k) databases).
* **Agent Intelligence Layer:** The system uses semantic embeddings and vector-space modeling to identify the three closest historical device predicates. It then builds a dynamic **Substantial Equivalence (SE) Predictor Matrix**.
* **User Interface Display:** The comparison is presented as an interactive dashboard that maps performance gaps, flags potential equivalence challenges, and estimates the probability of clearance, giving regulatory teams actionable predictive insights.

```
+---------------------------------------------------------------------------------------+
|                 SUBSTANTIAL EQUIVALENCE (SE) HISTORICAL PRECEDENT PANEL               |
+---------------------------------------------------------------------------------------+
| TARGET INGESTION DEVICE: NeuroMed PulseSurg (High-Frequency Monopolar Ablation)       |
+---------------------------------------------------------------------------------------+
| IDENTIFIED HISTORICAL PREDICATES:                                                     |
| 1. K210849 - ValleyLab Precision (Match Rating: 94.2%) -> Status: CLEARED             |
| 2. K192031 - MegaSurg SolidState (Match Rating: 88.7%) -> Status: ADDITIONAL INFO REQ  |
+---------------------------------------------------------------------------------------+
| PREDICTIVE RISK VECTOR PROFILE:                                                       |
| [X] Energy output matches K210849 parameters within acceptable variance thresholds.   |
| [!] ALERT: The software validation loop indicates a newer firmware protocol version.  |
|               This could trigger an FDA feedback flag for cyber risk evaluation.      |
+---------------------------------------------------------------------------------------+

```

---

### 4.2 Feature 2: Contradiction Vector Triangulation Loop (Internal Consistency Auditing)

Large technical submissions are often written by distributed, cross-functional teams, which can introduce conflicting statements across different sections of the documentation. This feature acts as an automated internal consistency auditor.

* **Mechanism:** The agent builds a synchronized cross-reference graph of all data tables, numbers, and technical claims extracted from the dossier. It maps values found in early sections (e.g., Executive Summary descriptions) against dense tables in later sections (e.g., technical specifications, bench testing protocols, or appendix logs).
* **Agent Intelligence Layer:** The system scans the document graph to isolate conflicting technical data points, such as mismatched dimensions, conflicting operating temperatures, or inconsistent sample sizes ($n$).
* **User Interface Display:** Any detected discrepancies are isolated and flagged in a dedicated validation interface, allowing users to trace and resolve data inconsistencies before final compilation.

```
> ⚠️ CRITICAL DOSSIER CONTRADICTION DETECTED BY AUDITING AGENT:
> -------------------------------------------------------------------------------------
> Source Location 1: Section 2.1 (Device Specs), Page 14:
> "The platform maximum radiofrequency energy discharge is bound to a ceiling of 50W."
> 
> Source Location 2: Appendix D-2 (Bench Testing Report), Page 142:
> "During stress evaluation loops, output values reached 62W under high impedance conditions."
> 
> Analysis Vector: The bench testing data indicates an operational envelope that exceeds 
> the safety profile specified in Section 2.1, which could impact compliance with safety standards.

```

---

### 4.3 Feature 3: Self-Correcting Regulatory Agent Simulator (Adversarial Prompting Layer)

To ensure the generated review report stands up to rigorous real-world regulatory scrutiny, this module adds an adversarial refinement layer to the pipeline.

* **Mechanism:** Before presenting the 30-question matrix or the final report to the user, the platform runs an autonomous, multi-turn adversarial simulation. The system spawns two distinct AI personas that review and refine the output through a structured critique loop:

```
[Report Generation Agent] ---> Compiles Draft Report Data Structures
                                          |
                                          v
[Adversarial Critic Agent] --> Evaluates Draft using Strict Regulatory Constraints
                                          |
                                          v
[Critique Log Output] --------> Flags weak metrics, missing data, or thin arguments
                                          |
                                          v
[Report Generation Agent] ---> Refines report content to resolve flagged critique areas
                                          |
                                          v
[Final High-Fidelity Artifact] Delivered to user workspace after validation checks pass

```

* **Agent Intelligence Layer:** The **Adversarial Critic Agent** evaluates the draft report against strict international standards, flagging weak metrics, vague arguments, or missing data points. The **Generation Agent** then processes this critique to fill gaps and refine the report's reasoning.
* **Value Delivery:** This automated iteration loop eliminates generic or surface-level AI outputs, ensuring that the final report delivered to the user is highly rigorous, technical, and clinically accurate.

---

## 5. Prompt Engineering & LLM Context Architectures

### 5.1 Token Budget Optimization Matrix

To efficiently process long documents within the context constraints of advanced LLMs, the platform utilizes a structured token allocation framework. The matrix below outlines how the 1,048,576-token context window of `gemini-3.1-flash-lite` is allocated during a typical execution loop:

| Context Window Segment | Component Focus | Token Budget Allocation | Optimization Strategy |
| --- | --- | --- | --- |
| `0x00000 - 0x01FFF` | System Directives & Logic Definitions | 8,000 tokens | Static allocation; cached using persistent context arrays. |
| `0x02000 - 0x05FFF` | Optimized Core `skill.md` Framework | 16,000 tokens | Dynamic injection; prioritized based on current state transitions. |
| `0x06000 - 0xEFFFF` | Extracted Submission Text Blocks | 960,000 tokens | Direct document loading; utilizes structural markers. |
| `0xF0000 - 0xFFFFF` | Interactive QA History & Scratchpad | 64,576 tokens | Active conversation buffer; managed via trailing pruning loops. |

### 5.2 Structured JSON Schema Output Validation

To maintain rock-solid reliability across automated workflows, the platform enforces strict JSON schema conformance for all structured LLM responses. When calling the Gemini API, the platform passes an explicit schema definition to ensure outputs are parsed predictably by backend services.

#### 5.2.1 Unified Assessment Questionnaire Target Schema Definition

```json
{
  "$schema": "[https://json-schema.org/draft/2020-12/schema](https://json-schema.org/draft/2020-12/schema)",
  "title": "RegulatoryAssessmentQuestionnaire",
  "type": "object",
  "properties": {
    "submissionHash": { "type": "string" },
    "categoryDistribution": {
      "type": "object",
      "properties": {
        "administrative": { "type": "integer" },
        "technicalSpecs": { "type": "integer" },
        "riskMitigation": { "type": "integer" },
        "softwareSafety": { "type": "integer" }
      },
      "required": ["administrative", "technicalSpecs", "riskMitigation", "softwareSafety"]
    },
    "questionsList": {
      "type": "array",
      "minItems": 30,
      "maxItems": 30,
      "items": {
        "type": "object",
        "properties": {
          "id": { "type": "integer", "minimum": 1, "maximum": 30 },
          "category": { "type": "string", "enum": ["Administrative & Biocompatibility", "Technical Specs & Verification", "Risk & Hazard Mitigation", "Software, Cyber & Electronics"] },
          "question": { "type": "string", "minLength": 40 },
          "answer": { "type": "string", "minLength": 100 },
          "evidenceReference": {
            "type": "object",
            "properties": {
              "sourceDocumentName": { "type": "string" },
              "extractedTextQuote": { "type": "string" }
            },
            "required": ["sourceDocumentName", "extractedTextQuote"]
          },
          "gapIdentified": { "type": "boolean" }
        },
        "required": ["id", "category", "question", "answer", "evidenceReference", "gapIdentified"]
      }
    }
  },
  "required": ["submissionHash", "categoryDistribution", "questionsList"]
}

```

---

## 6. Security, Compliance, and Data Governance

Because medical device documentation contains highly sensitive intellectual property and confidential health-related design data, the platform is engineered to meet strict institutional security and regulatory compliance standards.

```
+-----------------------------------------------------------------------------------+
|                        SECURITY & COMPLIANCE GUARD RAILS                          |
+-----------------------------------------------------------------------------------+
|  [DATA REST]       AES-256 Bit Encryption on Isolated Storage Volumes             |
|  [DATA TRANSIT]    TLS 1.3 Cryptographic Tunneling Enforcement                   |
|  [COMPLIANCE]      HIPAA Guarded Architecture, SOC2 Type II, and FDA 21 CFR Part 11|
|  [ISOLATION]       Sandboxed Container Instances running No-Data-Retention API    |
+-----------------------------------------------------------------------------------+

```

### 6.1 Data Encryption Architecture

* **Data at Rest:** All ingested files, generated summaries, intermediate OCR data maps, and compiled review reports are encrypted using AES-256 with unique data encryption keys (DEKs) managed through a secure cloud Key Management Service (KMS).
* **Data in Transit:** External API orchestration and internal microservice communications run over TLS 1.3 cryptographic connections. Cleartext transmission is programmatically blocked across the network infrastructure.

### 6.2 Regulatory Compliance Alignments

* **FDA 21 CFR Part 11 Compliance:** The application platform maintains chronological audit trails tracking all user actions, including file uploads, text edits, adjustments to `skill.md`, and report modifications. System logs are secure, immutable, and exportable for institutional auditing.
* **HIPAA & GDPR Structural Design:** Although submission files focus primarily on technical device specifications rather than patient medical histories, the ingestion pipeline automatically scans for and masks Protected Health Information (PHI) or Personally Identifiable Information (PII) using local anonymization layers before cloud data routing occurs.
* **No-Data-Retention API Configurations:** Cloud LLM API gateways are configured to use zero-data-retention enterprise tiers. This ensures that uploaded text arrays, system instructions, and user prompt payloads are never cached, logged, or used for model training by upstream AI vendors.

---

## 7. Non-Functional Requirements & Scalability Metrics

To ensure reliable operation within enterprise regulatory workflows, Project Aetheris is designed to meet strict performance, throughput, and system scalability targets.

### 7.1 Performance and Latency Targets

* **Document Trimming Execution Time:** Slicing a 500-page PDF document and rebuilding its internal XREF tables must complete within 4.5 seconds of user validation.
* **Local Python OCR Throughput:** Local OCR workers must process document pages at a target throughput rate of $\le 1.8\text{ seconds per page}$ when utilizing GPU-accelerated computing pipelines.
* **LLM API Response Times:** Summary generation, prompt expansion, and questionnaire compilation tasks must maintain a target response latency profile within a P95 threshold of $\le 12\text{ seconds}$ when leveraging high-throughput models like `gemini-3.1-flash-lite`.

### 7.2 Scalability and Resource Concurrency

* **Horizontal Autoscaling:** Backend worker pods are configured to auto-scale horizontally using Kubernetes Horizontal Pod Autoscalers (HPA). Scaling criteria are tied directly to active queue lengths and CPU utilization metrics, ensuring seamless adjustments during peak enterprise workloads.
* **Concurrent Session Capacity:** The system architecture is designed to support up to 250 active, simultaneous user assessment sessions per tenant cluster without causing performance degradation or api timeout errors.
* **State Recovery & Fault Tolerance:** Session state is decoupled from individual compute containers and managed via a high-availability Redis cache database layer. If a processing container encounters an unrecoverable exception mid-workflow, user states can be recovered with a maximum data loss window of $\le 1.5\text{ seconds}$.
