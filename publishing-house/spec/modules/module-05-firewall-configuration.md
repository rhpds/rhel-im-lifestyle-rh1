# Module 05 -- Firewall Configuration

### Brief Overview

This module covers configuring firewall rules on a RHEL image-mode system using standard RHEL firewall tooling. Participants will inspect the current firewall state, add rules to allow or restrict specific services and ports, and verify that the rules are active and enforced. This demonstrates that familiar RHEL firewall management workflows apply within image-mode deployments.

### Audience and Time

- **Target personas:** Red Hat technical sellers and Technical Account Managers (solutions architects, platform TAMs)
- **Experience level:** Intermediate -- familiar with RHEL system administration and basic networking concepts
- **Prerequisites for this module:** Completion of Module 04 (Security Hardening with OpenSCAP)
- **Estimated duration:** 15 minutes

### Learning Objectives

- Configure firewall rules on a RHEL image-mode deployment using standard RHEL firewall tooling (firewalld/firewall-cmd)
- Verify that specified firewall rules are active and enforced on the running system
- Describe how firewall configuration persists (or does not persist) across image updates in image-mode systems

### Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1 | Inspect the current firewall state | 3 min |
| 2 | Add firewall rules for specific services and ports | 5 min |
| 3 | Verify rule enforcement | 4 min |
| 4 | Review persistence considerations | 3 min |

### Detailed Steps

1. Check that the firewalld service is running using `systemctl status firewalld`.
2. List the current active zones and their associated rules using `firewall-cmd --list-all`.
3. Identify the default zone and note which services and ports are currently permitted.
4. Add a firewall rule to allow a specific service (e.g., HTTP) using `firewall-cmd --add-service`.
5. Add a firewall rule to open a specific port (e.g., 8080/tcp) using `firewall-cmd --add-port`.
6. Make the rules permanent so they survive a firewalld reload using `firewall-cmd --runtime-to-permanent` or the `--permanent` flag.
7. Reload the firewall configuration with `firewall-cmd --reload` and verify the permanent rules are active.
8. List the updated rules with `firewall-cmd --list-all` to confirm the new service and port entries appear.
9. Discuss how these runtime firewall changes relate to image-mode -- whether they persist across image updates or need to be baked into the container image for durability.

### Key Takeaways

- Standard RHEL firewall tooling (firewalld, firewall-cmd) works on image-mode systems without modification
- Firewall rules can be configured at runtime, but their persistence across image updates depends on how the image-mode system manages configuration layers
- For durable firewall configuration in image mode, rules should be incorporated into the container image build process
- Verifying active rules with `firewall-cmd --list-all` confirms that the configuration is enforced as expected

### Infrastructure Notes

- firewalld must be running on the lab VM -- confirmed by setup automation
- Validation checks that specified firewall rules are active on the system
- The module highlights the distinction between runtime configuration and image-level configuration for persistence across updates
