---
subcategory: "RDS"
layout: "aws"
page_title: "AWS: aws_db_cluster_snapshot"
description: |-
  Manages a RDS database cluster snapshot.
---

# Resource: aws_db_cluster_snapshot

Manages a RDS database cluster snapshot for Aurora clusters. For managing RDS database instance snapshots, see the [`aws_db_snapshot` resource](/docs/providers/aws/r/db_snapshot.html).

## Example Usage

```hcl
resource "aws_db_cluster_snapshot" "example" {
  db_cluster_identifier          = "${aws_rds_cluster.example.id}"
  db_cluster_snapshot_identifier = "resourcetestsnapshot1234"
}
```

## Argument Reference

The following arguments are supported:

* `db_cluster_identifier` - (Required) The DB Cluster Identifier from which to take the snapshot.
* `db_cluster_snapshot_identifier` - (Required) The Identifier for the snapshot.
* `tags` - (Optional) A mapping of tags to assign to the DB cluster.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `allocated_storage` - Specifies the allocated storage size in gigabytes (GB).
* `availability_zones` - List of EC2 Availability Zones that instances in the DB cluster snapshot can be restored in.
* `db_cluster_snapshot_arn` - The Amazon Resource Name (ARN) for the DB Cluster Snapshot.
* `engine` - Specifies the name of the database engine.
* `engine_version` - Version of the database engine for this DB cluster snapshot.
* `kms_key_id` - If storage_encrypted is true, the AWS KMS key identifier for the encrypted DB cluster snapshot.
* `license_model` - License model information for the restored DB cluster.
* `port` - Port that the DB cluster was listening on at the time of the snapshot.
* `source_db_cluster_snapshot_identifier` - The DB Cluster Snapshot Arn that the DB Cluster Snapshot was copied from. It only has value in case of cross customer or cross region copy.
* `storage_encrypted` - Specifies whether the DB cluster snapshot is encrypted.
* `status` - The status of this DB Cluster Snapshot.
* `vpc_id` - The VPC ID associated with the DB cluster snapshot.

## Timeouts

`aws_db_cluster_snapshot` provides the following [Timeouts](/docs/configuration/resources.html#timeouts) configuration options:

* `create` - (Default `20m`) How long to wait for the snapshot to be available.

## Import

`aws_db_cluster_snapshot` can be imported by using the cluster snapshot identifier, e.g.

```
$ terraform import aws_db_cluster_snapshot.example my-cluster-snapshot
```
