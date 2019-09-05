# ASR - Azure Site Recovery

Lessons Learned

- First time sync requires FULL VHD needs to be pushed over the wire. - You can schedule this during non-busy hours and throttle bandwidth.
- After full sync, only deltas are pushed.
- Only the data used in the VHD(not in the virtual size) will be sent to Azure and stored in Azure.
- Express route is recommended for frequent large data
- Make sure azure subscription has enough cores to receive and not maxed out.

Requirements
- Windows Server 2012 R2 +
- Network, Storage and IOPS (Fail over and replication same time) capacity planning

Limitations
- No Support for UEFI
- Hyper V - Gen 2 not supported - Gen 2 converts to Gen 1 when failed over.
- Data disks can be dynamic but not OS disk
- Physical can be converted to VM but NO fail back.
- Less than 1 TB disks and can support up to 64 Disks

Steps
- Create recovery services vault
- Create Container
- Create Provider installation
- Connect with Azure Site Recovery
- Choose target Azure subscriptions
- Create Replication policy
- Select your source
- Choose target
- Select virtual machines
- Configure properties
- Select your replication policy
- Jobs fire, replication starts

Steps for failover
- Create Recovery Plan
- Select your machines
- customize failover

Physical and Vmware
- Requires Config Server (8 cores, 16GB RAM, 2012R2+ and 600 GB Free Disk)
- configuration server = Use for centralized management
- process server = Used for caching, compression and encryption
- Mobility service is running on the physcial server = captures all data writes from memory
- master target server = Used for FAILBACK only



