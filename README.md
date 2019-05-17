# scrapER2019

This script downloads all data from `2019electionresults.comelec.gov.ph` by storing the json responses of the backend API. The `results` directory mirrors the levels of administrative divisions. Slashes (`/`) in the name of a division is replaced by `_`. Each directory stores information about that level (`info.json`) and the corresponding certificate of canvas (`coc.json`) or clustered precinct results. It will not redownload an already existing json file so multiple invocations of the script won't download everything again.

Results information of COCs and precincts are stored as a list of key-value pairs pointing to the contest code (`cc`) and ballot order (`bo`). Information about a candidate such as their name (`bon`) can be retrieved by looking up their ballot order (`boc`) from the corresponding contest json file in the `contests` directory.

## Dependencies

* OpenSSL 1.1.1 or higher
* python-requests
* python-click
 
## Invocation

This is a python script which can be invoked by

    python scraper.py

or

    ./scraper.py

if on a Ubuntu or Debian-based machine.

It also accepts the following parameters:

    -b, --base-dir TEXT             directory from which all downloaded data
                                    will be stored
    -d, --download-delay FLOAT      minimum delay between successive downloads
    -l, --log-level [CRITICAL|ERROR|WARNING|INFO|DEBUG]
                                    log output level

