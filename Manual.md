## EPEPT _Version 2.0_ ##
**[EPEPT: A web service for enhanced P-value estimation in permutation tests](http://www.biomedcentral.com/1471-2105/12/411/abstract)**<br>
Theo Knijnenburg, Jake Lin, Hector Rovira, John Boyle, Ilya Shmulevich<br>

<b><a href='http://bioinformatics.oxfordjournals.org/cgi/content/abstract/25/12/i161?eto'>Fewer Permutations, More Accurate P-Values</a></b><br>
Theo Knijnenburg, Lodewyk Wessels, Marcel Reinders, Ilya Shmulevich<br>

<b><i><a href='http://www.systemsbiology.org'>Institute for Systems Biology</a></i></b><br>
401 Terry Ave North<br>
Seattle, WA 98109-5234, US<br>
(206) 732-1200<br>
<a href='mailto:codefor@systemsbiology.org'>Contact Us</a><br>

<i><b>Software License</b></i><br>
The software presented in this project is offered under the following open source license:  <a href='http://www.gnu.org/licenses/lgpl.html'>GNU Lesser GPL</a>

<hr />
<h3>Workflow</h3>
A data file is required for the EPEPT web application. Once that file is entered, fill in the other input parameters and click the Execute button. The page will automatically refresh itself <a href='BrowserSettings.md'>(see browser settings)</a> and once completed, display the results (see screen shot below). If the email address field is filled, a message containing the results URL will be sent to that address. Please see <a href='WebServiceClients.md'>web service clients</a> for different programming language http workflow details.<br>
<h3>Inputs</h3>
<i><b>File</b></i> : Required input file containing test statistics and permutation values or labeled dataset.  For example,  <a href='ExampleDatasets.md'>download example datasets</a>.<br>
<blockquote>The file should be a tab delimited text file, a comma separated text file or an Excel file. EPEPT checks the extension of the file to decide upon its format: Excel files should have the <i>.xls</i> or <i>.xlsx</i> extension and the data should be on the first sheet. Comma-separated files should have the extension <i>.csv</i>.  All other files are assumed to be tab-delimited text files.<br><br>
In the <b><i>Permutation Values</i></b> setting, each column in the file should contain one test statistic and its corresponding permutation values. Since multiple columns are allowed, different events (e.g. different genes or gene sets) can be tested simultaneously, yet independently.<br><br>
<i><b>Header Row</b></i>: The file is allowed to have one header row. In case of a header row, the test statistics should be on the second row. In case no header row is used, the test statistics should be on the first row.<br><br>
All numerical values in the rows below the test statistic are assumed to be the permutation values. Non-numerical values, NaN's (not a number) and Inf's (infinite) are ignored. At least 1,000 permutation values per column should be reported in order for the tail estimation procedure to be used.<br><br>
In the <i><b>SAM</b></i> and <i><b>GSEA</b></i> settings, each column should contain the expression levels of all genes in the dataset. The first row should contain the class labels or other response type assigned to the columns. Possible configurations of the first row should match the `resp.type' options of the <a href='http://cran.r-project.org/web/packages/samr/index.html'>samR</a> package (see Response Type parameters). <br><br>
The first column can be used as a header column for the gene names.</blockquote>

<i><b>EPEPT Mode</b></i><br>
<blockquote>Three different modes are available. The default is <i><b>Permutation Values</b></i>, where the expected input is a matrix of permutation values. The second mode is <i><b>SAM</b> (Significance Analysis of Mircoarrays)</i>, which requires the user to upload a labeled microarray gene expression data set. EPEPT uses the <a href='http://cran.r-project.org/web/packages/samr/index.html'>samR</a> package to compute permutation values, which are subsequently used for P-value estimation. The third mode is <i><b>GSEA</b> (Gene Set Enrichment Analysis)</i>, which requires a labeled microarray gene expression data set and a file with gene sets in the <i>.gmt</i> format. In this case, EPEPT uses the <a href='http://cran.r-project.org/web/packages/GSA/index.html'>GSA</a> to compute permutation values, which are subsequently used for P-value estimation.</blockquote>

<i><b>Estimation method</b></i><br>
<blockquote>Three different methods are available to estimate the parameters of the generalized <i>Pareto</i> distribution (which models the tail of the distribution of the permutation values): <i><b>probability weighted moments (PWM)</b></i>, <i><b>maximum likelihood (ML)</b></i>, and <i><b>method of moments (MOM)</b></i>. Using theoretical distributions and practical applications we found that all methods performed comparably to each other. Some studies have been done comparing these estimators, often favoring ML.<br><br>
See <a href='http://bioinformatics.oxfordjournals.org/cgi/content/abstract/25/12/i161?eto'>paper</a> for more details.</blockquote>

<i><b>Confidence interval</b></i><br>
<blockquote>The confidence interval of the estimated P-value indicates the reliability of the estimate. The confidence interval is qualified by the confidence level <i>(default 95%)</i>. Loosely speaking, the confidence level indicates how sure (e.g. 95% sure) we can be that the actual P-value is within the confidence interval. This level can be set between 10 and 99.</blockquote>

<i><b>Confidence interval checkbox</b></i><br>
<blockquote>A flag determining whether the confidence interval should be computed or not.</blockquote>

<i><b>Optimal order preserving transform checkbox</b></i><br>
<blockquote>A flag determining whether the optimal order preserving transform should be applied or not.</blockquote>

<i><b>Convergence criteria checkbox</b></i><br>
<blockquote>A flag determining whether the convergence criteria should be applied or not.</blockquote>

<i><b>Random seed</b></i><br>
<blockquote>If a numerical value between 1 and 1,000,000 is given, this will be used as a random seed allowing the user to reproduce EPEPT runs. When the (default) value 0 is selected, the random seed will be chosen arbitrarily.</blockquote>

<i><b>Response type: (SAM/GSEA mode)</b></i><br>
<blockquote>When EPEPT is used to generate permutation values in the <i><b>SAM</b></i> or <i><b>GSEA</b></i> setting, the user can choose the response type.  The value must be one of the following:  <b>Quantitative</b>, <b>Two class unpaired</b>, <b>Two class paired</b>, <b>Survival</b>, or <b>Multiclass</b>.</blockquote>

<i><b>NPerms:SAM/GSEA mode</b></i><br>
<blockquote>When EPEPT is used to generate permutation values in the <i><b>SAM</b></i> or <i><b>GSEA</b></i> setting, the user can choose the number of permutations to be performed. In the <i><b>SAM</b></i> setting the maximum is 1,000. (SAM evaluates the P-value of one gene using the permutation values of all genes, effectively multiplying the number of permutations used by the number of genes.) In the <i><b>GSEA</b></i> setting the maximum is 10,000.</blockquote>

<i><b>Geneset_file: GSEA mode</b></i><br>
<blockquote>When EPEPT is used to generate permutation values in the <i><b>GSEA</b></i> setting, a file with gene set annotations in gene matrix transposed (.gmt) format has to be given. Such a tab delimited text file contains one gene set per row. The first two columns contain the gene set ID and description. The following columns contain the genes for that particular gene set. The annotation of these genes should match the gene annotation in the header column of the gene expression data file.</blockquote>

<i><b>GSEA statistic: GSEA mode</b></i><br>
<blockquote>When EPEPT is used to generate permutation values in the <i><b>GSEA</b></i> setting, the user can choose the statistic used to summarize genesets. The value must be one of the following: maxmean, mean or absmean.</blockquote>

<i><b>Email address (optional)</b></i><br>
<blockquote>An email will be sent to the provided email address when the EPEPT run completes. This mail contains links to the results and logs. This email address is completely confidential and will not be used or shared with other systems and purposes. On the results page, this email address will be displayed as xxx@your_domain for added security.</blockquote>

<h3>Outputs</h3>
<i><b>Estimated P-values</b></i><br>
<blockquote>The main output of EPEPT are the estimated P-values. These are reported in a tab-delimited text file.  Any headers provided in the original file will be included in the output file.  If <i>confidence intervals</i> were requested the two rows under the P-value estimates indicate the lower and upper bound of the confidence intervals.  If <i>convergence criteria</i> were applied an additional row is included with binary values indicating whether the estimate converged (1) or not (0).<br><br>
Images (<i>.png</i> and  <i>.eps</i> format) are generated to visually depict the estimated P-values and their confidence bounds.</blockquote>

<img src='http://epept.googlecode.com/files/epeptResults.png' />