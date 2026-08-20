# RHEL Image Mode Lifestyle, preparing for RHEL 11

## Overview

This hands-on lab covers the day-2 operational and security aspects of Red Hat Enterprise Linux Image Mode. It extends the foundational concepts from the "Image Mode is the Best Mode" lab with a focus on ongoing maintenance, security hardening, and compliance workflows.

Participants will configure automatic system updates and scheduling, perform system rollbacks, apply CIS security benchmarks using OpenSCAP, configure firewall rules, and deploy containerized applications — all within the image-mode lifecycle. If the feature is sufficiently mature, participants will also explore sealed images for immutable system configurations.

## Target Audience

- **Role:** Red Hat technical sellers and Technical Account Managers — solutions architects, platform TAMs
- **Experience level:** Intermediate
- **What they already know:** RHEL system administration fundamentals, basic familiarity with containerized workflows, comfort with the command line
- **What they don't know:** RHEL Image Mode day-2 operations — how to manage updates, rollbacks, security hardening, and application deployment in an image-based model

## Prerequisites

- Basic RHEL system administration experience (managing packages, services, file systems)
- Familiarity with container concepts (images, registries, Containerfiles)
- No prior RHEL Image Mode experience required — the lab provides orientation

Automated prerequisite validation: No — prerequisites are based on prior knowledge, not environment state.

## Learning Objectives

1. Configure automatic system updates for RHEL image-mode systems using scheduled update policies
2. Implement system rollback to restore a previous image version after a failed or unwanted update
3. Apply CIS security benchmarks to image-mode systems using OpenSCAP profiles
4. Verify system compliance status against applied security hardening profiles
5. Configure firewall rules within image-mode deployments using standard RHEL firewall tooling
6. Deploy containerized applications on a RHEL image-mode host
7. Explore sealed images for fully immutable system configurations (if feature is available)

## Content Type

Lab (hands-on, zero-touch with solve/validate buttons)

## Products & Technologies

- Red Hat Enterprise Linux 10 (Image Mode)
- bootc (boot container tooling)
- OpenSCAP
- Podman

## Module Map

| Module | Title | Duration |
|--------|-------|----------|
| 1 | Introduction and Lab Orientation | 10 min |
| 2 | System Updates and Automatic Scheduling | 20 min |
| 3 | System Rollback | 15 min |
| 4 | Security Hardening with OpenSCAP | 25 min |
| 5 | Firewall Configuration | 15 min |
| 6 | Deploying Containerized Applications | 20 min |
| 7 | Sealed Images (Tentative) | 15 min |
| — | **Total hands-on** | **~2 hours** |

Module 7 (Sealed Images) is tentative — included if the feature reaches sufficient maturity. Without it, the lab runs approximately 1 hour 45 minutes.

## Difficulty Level

Intermediate

## Environment

**Learner view:** A RHEL 10 build host (package mode) accessible via web terminal, with nested virtualization enabled. An image-mode guest VM runs on the build host — participants perform lab exercises on the guest. A container registry is available for pulling and pushing bootc images.

**Automation needed:** Yes

- RHEL 10 build host provisioned via setup automation with nested virtualization enabled
- Image-mode guest VM created and running on the build host
- Base bootc container image pre-built and available in a registry
- OpenSCAP packages and CIS profiles pre-installed or available on the guest
- Sample containerized application image available for deployment module

## Infrastructure Requirements

- **Cloud provider:** Troshka (nested virtualization required)
- **Platform:** RHEL VMs
- **Topology:** Per-student
- **Per student:** 1 RHEL 10 build host — package mode (4 vCPU, 16GB RAM, 100GB disk) with nested virtualization enabled, hosting an image-mode guest VM for lab exercises
- **Automation approach:** Ansible
- **AI/MaaS:** None
- **External services:** registry.redhat.io, cdn.redhat.com, github.com
- **Non-GA products:** None (all products are GA)

## Assessment Strategy

Each module uses zero-touch solve/validate buttons:

| Module | Validation approach |
|--------|-------------------|
| 1 — Introduction | No validation (orientation only) |
| 2 — System Updates | Validate that automatic update schedule is configured and an update has been applied |
| 3 — Rollback | Validate that the system has been rolled back to the previous image |
| 4 — OpenSCAP | Validate that CIS profile scan has been run and results are available |
| 5 — Firewall | Validate that specified firewall rules are active |
| 6 — Containerized Apps | Validate that the application container is running and accessible |
| 7 — Sealed Images | Validate sealed image configuration (if included) |
