---

copyright:
  years: 2018, 2020
lastupdated: "2020-06-01"

keywords: SAP HANA, {{site.data.keyword.baremetal_short}}, {{site.data.keyword.cloud_notm}}, database, application server

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}
{:note: .note}


# 5. Determining your configuration
{: #determine_configuration}

The following tables list the {{site.data.keyword.baremetal_long}} configurations available with the {{site.data.keyword.cloud}} SAP-Certified Infrastructure offering. For additional considerations when running SAP HANA in a virtualized environment, see [VMware ESXi server deployments](/docs/sap-hana?topic=sap-hana-considerations#vmware_server).
{: #shortdesc}

## Deciphering the server names
{: #server-names}

Here's an example on how to decipher the SAP HANA server names.

| Server name | Naming convention component | What it means |
| --- | --- | --- |
| BI.S3.H8401 | BI | Bluemix Interface |
| | S2 | Series 2 (processor generation) |
| | | S2 is Broadwell |
| | | S3 is Skylake/Kaby Lake |
| | | S4 is Cascade Lake
| | H | HANA-certified server |
| | 8 | 8-socket server |
| | 4 | 4 TB RAM |
| | 01 | Revision number (00 is launch, 01 is first revision, and so on) |
| | A or B | Available as appliances with preconfigured built-in disks (A) or as boot servers only (B) |


## BI.S2.H4100 (VMware)
{: #H4100}

[BI.S2.H4100 (VMware)](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=975&itemId=10633){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | `hdd0, hdd1, hdd2` | RAID1-A | 800 GB |
| RAID 5 | 3x 800 GB s3710 | `hdd3, hdd4, hdd5, hdd6` | RAID5-B | 1600 GB |
| RAID 5 | 4x 800 GB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` | RAID5-C | 2400 GB |
| Dedicated hot spare | 1X 800 GB s3710 | `hdd2, hdd6, hdd11` | 800 GB DHS | 800 GB |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4101
{: #H4101}

[BI.S2.H4101](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=885&presetId=545){: external}

Available for multi-node.

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 1 + hot spare | 3x 3.84 TB 5100 | `hdd3, hdd4, hdd5` | RAID1-B | 3.84 TB |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` |
|   | `/dev/sda4` | `/hana/log` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H4200 (VMware)
{: #H4200}

[BI.S2.H4200 (VMware)](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=969&itemId=10777){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | `hdd0, hdd1, hdd2` | RAID1-A | 800 GB |
| RAID 5 | 3x 1.2 TB s3710 | `hdd3, hdd4, hdd5, hdd6` | RAID5-B | 2.4 TB |
| RAID 5 | 5x 1.2 TB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` | RAID5-C | 4.8 TB |
| Dedicated hot spare | 1X 800 GB s3710 | `hdd2, hdd6, hdd11` | 800 GB DHS | 800 GB |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4201
{: #4201}

[BI.S2.4201](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=885&presetId=547){: external}

Available for multi-node.

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 7x 1.92 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 5.76 TB |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H4400 (VMware)
{: #4096_GB_memory}

[BI.S2.H4400 (VMware)](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=967&itemId=10775){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 3x 800 GB s3710 |`hdd0` | RAID1-A | 800 GB |
| RAID 5 | 6x 1.2 TB s3710 | `hdd1` | RAID5-B | 4100 GB |
| RAID 5 | 9x 1.2 TB s3710 | `hdd2` | RAID-5C | 8400 GB |
|Global hot spare | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4401
{: #H4401}

[BI.S2.H4401](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=885&presetId=549){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 5x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 7.68 TB |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H4601
{: #H4601}

[BI.S2.H4601](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=885&presetId=551){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 7x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 11.52 TB |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H8401
{: #H8401}

[BI.S2.H8401](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=861&presetId=537){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 5x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 7.68 TB |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `hana/data` | `rest` |


## BI.S2.H8801
{: #H8801}

[BI.S2.H8801](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=861&presetId=539){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 7x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 15.36 TB |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S3.H2.192 (Supports SAP Business One)
{: #2192_GB_memory}

[BI.S3.H2.192](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1045&presetId=823){: external}

Supports [SAP Business One](https://www.sap.com/products/business-one.html){: external}.

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 | `hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 1 | 2x 960 GB 5100 | `hdd2, hdd3` | RAID1-B | 960 GB |
| Global hot spare | 1x 960 GB 5100 | `hdd4` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 250 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S3.H2.384 (Supports SAP Business One)
{: #2384_GB_memory}

[BI.S3.H2.384](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1045&presetId=825){: external}

Supports [SAP Business One](https://www.sap.com/products/business-one.html){: external}.

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 960 GB 5100 | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 1920 GB |
| Global hot spare | 1x 960 GB 5100 | `hdd6` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 500 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S3.H2.768 (Supports SAP Business One)
{: #2768_GB_memory}

[BI.S3.H2.768](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1045&presetId=827){: external}

Supports [SAP Business One](https://www.sap.com/products/business-one.html){: external}.

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 960 GB 5100 | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 1920 GB |
| Global hot spare | 1x 960 GB 5100 | `hdd6` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 800 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## Appliance servers
{: #appliance-boot}

The following dual-socket servers are available as appliances with preconfigured built-in disks Appliance or as boot servers only; you have to attach the NFS storage. For more information, see [SAP Note 2414097)](https://launchpad.support.sap.com/#/notes/2414097){: external}.
{: note}

### BI.S4.H2.192 Appliance (Supports SAP Business One)
{: #S4192A}

[BI.S4.H2.192 Appliance](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1109&presetId=1087&location=dal13&imageItemId=13467){: external}

Supports [SAP Business One](https://www.sap.com/products/business-one.html){: external}.

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 | `hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 1 | 2x 960 GB 5100 | `hdd2, hdd3` | RAID1-B | 960 GB |
| Global hot spare | 1x 960 GB 5100 | `hdd4` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 250 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H2.384 Appliance (Supports SAP Business One)
{: #S4384A}

[BI.S4.H2.384 Appliance](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1109&presetId=1091&location=dal13&imageItemId=13467){: external}

Supports [SAP Business One](https://www.sap.com/products/business-one.html){: external}.

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 960 GB 5100 | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 1920 GB |
| Global hot spare | 1x 960 GB 5100 | `hdd6` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 500 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H2.768 Appliance (Supports SAP Business One)
{: #S4768A}

[BI.S4.H2.768 Appliance](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1109&presetId=1095&location=dal13&imageItemId=13467){: external}

Supports [SAP Business One](https://www.sap.com/products/business-one.html){: external}.

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 960 GB 5100 | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 1920 GB |
| Global hot spare | 1x 960 GB 5100 | `hdd6` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 800 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H2.1500 Appliance
{: #S41500A}

[BI.S4.H2.1500 Appliance](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1109&presetId=1099&location=dal13&imageItemId=13467){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
|  |  | |  |  |

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB SSD SED |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 1 | 2x 3.8 TB SSD SED | `hdd2, hdd3` | RAID1-B | 3.8 TB |
| Global hot spare | 1x 3.8 TB SSD SED | `hdd4` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H2.3000 Appliance
{: #S43000A}

[BI.S4.H2.3000 Appliance](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1109&presetId=1103&location=dal13&imageItemId=13467){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB SSD SED |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 3.8 TB SSD SED | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 7.6 TB |
| Global hot spare | 1x 3.8 TB SSD SED | `hdd6` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H4.3000 Appliance
{: #S4H43000A}

[BI.S4.H4.3000 Appliance](http://ibm.biz/S4_H4_3000A){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB SSD SED |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 3.8 TB SSD SED | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 7.6 TB |
| Global hot spare | 1x 3.8 TB SSD SED | `hdd6` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H4.6000 Appliance
{: #S4H46000A}

[BI.S4.H4.6000 Appliance](http://ibm.biz/S4_H4_6000A){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB SSD SED |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 3.8 TB SSD SED | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 7.6 TB |
| Global hot spare | 1x 3.8 TB SSD SED | `hdd6` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H8.6000 Appliance
{: #S4H86000A}

[BI.S4.H8.6000 Appliance](http://ibm.biz/S4_H8_6000A){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB SSD SED |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 3.8 TB SSD SED | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 7.6 TB |
| Global hot spare | 1x 3.8 TB SSD SED | `hdd6` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H8.12000 Appliance
{: #S4H81200A}

[BI.S4.H8.12000 Appliance](http://ibm.biz/S4_H8_12000A){: external}

| RAID | Components | Drives | Array | Size |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB SSD SED |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 8x 3.8 TB SSD SED | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID1-B | 15.2 TB |
| Global hot spare | 1x 3.8 TB SSD SED | `hdd6` |  |  |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## Boot-only servers
{: #boot-only}

By default, {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}s come with high-performance and highly-reliable internal storage based on solid state disks and high-performance RAID adapters. For projects with different requirements, such as storage snapshots, and that don't have a very high through-put requirement, {{site.data.keyword.cloud_notm}} offers "boot-only servers."

Boot-only servers have the same configuration as standard {{site.data.keyword.baremetal_short}}s, however, only the boot disks for the operating system is configured. The storage required for the SAP file systems - `/usr/sap`, `/hana/shared`, `/hana/data`, and `/hana/log` - is not provided, which means the cost for these servers is significantly reduced. To run SAP HANA on top of a boot-only server, you have to add {{site.data.keyword.cloud_notm}} storage to the server.

SAP HANA Tailored Data Center Integration (TDI) requirements must be met to run SAP HANA in production, or in a production-like environment. {{site.data.keyword.filestorage_full_notm}}, based on the Network File System (NFS), has two options - _Endurance_ and _Performance_. Endurance storage is a predefined IOPS per GB of storage, for example, 0.25 up to 10 IOPS per GB. Performance storage has different ranges of IOPS per GB, depending on the total size of the storage device.

| Size (GB) | Performance custom IOPS |
| --- | --- |
| 20-39 | 100-1,000 |
| 40-79 | 100-2,000 |
| 80-99 | 100-4,000 |
| 100-499 | 100-6,000 |
| 500-999 | 100-10,000 |
| 1,000-1,999 | 100-20,000 |
| 2,000-2,999 | 200-40,000 |
| 3,000-3,999 | 200-48,000 |
| 4,000-7,999 | 300-48,000 |
| 8,000-9,999 | 500-48,000 |
| 10,000-12,000 | 1,000-48,000 |
| 12,001-13,999 | 6,000-56,000 |
| 14,000-15,999 | 8,000-64,000 |
| 16,000-18,999 | 10,000-76,000 |
| 19,000-24,000 | 10,000-96,000 |
{: caption="Table 1. Performance storage GB and IOPS" caption-side="top"}

To fulfill SAP HANA TDI key performance indicators (TDIs), the minimum values to run SAP HANA in produciton and production-like setups is 8 K IOPS for `/hana/log` and a minimum of 7 K IOPS for `/hana/data`. These minimums are for Endurance and Performance storage. You can share storage areas for `/hana/shared` with `/hana/log` or `/hana/data` if these areas are too large for your particular use case. For non-production use, you can use one storage area for `/hana/shared`, `/hana/log`, and `/hana/data`.

### BI.S4.H2.192 (boot only)
{: #S4192B}

[BI.S4.H2.192 (boot only)](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1109&presetId=1089&location=dal13&imageItemId=13467){: external}

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 250 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H2.384 (boot only)
{: #S4384B}

[BI.S4.H2.384 (boot only)](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1109&presetId=1093&location=dal13&imageItemId=13467){: external}

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 500 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H2.768 (boot only)
{: #S4768B}

[BI.S4.H2.768 (boot only)](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1109&presetId=1097&location=dal13&imageItemId=13467){: external}

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 800 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H2.1500 (boot only)
{: #S41500B}

[BI.S4.H2.1500 (boot only)](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1109&presetId=1101&location=dal13&imageItemId=13467){: external}

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


### BI.S4.H2.3000 (boot only)
{: #S43000B}

[BI.S4.H2.3000 (boot only)](https://cloud.ibm.com/gen1/infrastructure/provision/bm?packageId=1109&presetId=1105&location=dal13&imageItemId=13467){: external}

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | 'rest' |

| Array | Partition | Name | Size (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## VMware
{: #vmware}

You are responsible for setting up VMware-related configurations for your server. For more information on configuring VMware on your SAP-certified {{site.data.keyword.baremetal_short}}, see [Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide)](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: external} (PDF) and explore the VMware wiki [SAP HANA on VMware vSphere](https://wiki.scn.sap.com/wiki/display/VIRTUALIZATION/SAP+HANA+on+VMware+vSphere){: external}.

## Next Steps

You are now ready to begin Provisioning your {{site.data.keyword.baremetal_short}}. See [Provisioning your SAP HANA environment](/docs/sap-hana?topic=sap-hana-provision_environment#provision_environment) for your next steps.
