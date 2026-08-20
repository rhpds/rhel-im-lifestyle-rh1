# Module 01 -- Introduction and Lab Orientation

### Brief Overview

This module introduces participants to the lab environment and provides orientation on RHEL Image Mode day-2 operations. Participants will review the pre-provisioned RHEL 10 image-mode virtual machine, confirm connectivity via the web terminal, and examine the base system configuration. The module sets the context for the remaining hands-on exercises by explaining how image-mode differs from traditional RHEL administration for ongoing maintenance, security, and application deployment tasks.

### Audience and Time

- **Target personas:** Red Hat technical sellers and Technical Account Managers (solutions architects, platform TAMs)
- **Experience level:** Intermediate -- familiar with RHEL system administration fundamentals, basic container concepts, and the command line
- **Prerequisites for this module:** None beyond the general lab prerequisites
- **Estimated duration:** 10 minutes

### Learning Objectives

- Identify the key components of the lab environment, including the RHEL 10 image-mode VM and the container registry
- Verify connectivity to the lab VM via the web terminal
- Examine the current bootc image status and container image baseline on the running system
- Describe the day-2 operational topics covered in this lab: updates, rollbacks, security hardening, firewall configuration, containerized applications, and (tentatively) sealed images

### Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1 | Welcome and lab overview | 3 min |
| 2 | Connect to the lab environment | 3 min |
| 3 | Examine the image-mode system baseline | 4 min |

### Detailed Steps

1. Read the welcome text and review the list of modules and learning objectives for the lab.
2. Open the web terminal tab and confirm a shell prompt is available on the RHEL 10 image-mode VM.
3. Run `bootc status` to view the current image, image version, and staging state.
4. Run `podman images` to list container images available locally.
5. Run `rpm-ostree status` or equivalent bootc command to confirm the system is booted from the expected base image.
6. Review the output and note the image reference and digest -- these will change as updates and rollbacks are performed in later modules.

### Key Takeaways

- RHEL Image Mode treats the operating system as a container image, enabling container-native lifecycle operations for day-2 tasks
- The `bootc status` command is the primary tool for inspecting the current and staged images on an image-mode system
- Day-2 operations in image mode -- updates, rollbacks, hardening, application deployment -- follow a different workflow than traditional package-based RHEL administration
- The lab environment provides a single RHEL 10 image-mode VM with a container registry for pulling updated images

### Infrastructure Notes

- The RHEL 10 image-mode VM is pre-provisioned via setup automation before the participant begins
- A base container image is pre-built and available in the registry
- No solve/validate buttons for this module -- it is orientation only
