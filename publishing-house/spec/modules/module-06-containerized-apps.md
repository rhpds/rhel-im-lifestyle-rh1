# Module 06 -- Deploying Containerized Applications

### Brief Overview

This module covers deploying containerized applications on a RHEL image-mode host using Podman. Participants will pull a sample application container image, run it on the image-mode system, verify it is accessible, and explore how containerized application deployment fits into the image-mode operational model. This demonstrates that RHEL image-mode systems serve as fully capable container hosts for running workloads alongside the image-based OS.

### Audience and Time

- **Target personas:** Red Hat technical sellers and Technical Account Managers (solutions architects, platform TAMs)
- **Experience level:** Intermediate -- familiar with RHEL system administration and basic container concepts (images, registries, Containerfiles)
- **Prerequisites for this module:** Completion of Module 05 (Firewall Configuration)
- **Estimated duration:** 20 minutes

### Learning Objectives

- Deploy a containerized application on a RHEL image-mode host using Podman
- Verify that the deployed container is running and the application is accessible
- Configure the container to run as a systemd service for persistence across reboots
- Describe how containerized application deployment complements the image-mode lifecycle

### Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1 | Pull the sample application image | 3 min |
| 2 | Run the containerized application | 5 min |
| 3 | Verify application accessibility | 4 min |
| 4 | Configure the container as a systemd service | 5 min |
| 5 | Validate persistent container operation | 3 min |

### Detailed Steps

1. List existing container images on the system with `podman images` to see the current baseline.
2. Pull the sample application container image from the registry using `podman pull`.
3. Run the container using `podman run` with appropriate flags (detached mode, port mapping, container name).
4. Verify the container is running with `podman ps` and note the container ID, port mapping, and status.
5. Test that the application is accessible by sending a request to the mapped port (e.g., `curl localhost:<port>`).
6. Generate a systemd unit file for the container using `podman generate systemd` so the application starts automatically on boot.
7. Install the generated systemd unit file and enable it.
8. Reload systemd and start the service to confirm it works under systemd management.
9. Verify the application is still accessible after the systemd transition.
10. Optionally, reboot and confirm the container starts automatically via the systemd service.

### Key Takeaways

- RHEL image-mode systems are fully capable container hosts -- Podman is available for deploying and managing containerized workloads
- Applications are deployed as containers on top of the image-based OS, keeping the OS layer clean and immutable
- Using `podman generate systemd` creates persistent services that survive reboots, integrating containers into the standard RHEL service management model
- The separation between the OS image and application containers simplifies updates -- the OS and applications can be updated independently

### Infrastructure Notes

- A sample containerized application image must be available in the registry -- pre-staged by setup automation
- Firewall rules from Module 05 may need to include the port used by the sample application
- Validation checks that the application container is running and accessible on the expected port
