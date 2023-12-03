# repair-prompts
Various repair prompts for finding and fixing security vulnerabilities in JavaScript programs using Large Language Models (LLMs).

## Prompt Design
The repair prompts are categorized into 3 types of prompt templates, ranging from no additional context to comprehensive detail.

* `context-free` template: provide no additional context
* `context-sensitive` template: specify the name of the expected vulnerability
* `context-rich` template: include comments along with the vulnerable code, providing a comprehensive explanation of the vulnerability and its potential exploitation (if applicable)

## Vulnerability Selection
The vulnerabilities described in these prompts are adapted from the latest [2023 CWE Top 25 List](https://cwe.mitre.org/top25/archive/2023/2023_top25_list.html).
However, as not all vulnerabilities in this list are applicable to JavaScript, 20 out of the 25 vulnerabilities that are most relevant to JavaScript are selected.

## Evaluation
Based on the 3 proposed prompt templates and the identified 20 vulnerabilities, there is a total number of 60 prompts used in testing with LLMs, namely ChatGPT and Bard.

The performance of these LLMs is as follows:
