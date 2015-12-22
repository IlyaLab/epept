### Web Service Clients ###
EPEPT is available via a REST+JSON web service.  It can be accessed from any programming language (C, Java, Matlab, Perl, Ruby, R,...) with HTTP support and [JSON parsing libraries](http://json.org).

The web service client must define and initialize the following set of input parameters in order to make a request to the processing host.  These input parameters are identical to the input text and check boxes on the HTML input form.

Below are example web service clients that demonstrate the initiation of required parameters, request submission, status checking, and retrieval of outputs.  All the examples follow these four steps:
  1. The required input parameters, including data files, are initialized and set to the user-defined values.
  1. The client makes a POST request with the input parameters to the service host. An unique URI is returned.
  1. The client checks the status of the submitted request using the unique URI. The status can be: RUNNING, COMPLETED or ERROR.
    * The client program will loop until the status is COMPLETED or ERROR or if it exceeds the maximum number of defined loop iterations.
  1. The client downloads the output and/or log files from the service host and stores these locally.


### Examples ###
  * [R](RClient.md)
  * [Matlab](MatlabClient.md)
  * [Perl](PerlClient.md)
  * [Ruby](RubyClient.md)

[Example Datasets](ExampleDatasets.md)

[EPEPT Source Code Distribution](http://epept.googlecode.com/files/PermutationSource.zip)