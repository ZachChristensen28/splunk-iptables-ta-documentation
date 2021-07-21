# Configure Splunk Input

**Objective**: Set the sourcetype to `linux:iptables` in the inputs.conf file on the forwarder.

## Create a new index

!!! note
    This is an optional step. If you do not wish to create a new index, skip to [Splunk Universal Forwarder Configuration](#splunk-universal-forwarder-configuration).

Splunk stores data in indexes. This add-on may be configured to send to a custom event index instead of the default index, main. For more information and steps to create a new index, see [Splunk Docs: Create events indexes](https://docs.splunk.com/Documentation/Splunk/latest/Indexer/Setupmultipleindexes#Create_events_indexes_2).

### Purpose for Creating a new index

The out of the box Splunk configuration stores all data in the default index, main. It is encouraged to create a new index to ensure optimal performance, for setting retention policies, and for providing stricter access controls. For more information about how Splunk indexes work with add-ons, see [Splunk Docs: Add-ons and indexes](https://docs.splunk.com/Documentation/AddOns/released/Overview/Add-onsandindexes).

## Splunk Universal Forwarder Configuration

Download the latest [Splunk Universal Forwarder (UF)](https://www.splunk.com/en_us/download/universal-forwarder.html) appropriate for your server. 

!!! note
    Unless utilizing a syslog server, this UF should be installed on the same server that you wish to collect linux firewall events from.

Install the UF according to [Splunk Docs: Install the Universal Forwarder](https://docs.splunk.com/Documentation/Forwarder/latest/Forwarder/Installtheuniversalforwardersoftware).

Once installed the configurations can be made. The following is a sample inputs.conf that can be pushed using a deployment server or configured on the UF itself. 

```shell
# inputs.conf
[monitor:///var/log/iptables.log]
disabled = 0
sourcetype = linux:iptables
# optionally specify an index, if configured.
index = osnixfw
```

Push the configuration to the forwarder, if using a deployment server, or restart the UF if configuring on the UF itself.

## Verify

Verify the setup has completed successfully by navigating to Splunk web and running a search similar to the following:

```
index=<chosen index> sourcetype=linux:iptables
```

If you see data then you are all set! If you are not seeing your data, see [Troubleshooting Monitoring Inputs](../troubleshooting/troubleshoot-inputs.md).

--8<-- "docs/includes/abbreviations.md"