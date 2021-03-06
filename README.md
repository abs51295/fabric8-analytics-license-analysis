# fabric8-analytics-license-analysis
License Analysis Service analyzes the given stack and returns the following:
 - unknown licenses, if any
 - conflicting licenses, if any
 - license based outlier packages, if any
 - stack level license, if possible


## How to test locally:

*  `./run-test-local.sh`

    * To run with different threshold `./run-test-local.sh -t <[0-1]>`


## How to run the API locally:

* `./run-api-local.sh`

    * To run on different port `./run-api-local.sh -p <Port>`

    * To run with different threshold `./run-test-local.sh -t <[0-1]>`

    * To run with different port and threshold `./run-api-local.sh -p <Port> -t <[0-1]>`

* curl localhost:<SERVICE_PORT> should return `{status: ok}`


## Notes:

* By default the value of `MAJORITY_THRESHOLD` used is 0.6. If you wish to use any other value, modifications in the test cases will be required to reflect the new outliers.

* To run tests the the value of `DATA_DIR` is set to `.`

* To run the API locally the value of `DATA_DIR` is to `tests


## Sample License analysis request input
```
ENDPOINT: /api/vi/stack_license
BODY: JSON data
{
    "packages": [
            {
                "package": "p1",
                "version": "1.1",
                "licenses": ["APACHE", "EPL 1.0"]
            }
        ]
}
```


## Tree used for license comparision

![License Diagram](https://user-images.githubusercontent.com/7105965/35150022-87594334-fd3e-11e7-8fad-380eaadf47fd.jpg)

### References:

* [The Free-Libre / Open Source Software (FLOSS) License Slide  by by David A. Wheeler](https://www.dwheeler.com/essays/floss-license-slide.pdf)

### Footnotes

## Coding standards


- You can use scripts `run-linter.sh` and `check-docstyle.sh` to check if the code follows [PEP 8](https://www.python.org/dev/peps/pep-0008/) and [PEP 257](https://www.python.org/dev/peps/pep-0257/) coding standards. These scripts can be run w/o any arguments:

```
./run-linter.sh
./check-docstyle.sh
```

The first script checks the indentation, line lengths, variable names, white space around operators etc. The second
script checks all documentation strings - its presence and format. Please fix any warnings and errors reported by these
scripts.
