# Module 07 -- Sealed Images (Tentative)

> **Note:** This module is tentative. It will be included in the lab only if the sealed images feature reaches sufficient maturity in RHEL Image Mode. Without this module, the lab runs approximately 1 hour 45 minutes.

### Brief Overview

This module introduces sealed images for fully immutable system configurations in RHEL Image Mode. Participants will explore how sealed images lock down the OS configuration so that no runtime modifications are possible, examine the trade-offs between flexibility and immutability, and configure a sealed image deployment. This represents the most restrictive end of the image-mode spectrum, where the container image is the sole source of truth for the system state.

### Audience and Time

- **Target personas:** Red Hat technical sellers and Technical Account Managers (solutions architects, platform TAMs)
- **Experience level:** Intermediate -- familiar with RHEL system administration, image-mode concepts from the preceding modules
- **Prerequisites for this module:** Completion of Modules 01 through 06
- **Estimated duration:** 15 minutes

### Learning Objectives

- Describe the purpose and trade-offs of sealed images in the RHEL Image Mode lifecycle
- Configure a sealed image deployment that enforces fully immutable system configuration
- Verify that runtime modifications are blocked on a sealed image system
- Compare sealed images to the standard image-mode configuration used in earlier modules

### Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1 | Review sealed image concepts | 3 min |
| 2 | Configure a sealed image | 5 min |
| 3 | Verify immutability enforcement | 4 min |
| 4 | Compare sealed vs. standard image mode | 3 min |

### Detailed Steps

1. Review the concept of sealed images -- what "sealed" means in the context of image mode and how it differs from the standard image-mode configuration used throughout the lab.
2. Examine the bootc configuration or Containerfile directives that enable sealed image behavior.
3. Apply the sealed image configuration to the system or deploy a pre-built sealed image from the registry.
4. Attempt a runtime modification (e.g., writing to a normally writable configuration path) and observe that the modification is blocked or reverted.
5. Run `bootc status` to confirm the system is operating in sealed mode.
6. Compare the sealed image system behavior with the standard image-mode behavior experienced in earlier modules -- noting which operations are now restricted.
7. Discuss when sealed images are appropriate: high-security environments, compliance-driven deployments, edge or kiosk systems where configuration drift is unacceptable.

### Key Takeaways

- Sealed images represent the most restrictive configuration in RHEL Image Mode, enforcing complete immutability at runtime
- The container image becomes the sole source of truth -- all configuration, packages, and system state must be defined at build time
- Sealed images eliminate configuration drift by design, making them suitable for compliance-critical and edge deployments
- The trade-off is reduced runtime flexibility -- administrators cannot make ad-hoc changes without rebuilding and redeploying the image

### Infrastructure Notes

- This module depends on the sealed images feature being available and sufficiently mature in RHEL 10 Image Mode
- A pre-built sealed image may need to be staged in the registry by setup automation, depending on the configuration workflow
- Validation checks sealed image configuration (specific checks to be defined once feature details are finalized)
- If this module is excluded, no changes are needed to earlier modules -- they are self-contained
