---
sidebar_label: Overview
slug: /en/manage/billing
title: Billing
---

## Pricing

For pricing information see the [ClickHouse Cloud Pricing](https://clickhouse.com/pricing) page.  To understand what can affect your bill, and ways that you
can manage your spend, keep reading.

## Amazon Web Services(AWS) Examples

:::note
Prices reflect AWS `us-east-1` pricing.
:::

### Development: From $51 per month

Best for: Starter projects & staging
- Development service
- 16 GiB RAM, 2 vCPU
- 1 TB Data

#### Pricing breakdown for this example:

  |         | 10% active | 50% active | Always on |
  |---------|-----------:|-----------:|----------:|
  | Compute |  $16       |  $79       |  $158     |
  | Storage |  $35       |  $35       |   $35     |
  | Total   |  $51       | $114       |  $193     |

:::note
Consumption can be even lower if less than 1TB disk is used
:::

### Production (Idling, Auto-scaling): From $172 per month

#### Best for: Cost-sensitive ad-hoc analytics applications
- Production Service
- Active workload ~25% time
- Idling on with default settings
- Auto-scaling maximum set to prevent runaway bills

#### Pricing breakdown for this example:

  |         | Example 1                    | Example 2                       | Example 3 |
  |---------|-----------------------------:|--------------------------------:|---------------------------------:|
  | Compute | 24 GiB RAM, 6 vCPU<br />$125 | 192 GiB RAM, 48 vCPU<br />$1000 | 720 GiB RAM, 180 vCPU<br />$3750 |
  | Storage | 1 TB Data<br />$47           | 5 TB Data<br />$235             | 10 TB Data<br />$470             |
  | Total   | $172                         | $1,235                          | $4,220                           |

### Production (Always-on, Reserved capacity): From $550 per month​

Best for: Latency-sensitive applications

- Production Service
- Active workload ~100% time
- Auto-scaling minimum set to reserve capacity

#### Pricing breakdown for this example:

  |         | Example 1                    | Example 2                       | Example 3 |
  |---------|-----------------------------:|--------------------------------:|---------------------------------:|
  | Compute | 24 GiB RAM, 6 vCPU<br />$503 | 96 GiB RAM, 24 vCPU<br />$2,012 | 360 GiB RAM, 90 vCPU<br />$7,545 |
  | Storage | 1 TB Data<br />$47           | 4 TB Data<br />$188             | 8 TB Data<br />$376              |
  | Total   | $550                         | $2,200                          | $7,921                           |

For help with further estimation, please contact [support](https://clickhouse.cloud/support) if you are already a ClickHouse Cloud user, or [sales@clickhouse.com](mailto:sales@clickhouse.com) otherwise.

## Google Cloud Platform(GCP) Examples

:::note
Prices reflect GCP `us-central-1` pricing.
:::

### Development: From $46 per month

Best for: Starter projects & staging
- Development service
- 16 GiB RAM, 2 vCPU
- 1 TB Data

#### Pricing breakdown for this example:

  |         | 10% active | 50% active | Always on |
  |---------|-----------:|-----------:|----------:|
  | Compute |  $15       |  $74       |  $147     |
  | Storage |  $31       |  $31       |   $31     |
  | Total   |  $46       | $105       |  $178     |

:::note
Consumption can be even lower if less than 1TB disk is used
:::

### Production (Idling, Auto-scaling): From $146 per month

#### Best for: Cost-sensitive ad-hoc analytics applications
- Production Service
- Active workload ~25% time
- Idling on with default settings
- Auto-scaling maximum set to prevent runaway bills

#### Pricing breakdown for this example:

  |         | Example 1                    | Example 2                       | Example 3 |
  |---------|-----------------------------:|--------------------------------:|---------------------------------:|
  | Compute | 24 GiB RAM, 6 vCPU<br />$105 | 192 GiB RAM, 48 vCPU<br />$843  | 720 GiB RAM, 180 vCPU<br />$3162 |
  | Storage | 1 TB Data<br />$41           | 5 TB Data<br />$205             | 10 TB Data<br />$410             |
  | Total   | $146                         | $1,048                          | $3,572                           |

### Production (Always-on, Reserved capacity): From $463 per month​

Best for: Latency-sensitive applications

- Production Service
- Active workload ~100% time
- Auto-scaling minimum set to reserve capacity

#### Pricing breakdown for this example:

  |         | Example 1                    | Example 2                       | Example 3 |
  |---------|-----------------------------:|--------------------------------:|---------------------------------:|
  | Compute | 24 GiB RAM, 6 vCPU<br />$422 | 96 GiB RAM, 24 vCPU<br />$1,686 | 360 GiB RAM, 90 vCPU<br />$6,342 |
  | Storage | 1 TB Data<br />$41           | 4 TB Data<br />$164             | 8 TB Data<br />$328              |
  | Total   | $463                         | $1,850                          | $6,652                           |

For help with further estimation, please contact [support](https://clickhouse.cloud/support) if you are already a ClickHouse Cloud user, or [sales@clickhouse.com](mailto:sales@clickhouse.com) otherwise.

## FAQs

### How is compute metered?
ClickHouse Cloud meters compute on a per-minute basis, in 8G RAM increments.

### How is storage on disk calculated?
ClickHouse Cloud uses cloud object storage and is metered on the compressed size of data stored in ClickHouse tables.

### Do backups count toward total storage?

ClickHouse Cloud offers two free backups for production services, and one free backup for development services. Backups do not count toward storage.

### How do I estimate compression?

Compression can vary quite a bit by dataset. It is dependent on how compressible the data is in the first place (number of high vs. low cardinality fields), and how the user sets up the schema (using optional codecs or not, for instance). It can be on the order of 10x for common types of analytical data, but it can be significantly lower or higher as well. See the [optimizing](/docs/en/guides/best-practices/asyncinserts.md) documentation for guidance and this [Uber blog](https://www.uber.com/blog/logging/) for a detailed logging use case example.
The only practical way to know exactly is to ingest your dataset into ClickHouse and compare the size of the dataset with the size stored in ClickHouse.

You can use the query `SELECT formatReadableSize(total_bytes) FROM system.tables WHERE name = <your table name>`.

### What tools does ClickHouse offer to estimate the cost of running a service in the cloud if I have a self-managed deployment?

The ClickHouse query log captures [key metrics](/docs/en/operations/system-tables/query_log.md) that can be used to estimate the cost of running a workload in ClickHouse Cloud.  For details on migrating from self-managed to ClickHouse Cloud please refer to the [migration documentation](/docs/en/integrations/migration/clickhouse-to-cloud.md), and contact [ClickHouse Cloud support](https://clickhouse.cloud/support) if you have further questions.

### What billing options are available for ClickHouse Cloud?

ClickHouse Cloud supports the following billing options:
- Self-service monthly (in USD, via credit card)
- Direct-sales annual / multi-year (through pre-paid "ClickHouse Credits", in USD, with additional payment options)

### How long is the billing cycle?

Billing follows a monthly billing cycle and the start date is tracked as the date when the ClickHouse Cloud organization was created.

### What controls does ClickHouse Cloud offer to manage costs for Production services?

- Trial and Annual Commit customers will be notified with automated emails when the consumption hits certain thresholds-50%, 75%, and 90%, so that users can take action.
- ClickHouse Cloud allows users to set a maximum auto-scaling limit on their compute via [Advanced scaling control](/docs/en/cloud/manage/scaling.md), a significant cost factor for analytical workloads.
- The [Advanced scaling control](/docs/en/cloud/manage/scaling.md) lets you set memory limits with an option to control the behavior of pausing/idling during inactivity.

### What controls does ClickHouse Cloud offer to manage costs for Developer services?

- The [Advanced scaling control](/docs/en/cloud/manage/scaling.md) lets you control the behavior of pausing/idling during inactivity. Adjusting memory allocation is not supported for Developer services
- Note that the default setting pauses the service after a period of inactivity

### If I have multiple services, do I get an invoice per service or a consolidated invoice?

A consolidated invoice is generated for all services in a given organization for a billing period.

### If I add my credit card and upgrade before my trial period and credits expire, will I be charged?

When a user converts from trial to paid before the 30-day trial period ends, but with credits remaining from the trial credit allowance, we continue to draw down from the trial credits during the initial 30-day trial period, and then charge the credit card.

### How can I keep track of my spending?

ClickHouse Cloud console includes a Usage display that gives detailed information about usage per service on compute and storage. This can be used to understand the cost breakdown by metered units.

### How do I access my invoice for my AWS marketplace subscription to the ClickHouse Cloud service?

All marketplace subscriptions will be billed and invoiced by AWS. You can download the invoice from the AWS Billing Dashboard.

### Why do the dates on the Usage statements not match my AWS Marketplace Invoice?

AWS Marketplace billing follows the calendar month cycle e.g., for usage between dates 01-Dec-2022 and 01-Jan-2023, an invoice will be generated between 3-Jan and 5-Jan-2023

ClickHouse Cloud usage statements follow a different billing cycle where usage is metered and reported over 30 days starting from the day of sign up

The usage and invoice dates will differ if these dates are not the same. Since usage statements track usage by day for a given service, users can rely on statements to see the breakdown of costs.

### Are there any restrictions around the usage of prepaid credits?

ClickHouse Cloud prepaid credits (whether direct through ClickHouse, or via a cloud provider's marketplace) can only be leveraged for the terms of the contract. This means they can be applied on the acceptance date, or a future date, and not for any prior periods. Any overages not covered by prepaid credits must be covered by a credit card payment, or marketplace monthly billing.

## Is there a difference in ClickHouse Cloud pricing, whether paying through the cloud provider marketplace or directly to ClickHouse?

There is no difference in pricing between marketplace billing and signing up directly with ClickHouse. In either case, your usage of  ClickHouse Cloud is tracked in terms of ClickHouse Cloud Credits (CHCs), which are metered in the same way and billed accordingly.
