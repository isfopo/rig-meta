---
id: T-002
title: Add MIDI mapping table to rig-core
status: Done
assignee: []
created_date: '2026-11-06T14:51:00Z'
updated_date: '2026-11-16T05:03:00Z'
labels:
  - midi
  - config
  - rig-core
milestone: m-0
dependencies: []
priority: high
type: task
ordinal: 2000
---

## Description

<!-- SECTION:DESCRIPTION:BEGIN -->
Define reusable config-driven MIDI mapping schema in rig-core.
<!-- SECTION:DESCRIPTION:END -->

## Acceptance Criteria
<!-- AC:BEGIN -->
- [x] #1 Define reusable config-driven MIDI mapping schema.
- [x] #2 Add tests.
- [x] #3 Document usage.
<!-- AC:END -->

## Final Summary

<!-- SECTION:FINAL_SUMMARY:BEGIN -->
Implemented config-driven MIDI mapping schema in rig-core/midi: Mapping/MappingTable types with TOML tags, validation, device filtering, and Match/Action helpers. Added mapping_test.go (validation, matching, value filters, device handling, TOML round trip). Verified with go test ./midi/.
<!-- SECTION:FINAL_SUMMARY:END -->
