---
id: T-003
title: Scaffold rig-midimon
status: Done
assignee: []
created_date: '2026-11-06T14:51:00Z'
updated_date: '2026-11-17T01:32:00Z'
labels:
  - midi
  - ui
  - app
  - rig-template
dependencies: []
priority: medium
type: feature
ordinal: 3000
---

## Description

<!-- SECTION:DESCRIPTION:BEGIN -->
Create rig-midimon app from template with basic MIDI monitor UI.
<!-- SECTION:DESCRIPTION:END -->

## Acceptance Criteria
<!-- AC:BEGIN -->
- [x] #1 Create app from template.
- [x] #2 Implement basic MIDI monitor UI.
- [x] #3 Update README, SPEC, and NOTES.
<!-- AC:END -->

## Implementation Notes

<!-- SECTION:NOTES:BEGIN -->
Reminder: ensure the MIDI monitor displays/logs raw MIDI values (channel, message type, note/CC number, velocity/value) so users can discover the exact identifiers needed when authoring config-driven mappings (see T-002/T-014).
<!-- SECTION:NOTES:END -->

## Final Summary

<!-- SECTION:FINAL_SUMMARY:BEGIN -->
Scaffolded rig-midimon as a new standalone app: git repo with core/components submodules, Makefile/Dockerfile/scripts, go.mod, cmd/rig/main.go (engine flag + watch), internal/ui MIDI monitor (port list, open/close, counters, lamps, raw value display), README/NOTES/SPEC. Verified go build/vet and -watch smoke test.
<!-- SECTION:FINAL_SUMMARY:END -->
