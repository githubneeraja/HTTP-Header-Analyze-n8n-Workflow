 HTTP-Header-Analyze-project
building HTTP Header Analyze using n8n automation



  HTTP Header Analyze — n8n Security Workflow

This project is an automated website security auditing workflow built in [n8n](https://n8n.io).  
It analyzes HTTP headers, client-side vulnerabilities, and page security configurations using AI-powered analysis.



Overview

The workflow performs a full web security audit in real time by combining HTTP inspection and AI-driven analysis.

 Features
- Fetches HTTP response headers from a target URL
- Uses OpenAI (GPT-4.1-mini) for intelligent analysis
- Detects missing or misconfigured security headers
- Audits insecure cookie configurations
- Reviews client-side HTML for vulnerabilities (e.g., XSS, leaks)
- Grades website security (A–F)
- Sends an email security report via Gmail



 Workflow Components

| Node Name | Type | Description |
|||-|
| Landing Page URL | Form Trigger | Collects user input (URL) to scan |
| HTTP Request | HTTP Node | Fetches headers and page content |
| Code in JavaScript | Code Node | Formats HTTP headers |
| AI Agent | LangChain Agent | Analyzes HTTP headers and security configuration |
| AI Agent1 | LangChain Agent | Scans HTML content for client-side vulnerabilities |
| Merge | Merge Node | Combines results from both AI analyses |
| Aggregate | Aggregate Node | Merges structured output |
| Code in JavaScript1 | Code Node | Grades security (A, B, C, F) and formats results |
| Code in JavaScript2 | Code Node | Builds a professional HTML audit report |
| Send a message | Gmail Node | Emails the final security report |



Security Grading Logic

The system assigns a grade based on essential security headers:

| Header | Points Deducted if Missing |
|||
| Content-Security-Policy | −20 |
| Strict-Transport-Security | −20 |
| X-Content-Type-Options | −10 |
| X-Frame-Options | −10 |
| Referrer-Policy | −10 |

Grades:
- A → 90–100  
- B → 75–89  
- C → 60–74  
- F → Below 60



Email Output Example

Each scan result is emailed to the configured Gmail account with the following sections:



 Website Security Audit Report

URL: [https://example.com](https://example.com)
Grade: A
Timestamp: 2025-11-02T18:45:00Z

Configuration Audit:
[List of secure/missing headers]

Vulnerability Audit:
[List of detected issues or “No vulnerabilities found”]





Setup Instructions

1. Import the workflow  
   - In n8n → Workflows → Import from file
   - Select `HTTP Header Analyze.json`

2. Add credentials
   - OpenAI API` (your API key)
   - Gmail OAuth2` (for sending reports)

3. Activate the workflow
   - Click the toggle switch to enable
   - Access via the generated Form URL



 Use Case Scenarios

- Web security audit automation  
- Continuous website header scanning  
- Client-side vulnerability reports  
- Pre-deployment web configuration checks  



Project Structure



HTTP-Header-Analyze-project/
│
├── HTTP Header Analyze.json      Main n8n workflow
└── README.md                     Project documentation





License

This project is open-source and available under the MIT License.




If you found this helpful, give it a star on GitHub!



