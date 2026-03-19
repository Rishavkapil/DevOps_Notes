Bridge between on-prem and cloud data. 

## Types of Storage Gateway

- File Gateway
- Volume Gateway
- Tape Gateway

### File Gateway

Configured S3 bucket are accessible using NFS and SMB protocol. 

NFS : File Sharing protocol for Linux
SMB: File Sharing protocol for Windows.

- Most recently used data is cached in file gateway. 

### Volume Gateway

Block Storage using ISCSI backed by S3. 
- Backed by EBS Snapshots which can help restore on-premise volume. 

**Cached Volume**: Low latency access to most recent data. 
**Stored Volume**: Entire data is on-premise , scheduled Backups to S3

### Tape Gateway

- Some companies have backup process using physical tapes. 
- Replaces physical tapes libraries with virtual tapes. 

