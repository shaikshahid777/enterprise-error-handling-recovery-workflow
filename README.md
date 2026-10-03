<!-- SHOWCASE_START --><div align="center">[![Typing](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=22&duration=2800&pause=900&color=58A6FF&center=true&vCenter=true&width=900&lines=enterprise%20error%20handling%20recovery%20workflow;AI%20%7C%20Automation%20%7C%20Engineering;Explore%20the%20project%20%F0%9F%9A%80)](https://github.com/shaikshahid777/enterprise-error-handling-recovery-workflow)<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:161B22,100:58A6FF&height=110&section=header&text=enterprise-error-handling-recovery-workflow&fontSize=26&fontColor=FFFFFF&animation=twinkling&fontAlignY=65" width="100%" alt="Animated project banner"/>

[![Repository](https://img.shields.io/badge/Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/shaikshahid777/enterprise-error-handling-recovery-workflow) [![Issues](https://img.shields.io/badge/Report-Issue-red?style=for-the-badge&logo=github)](https://github.com/shaikshahid777/enterprise-error-handling-recovery-workflow/issues/new) [![Stars](https://img.shields.io/github/stars/shaikshahid777/enterprise-error-handling-recovery-workflow?style=for-the-badge&logo=github)](https://github.com/shaikshahid777/enterprise-error-handling-recovery-workflow/stargazers) [![Fork](https://img.shields.io/github/forks/shaikshahid777/enterprise-error-handling-recovery-workflow?style=for-the-badge&logo=github)](https://github.com/shaikshahid777/enterprise-error-handling-recovery-workflow/fork) [![Profile](https://img.shields.io/badge/Profile-Visit-0A66C2?style=for-the-badge&logo=github)](https://github.com/shaikshahid777)</div>

> ✨ **Project Showcase Mode:** animated banner • interactive navigation • live repository actions

[🚀 Repository](https://github.com/shaikshahid777/enterprise-error-handling-recovery-workflow) · [🐞 Report Issue](https://github.com/shaikshahid777/enterprise-error-handling-recovery-workflow/issues/new) · [⭐ Star](https://github.com/shaikshahid777/enterprise-error-handling-recovery-workflow/stargazers) · [🔱 Fork](https://github.com/shaikshahid777/enterprise-error-handling-recovery-workflow/fork) · [👤 Profile](https://github.com/shaikshahid777)

<!-- SHOWCASE_END -->

# Enterprise Error Handling & Recovery Workflow — Lesson 5 Assessment

Production-ready n8n error handling and recovery pattern using automatic retries, exponential backoff, centralized Error Trigger handling, PostgreSQL failure logging, and operational alerting.

## Architecture

```text
Primary Business Workflow
Manual Trigger
      ↓
HTTP_CallBusinessAPI
      ↓
Retry on Fail (3 tries / 5000 ms / exponential backoff)
      ↓
Final Failure
      ↓
Global Error Handler
      ↓
Error Trigger
      ↓
PostgreSQL_LogError
      ↓
Slack_DispatchAlert
```

## PostgreSQL Audit Table

`system_error_logs` stores:
- `execution_id`
- `workflow_id`
- `workflow_name`
- `failed_node`
- `error_message`
- `occurred_at`

An index on `workflow_id` supports operational lookup.

## Validation

The primary workflow uses a controlled HTTP 500 response to simulate an outbound API failure. The configured retry policy is intended to attempt the request three times before the final failure is routed to the centralized Error Handler.

## Files

```text
enterprise-error-handling-recovery-workflow/
├── README.md
├── workflow/
│   ├── Primary_Business_Workflow.json
│   ├── Global_Error_Handler.json
│   └── Setup_system_error_logs.json
├── sql/
│   └── system_error_logs.sql
├── documentation/
│   └── Enterprise_Error_Handling_Recovery_Documentation.pdf
├── screenshots/
└── deployment/
    └── deployment-instructions.md
```

## Security

Do not commit PostgreSQL passwords, Slack tokens, API keys, or other secrets. Keep credentials in n8n Credential Manager.

## Loom

https://www.loom.com/share/c0100daa1170408c90d6538496b13ba5
