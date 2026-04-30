# Remediation Plan — SCRUM-169
**Generated:** 2026-04-30T13:33:35.212269+00:00  **Plan Version:** 2  
**Repo:** Application-repo | **Branch:** main | **Commit:** c5f38ab077ede13b6cb0bc2a33f2b520fd882414

## Executive Summary
| Category | Count | Risk |
|----------|-------|------|
| Dependency Upgrades | 6 | MEDIUM |
| Code Fixes | 3 | MEDIUM |
| Breaking API Changes | 1 | — |

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

### com.thoughtworks.xstream:xstream
- **Current version:** 1.3.1
- **Target version:** 1.4.14
- **Vulnerabilities fixed:** SNYK-JAVA-COMTHOUGHTWORKSXSTREAM-1040458
- **Version declared as:** direct literal
- **XML section:** dependencies
- **Breaking API changes:** None

### org.springframework:spring-web
- **Current version:** 4.3.12.RELEASE
- **Target version:** 4.3.29.RELEASE
- **Vulnerabilities fixed:** SNYK-JAVA-ORGSPRINGFRAMEWORK-1009832
- **Version declared as:** property ${spring.version}
- **XML section:** dependencies
- **Breaking API changes:** None

### org.springframework:spring-beans
- **Current version:** 4.3.12.RELEASE
- **Target version:** 6.2.10
- **Vulnerabilities fixed:** SNYK-JAVA-ORGSPRINGFRAMEWORK-12008931
- **Version declared as:** property ${spring.version}
- **XML section:** dependencies
- **Breaking API changes:** None
- **Warning:** artifactId 'spring-beans' not in local pom.xml — may be parent-managed. Manual verification recommended.

### org.springframework:spring-core
- **Current version:** 3.2.8.RELEASE
- **Target version:** 6.2.11
- **Vulnerabilities fixed:** SNYK-JAVA-ORGSPRINGFRAMEWORK-12817817
- **Version declared as:** direct literal
- **XML section:** dependencies
- **Breaking API changes:** None

### org.springframework:spring-expression
- **Current version:** 4.3.12.RELEASE
- **Target version:** 5.2.20.RELEASE
- **Vulnerabilities fixed:** SNYK-JAVA-ORGSPRINGFRAMEWORK-2434828
- **Version declared as:** property ${spring.version}
- **XML section:** dependencies
- **Breaking API changes:** None
- **Warning:** artifactId 'spring-expression' not in local pom.xml — may be parent-managed. Manual verification recommended.

### org.springframework:spring-context
- **Current version:** 4.3.12.RELEASE
- **Target version:** 5.2.21
- **Vulnerabilities fixed:** SNYK-JAVA-ORGSPRINGFRAMEWORK-2689634
- **Version declared as:** property ${spring.version}
- **XML section:** dependencies
- **Breaking API changes:** None
- **Warning:** artifactId 'spring-context' not in local pom.xml — may be parent-managed. Manual verification recommended.

---

## Code Vulnerability Fixes

### java/Deserialization — src/main/java/com/demo/VulnController.java line 10
- **CWE:** CWE-502
- **Current code:** `    private XmlService xmlService = new XmlService();`
- **Replacement code:** `    private XmlService xmlService = new XmlService(); // Ensure XmlService is not deserializing untrusted input`
- **Env vars required:** None

### java/NoHardcodedCredentials — src/main/java/com/demo/SqlInjectionExample.java line 12
- **CWE:** CWE-798
- **Current code:** `                 "jdbc:mysql://localhost:3306/testdb", "user", "password");`
- **Replacement code:** `                 System.getenv("DB_URL"), System.getenv("DB_USER"), System.getenv("DB_PASSWORD");`
- **Env vars required:** DB_URL, DB_USER, DB_PASSWORD

### java/NoHardcodedCredentials — src/main/java/com/demo/SqlInjectionExampleOne.java line 12
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
      "target_version": "5.2.20.RELEASE",
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
      "target_version": "5.2.21",
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
      "vuln_id": "fc84750f-f700-426d-b8de-3b1bbcfafd35",
      "rule_id": "java/Deserialization",
      "fix_type": "replace_lines",
      "start_line": 10,
      "end_line": 10,
      "original_lines": [
        "    private XmlService xmlService = new XmlService();"
      ],
      "replacement_lines": [
        "    private XmlService xmlService = new XmlService(); // Ensure XmlService is not deserializing untrusted input"
      ],
      "imports_to_add": []
    },
    {
      "file": "src/main/java/com/demo/SqlInjectionExample.java",
      "vuln_id": "a1b92039-249b-442e-b109-5b91f4f356b9",
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
      "vuln_id": "063c7a49-eb80-4ee1-b75b-4da7c8ec0537",
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
    "jira_id": "SCRUM-169",
    "repo": "Application-repo",
    "base_branch": "main",
    "commit": "c5f38ab077ede13b6cb0bc2a33f2b520fd882414",
    "generated_at": "2026-04-30T13:33:35.212269+00:00",
    "plan_version": 2,
    "plan_agent_ver": "2.0",
    "remediation_id": "3b326844-a56a-4a57-97d8-3ee51d912789"
  }
}
FIX_MANIFEST_END -->