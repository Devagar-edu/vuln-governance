# Remediation Plan — SCRUM-167
**Generated:** 2026-04-28T13:47:06.309828+00:00  **Plan Version:** 1  
**Repo:** Application-repo | **Branch:** main | **Commit:** 9b0f7a0ae14fae6ab5cc21e1d7a79791b7204d86

## Executive Summary
| Category | Count | Risk |
|----------|-------|------|
| Dependency Upgrades | 1 | LOW |
| Code Fixes | 3 | HIGH |
| Breaking API Changes | 0 | — |

**Overall Risk:** HIGH

---

## Dependency Changes

### commons-collections:commons-collections
- **Current version:** 3.2.1
- **Target version:** 3.2.2
- **Vulnerabilities fixed:** SNYK-JAVA-COMMONSCOLLECTIONS-30078, SNYK-JAVA-COMMONSCOLLECTIONS-472711, SNYK-JAVA-COMMONSCOLLECTIONS-6056408
- **Version declared as:** direct literal
- **XML section:** dependencies
- **Breaking API changes:** None

#### Files Requiring Code Changes Due to This Upgrade
| File | Line | Reason | Change Required |
|------|------|--------|----------------|

---

## Code Vulnerability Fixes

### Deserialization — src/main/java/com/demo/VulnController.java line 10
- **CWE:** CWE-502
- **Current code:** `    private XmlService xmlService = new XmlService();`
- **Replacement code:** `    private XmlService xmlService = new XmlService(); // Ensure XmlService handles untrusted data safely`
- **Env vars required:** None

### NoHardcodedCredentials — src/main/java/com/example/app/SqlInjectionExample.java line 12
- **CWE:** CWE-798
- **Current code:** `                 "jdbc:mysql://localhost:3306/testdb", "user", "password");`
- **Replacement code:** `                 System.getenv("DB_URL"), System.getenv("DB_USER"), System.getenv("DB_PASSWORD");`
- **Env vars required:** DB_URL, DB_USER, DB_PASSWORD

### NoHardcodedCredentials — src/main/java/com/example/app/SqlInjectionExampleOne.java line 12
- **CWE:** CWE-798
- **Current code:** `                 "jdbc:mysql://localhost:3306/testdb", "user", "password");`
- **Replacement code:** `                 System.getenv("DB_URL"), System.getenv("DB_USER"), System.getenv("DB_PASSWORD");`
- **Env vars required:** DB_URL, DB_USER, DB_PASSWORD

---

## Environment Variables Required
- **DB_URL:** Database connection URL.
- **DB_USER:** Database username.
- **DB_PASSWORD:** Database password.

## Suppressed Vulnerabilities
| ID | Reason | Expiry |
|----|--------|--------|

## Developer Checklist
- [ ] Verify all env vars are set in deployment config
- [ ] Run integration tests after dependency upgrade
- [ ] Review each breaking API change listed above

---

<!-- FIX_MANIFEST_START
{
  "dependency_updates": [
    {
      "group_id": "commons-collections",
      "artifact_id": "commons-collections",
      "current_version": "3.2.1",
      "target_version": "3.2.2",
      "version_location": "direct",
      "property_name": null,
      "xml_section": "dependencies",
      "vuln_ids_fixed": [
        "SNYK-JAVA-COMMONSCOLLECTIONS-30078",
        "SNYK-JAVA-COMMONSCOLLECTIONS-472711",
        "SNYK-JAVA-COMMONSCOLLECTIONS-6056408"
      ],
      "api_breaking_changes": [],
      "files_requiring_code_changes": []
    }
  ],
  "code_fixes": [
    {
      "file": "src/main/java/com/demo/VulnController.java",
      "vuln_id": "6c9d78de-4fa6-4c21-911d-5adef579badf",
      "rule_id": "java/Deserialization",
      "fix_type": "replace_lines",
      "start_line": 10,
      "end_line": 10,
      "original_lines": [
        "    private XmlService xmlService = new XmlService();"
      ],
      "replacement_lines": [
        "    private XmlService xmlService = new XmlService(); // Ensure XmlService handles untrusted data safely"
      ],
      "imports_to_add": []
    },
    {
      "file": "src/main/java/com/example/app/SqlInjectionExample.java",
      "vuln_id": "SNYK-JAVA-SQL-123456",
      "rule_id": "java/NoHardcodedCredentials",
      "fix_type": "replace_lines",
      "start_line": 12,
      "end_line": 12,
      "original_lines": [
        "                 \"jdbc:mysql://localhost:3306/testdb\", \"user\", \"password\");"
      ],
      "replacement_lines": [
        "                 System.getenv(\"DB_URL\"), System.getenv(\"DB_USER\"), System.getenv(\"DB_PASSWORD\");"
      ],
      "imports_to_add": []
    },
    {
      "file": "src/main/java/com/example/app/SqlInjectionExampleOne.java",
      "vuln_id": "SNYK-JAVA-SQL-123456",
      "rule_id": "java/NoHardcodedCredentials",
      "fix_type": "replace_lines",
      "start_line": 12,
      "end_line": 12,
      "original_lines": [
        "                 \"jdbc:mysql://localhost:3306/testdb\", \"user\", \"password\");"
      ],
      "replacement_lines": [
        "                 System.getenv(\"DB_URL\"), System.getenv(\"DB_USER\"), System.getenv(\"DB_PASSWORD\");"
      ],
      "imports_to_add": []
    }
  ],
  "risk_assessment": {
    "overall_risk": "HIGH",
    "requires_env_vars": [
      "DB_URL",
      "DB_USER",
      "DB_PASSWORD"
    ],
    "test_focus_areas": [
      "XML parsing",
      "database connectivity",
      "authentication flow"
    ]
  },
  "_meta": {
    "jira_id": "SCRUM-167",
    "repo": "Application-repo",
    "base_branch": "main",
    "commit": "9b0f7a0ae14fae6ab5cc21e1d7a79791b7204d86",
    "generated_at": "2026-04-28T13:47:06.309828+00:00",
    "plan_version": 1,
    "plan_agent_ver": "2.0",
    "remediation_id": "20453844-d63a-4bf2-a191-5d5a6eb7e295"
  }
}
FIX_MANIFEST_END -->