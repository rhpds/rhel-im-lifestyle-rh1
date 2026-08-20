# Module 04 -- Security Hardening with OpenSCAP

### Brief Overview

This module covers applying CIS security benchmarks to a RHEL image-mode system using OpenSCAP. Participants will run a compliance scan against a CIS profile, review the scan results to identify non-compliant items, apply remediation where applicable within the image-mode context, and re-scan to verify improved compliance. This demonstrates how standard RHEL security tooling integrates with the image-mode lifecycle.

### Audience and Time

- **Target personas:** Red Hat technical sellers and Technical Account Managers (solutions architects, platform TAMs)
- **Experience level:** Intermediate -- familiar with RHEL system administration, comfort with security concepts
- **Prerequisites for this module:** Completion of Module 03 (System Rollback); OpenSCAP packages and CIS profiles are pre-installed on the lab VM
- **Estimated duration:** 25 minutes

### Learning Objectives

- Apply a CIS security benchmark profile to a RHEL image-mode system using OpenSCAP
- Execute a compliance scan and interpret the results to identify non-compliant configuration items
- Remediate selected findings within the image-mode context and verify improved compliance status
- Verify system compliance status by re-running the scan after remediation

### Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1 | Review available OpenSCAP profiles | 4 min |
| 2 | Run an initial compliance scan | 6 min |
| 3 | Analyze scan results | 5 min |
| 4 | Apply remediation for selected findings | 5 min |
| 5 | Re-scan and verify compliance improvement | 5 min |

### Detailed Steps

1. List the available SCAP content and security profiles on the system using `oscap info` on the RHEL datastream file.
2. Identify the CIS benchmark profile to be used for the scan.
3. Run an initial compliance scan against the CIS profile using `oscap xccdf eval`, generating both terminal output and an HTML report.
4. Review the scan summary to note the overall pass/fail counts and compliance percentage.
5. Examine specific failed rules in the scan results to identify actionable remediation items.
6. Select one or more findings that can be remediated within the image-mode system (e.g., configuration file changes, service settings).
7. Apply the remediation steps for the selected findings.
8. Re-run the compliance scan against the same CIS profile.
9. Compare the second scan results to the initial scan and confirm that the remediated items now pass.
10. Review the HTML report for a visual summary of the compliance status.

### Key Takeaways

- OpenSCAP and CIS security benchmarks work on RHEL image-mode systems using the same tooling and profiles as traditional RHEL
- Compliance scanning provides a measurable baseline and actionable findings for security hardening
- Some remediation actions can be applied at runtime on image-mode systems; others are better applied in the container image build process for persistent hardening
- Re-scanning after remediation provides verification that changes achieved the intended compliance improvement

### Infrastructure Notes

- OpenSCAP packages and CIS profiles must be pre-installed or available on the lab VM -- handled by setup automation
- The SCAP datastream file path depends on the RHEL 10 content package version installed
- Validation checks that a CIS profile scan has been run and results are available on the system
