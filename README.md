# Splunk_SA_IndexedField

``` props.conf
# Apply this to a specific sourcetype or host configuration:
[monitor:///var/log/syslog-ng/paloalto/*/*/messages.log]
TRANSFORMS-site_src = site_src
```

``` transforms.conf
# you need to create a regex to match the host and set the site_src
[site_src]
REGEX = <matchinghostregex>
FORMAT = site_src::JAPAN
WRITE_META = true
SOURCE_KEY = MetaData:Host

Alternatively if the you named the site_src in you path you could regex for that:
* eg: source = "/var/log/syslog-ng/paloalto/japan/10.0.0.13/YYYY-MM-DD/messages.log"
[site_src]
REGEX = <regex_matching_path>
FORMAT = site_src::"$1"
WRITE_META = true
SOURCE_KEY = MetaData:Source
```
