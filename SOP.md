# Team SOPs v1.0
Ratified 2026-10-19. Maintained by Pizzapan. Changes are reviewed by the team and need Leon Tucker's final OK.

## Tester SOP v1.0
### Bug reports
Every bug report includes:
- **Severity**: Blocker, Critical, Major, Minor or Cosmetic
- **Frequency**: Always, Sometimes or Once
- **Status**: Open, Fixed, Verified, Reopened or Closed

### Severity levels (highest first)
1. **Blocker**: you can't continue, or the game won't launch. Report it immediately.
2. **Critical**: a crash, lost data or saves, or a progression stopper that has a workaround.
3. **Major**
4. **Minor**
5. **Cosmetic**

### No checklist for a build
Ask the build's Design owner for one. Do exploratory testing while you wait.

### Regression
- The dev or Design owner sets a bug to **Fixed** and records the build number of the fix.
- Testers retest Fixed bugs on the next build:
  - If the fix works: set **Verified** and record the build number. The bug becomes **Closed** once the Design owner or dev confirms.
  - If the bug is still there: set **Reopened** and record the build number. Don't file a new report.

### Who sets each status
| Status | Set by |
|---|---|
| Open | Tester |
| Fixed | Dev / Design owner |
| Verified | Tester |
| Reopened | Tester |
| Closed | Dev / Design owner |

## Designer SOP v1.0
- A doc is **Approved** only when the reviewer and Leon both sign off. If the reviewer hasn't responded after 2 working days, Leon's sign-off alone is enough.
- Each QA checklist item lists: feature or area, steps, expected result, known issues and target platforms.
- Triage feedback every Monday. Post each result with its reason. If 3 or more testers report the same item, review it within 24 hours.
- Balance log entries record: old value, new value, rationale and build number.
- Mark cut docs **Cut**. Don't delete them.
