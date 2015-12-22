Required Perl Modules
  * [Perl Installation and Administration](http://www.perl.org/)
  * [JSON](https://github.com/makamaka/JSON)
  * [LWP (Web Agent)](https://github.com/gisle/libwww-perl)
  * [How to Build and Install Perl Modules - Linux/Mac/Unix/Windows](http://www.cpan.org/modules/INSTALL.html)

### Source and run script for Linux/Mac/Unix ###
  * [Shell and script (tar)](http://epept.googlecode.com/hg/src/wsclients/perl/EPEPT_perl_sh.tar)
  * [Perl script](http://epept.googlecode.com/hg/src/wsclients/perl/EPEPT_AddamaWSClient.pl)
  * [Perl script for SAM mode](http://epept.googlecode.com/hg/src/wsclients/perl/EPEPT_SAMAddamaWSClient.pl)
  * [Perl script for GSEA mode](http://epept.googlecode.com/hg/src/wsclients/perl/EPEPT_GSAddamaWSClient.pl)

### Source and run script for Windows ###
  * [Batch and script (tar)](http://epept.googlecode.com/hg/src/wsclients/perl/EPEPT_perl_bat.zip)
  * [Perl script](http://epept.googlecode.com/hg/src/wsclients/perl/EPEPT_AddamaWSClient_win.pl)
  * [Perl script for SAM mode](http://epept.googlecode.com/hg/src/wsclients/perl/EPEPT_SAMAddamaWSClient_win.pl)
  * [Perl script for GSEA mode](http://epept.googlecode.com/hg/src/wsclients/perl/EPEPT_GSAddamaWSClient_win.pl)

The shell/batch executables allows users to run the corresponding Perl script from the command line. The shell/batch defines the (path to the) input file, the output path for the results and the [input parameters](http://code.google.com/p/epept/wiki/ClientInputs).

The input parameters are stated in a [JSON](http://json.org) format, for example:
```
      {
         method: 'ML',
         ci_chk: true,
         ci: 40,
         oopt_chk: ture,
         cc_chk: false,
         mail_address:'user@example.com'
      }
```

In the above example, _**ci**_ indicates _confidence interval_ of 40, _**oopt\_chk**_ indicates _optimal order preserving transform_ is enabled, _**cc\_chk**_ indicates _convergence criterion_ is disabled and _**method**_ indicates _maximum likelihood for parameter estimation_.

**Optional** Including an email address in the EPEPT web service request will ensure that the user receives a notification upon completion of the computation, as opposed to polling the web service for a result. The examples include looping logic to check on EPEPT status, but large datasets can translate to long computation times.

For the individual Perl script, these parameters are defined and can be altered by editing the script itself.

The system will display the output and error logs of each Perl command in the command/terminal console. On completion the EPEPT results (the P-values and visualization of these in png format) are stored in the user-defined output path.