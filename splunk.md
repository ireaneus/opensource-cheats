# Splunk

## Intermediate Search
```sh
host=server1 state=* level=critical | top state by level
host=server1 state=* level=critical | rare state by level
host=server1 state=* level=critical | stats avg(kbps) BY host
host=server1 state=* level=critical | stats count(failed_logins) BY user
```

## Date Variables
```sh
%A	    # Day of the Week ie.. Monday
%B	    # Month ie.. January
%d	    # date
%Y	    # Year ie.. 1985
```

## Time Variables
```sh
%c	    # Date and time in the format of the server
%H	    # Hour (24-hour clock)
%I	    # Hour (12-hour clock)
%M	    # Minutes (00-59)
%p	    # AM or PM
%S	    # Seconds (00-59)
```

```sh
eval <new field> = strftime(<time field>, "<format>")
eval New_Time = strftime(_time, "%I:%M, %p")
```

## Search
```sh 
host=splunkmain backupduration=* domain=* | table _time backupduration domain
host=splunkmain backupduration=* domain=* | stats avg(backupduration)
host=splunkmain backupduration=* domain=* | stats max(backupduration) by domain
```

## Extract field
```sh
index=_internal		      # +Extract New Fields -> Source Type -> extract Regex or Delimiter
index=_* OR index=* soucetype=splunk_web_access | table _time protocol    # protocol is an extract new fields
```

## Data Model
```sh
index=_audit				# constraints
action=search NOT
action=edit_user OR action=edit_roles OR action=update
```
