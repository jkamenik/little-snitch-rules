# [little-snitch-rules](https://github.com/jkamenik/little-snitch-rules)

Personal Rules for Little Snitch.

[Download Little Snitch](https://www.obdev.at/products/littlesnitch/index.html) then use one of the below links to automtically install one of the rules.

Copy one of the following URLs:

1.  Example Rules: <https://raw.githubusercontent.com/jkamenik/little-snitch-rules/master/example.lsrules>
2.  Global Allow Rules: <https://raw.githubusercontent.com/jkamenik/little-snitch-rules/master/Allow.lsrules>
3.  Global Deny Rules: <https://raw.githubusercontent.com/jkamenik/little-snitch-rules/master/Deny.lsrules>
4.  Common App Rules: <https://raw.githubusercontent.com/jkamenik/little-snitch-rules/master/CommonApps.lsrules>
5.  Firefox Rules (default browser): <https://raw.githubusercontent.com/jkamenik/little-snitch-rules/master/Firefox.lsrules>

Once the URL is copied then it can be imported into Little Snitch:
1.  Open Little Snitch Rules preference pane
2.  Click File -> New Rule Group Subscription
3.  Paste the URL
4.  Click "Subscribe..."
5.  Enter your admin password if required
6.  Adjust any settings
    1.  Recommend Unchecking "Disable new allow rules" as most of the items above are "allow" rules.
    2.  Recommend setting updates to "Daily"
    3.  Recommend checking "Active"
8.  Click "Subscribe"

## Getting URLs manually

If you want to install the rules manually you will need to get the "raw" url of the file from github:
1.  Open github
2.  Go to repo in question
3.  Click on the filename
4.  Click "Raw" to get the raw view
    -   Usually "raw.githubusercontent.com/<user>/<repo>/<branch>/path/to/file"

## Understanding the Rule file structure

The structure is JSON in the form of

```json
{
  "description": "Some useful description, usually including the subscription link",
  "name": "A short human name, seen in Little Snitch on the rules",
  "rules": [<rule 1>,<rule 2>,...]
}
```

Rules have the following fields:

-   action  - "allow" or "deny"
-   notes   - Human discription of this specific rule
-   process - "any" for any or the escaped path of the executable (i.e., "\/Applications\/Dropbox.app\/Contents\/MacOS\/Dropbox")

Optional Fields (ommit for "any"):

-   ports    - A port number (e.g. "53" for DNS, "22" for ssh, etc...)
-   protocol - A protocol string:
    -   "icmp"
    -   "tcp"
    -   "udp"
    -   "irtp"
    -   "ipv6-icmp"

The following are exclusive rule types (you can only pick one in a rule):

-   remote           - One of the following (generally best to not include rules of this type in a subscription.)
    -   any         - Allow Berkley
    -   bonjour     - Any bonjour network connection
    -   broadcast   - Any broadcast address
    -   dns-servers - Any DNS-like connection (tcp/upd port 54)
    -   local-net   - Any local network connection
    -   multicast   - Any multicast connection
-   remote-addresses - A JSON array of IPs
    -   `["1.1.1.1", "2.2.2.2"]`
-   remote-hosts     - A JSON array of FQDNs.
    -   `["www.example.com", "mail.example.com"]`
-   remote-domains   - A JSON array of domains.  Note: this rule applies to any subdomain as well (i.e., **.example.com)
    -   `["yahoo.com", "apple.com"]`
