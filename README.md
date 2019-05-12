# R Client for the MTurk Requester API using the AWS SDK for Python (Boto3) #

**pyMTurkR** is a successor to [MTurkR](https://github.com/cloudyr/MTurkR), and a work in progress. pyMTurkR provides access to the Amazon Mechanical Turk [Amazon Mechanical Turk](https://requester.mturk.com) (MTurk) [Requester API](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/Welcome.html), by wrapping around the [AWS SDK for Python (Boto3)](https://aws.amazon.com/sdk-for-python) [MTurk Client](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/mturk.html).

Because pyMTurkR uses Python, it requires some additional setup and configuration:

  1. Install Python 2 (>= 2.7) or Python 3 (>= 3.3) ([download page](https://www.python.org/downloads))
  2. Install `pip` for Python ([see "Installing with get-pip.py" here](https://pip.pypa.io/en/stable/installing))
  3. Use `pip` to install boto3 ([see "Installation" here](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html#installation))
  
You'll also need to configure an AWS credentials file.

  1. Find your AWS credentials (Key and Secret Key) in the [IAM Console](https://console.aws.amazon.com/iam/home)
  2. Use [AWS CLI](http://aws.amazon.com/cli) to configure the credentials file, or manually create a credentials file ([see "Configuration" here](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html#configuration))

## Why make this? ##

pyMTurkR was started because Amazon decided to [deprecate the API](https://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI-legacy/Welcome.html) that MTurkR was using (meaning MTurkR would stop working). The goal of this project is to create a package that functions in a way that will be familiar to MTurkR users, making the transition easier.

Unlike MTurkR, pyMTurkR is not a native R-language package. This is because it uses Python and the `boto3` module for Python. This is not necessarily a bad thing, and from the user perspective there is probably in most cases little difference. With recent developments in R, such as the [`reticulate`](https://rstudio.github.io/reticulate) package which this package depends on, R can interface with Python relatively seamlessly, and in the case of this package there shouldn't be any noticeable issues with speed or performance. 

Because this package relies on python and boto3, this might create some additional work for the user. Namely, in addition to updating R and the R packages that pyMTurkR depends on, there is the potential additional work of updating Python and the boto3 module, should those require updating in the future. 

For a deeper dive on issues related to dependencies, see [Dependency Hell on Wikipedia](https://en.wikipedia.org/wiki/Dependency_hell).

## What can it do? ##

Not much — yet.

The following verbs have been implemented so far:

- AccountBalance()
- ApproveAssignment()
- AssignQualification()
- CreateQualificationType()

## Installation ##

The development version of pyMTurkR can be installed from this repo using `devtools`.

```R
library(devtools)
install_github("cloudyr/pyMTurkR")
```

## Usage ##

```R
library("pyMTurkR")
AccountBalance()
```

## Development status ##

For development updates see the [Changelog](https://github.com/cloudyr/pyMTurkR/blob/master/CHANGELOG.md)

## Troubleshooting ##

One of the issues you might encounter, especially if you maintain multiple installs of python on your system, is that when `reticulate` loads python it loads a version that you didn't install the `boto3` module into. 

After loading pyMTurkR, or manually loading `reticulate`, you can check the version and system path of the python install that it's using

```
> reticulate::py_config()

python:         C:\Users\tyler\AppData\Local\Programs\Python\Python37\\python.exe
libpython:      C:/Users/tyler/AppData/Local/Programs/Python/Python37/python37.dll
pythonhome:     C:\Users\tyler\AppData\Local\Programs\Python\Python37
version:        3.7.1 (v3.7.1:260ec2c36a, Oct 20 2018, 14:57:15) [MSC v.1915 64 bit (AMD64)]
Architecture:   64bit
numpy:          C:\Users\tyler\AppData\Roaming\Python\Python37\site-packages\numpy
numpy_version:  1.15.4

python versions found: 
 C:\Users\tyler\AppData\Local\Programs\Python\Python37\\python.exe
 C:\Python27\\python.exe
 C:\Python36\\python.exe
```

For example, here I see that it's using an install of python that's located in my users folder, and it found 3 different python installs in my system. 

If I try to load the boto3 module, `reticulate` might complain that it can't find it because it's pointing to a different install path.

This can be solved in one of two ways.

1. Change the python path: The python path can be manually changed after loading pyMTurkR, to specify an install that has the boto3 module. However, note that you will have to set this path at the very beginning of your script. There's a quirk in reticulate that doesn't allow it to be changed after python commands have been invoked.

```
library("pyMTurkR")
reticulate::use_python("C:\\Python36\\python.exe")
```

2. Install the boto3 module for the python it defaults to: You can install the boto3 module for whatever python install `reticulate` happens to be using by issuing a system command through the R console, with the same pip install code as before.

```
system("pip install boto3")
```