# repair-prompts
[![DOI](https://zenodo.org/badge/720187426.svg)](https://zenodo.org/doi/10.5281/zenodo.10783762)

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

<table>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>ChatGPT</th>
            <th colspan=3>Bard</th>
        </tr>
    </thead>
    <tbody>
        <tr>
          <td></td>
          <td>context-free</td>
          <td>content-sensitive</td>
          <td>context-rich</td>
          <td>context-free</td>
          <td>content-sensitive</td>
          <td>context-rich</td>
        </tr>
        <tr>
          <td><b>CWE-20</b></td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-22</b></td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-77</b></td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-78</b></td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-79</b></td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-89</b></td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-94</b></td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-125</b></td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-190</b></td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
        </tr>
        <tr>
          <td><b>CWE-269</b></td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-276</b></td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-287</b></td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-306</b></td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-434</b></td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-476</b></td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
        </tr>
        <tr>
          <td><b>CWE-502</b></td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-787</b></td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-798</b></td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
        </tr>
        <tr>
          <td><b>CWE-862</b></td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
        </tr>
        <tr>
          <td><b>CWE-863</b></td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
          <td align="center">&cross;</td>
          <td align="center">&check;</td>
          <td align="center">&check;</td>
        </tr>
    </tbody>
</table>

## Citation
If you find this repository helpful, feel free to cite our publication [A Study of Vulnerability Repair in JavaScript Programs with Large Language Models](https://doi.org/10.1145/3589335.3651463):
```
@inproceedings{le2024study,
  title={A Study of Vulnerability Repair in JavaScript Programs with Large Language Models},
  author={Le, Tan Khang and Alimadadi, Saba and Ko, Steven Y},
  booktitle={Companion Proceedings of the ACM on Web Conference 2024},
  pages={666--669},
  year={2024}
}
```
