Munin plugin for CSF: ConfigServer Firewall
This plugin graphs your csf.allow and csf.deny data. 
Version 0.5 
Public beta

Usage
---------------------
1. Copy CSF_.pl to /usr/share/munin/plugins
2. chmod +x /usr/share/munin/plugins/CSF_.pl
3. Create a symbolic link to CSF_<allow|deny>_<reseller|country|service|cluster>
	ln -s /usr/share/munin/plugins/CSF_ /etc/munin/plugins/CSF_allow_reseller
	Valid combinations:
	 - CSF_allow_reseller
	 - CSF_deny_reseller
	 - CSF_deny_cluster
	 - CSF_deny_country
	 - CSF_deny_service
	Note: any other combinations can result in data loss/corruption!

Log
---------------------
Revision 0.1  2013/10/28  F. Katzenberger
 - First version tested reading csf.deny and countying IP addresses w/ CIDR support
Revision 0.2  2013/10/31  F. Katzenberger
 - Added/developed regex for detecting resellers, countries, and services
Revision 0.3  2013/11/02 F. Katzenberger
 - developed the param structure for the munin config call
Revision 0.4  2013/11/03  F. Katzenberger
 - touch ups for alpha testing
Revision 0.5  2013/11/03  F. Katzenberger
 - adjusted the service lookup regex to include port scans
 - added cluster member deny graph support
 - fixed issue where login was not displayed for SMTP failed logins

Known Issues / Planned Features
---------------------
1. when a country or service no longer has an entry in csf.deny, it will be removed by munin from the graph regardless of any datapoints still on the graph.
2. distributed attacks are not yet detected and categorized into the existing services
3. distributed attacks are not yet graphed by account names
4. add a graph that shows deny by distributed on accounts.
5. no ipv6 support yet
6. does not yet track other lfd features such as excessive resources and ignore or temporary
