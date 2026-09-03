## Link/Package Name
https://github.com/synacktiv/ntdissector/
## Description
Tool for parsing records of an NTDS (NT Directory Services) database. 
## Usage
Use on NTDS.dit files with appropriate flags for a json output that can be piped into jq.
```
$ ntdissector -h                           
usage: ntdissector [-h] [-system SYSTEM] -ntds NTDS [-bootKey BOOTKEY] [-outputdir OUTPUTDIR] [-cachedir CACHEDIR] [-f FILTER] [-filters] [-limit LIMIT] [-cn] [-debug] [-verbose]
                      [-silent] [-ts] [-w WORKERS] [-nocache] [-dryRun]

NTDS Dissector

optional arguments:
  -h, --help            show this help message and exit
  -V, --version         Display version info

Files:
  -system SYSTEM        SYSTEM hive to parse
  -ntds NTDS            NTDS file to parse
  -bootKey BOOTKEY      Force bootkey (skips the SYSTEM hive parsing)
  -outputdir OUTPUTDIR  Base output directory
                        (Default: /home/mehdie/.ntdissector/out/)
  -cachedir CACHEDIR    Base cache directory
                        (Default: /home/mehdie/.ntdissector/.cache/)

Filter options:
  -f FILTER, --filter FILTER
                        Filter object classes, 'all' to dump everything.
                        Use -filters to get a list of available object classes
                        Default: [user, secret, group, domainDNS].
  -filters              Print all classes available for filtering
  -limit LIMIT          Dump a specific number of objects then stop

Display options:
  -cn                   Toggle CN naming output (Default: LDAP naming)
  -debug                Turn DEBUG output ON
  -verbose              Turn INFO output ON
  -silent               Silent
  -ts                   Adds a timestamp to every logging output
  -keepDel              Keeps deleted records

Miscellaneous:
  -w WORKERS, -workers WORKERS
                        Number of workers (default: 5)
  -nocache              Disable cache
  -dryRun               Launch in dry run mode, ignores cache files

Examples:

> Dump users, groups and domain backup keys
$ ntdissector -ntds NTDS.dit -system SYSTEM -outputdir /tmp/ntdissector/ -ts -f user,group,secret

> Dump all records from the database
$ ntdissector -ntds NTDS.dit -system SYSTEM -outputdir /tmp/ntdissector/ -ts -f all

> Dump user objects and include deleted records
$ ntdissector -ntds NTDS.dit -system SYSTEM -outputdir /tmp/ntdissector/ -ts -f user -keepDel

> List object classes available to filter records
$ ntdissector -ntds NTDS.dit  -filters
```

## Related