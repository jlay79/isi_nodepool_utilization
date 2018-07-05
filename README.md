# isi_nodepool_utilization

From an Isilon cluster, run 'isi storagepool list' and parse the output.  If any node pool exceeds the utilization threshold, send an email.  The default threshold is 80%, but can be changed with the `-T` option.

- If nodepools do not exceed threshold, no email will be sent and script will exit.
- The recipients (To:) must be specified manually in the script options.  This is the only requirement.
- This uses the cluster's internal SMTP configuration for mail servers.  No need to configure SMTP servers in the script.

## Testing

To test the script, run it with a low threshold to generate the email.  

Example:  
`python nodepool_util_email.py --to storageadmins@company.com --threshold 5 --subject TEST`  

## Cron

You can add the script to a crontab to have it run automatically on a schedule.  

Example:  
`0 0 * * 7 root /usr/bin/python /ifs/data/scripts/nodepool_util_email.py --to storageadmins@company.com`  

This would use the default 80% threshold and the default subject line.


## Multiple Recipients

To add multiple recipients, just add multiple `--to` arguments.  At least one is required.

Example:  
`python nodepool_util_email.py --to storageadmins@company.com --to bob@company.com --to suzie@company.com`

