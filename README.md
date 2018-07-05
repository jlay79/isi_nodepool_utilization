# isi_nodepool_utilization

From an Isilon cluster, run 'isi storagepool list' and parse the output.  If any node pool exceeds the utilization threshold, send an email.  The default threshold is 80%, but can be changed with the `-T` option.

- If nodepools do not exceed threshold, no email will be sent and script will exit.
- The recipients (To:) must be specified manually in the script options.  This is the only requirement.
- This uses the cluster's internal SMTP configuration for mail servers.  
