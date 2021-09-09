[[AWS VPC]]
tags: #howto 

# Connect apps between 2 VPCs

## Prerequisites

VPC ids : VPC_ID_1 and VPC_ID_2

## How to

First create a peering connexion between the VPCs using the user interface and define a variable PEERING_CNX_ID=<id of the peering cnx>

Get the CIDR blocks:

```bash
export CIDR_1=$(aws ec2 describe-vpcs | jq -r ".Vpcs[] | select(.VpcId==\\"$VPC_ID_1\\") | .CidrBlock")
```

```bash
export CIDR_2=$(aws ec2 describe-vpcs | jq -r ".Vpcs[] | select(.VpcId==\\"$VPC_ID_2\\") | .CidrBlock")
```

Get the id of the main routing table of each VPC 1:

```bash
export ROUTE_TABLE_ID_1=$(aws ec2 describe-route-tables | jq -r ".RouteTables[] | select(.VpcId==\\"$VPC_ID_1\\") | .RouteTableId")
```

```bash
export ROUTE_TABLE_ID_2=$(aws ec2 describe-route-tables | jq -r ".RouteTables[] | select(.VpcId==\\"$VPC_ID_2\\") | .RouteTableId")
```

Then create a route in each route table toward the other CIDR through the peering connection:

```bash
aws ec2 create-route --destination-cidr-block $CIDR_1  --vpc-peering-connection-id $PEERING_CNX_ID --route-table-id $ROUTE_TABLE_ID_2
```

```bash
aws ec2 create-route --destination-cidr-block $CIDR_2  --vpc-peering-connection-id $PEERING_CNX_ID --route-table-id $ROUTE_TABLE_ID_1
```

