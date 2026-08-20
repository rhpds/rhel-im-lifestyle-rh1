# Module 03 -- System Rollback

### Brief Overview

This module demonstrates how to perform a system rollback on a RHEL image-mode system. After the update applied in Module 02, participants will roll back to the previous image version, simulating a real-world scenario where an update introduces an unwanted change or failure. The atomic nature of image-mode makes rollback a straightforward operation -- switching back to the previously booted image without manual package downgrades or configuration restoration.

### Audience and Time

- **Target personas:** Red Hat technical sellers and Technical Account Managers (solutions architects, platform TAMs)
- **Experience level:** Intermediate -- familiar with RHEL system administration, comfortable with the command line
- **Prerequisites for this module:** Completion of Module 02 (System Updates and Automatic Scheduling)
- **Estimated duration:** 15 minutes

### Learning Objectives

- Implement a system rollback to restore the previous image version on a RHEL image-mode system
- Verify that the rollback was successful by confirming the system is running the prior image
- Compare the rollback workflow in image mode to traditional RHEL rollback or recovery approaches

### Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1 | Review current and previous images | 3 min |
| 2 | Perform the rollback | 5 min |
| 3 | Verify the rollback result | 4 min |
| 4 | Review rollback implications | 3 min |

### Detailed Steps

1. Run `bootc status` to confirm the system is running the updated image from Module 02 and note the previous image listed in the status output.
2. Identify the rollback target -- the previously booted image that is still available on the system.
3. Execute the rollback command using `bootc rollback` or the appropriate bootc subcommand to stage the previous image.
4. Confirm that the previous image is now staged for the next boot by re-checking `bootc status`.
5. Reboot the system to apply the rollback.
6. After reboot, run `bootc status` and verify the system is now running the original (pre-update) image version.
7. Compare the current image reference with the baseline recorded in Module 02 to confirm the rollback is complete.
8. Reflect on how this rollback process compares to recovering from a bad update on a traditional package-based RHEL system.

### Key Takeaways

- Image-mode rollback is an atomic operation that restores the entire OS to a known-good previous image
- The system retains the previous image after an update, making rollback immediately available without re-downloading
- Rollback in image mode eliminates the complexity of package-level downgrades, dependency resolution, and configuration file conflicts
- This capability provides a safety net that makes update adoption less risky in production environments

### Infrastructure Notes

- This module depends on the update performed in Module 02 -- the system must have both a current and a previous image available
- The reboot step is required to complete the rollback; participants should expect a brief terminal session interruption
- Validation checks that the system has been rolled back to the previous image version
