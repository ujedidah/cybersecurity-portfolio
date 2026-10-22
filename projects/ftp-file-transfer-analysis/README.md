# FTP File Transfer Activity Analysis with Splunk

## Project Overview

This project involved analyzing FTP activity in Splunk to understand file-transfer patterns, identify the users and IP addresses involved, examine transferred file types, and summarize transfer volumes.

The project focused on transforming raw FTP log events into structured data using Splunk Search Processing Language (SPL), then using statistical aggregation and sorting to identify useful patterns.

## Objectives

- Analyze the frequency of FTP file-transfer activity.
- Identify users and IP addresses associated with transfers.
- Categorize transferred files by extension and file type.
- Extract relevant fields from raw log events.
- Calculate transfer counts, average sizes, and total transferred bytes.
- Investigate and troubleshoot SPL queries when extraction or aggregation results were inaccurate.

## Tools and Techniques

- **SIEM:** Splunk
- **Query language:** Splunk Search Processing Language (SPL)
- **Field extraction:** `rex`
- **Calculated fields and categorization:** `eval`
- **Statistical aggregation:** `stats`
- **Result ordering:** `sort`

## Methodology

### 1. Raw Log Analysis

I examined FTP log events to understand their structure and identify the information needed for analysis, including transfer-related commands, IP addresses, file extensions, and byte values.

### 2. Field Extraction with `rex`

I used regular-expression-based extraction to retrieve relevant values from raw log messages.

This required testing and refining patterns when queries returned no results or extracted incorrect values.

### 3. File-Type Classification

I worked on grouping transferred files into categories such as documents, executables, and archives.

This stage required troubleshooting classification logic to improve consistency and avoid incorrect groupings.

### 4. Statistical Analysis with `stats`

I used statistical aggregation to summarize transfer activity, including counts, average transfer sizes, and total transferred bytes where the required fields were available.

### 5. Calculated Fields and Sorting

I used `eval` to derive or classify values and `sort` to order results for easier comparison and investigation.

## Investigation Questions

The analysis was designed to answer questions such as:

- How frequently did file transfers occur?
- Which users or IP addresses were associated with the most transfer activity?
- Which file types appeared in the logs?
- What were the average and total transfer sizes?
- Which patterns might warrant additional investigation?

## Challenges and Troubleshooting

A major part of the project involved debugging SPL queries and understanding how each command affected the output.

Challenges included zero-result searches, incorrect field extraction, regular-expression refinement, and inaccurate file-type grouping.

Rather than relying on queries simply because they ran, I investigated why the results were incorrect and refined the logic accordingly.

## Security Relevance

FTP activity analysis can help security teams understand file-transfer behavior and identify activity that may require further review, such as unexpected transfer volumes, unusual source systems, or transfers involving sensitive file types.

Log evidence must be interpreted in context. A large transfer or executable file alone does not establish malicious activity.

## Key Takeaways

This project strengthened my understanding of raw log analysis, SPL query development, regular expressions, field extraction, data classification, statistical aggregation, and troubleshooting.

It also reinforced the importance of validating extracted fields and understanding query logic before drawing conclusions from security data.

## Evidence and Documentation

<img width="1280" height="476" alt="image" src="https://github.com/user-attachments/assets/fcf231fd-439c-4c4b-8d46-f8e9e3f3367b" />


## Project Status

This page documents the project and techniques used. Specific findings and numerical results will be included when supported by retained query outputs or other available evidence.
