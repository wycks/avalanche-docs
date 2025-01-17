# How to Deploy a Subnet on a Local Network

This how-to guide focuses on taking an already created Subnet configuration and deploying it to a
local Avalanche network.

## Prerequisites

- [Avalanche-CLI installed](install-avalanche-cli)
- You have [created a Subnet configuration](create-evm-subnet-config)

## Deploying Subnets Locally

In the following commands, make sure to substitute the name of your Subnet configuration for
`<subnetName>`.

To deploy your Subnet, run

`avalanche subnet deploy <subnetName>`

and select `Local Network` to deploy on. Alternatively, you can bypass this prompt by providing
the `--local` flag. For example:

`avalanche subnet deploy <subnetName> --local`

The command may take a couple minutes to run.

### Results

If all works as expected, the command output should look something like this:

<!-- markdownlint-disable MD013 -->

```text
> avalanche subnet deploy mySubnet
✔ Local Network
Deploying [mySubnet] to Local Network
Installing subnet-evm-v0.4.3...
subnet-evm-v0.4.3 installation successful
Backend controller started, pid: 93928, output at: /Users/subnet-developer/.avalanche-cli/runs/server_20221122_173138/avalanche-cli-backend
Installing avalanchego-v1.9.3...
avalanchego-v1.9.3 installation successful
VMs ready.
Starting network...
..................
Blockchain has been deployed. Wait until network acknowledges...
......
Network ready to use. Local network node endpoints:
+-------+----------+------------------------------------------------------------------------------------+
| NODE  |    VM    |                                        URL                                         |
+-------+----------+------------------------------------------------------------------------------------+
| node2 | mySubnet | http://127.0.0.1:9652/ext/bc/SPqou41AALqxDquEycNYuTJmRvZYbfoV9DYApDJVXKXuwVFPz/rpc |
+-------+----------+------------------------------------------------------------------------------------+
| node3 | mySubnet | http://127.0.0.1:9654/ext/bc/SPqou41AALqxDquEycNYuTJmRvZYbfoV9DYApDJVXKXuwVFPz/rpc |
+-------+----------+------------------------------------------------------------------------------------+
| node4 | mySubnet | http://127.0.0.1:9656/ext/bc/SPqou41AALqxDquEycNYuTJmRvZYbfoV9DYApDJVXKXuwVFPz/rpc |
+-------+----------+------------------------------------------------------------------------------------+
| node5 | mySubnet | http://127.0.0.1:9658/ext/bc/SPqou41AALqxDquEycNYuTJmRvZYbfoV9DYApDJVXKXuwVFPz/rpc |
+-------+----------+------------------------------------------------------------------------------------+
| node1 | mySubnet | http://127.0.0.1:9650/ext/bc/SPqou41AALqxDquEycNYuTJmRvZYbfoV9DYApDJVXKXuwVFPz/rpc |
+-------+----------+------------------------------------------------------------------------------------+

Browser Extension connection details (any node URL from above works):
RPC URL:          http://127.0.0.1:9650/ext/bc/SPqou41AALqxDquEycNYuTJmRvZYbfoV9DYApDJVXKXuwVFPz/rpc
Funded address:   0x8db97C7cEcE249c2b98bDC0226Cc4C2A57BF52FC with 1000000 (10^18) - private key: 56289e99c94b6912bfc12adc093c9b51124f0dc54ac7a766b2bc5ccf558d8027
Network name:     mySubnet
Chain ID:         54325
Currency Symbol:  TUTORIAL
```

<!-- markdownlint-enable MD013 -->

You can use the deployment details to connect to and interact with your Subnet.

To manage the newly deployed local Avalanche network, see
[the `avalanche network` command tree](reference-cli-commands#network).

### Deploying Multiple Subnets

You may deploy multiple Subnets concurrently, but you can't deploy the same Subnet multiple times
without resetting all deployed Subnet state.

## Redeploying the Subnet

To redeploy the Subnet, you first need to wipe the Subnet state. This permanently deletes all data
from all locally deployed Subnets. To do so, run

```shell
avalanche network clean
```

You are now free to redeploy your Subnet with

```shell
avalanche subnet deploy <subnetName> --local
```