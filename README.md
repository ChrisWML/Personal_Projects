## AI DataOps Labeling Pipeline POC

This repository contains a lightweight, end-to-end proof-of-concept pipeline designed to showcase key DataOps practices for AI model development—mirroring the challenges and requirements of a production-scale AI DataOps Lead role. Implemented in pure Python and Jupyter Notebook, it demonstrates:

- **Automated Data Ingestion**  
  Scrapes live eBay UK listings (title, URL, price) via Selenium & BeautifulSoup, handling non-API sources.

- **Robust Cleaning & Normalization**  
  Deduplicates entries, lower-cases text, standardizes units, strips fluff/emojis ... enforces a consistent schema.

- **Multi-Model Evaluation Loop**  
  Uses GPT-4o to translate titles into Chinese, then GPT-4.1 to rate translations (1–4) with confidence scores.

- **Human-in-the-Loop Review**  
  Interactive Jupyter section for sampling questionable translations and performing random spot-checks, capturing human labels and correction notes.

- **Rich Metadata Tracking**  
  Records pipeline_version, dataset_version, annotator_id, task_id, time_to_label, confidence scores, etc., for full lineage.

- **KPI Reporting & Visualization**  
  Generates summary tables and simple charts for completeness, class balance, pipeline latency, and more.

---

## Why This Matters

Large-scale AI projects demand end-to-end workflows that balance automation with human oversight, enforce data quality, and provide traceability. This POC shows how to:

1. Build scalable ingestion and labeling workflows  
2. Embed automated and human-centric quality gates  
3. Capture complete audit trails for compliance  
4. Deliver executive-friendly metrics

Use this as a foundation—extend with orchestration (e.g.Airflow), multi-annotator support, drift detection, and compliance controls to move from POC to production.

---

## Production Enhancements

To evolve this POC into a robust, multi-annotator pipeline suitable for enterprise AI operations, add the following:

1. **Clear Task Definitions & Labeling Guidelines**  
   - Define annotation tasks with precise specs, input/output formats, and acceptance criteria.  
   - Publish a versioned Markdown guide with examples, edge-case rules, and common pitfalls.  

2. **Taxonomy & Ontology Ownership**  
   - Assign a taxonomy owner responsible for label hierarchies and definitions.  
   - Track ontology versions in metadata so every dataset references the exact taxonomy used.  

3. **Multi-Annotator & Dispute Resolution**  
   - Support N (e.g. 2) annotators per sample; store each label with metadata (`annotator_id`, `timestamp`, `annotation_round`, `pipeline_version`).  
   - Introduce an adjudicator (senior annotator or consensus engine) to resolve conflicts when labels disagree.  

4. **Golden-Truth Audits & Regular Spot Checks**  
   - Seed hidden “gold” samples to silently measure annotator accuracy.  
   - Schedule ad-hoc manual reviews of random samples to catch drift or guideline misinterpretation.  

5. **Feedback Loops & Guidelines Updates**  
   - Provide annotators with periodic reports on golden-truth performance and agreement rates.  
   - Host quarterly calibration sessions to review challenging cases and update labeling guidelines accordingly.  

6. **Enhanced Dashboard Metrics**  
   - Track inter-annotator agreement (e.g. Cohen’s κ) per label class and over time.  
   - Monitor model drift by comparing new pipeline versions against historical benchmarks.  
   - Chart throughput (samples/hour) and end-to-end pipeline latency.  

7. **Automated Quality Gates & Alerts**  
   - Enforce pre-commit checks (<1% reject rate, >85% agreement rate, >90% gold accuracy rate) before accepting new dataset versions.  
   - Schedule daily runs in ETL orchestration tool that send alerts and trigger remediation workflows on failures.  

8. **Data Lineage, Audit Trail & Compliance**  
   - Use append-only logs for every annotation, inference, QC check, and guideline version.  
   - Enable drill-downs in dashboards to trace any KPI back to its pipeline version, annotator cohort, or taxonomy release.  
   - Anonymize PII, respect scraping policies, define GDPR-compliant retention/deletion rules, and enforce role-based access controls.  

9. **Orchestration & Scalability**  
   - Define a DAG in ETL orchestration tool or Prefect to schedule the full pipeline automatically.  
   - Implement retry logic, parallel task execution, and auto-scaling of workers/containers.  
   - Monitor resource usage and pipeline health with integrated logging and alerting.

10. **AI-Powered Data Cleaning**  
  - Leverages GPT-4 or similar models to automatically normalize text (e.g. standardizing units, removing noise, correcting typos), often yielding higher accuracy and catch-rates than rule-based scripts alone.

---

*Feel free to fork, experiment, and build upon this foundation—your feedback and contributions are welcome!*  
