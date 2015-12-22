### Required Libraries ###
  * [Matlab Install (commercial product)](http://www.mathworks.com/products/)
  * [HTTP Client for Java 1.6 (MATLAB 7.5 (R2007b) and later)](http://epept.googlecode.com/files/commons-httpclient-support-1.2.2-SNAPSHOT-jar-with-dependencies.jar)<br>
<ul><li><a href='http://epept.googlecode.com/files/commons-httpclient-support-1.2.1-SNAPSHOT-jar-with-dependencies.jar'>HTTP Client for Java 1.5 (MATLAB 7.0.4 (R14SP2) -MATLAB 7.4 (R2007a)</a></li></ul>

<h2>Source</h2>
<ul><li><a href='http://epept.googlecode.com/files/epept_script.zip'>Matlab Client Source (zip)</a> - contains epept_script.m, epept_makerequest.m, epept_checkstatus.m and epept_getoutput.m</li></ul>

The matlab file <i><b>epept_script.m</b></i> defines the (path to the) input file, the output path for the results and the <a href='http://code.google.com/p/epept/wiki/ClientInputs'>input parameters</a>.<br>
The input parameters are stated in a cell array, such as this example:<br>
<pre><code>params = cell(0,2); <br>
p = 0;<br>
p = p + 1;<br>
params{p,1} = 'mode';<br>
params{p,2} = mode;<br>
p = p + 1;<br>
params{p,1} = 'method';<br>
params{p,2} = 'pwm';<br>
p = p + 1;<br>
params{p,1} = 'ci_chk';<br>
params{p,2} = 'true';<br>
p = p + 1;<br>
params{p,1} = 'ci';<br>
params{p,2} = '95';<br>
p = p + 1;<br>
params{p,1} = 'oopt_chk';<br>
params{p,2} = 'false';<br>
p = p + 1;<br>
params{p,1} = 'cc_chk';<br>
params{p,2} = 'false';<br>
p = p + 1;<br>
params{p,1} = 'rseed';<br>
params{p,2} = '5884689';<br>
p = p + 1;<br>
params{p,1} = 'mail_address';<br>
params{p,2} = 'user@example.com';<br>
if strcmp(mode,'SAM')|strcmp(mode,'GSEA');<br>
   p = p + 1;<br>
   params{p,1} = 'resptype';<br>
   params{p,2} = 'Two class unpaired';<br>
   p = p + 1;<br>
   params{p,1} = 'nperms';<br>
   params{p,2} = num2str(nperms);<br>
end<br>
if strcmp(mode,'GSEA');<br>
   p = p + 1;<br>
   params{p,1} = 'gsa_method';<br>
   params{p,2} = 'maxmean';<br>
end<br>
</code></pre>
On successful completion the EPEPT results are stored in the user-defined output path.