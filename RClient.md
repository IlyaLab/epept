### Required Libraries and Dependencies ###
  * [R Installation and Administration](http://cran.r-project.org/doc/manuals/R-admin.html)
    * [More information on installing R packages](http://cran.r-project.org/doc/manuals/R-admin.html#Installing-packages)
  * [Download rjson](http://epept.googlecode.com/files/rjson_0.1.8.tar.gz)
    * [More information on rjson package](http://cran.r-project.org/web/packages/rjson/index.html)
  * [Curl (Install and add to system path)](http://curl.haxx.se/)

### Source and run script for Linux/Mac/Unix ###
  * [Shell and script (tar)](http://epept.googlecode.com/files/EPEPT_sh.tar)
  * [R script](http://epept.googlecode.com/hg/src/wsclients/r/EPEPT_AddamaWSClient.r)
  * [R script for SAM mode](http://epept.googlecode.com/hg/src/wsclients/r/EPEPT_SAMAddamaWSClient.r)
  * [R script for GSEA mode](http://epept.googlecode.com/hg/src/wsclients/r/EPEPT_GSAddamaWSClient.r)

### Source and run script for Windows ###
  * [Batch and script (zip)](http://epept.googlecode.com/files/EPEPT_win_bat.zip)
  * [R script](http://epept.googlecode.com/hg/src/wsclients/r/EPEPT_AddamaWSClient_win.r)
  * [R script for SAM mode](http://epept.googlecode.com/hg/src/wsclients/r/EPEPT_SAMAddamaWSClient_win.r)
  * [R script for GSEA mode](http://epept.googlecode.com/hg/src/wsclients/r/EPEPT_GSAddamaWSClient_win.r)

The shell/batch executables allow users to run the corresponding R script from the command line, for example:
> ` 'R CMD BATCH EPEPT_GSAddamaWSClient.r'. `

The shell/batch scripts define the (path to the) input file, the output path for the results and the [input parameters](ClientInputs.md).
<br><br>
The input parameters are defined in <a href='http://json.org'>JSON</a> format, for example:<br>
<pre><code>    { <br>
       mode:"SAM", <br>
       mail_address:"user@example.com",<br>
       ci:95,<br>
       oopt_chk:false,<br>
       ci_chk:true,<br>
       cc_chk:false,<br>
       method:"ML"<br>
    }<br>
</code></pre>

In the above example, <i><b>ci</b></i> indicates a confidence interval of 95; <i><b>oopt_chk</b></i> indicates that the optimal order preserving transform should be enabled; <i><b>cc_chk</b></i> indicates that the convergence criterion should be disabled.<br>

<i><b>Optional</b></i>  Including an email address in the EPEPT web service request will ensure that the user receives a notification upon completion of the computation, as opposed to polling the web service for a result.  The examples include looping logic to check on EPEPT status, but large datasets can translate to long computation times.<br>
<br>
For the individual R script, these parameters are defined and can be altered by editing the script itself.<br>
<br>
The system will generate a log file called EPEPT_AddamaWSClient.r.Rout which contains the output and error logs of each R command in the script. This log file is located in the same folder as the R Client program. On completion the EPEPT results (the P-values and visualization of these in png format) are stored in the user-defined output path.