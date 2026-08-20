# Module 02 -- System Updates and Automatic Scheduling

### Brief Overview

This module covers configuring automatic system updates for a RHEL image-mode system. Participants will explore how image-mode updates work -- pulling a new container image, staging it, and rebooting into the updated system. They will configure a scheduled update policy so the system checks for and applies updates automatically, then trigger an update and verify the system is running the new image version.

### Audience and Time

- **Target personas:** Red Hat technical sellers and Technical Account Managers (solutions architects, platform TAMs)
- **Experience level:** Intermediate -- familiar with RHEL system administration, comfortable with the command line
- **Prerequisites for this module:** Completion of Module 01 (Introduction and Lab Orientation)
- **Estimated duration:** 20 minutes

### Learning Objectives

- Configure an automatic update schedule for a RHEL image-mode system using bootc timer/scheduling mechanisms
- Apply a system update by pulling a new container image and staging it for the next boot
- Verify that the update was applied successfully by comparing image versions before and after the update
- Describe how image-mode updates differ from traditional package-based updates in RHEL

### Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1 | Review current image version | 3 min |
| 2 | Configure automatic update scheduling | 7 min |
| 3 | Trigger and apply an update | 5 min |
| 4 | Verify the updated system | 5 min |

### Detailed Steps

1. Run `bootc status` to record the current image reference and version as the pre-update baseline.
2. Examine the bootc update configuration files and timer units used for scheduling automatic updates.
3. Configure a scheduled update policy that defines when the system checks for new images and applies them.
4. Enable and start the timer or scheduling mechanism so that automatic updates are active.
5. Verify the schedule is registered by listing active timers or checking the configuration state.
6. Trigger a manual update to pull the latest image from the registry using `bootc upgrade` or the appropriate update command.
7. Observe that the new image is staged for the next boot.
8. Reboot the system to apply the staged update.
9. After reboot, run `bootc status` again and confirm the system is now running the new image version.
10. Compare the pre-update and post-update image references to confirm the update was applied.

### Key Takeaways

- Image-mode updates replace the entire OS image atomically rather than updating individual packages
- Scheduled update policies automate the process of checking for and staging new images
- Updates are staged first and applied on reboot, providing a safe transition point
- The `bootc status` command shows both the current running image and any staged image awaiting reboot

### Infrastructure Notes

- An updated container image must be available in the registry before the update step -- this is pre-staged by the lab setup automation
- The reboot step is required to apply the staged update; participants should expect a brief interruption in their terminal session
- Validation checks that the automatic update schedule is configured and that an update has been applied
