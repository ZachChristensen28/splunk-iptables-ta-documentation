# Release history for the Linux Iptables Add-on for Splunk

The latest version of the Pi-hole DNS app for Splunk is version 1.3.7. See [Release notes for the Linux Iptables Add-on for Splunk](../../releases/) of the latest version.

### v1.3.6 <small>July 20, 2021</small>

!!! warning "Notice"
    This updated simplifies the number of sourcetypes down to a single sourcetype (linux:iptables). Any existing reports/alerts/views that are utilizing the old sourcetypes ("linux:iptables:ufw" or "linux:iptables:firewalld") will be impacted. Verify before updating to this version.

- added support for firewalld rich rules - [#2](https://github.com/ZachChristensen28/TA-linux_iptables/issues/2)
- updated to only use the single sourcetype, 'linux:iptables'
- updated action lookup to use wildcards

### v1.3.5 <small>Nov 2, 2020</small>

- Adding support for Splunk Cloud
