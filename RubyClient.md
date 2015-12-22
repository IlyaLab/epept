### Required Libraries/Gems ###
  * [Ruby Installation and Administration](http://www.ruby-lang.org/en/downloads/)
  * [JSON for Ruby](http://flori.github.com/json/)
  * [HTTP Client for Ruby](http://code.google.com/p/ruby-httpclient/)
  * Linux/Unix/Mac gem install commands
```
     sudo gem install json
     sudo gem install httpclient
```
  * Window gem install commands (from Ruby command prompt)
```
     gem install json_pure
     gem install httpclient --source http://dev.ctor.org/download/
```

### Source and run script for Linux/Mac/Unix ###
  * [Shell and script (tar)](http://epept.googlecode.com/files/EPEPT_ruby_sh.tar)
  * [Ruby script](http://epept.googlecode.com/hg/src/wsclients/ruby/EPEPT_AddamaWSClient.rb)
  * [Ruby script for SAM mode](http://epept.googlecode.com/hg/src/wsclients/ruby/EPEPT_SAMAddamaWSClient.rb)
  * [Ruby script for GSEA mode](http://epept.googlecode.com/hg/src/wsclients/ruby/EPEPT_GSAddamaWSClient.rb)

### Source and run script for Windows ###
  * [Batch and script (zip)](http://epept.googlecode.com/files/EPEPT_ruby_bat.zip)
  * [Ruby script](http://epept.googlecode.com/hg/src/wsclients/ruby/EPEPT_AddamaWSClient_win.rb)
  * [Ruby script for SAM mode](http://epept.googlecode.com/hg/src/wsclients/ruby/EPEPT_SAMAddamaWSClient_win.rb)
  * [Ruby script for GSEA mode](http://epept.googlecode.com/hg/src/wsclients/ruby/EPEPT_GSAddamaWSClient_win.rb)

The shell/batch executable allows users to run the corresponding Ruby script from the command line. The shell/batch defines the (path to the) input file, the output path for the results and the [input parameters](http://code.google.com/p/epept/wiki/ClientInputs).

The input parameters are stated in [JSON](http://json.org) format, for example:<br>
<pre><code>      {<br>
         mode: 'GSEA', <br>
         method:'ML'<br>
         nperms: 1000,<br>
         gsa_method: 'maxmean',<br>
         rseed: 0,<br>
         resptype: 'Two class unpaired',<br>
         ci_chk: true,<br>
         ci: 40,<br>
         oopt_chk: true,<br>
         cc_chk: false,<br>
         mail_address: 'user@example.com'<br>
       }<br>
</code></pre>

In the above example, <i><b>mode</b></i> indicates mode of GSEA, with default <i><b>nperm</b></i> of 1000, <i><b>resptype</b></i> of <i>Two class unpaired</i>, confidence interval <i><b>ci</b></i> of 40, optimal order preserving transform <i><b>oopt_chk</b></i> enabled, convergence criterion <i><b>cc_chk</b></i> is disabled and <i><b>method</b></i> is set to <i>maximum likelihood for parameter estimation</i>.<br>
<br>
<b><i>Optional</i></b> Including an email address in the EPEPT web service request will ensure that the user receives a notification upon completion of the computation, as opposed to polling the web service for a result. The examples include looping logic to check on EPEPT status, but large datasets can translate to long computation times.<br>
<br>
For the individual Ruby script, these parameters are defined and can be altered by editing the script itself.<br>
<br>
The system will display the output and error logs of each Ruby command in the command/terminal console. On completion the EPEPT results (the P-values and visualization of these in png format) are stored in the user-defined output path.