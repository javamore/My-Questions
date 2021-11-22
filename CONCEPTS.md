Concepts of GCP and ACE Exam related.

[TOC]



## CloudStorage 存储类别

### Standard

Standard 存储空间最适合频繁访问的数据（“热门”数据）和/或短期存储的数据。

### Nearline

Nearline 存储空间是一项费用低廉、高度耐用的存储服务，用于存储不常访问的数据。如果您愿意牺牲少许可用性，可以接受最短 30 天存储时长并支付数据访问费用，以此来换取更低的[静态存储费用](https://cloud.google.com/storage/pricing#storage-pricing)，则 Nearline 存储空间是比 Standard 存储空间更好的选择。

非常适合用于存储您计划平均每月或更长时间读取或修改一次的数据。例如，如果您要将文件连续添加到 Cloud Storage 并计划每月访问一次这些文件以执行分析，则 Nearline 存储空间是一个很好的选择。

对于每季度访问频率低于一次的数据，Coldline 存储空间或 Archive 存储空间才是最具成本效益的选择，因为它们具有较低的存储费用。

### Coldline

Coldline 存储空间是一项费用低廉、高度耐用的存储服务，用于存储不常访问的数据。如果您愿意牺牲少许可用性，可以接受最短 90 天存储时长并支付较高的数据访问费用，以此来换取较低的[静态存储费用](https://cloud.google.com/storage/pricing#storage-pricing)，则 Coldline 存储空间是比 Standard 存储空间或 Nearline 存储空间更好的选择。

Coldline 存储空间非常适合用于存储您计划每季度最多读取或修改一次的数据。

### Archive

Archive 存储空间是一种费用最低、高度耐用的数据归档、在线备份和灾难恢复存储服务。与其他云服务提供商提供的“最冷”存储服务不同，您的数据在几毫秒内即可使用，而不是数小时或数天。

Archive 存储空间的数据访问和运营费用较高，所需最低存储时间为 365 天。Archive 存储空间最适合您计划每年访问不足一次的数据。比如：冷数据存储 - 已归档数据；灾难恢复 - 如果发生[灾难恢复](https://cloud.google.com/solutions/designing-a-disaster-recovery-plan)事件，恢复时间至关重要。

### Others

- **Multi-Regional 存储空间**：相当于 Standard 存储空间，但 Multi-Regional 存储空间只能用于存储在[多区域](https://cloud.google.com/storage/docs/locations#location-mr)或[双区域](https://cloud.google.com/storage/docs/locations#location-dr)中的对象。

- **Regional 存储空间**：相当于 Standard 存储空间，但 Regional 存储空间仅用于存储在[区域](https://cloud.google.com/storage/docs/locations#location-r)中的对象。

- **Durable Reduced Availability (DRA) 存储空间**：类似于 Standard 存储空间，差别在于：

  - DRA 的操作价格较高。
  - DRA 的性能较低，特别是在可用性方面（DRA 的服务等级协议承诺的可用性为 99％）。

  

























