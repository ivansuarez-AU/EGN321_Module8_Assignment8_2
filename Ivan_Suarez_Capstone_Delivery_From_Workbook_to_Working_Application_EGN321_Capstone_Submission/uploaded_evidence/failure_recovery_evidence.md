# Controlled Failure and Recovery Evidence

## Demo Scenario
The application expects the analysis database/history file to be available.

## Failure Introduced
The database file is temporarily renamed or moved so the application cannot access it.

## Expected Result
The application should not silently continue as if historical evidence is available.

## First Observable Symptom
The application reports that the database/history source is unavailable.

## Evidence
- application error/status message;
- operational log entry;
- missing database file;
- failed history query.

## Recovery Procedure
1. Stop the application if required.
2. Restore the database/history file.
3. Restart the application.
4. Reload the 720-record dataset if the database must be rebuilt.
5. Re-run the history query.
6. Verify the dashboard loads successfully.

## Recovery Verification
Recovery is considered successful only when:
- the system can access history again;
- all 720 reference records are available;
- the dashboard/analysis loads;
- the health/status returns to the expected normal state;
- no unresolved database error remains in the latest log output.

## Remaining Limitation
This classroom recovery test does not demonstrate production database replication, authentication, or high-availability failover.
