[comment]: # "Auto-generated SOAR connector documentation"
# Cisco Router BGP RTBH

Publisher: World Wide Technology  
Connector Version: 1\.10\.5  
Product Vendor: Cisco Systems  
Product Name: Cisco IOS\-XE  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 3\.0\.251  

This app interfaces with Cisco IOS\-XE devices to create a blackhole for configured IPs or networks in Cisco BGP networks

Cisco Router Remote Trigger Black Hole

Publisher: World Wide Technology
App Version: 1.7
Product Vendor: Cisco Systems
Product Name: Cisco IOS-XE
Product Version Supported (regex): ".*"

This app interfaces with Cisco IOS-XE devices to create a blackhole for
configured IPs or networks in Cisco BGP networks; it supports containment
actions like 'block ip', 'block network', correct actions like 'unblock ip',
'unblock network', and investigative actions like 'list blocked networks' on a
Cisco CSR device. It uses the SSH interface to log on and perform its actions.
The target host is required to have the SSH interface enabled and a user
account configured for privilege access (15).

Configuration Variables

The below configuration variables are required for this App to operate on Cisco
IOS-XE. These are specified when configuring an asset in Phantom.
VARIABLE     REQUIRED     TYPE     DESCRIPTION
username     required     string     User with access to the trigger node
tag     optional     string     Route Tag
password     required     password     Password
trigger_host     required     string     Device IP/Hostname
route_to_null     required     string     Null Route IP (x.x.x.x)
Supported Actions

unblock network - Unblocks an IP network
block network - Blocks an IP network
unblock ip - Unblocks an IP
block ip - Blocks an IP
list blocked networks - Lists currently blocked networks
test connectivity - Validate the asset configuration for connectivity
action: 'unblock network'

Unblocks an IP network

Type: correct

Read only: True

Action Parameters
PARAMETER     REQUIRED     DESCRIPTION     TYPE     CONTAINS
destination_network     required     IP/network to unBlock (X.X.X.X/NM)
string     
Action Output

No Output
action: 'block network'

Blocks an IP network

Type: contain

Read only: True

Action Parameters
PARAMETER     REQUIRED     DESCRIPTION     TYPE     CONTAINS
destination_network     required     IP/network to block (X.X.X.X/NM)
string     
Action Output

No Output
action: 'unblock ip'

Unblocks an IP

Type: correct

Read only: True

Action Parameters
PARAMETER     REQUIRED     DESCRIPTION     TYPE     CONTAINS
destination_network     required     IP to unBlock (X.X.X.X)     string     
Action Output

No Output
action: 'block ip'

Blocks an IP

Type: contain

Read only: True

Action Parameters
PARAMETER     REQUIRED     DESCRIPTION     TYPE     CONTAINS
destination_network     required     IP to block (X.X.X.X)     string     
name     required     Name route     string     
Action Output

No Output
action: 'list blocked networks'

Lists currently blocked networks

Type: investigate

Read only: True

Action Parameters

No parameters are required for this action
Action Output
DATA PATH     TYPE     CONTAINS
action_result.data.*.blackholed-network     string     
action_result.status     string     
action_result.message     string     
action: 'test connectivity'

Validate the asset configuration for connectivity

Type: test

Read only: True

This action logs into the Cisco router using a SSH call
Action Parameters

No parameters are required for this action
Action Output

No Output


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Cisco IOS\-XE asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**trigger\_host** |  required  | string | Device IP/Hostname
**username** |  required  | string | User with access to the trigger node
**password** |  required  | password | Password
**tag** |  optional  | string | Route Tag
**route\_to\_null** |  required  | string | Null Route IP \(x\.x\.x\.x\)

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity  
[list networks](#action-list-networks) - Lists currently blocked networks  
[block ip](#action-block-ip) - Blocks an IP  
[unblock ip](#action-unblock-ip) - Unblocks an IP  
[block network](#action-block-network) - Blocks an IP network  
[unblock network](#action-unblock-network) - Unblocks an IP network  

## action: 'test connectivity'
Validate the asset configuration for connectivity

Type: **test**  
Read only: **True**

This action logs into the Cisco router using a SSH call

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'list networks'
Lists currently blocked networks

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.data\.\*\.blackholed\-network | string | 
action\_result\.status | string | 
action\_result\.message | string |   

## action: 'block ip'
Blocks an IP

Type: **contain**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**destination\_network** |  required  | IP to block \(X\.X\.X\.X\) | string |  `ip` 
**name** |  optional  | Name route | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.message | string | 
action\_result\.parameter\.destination\_network | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'unblock ip'
Unblocks an IP

Type: **correct**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**destination\_network** |  required  | IP to unBlock \(X\.X\.X\.X\) | string |  `ip` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.message | string | 
action\_result\.parameter\.destination\_network | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'block network'
Blocks an IP network

Type: **contain**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**destination\_network** |  required  | IP/network to block \(X\.X\.X\.X/NM\) | string |  `ip network` 
**name** |  optional  | Name route | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.message | string | 
action\_result\.parameter\.destination\_network | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'unblock network'
Unblocks an IP network

Type: **correct**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**destination\_network** |  required  | IP/network to unBlock \(X\.X\.X\.X/NM\) | string |  `ip network` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.message | string | 
action\_result\.parameter\.destination\_network | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 