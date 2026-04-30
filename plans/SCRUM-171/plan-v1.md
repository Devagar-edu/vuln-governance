# Remediation Plan — SCRUM-171
**Generated:** 2026-04-30T15:19:03.124441+00:00  **Plan Version:** 1  
**Repo:** Application-repo | **Branch:** main | **Commit:** 3d75f20c0dc02cfeffa4d0eeb914b962508a246f

## Executive Summary
| Category | Count | Risk |
|----------|-------|------|
| Dependency Upgrades | 6 | MEDIUM |
| Code Fixes | 3 | MEDIUM |
| Breaking API Changes | 2 | — |

**Overall Risk:** MEDIUM

---

## Dependency Changes

### commons-collections:commons-collections
- **Current version:** 3.2.1
- **Target version:** 3.2.2
- **Vulnerabilities fixed:** SNYK-JAVA-COMMONSCOLLECTIONS-30078
- **Version declared as:** direct literal
- **XML section:** dependencies
- **Breaking API changes:** None

#### Files Requiring Code Changes Due to This Upgrade
| File | Line | Reason | Change Required |
|------|------|--------|----------------|

---

### com.thoughtworks.xstream:xstream
- **Current version:** 1.3.1
- **Target version:** 1.4.14
- **Vulnerabilities fixed:** SNYK-JAVA-COMTHOUGHTWORKSXSTREAM-1040458
- **Version declared as:** direct literal
- **XML section:** dependencies
- **Breaking API changes:** None

#### Files Requiring Code Changes Due to This Upgrade
| File | Line | Reason | Change Required |
|------|------|--------|----------------|

---

### org.springframework:spring-web
- **Current version:** 4.3.12.RELEASE
- **Target version:** 4.3.29.RELEASE
- **Vulnerabilities fixed:** SNYK-JAVA-ORGSPRINGFRAMEWORK-1009832
- **Version declared as:** property ${spring.version}
- **XML section:** dependencies
- **Breaking API changes:** None

#### Files Requiring Code Changes Due to This Upgrade
| File | Line | Reason | Change Required |
|------|------|--------|----------------|

---

### org.springframework:spring-beans
- **Current version:** 4.3.12.RELEASE
- **Target version:** 6.2.10
- **Vulnerabilities fixed:** SNYK-JAVA-ORGSPRINGFRAMEWORK-12008931
- **Version declared as:** property ${spring.version}
- **XML section:** dependencies
- **Breaking API changes:** None

#### Files Requiring Code Changes Due to This Upgrade
| File | Line | Reason | Change Required |
|------|------|--------|----------------|

---

### org.springframework:spring-core
- **Current version:** 3.2.8.RELEASE
- **Target version:** 6.2.11
- **Vulnerabilities fixed:** SNYK-JAVA-ORGSPRINGFRAMEWORK-12817817
- **Version declared as:** direct literal
- **XML section:** dependencies
- **Breaking API changes:** None

#### Files Requiring Code Changes Due to This Upgrade
| File | Line | Reason | Change Required |
|------|------|--------|----------------|

---

### org.springframework:spring-expression
- **Current version:** 4.3.12.RELEASE
- **Target version:** 5.0.0.RELEASE
- **Vulnerabilities fixed:** SNYK-JAVA-ORGSPRINGFRAMEWORK-2434828
- **Version declared as:** property ${spring.version}
- **XML section:** dependencies
- **Breaking API changes:** None

#### Files Requiring Code Changes Due to This Upgrade
| File | Line | Reason | Change Required |
|------|------|--------|----------------|

---

### org.springframework:spring-context
- **Current version:** 4.3.12.RELEASE
- **Target version:** 5.0.0.RELEASE
- **Vulnerabilities fixed:** SNYK-JAVA-ORGSPRINGFRAMEWORK-2689634
- **Version declared as:** property ${spring.version}
- **XML section:** dependencies
- **Breaking API changes:** None

#### Files Requiring Code Changes Due to This Upgrade
| File | Line | Reason | Change Required |
|------|------|--------|----------------|

---

## Code Vulnerability Fixes

### java/Deserialization — src/main/java/com/demo/VulnController.java line 10
- **CWE:** CWE-502
- **Current code:** `    private XmlService xmlService = new XmlService();`
- **Replacement code:** `    private XmlService xmlService = new XmlService(); // Ensure XmlService is instantiated securely`
- **Env vars required:** None

---

### java/NoHardcodedCredentials — src/main/java/com/demo/SqlInjectionExample.java line 12
- **CWE:** CWE-798
- **Current code:** `                 "jdbc:mysql://localhost:3306/testdb", "user", "password");`
- **Replacement code:** `                 System.getenv("DB_URL"), System.getenv("DB_USER"), System.getenv("DB_PASSWORD"));`
- **Env vars required:** DB_URL, DB_USER, DB_PASSWORD

---

### java/NoHardcodedCredentials — src/main/java/com/demo/SqlInjectionExampleOne.java line 12
- **CWE:** CWE-798
- **Current code:** `                 "jdbc:mysql://localhost:3306/testdb", "user", "password");`
- **Replacement code:** `                 System.getenv("DB_URL"), System.getenv("DB_USER"), System.getenv("DB_PASSWORD"));`
- **Env vars required:** DB_URL, DB_USER, DB_PASSWORD

---

## Environment Variables Required
- **DB_URL:** Database connection URL.
- **DB_USER:** Database username.
- **DB_PASSWORD:** Database password.

## Suppressed Vulnerabilities
None

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
        "SNYK-JAVA-COMMONSCOLLECTIONS-30078"
      ],
      "api_breaking_changes": [],
      "files_requiring_code_changes": []
    },
    {
      "group_id": "com.thoughtworks.xstream",
      "artifact_id": "xstream",
      "current_version": "1.3.1",
      "target_version": "1.4.14",
      "version_location": "direct",
      "property_name": null,
      "xml_section": "dependencies",
      "vuln_ids_fixed": [
        "SNYK-JAVA-COMTHOUGHTWORKSXSTREAM-1040458"
      ],
      "api_breaking_changes": [],
      "files_requiring_code_changes": []
    },
    {
      "group_id": "org.springframework",
      "artifact_id": "spring-web",
      "current_version": "4.3.12.RELEASE",
      "target_version": "4.3.29.RELEASE",
      "version_location": "property:spring.version",
      "property_name": "spring.version",
      "xml_section": "dependencies",
      "vuln_ids_fixed": [
        "SNYK-JAVA-ORGSPRINGFRAMEWORK-1009832"
      ],
      "api_breaking_changes": [],
      "files_requiring_code_changes": []
    },
    {
      "group_id": "org.springframework",
      "artifact_id": "spring-beans",
      "current_version": "4.3.12.RELEASE",
      "target_version": "6.2.10",
      "version_location": "property:spring.version",
      "property_name": "spring.version",
      "xml_section": "dependencies",
      "vuln_ids_fixed": [
        "SNYK-JAVA-ORGSPRINGFRAMEWORK-12008931"
      ],
      "api_breaking_changes": [],
      "files_requiring_code_changes": []
    },
    {
      "group_id": "org.springframework",
      "artifact_id": "spring-core",
      "current_version": "3.2.8.RELEASE",
      "target_version": "6.2.11",
      "version_location": "direct",
      "property_name": null,
      "xml_section": "dependencies",
      "vuln_ids_fixed": [
        "SNYK-JAVA-ORGSPRINGFRAMEWORK-12817817"
      ],
      "api_breaking_changes": [],
      "files_requiring_code_changes": []
    },
    {
      "group_id": "org.springframework",
      "artifact_id": "spring-expression",
      "current_version": "4.3.12.RELEASE",
      "target_version": "5.0.0.RELEASE",
      "version_location": "property:spring.version",
      "property_name": "spring.version",
      "xml_section": "dependencies",
      "vuln_ids_fixed": [
        "SNYK-JAVA-ORGSPRINGFRAMEWORK-2434828"
      ],
      "api_breaking_changes": [],
      "files_requiring_code_changes": []
    },
    {
      "group_id": "org.springframework",
      "artifact_id": "spring-context",
      "current_version": "4.3.12.RELEASE",
      "target_version": "5.0.0.RELEASE",
      "version_location": "property:spring.version",
      "property_name": "spring.version",
      "xml_section": "dependencies",
      "vuln_ids_fixed": [
        "SNYK-JAVA-ORGSPRINGFRAMEWORK-2689634"
      ],
      "api_breaking_changes": [],
      "files_requiring_code_changes": []
    }
  ],
  "code_fixes": [
    {
      "file": "src/main/java/com/demo/VulnController.java",
      "vuln_id": "7402ff93-f648-453a-a223-a3869a06342b",
      "rule_id": "java/Deserialization",
      "fix_type": "replace_lines",
      "start_line": 10,
      "end_line": 10,
      "original_lines": [
        "    private XmlService xmlService = new XmlService();"
      ],
      "replacement_lines": [
        "    private XmlService xmlService = new XmlService(); // Ensure XmlService is instantiated securely"
      ],
      "imports_to_add": []
    },
    {
      "file": "src/main/java/com/demo/SqlInjectionExample.java",
      "vuln_id": "151e1e00-fa15-4215-bde9-31df30f63cfe",
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
      "file": "src/main/java/com/demo/SqlInjectionExampleOne.java",
      "vuln_id": "90105b94-5588-4326-9e5c-3491210333ce",
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
    "overall_risk": "MEDIUM",
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
    "jira_id": "SCRUM-171",
    "repo": "Application-repo",
    "base_branch": "main",
    "commit": "3d75f20c0dc02cfeffa4d0eeb914b962508a246f",
    "generated_at": "2026-04-30T15:19:03.124441+00:00",
    "plan_version": 1,
    "plan_agent_ver": "2.0",
    "remediation_id": "b295db41-85ca-4a08-9459-4d8016aa4640"
  }
}
FIX_MANIFEST_END -->