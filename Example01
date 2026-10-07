```mermaid
flowchart TB
    subgraph ServerA [Server A: App & Control Node]
        subgraph DirApp [/var/www/app/bin]
            J1[Job A1: DB Migration]
            J2[Job A2: Cache Clear]
        end
        subgraph DirConfig [/etc/app/config]
            J3[Job A3: Sync Config]
        end
    end

    subgraph ServerB [Server B: Compute & Worker Node]
        subgraph DirData [/opt/worker/data]
            J4[Job B1: Ingest CSV]
            J5[Job B2: Process Images]
        end
        subgraph DirLogs [/var/log/worker]
            J6[Job B3: Rotate Logs]
        end
    end

    subgraph StorageServer [Shared NAS Server]
        subgraph DirShared [/mnt/shared/backups]
            J7[Job S1: Database Dump]
            J8[Job S2: File Archiving]
        end
    end

    %% Cross-Server and Cross-Directory Dependencies
    J1 -->|Triggers data ingest| J4
    J2 -->|Notifies worker| J5
    J3 -->|Updates config| J6
    J4 -->|Saves output| J7
    J5 -->|Saves media| J8
    J7 -->|Triggers rotation| J6
```
