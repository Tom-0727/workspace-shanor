# HEARTBEAT.md

# Keep this file empty (or with only comments) to skip heartbeat API calls.

# Add tasks below when you want the agent to check something periodically.

---

## OKR Check

During each heartbeat:

1. **Read** `okr/current.md`
2. **Check status**:
   - If `status: empty` → Prompt human: "No OKR set. Want to set one?"
   - If `status: active` → Check each KR progress
3. **Identify issues**:
   - `at_risk` → Prioritize related tasks, or notify human
   - `blocked` → Escalate to human with blocker details
4. **Cycle end check**:
   - If today >= `end` date → Generate weekly report
   - Move completed OKR to archive
5. **Update** `current.md` with any progress changes

---

## Priority Order

When multiple tasks compete:
1. Blocked KRs (escalate immediately)
2. At-risk KRs (prioritize work)
3. Normal heartbeat checks
4. Proactive work (memory maintenance, etc.)
