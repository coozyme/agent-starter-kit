---
description: Workflow for handling production incidents
---

# Incident Response Workflow

Steps for triaging, diagnosing, resolving, and learning from production incidents.

## Steps

### 1. Detection & Triage
- Acknowledge the alert/report
- Assess severity:

| Severity | Impact | Response Time |
|----------|--------|---------------|
| **SEV-1** | Service down, data loss | Immediate |
| **SEV-2** | Major feature broken | < 1 hour |
| **SEV-3** | Minor feature broken | < 4 hours |
| **SEV-4** | Cosmetic/low impact | Next business day |

- Notify stakeholders based on severity
- Assign an incident commander

### 2. Communicate
- Update the status page
- Notify affected users (if appropriate)
- Set up a war room / communication channel
- Provide regular updates every 15-30 minutes

### 3. Diagnose
- Review logs and metrics around the incident start time
- Check recent deployments or configuration changes
- Identify the blast radius (what's affected)
- Use `skills/debugging-skill.md` for systematic investigation

### 4. Mitigate
Priority: **Restore service first, root cause later**
- Rollback the last deployment if suspected
- Scale up resources if under load
- Disable the broken feature (feature flag)
- Redirect traffic if needed

### 5. Resolve
- Implement a permanent fix
- Test the fix thoroughly
- Deploy following `workflows/deployment.md`
- Verify the issue is fully resolved

### 6. Postmortem
Create a postmortem document within 48 hours:
- **Timeline**: What happened, when
- **Root cause**: Why it happened
- **Impact**: Who/what was affected, duration
- **Resolution**: How it was fixed
- **Action items**: Preventive measures with owners and deadlines
- **Lessons learned**: What went well, what could improve

### Postmortem Rules
- Blameless — focus on systems, not individuals
- Be honest and thorough
- Follow up on action items
- Share with the broader team
