# i2-workshop-2016
## Hands on with the ORCID API 
### Internet 2 Tech Exchange, Sept 2016

<p>This workshop provides a hands-on tutorial for using the ORCID Member and Public APIs. </p>
--
<h1><a name="top"></a>Contents</h1>
<p><a href="#1">1. About the ORCID APIs</a></p>
<blockquote>
  <p><a href="#1.1">1.1  ORCID API types &amp; features</a></p>
  <p><a href="#1.2">1.2  QA test environment</a></p>
  <p><a href="#1.3">1.3  ORCID API technologies</a></p>
  <p><a href="#1.4">1.4  ORCID API tools</a></p>
</blockquote>
<p><a href="#2">2. Public API: Searching  &amp; retrieving ORCID records</a></p>
<blockquote>
  <p><a href="#2.1">2.1  Create a QA user account</a></p>
  <p><a href="#2.2">2.2  Accessing the QA public API</a></p>
</blockquote>
<p><a href="#3">3. Public API: Searching &amp; retrieving ORCID records</a></p>
<blockquote>
  <p><a href="#3.1">3.1  Retrieving public record data</a></p>
  <p><a href="#3.2">3.2  Searching public record data</a></p>
  <blockquote>
    <p><a href="#3.2.1">3.2.1 Basic keyword search</a></p>
    <p><a href="#3.2.2">3.2.2 Boolean keyword search</a></p>
    <p><a href="#3.2.3">3.2.3 Fielded search</a></p>
    <p><a href="#3.2.4">3.2.4. More searches to try!</a></p>
  </blockquote>
</blockquote>
<p><a href="#4">4. Public API: Getting authenticated ORCID iDs</a></p>
<blockquote>
  <p><a href="#4.1">4.1  OAuth introduction</a></p>
  <p><a href="#4.2">4.2  Setting up the OAuth Playground</a></p>
  <p><a href="#4.3">4.3  Get an authorization code</a></p>
  <p><a href="#4.4">4.4  Exchange the authorization code for the user&rsquo;s ORCID iD</a></p>
</blockquote>
<p><a href="#5">5. Member API: Access to amend ORCID records</a></p>
<blockquote>
  <p><a href="#5.1">5.1  Accessing the QA Member API</a></p>
  <p><a href="#5.2">5.2  Setting up the OAuth Playground</a></p>
</blockquote>
<p><a href="#6">6. Member API: Getting permission to edit ORCID records</a></p>
<p><a href="#6.1">6.1  Obtaining access tokens</a></p>
<blockquote>
  <p><a href="#6.1.1">6.1.1 Get an authorization code</a></p>
  <p><a href="#6.1.2">6.1.2 Exchange the authorization code for an access token</a></p>
</blockquote>
<p><a href="#7">7. Member API: Writing to ORCID records via the API</a></p>
<blockquote>
  <p><a href="#7.1">7.1  Adding a new affiliation to an ORCID record</a></p>
  <p><a href="#7.2">7.2  Updating an affiliation</a></p>
</blockquote>
<p><a href="#8">8. Member API: Creating new records</a></p>
<blockquote>
  <p><a href="#8.1">8.1  Construct the authorization URL</a></p>
  <blockquote>
    <p><a href="#8.1.1">8.1.1 Base URL</a></p>
    <p><a href="#8.1.2">8.1.2 Required parameters</a></p>
    <p><a href="#8.1.3">8.1.3 Optional parameters</a></p>
  </blockquote>
  <p><a href="#8.2">8.2 Build a redirect page/application</a></p>
  <p><a href="#8.3">8.3  Prompt users to create or connect their ORCID iD</a></p>
  <p><a href="#8.4">8.4  Obtain access tokens and ORCID iDs</a></p>
  <p><a href="#8.5">8.5  Read from/write to users&rsquo; ORCID records</a></p>
</blockquote>
<p><a href="#9">9. ORCID API resources</a></p>
  <hr />
<h1><a name="1"></a>1. About the ORCID APIs</h1>
<h2><a name="1.1"></a>1.1 ORCID API types &amp; features</h2>
<p>ORCID offers several APIs (Application Programming Interfaces) that allow your systems to connect to the  ORCID registry, including reading from and writing to ORCID records. Some API  functions are freely available to anyone; others are available to organizations  that financially support ORCID with an annual membership subscription.</p>
<table border="1" cellspacing="0" cellpadding="0" width="680">
  <tr>
    <td width="95" valign="top"><br />
      <strong>API Version</strong></td>
    <td width="172" valign="top"><p><strong>Access</strong></p></td>
    <td width="413" valign="top"><p><strong>Features</strong></p></td>
  </tr>
  <tr>
    <td width="95" valign="top"><p>Public API</p></td>
    <td width="172" valign="top"><p>Freely available to anyone</p></td>
    <td width="413" valign="top"><p><strong>Authenticate:</strong> Obtain a user&rsquo;s authenticated ORCID iD<br />
      <strong>Read (Public)</strong>:<strong> </strong>Search/retrieve public data<br />
      <strong>Create:</strong> Create new ORCID records on demand</p>
	</td>
  </tr>
  <tr>
    <td width="95" valign="top"><p>Member API</p></td>
    <td width="172" valign="top"><p>Available to organizations that support ORCID with an annual membership subscription<br /><i>Sandbox Member API freely available to all for testing</i></p></td>
    <td width="413" valign="top"><p><strong>Read (Limited)</strong>: Search/retrieve limited-access data<br />
      <strong>Add</strong>: Post new items to a record (affiliations, works, etc.)<br />
      <strong>Update</strong>: Edit or delete items you previously added</p></td>
  </tr>
</table>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="1.2"></a>1.2 Sandbox test environment</h2>
<p>In addition to the  production Registry and APIs, ORCID also offers a testing environment, the ORCID Sandbox, which we will be using for this boot camp. The Sandbox is open  to all users and provides a place to develop and test applications without affecting data in the live ORCID registry.</p>
<p> The Sandbox includes:</p>
<ul>
  <li><strong><a href="https://qa.orcid.org/signin" target="_blank">Sandbox Registry</a></strong>: Simulates the ORCID Registry <br />&nbsp;</li>
  <li><strong><a href="https://members.orcid.org/api/introduction-orcid-member-api">Sandbox Member API</a></strong>: Simulates the Member API<br />&nbsp;</li>
  <li><strong><a href="https://members.orcid.org/api/introduction-orcid-public-api">Sandbox Public API</a></strong>: Simulates the Public API</li>
</ul>
<p>The sandbox behaves the same  way as the production ORCID Registry with a few exceptions: </p>
<ul>
  <li>Search &amp; Link tools do not function.<br />&nbsp;</li>
  <li>To avoid unintentional spamming, the Sandbox sends  emails only to @mailinator.com addresses. <a href="https://mailinator.com/" target="_blank">Mailinator.com</a> is an inbox testing service  that is free and requires no registration. To receive emails from the Sandbox,  use an @mailinator.com email address when creating Sandbox record(s).<br />&nbsp;</li>
  <li>Links in the top menu bar (For Researchers, For  Organizations, About, etc.) do not function.</li>
</ul>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="1.3"></a>1.3 ORCID  API technologies</h2>
<p>All of the ORCID APIs are  based on the same set of technologies:</p>
<ol>
  <li><strong>REST: </strong>ORCID APIs are &ldquo;RESTful&rdquo;, which  means that they use HTTP (hyper-text transfer) calls to transfer information.<br />&nbsp;</li>
  <li><strong>OAuth:</strong> ORCID  APIs use the OAuth 2.0 authentication protocol in order to grant client  applications access to users&rsquo; ORCID records.<br />&nbsp;</li>
  <li><strong>XML/JSON:</strong> ORCID APIs support data exchange in either XML or JSON format.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="1.4"></a>1.4 ORCID  API Tools</h2>
<p>In order to use the ORCID  APIs you will need the following software tools:</p>
<ol>
  <li>Web browser: Firefox (33+), Chrome (38+), Internet Explorer (10+), Safari (6+)<br />&nbsp;</li>
  <li>Internet connection<br />&nbsp;</li>
  <li>Plain text editor: TextEdit (Mac), Notepad++ (Win), or your preferred plain text editor<br />&nbsp;</li>
  <li>Software capable of making HTTP requests:</li>
  <ul>
    <li>cURL: free, command-line application available for Mac  or Windows at <a href="http://curl.haxx.se/download.html">http://curl.haxx.se/download.html</a> (pre-installed on most Mac OS versions; accessible within Terminal application)<br />&nbsp;</li>
    <li>Online tools, e.g. <a href="http://hurl.it">hurl.it</a> or <a href="https://developers.google.com/oauthplayground/">Google OAuth Playground</a><br />&nbsp;</li>
    <li>Your own web application, in a language such as Java,  Ruby, Python, PHP, etc.</li>
  </ul>
</ol>
<p>For this boot camp, we will  be using the online tool <a href="https://developers.google.com/oauthplayground/">Google OAuth Playground</a>.</p>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h1><a name="2"></a>2. Public API: Searching &amp; retrieving ORCID records</h1>
<h2><img width="194" height="336" src="http://alainna.org/orcid/clip_image002.gif" align="right" hspace="12" vspace="12" alt="Screen Shot 2015-06-04 at 4.43.26 PM.png" /><a name="_2.1_Create_a" id="_2.1_Create_a"></a>2.1 Create a  Sandbox User Account</h2>
<p>In order to try out API  calls, such as a reading a record and adding information to it, you will also  need to create a test ORCID record in the Sandbox. This can be done through the  user interface, much like in the live ORCID registry.</p>
<ol>
  <li>Open a web browser and navigate to <a href="https://qa.orcid.org/signin" target="_blank">https://qa.orcid.org/signin</a><br />&nbsp;</li>
  <li>Click <strong>Register  for an ORCID iD</strong>.<br />&nbsp;</li>
  <li>Complete the form with a name, email, and password.</li>
<p><strong><em>IMPORTANT! </em></strong><em>Don&rsquo;t use a real email address! Instead, make up an address  ending in @mailinator.com (use any prefix, e.g. sgarcia@mailinator.com).</em></p>
  <li>Click the <strong>I  consent…</strong> checkbox and click <strong>Register</strong>.<br />&nbsp;</li>
  <li>After completing the registration process, you will be  taken to your new Sandbox ORCID record. Make note of the 16-digit ORCID iD for  this record – you will need this in order to make API calls later during the boot  camp.<br />
    <img src="http://alainna.org/orcid/clip_image004.jpg" alt="" width="645" height="107" border="0" /><br />&nbsp;</li>
  <li>Add a few pieces of information to your new Sandbox  record – biography, education, employment, etc. – so that you have some data to  work with in future steps.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="2.2"></a>2.2  Accessing the Sandbox public API</h2>
<p>Access to the ORCID Public  API requires a set of credentials consisting of a Client ID and a Client  Secret. Public API credentials are tied to an individual's ORCID record and  cannot be transferred to another person. The process for getting Public API  credentials is identical in the sandbox and production environments.</p>
<ol>
  <li>To access the Public API, you&rsquo;ll first need to verify  your email address. Visit <a href="http://mailinator.com/">http://mailinator.com/</a> and enter the email  that you used to create your Sandbox account.<br />&nbsp;</li>
  <li>Open the confirmation message from ORCID and click <strong>Verify your email address</strong>.<br />&nbsp;</li>
  <li>Back in your ORCID account, click <strong>Developer Tools</strong> at the top of the screen.<br />&nbsp;</li>
  <li>Click the <strong>Register  for the free ORCID public API button</strong>.<br />&nbsp;</li>
<p><img src="http://alainna.org/orcid/clip_image006.gif" alt="" width="433" height="97" border="0" /></p>
  <li>Review and agree to the terms of service when prompted.<br />&nbsp;</li>
  <li>In the form that appears, enter the following values:<br />&nbsp;</li>
  <table border="1" cellspacing="0" cellpadding="0" width="612">
    <tr>
      <td width="102" valign="top"><p><strong>Name</strong></p></td>
      <td width="510" valign="top"><p>Name of the ORCID application that you are developing.</p>
        <p> Ex: State University ORCID Connector</p></td>
    </tr>
    <tr>
      <td width="102" valign="top"><p><strong>Website</strong></p></td>
      <td width="510" valign="top"><p>URL for the homepage of your ORCID application.</p>
        <p> Ex: http://stateuniversity.edu/orcid</p></td>
    </tr>
    <tr>
      <td width="102" valign="top"><p><strong>Description</strong></p></td>
      <td width="510" valign="top"><p>Description of the ORCID application that you are developing.</p>
        <p> Ex: An application that allows users to connect their ORCID iD to    their State University faculty profile.</p></td>
    </tr>
    <tr>
      <td width="102" valign="top"><p><strong>Redirect URIs</strong></p></td>
      <td width="510" valign="top"><p>URIs for use with the OAuth 2.0 protocol; for more information, see <a href="http://support.orcid.org/knowledgebase/articles/116739-register-a-client-application#Redirect" target="_blank">About redirect URIs</a>.</p>
        <p> For this boot camp, use: <a href="https://developers.google.com/oauthplayground/" target="_blank">https://developers.google.com/oauthplayground/</a></p>
        <p><em>(Add this URI automatically by    clicking &quot;+Google OAuth2 Playground&quot; under Test redirect URIs.)</em></p></td>
    </tr>
  </table><br />&nbsp;
  <li>Click the Save icon at the bottom of the form to  generate your API credentials.</li>
<p><img src="http://alainna.org/orcid/clip_image008.jpg" alt="" width="500" height="62" border="0" /><br />&nbsp;  </p>
<li>To view your API credentials, click <strong>Show Details</strong>.</li>
<p><img src="http://alainna.org/orcid/clip_image010.jpg" alt="" width="412" height="124" border="0" /><br />&nbsp;  </p>
<li>Your API credentials – Client ID and Client Secret – are  shown just beneath your Redirect URIs. We&rsquo;ll be using these later in the boot  camp, but no need to copying them down – they are always available in the <strong>Developer Tools</strong> section of your  account.<br />
</li>
<p><img src="http://alainna.org/orcid/clip_image012.jpg" alt="" width="416" height="110" border="0" /></p>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h1><a name="3"></a>3. Public API: Searching &amp; Retrieving ORCID Records</h1>
<h2><a name="3.1"></a>3.1 Retrieving Public Record Data</h2>
<p>Using the Public API, you  can retrieve the XML version of any user&rsquo;s public ORCID record. This is same  information that you&rsquo;ll see by viewing a record in the user interface of the  ORCID registry, but in machine-readable XML format. In a real-world web  application, this process can be used to retrieve and copy information from  ORCID records into your own system.</p>
<ol>
  <li><img src="http://alainna.org/orcid/clip_image014.gif" alt="" width="239" height="113" align="right" hspace="12" vspace="12" />Visit <a href="https://developers.google.com/oauthplayground/">https://developers.google.com/oauthplayground/</a><br />&nbsp;</li>
  <li>Beneath <strong>Step 3:  Configure request to API</strong> on the left side of the screen, set <strong>HTTP</strong> Method to <strong>GET</strong>.<br />
    &nbsp;</li>
  <li>Click <strong>Add  headers</strong> and enter the following values:</li>
  <ul>
    <li><strong>Header name:</strong> Accept</li>
    <li><strong>Header value:</strong> application/vnd.orcid+xml</li><br />&nbsp;
  </ul>
  <li><img src="http://alainna.org/orcid/clip_image016.jpg" alt="" width="315" height="185" align="right" hspace="12" />In the <strong>Request URI</strong> field, enter  https://pub.qa.orcid.org/v1.2/[orcid-id]/orcid-profile, replacing  [orcid-id] with the ORCID iD of the Sandbox record that you created earlier  (ex: https://pub.qa.orcid.org/v1.2/0000-0002-1223-3173/orcid-profile).<br />
    &nbsp;
  </li>
  <li>Leave the Request Body and Content-Type fields blank,  and click <strong>Send the request</strong>.<br />&nbsp;
  </li>
  <li>The XML for the ORCID record that you requested will  appear in the <strong>Request/Response</strong> section on the right side of the screen.<p><img src="http://alainna.org/orcid/clip_image017.jpg" alt="" width="700" height="297" border="0" /></p></li><br />&nbsp;
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="3.2"></a>3.2 Searching  Public Record Data</h2>
<p>In addition to retrieving  an individual&rsquo;s entire ORCID record, the Public API can be used to search for  all records whose public data contain particular search terms.</p>
<p> Note that only a portion of  the ORCID record is returned for each matching result. To view the entire record,  use the Public API to retrieve the record, as in section 3.1.</p>
<p> This tutorial provides a  very brief introduction to searching with the API. For much more information,  see <a href="https://members.orcid.org/api/tutorial-searching-data-using-api">https://members.orcid.org/api/tutorial-searching-data-using-api</a></p>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h3><a name="3.2.1"></a>3.2.1 Basic  Keyword Search</h3>
<p>A basic keyword search  performs a full-text search of all publicly-visible information in users&rsquo; ORCID  records (Names, ORCID iDs, and any other data with a privacy setting of  &ldquo;Everyone&rdquo;).</p>
<ol>
  <li>Visit <a href="https://developers.google.com/oauthplayground/" target="_blank">https://developers.google.com/oauthplayground/</a><br />&nbsp;</li>
  <li>Beneath <strong>Step 3:  Configure request to API</strong> on the left side of the screen, enter the  following:<br />&nbsp;</li>
<table border="1" cellspacing="0" cellpadding="0" width="576">
  <tr>
    <td width="101" valign="top"><p><strong>HTTP Method</strong></p></td>
    <td width="475" valign="top"><p>GET</p></td>
  </tr>
  <tr>
    <td width="101" valign="top"><p><strong>Add Headers</strong></p></td>
    <td width="475" valign="top"><p>Header name: Accept<br />
      Header value: application/vnd.orcid+xml</p></td>
  </tr>
  <tr>
    <td width="101" valign="top"><p><strong>Request URI</strong></p></td>
    <td width="475" valign="top"><p><a href="https://pub.qa.orcid.org/v1.2/search/orcid-bio?q=newman">https://pub.qa.orcid.org/v1.2/search/orcid-bio?q=newman</a><br />
      <em>Searches for records with the term &ldquo;newman&rdquo; in any field</em></p></td>
  </tr>
</table>
  <li>Leave the Request Body and Content-Type fields blank,  and click <strong>Send the request</strong>.<br />&nbsp;</li>
  <li>XML for matching records appears in the <strong>Request/Response</strong> section on the right.<br />&nbsp;</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h3><a name="3.2.2"></a>3.2.2 Boolean  Keyword Search</h3>
<p>In addition to the basic  keyword search, multiple keywords keywords can be included using Boolean terms  &ldquo;AND&rdquo; or &ldquo;OR&rdquo;. Exact phrases can be included using quotation marks. Note that  &ldquo;+&rdquo; signs must be substituted for spaces and that Boolean terms must be  uppercase.</p>
<ol>
  <li>Beneath <strong>Step 3:  Configure request to API</strong> on the left side of the screen, enter the  following:<br />&nbsp;</li>
<table border="1" cellspacing="0" cellpadding="0" width="576">
  <tr>
    <td width="101" valign="top"><p><strong>HTTP Method</strong></p></td>
    <td width="475" valign="top"><p>GET</p></td>
  </tr>
  <tr>
    <td width="101" valign="top"><p><strong>Add Headers</strong></p></td>
    <td width="475" valign="top"><p>Header name: Accept<br />
      Header value: application/vnd.orcid+xml</p></td>
  </tr>
  <tr>
    <td width="101" valign="top"><p><strong>Request URI</strong></p></td>
    <td width="475" valign="top"><p>http://pub.qa.orcid.org/v1.2/search/orcid-bio?q=michael+AND(hkbu+OR+&quot;Hong+Kong+Baptist+University&quot;)<br />
      <br />
      <em>Searches for records with the term &ldquo;michael&rdquo; and &ldquo;hkbu&rdquo; or &ldquo;Hong Kong Baptist University&rdquo; in any field</em>.</p></td>
  </tr>
</table><br />&nbsp;
  <li>Leave the Request Body and Content-Type fields blank   and click <strong>Send the Request</strong>.<br />&nbsp;</li>
  <li>XML for matching records appears in the <strong>Request/Response</strong> section on the right.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h3><a name="3.2.3"></a>3.2.3  Fielded search</h3>
<p>For more specific results, search for terms in particular record fields rather than entire ORCID records. </p>
<p> Available search fields include:</p>
<ul>
  <li>ORCID iD</li>
  <li>Names (given names, family name, credit name, other names)</li>
  <li>Email address</li>
  <li>Work titles</li>
  <li>External identifiers (DOIs, PMIDs, etc.)</li>
  <li>Creation/last modified dates</li>
</ul>
<p>For a complete list, see <a href="https://members.orcid.org/api/tutorial-searching-data-using-api" target="_blank">https://members.orcid.org/api/tutorial-searching-data-using-api</a></p>
<ol>
  <li>Beneath <strong>Step 3:  Configure request to API</strong> on the left side of the screen, enter the  following:<br />&nbsp;</li>
<table border="1" cellspacing="0" cellpadding="0" width="576">
  <tr>
    <td width="101" valign="top"><p><strong>HTTP Method</strong></p></td>
    <td width="475" valign="top"><p>GET</p></td>
  </tr>
  <tr>
    <td width="101" valign="top"><p><strong>Add Headers</strong></p></td>
    <td width="475" valign="top"><p>Header name: Accept<br />
      Header value: application/vnd.orcid+xml</p></td>
  </tr>
  <tr>
    <td width="101" valign="top"><p><strong>Request URI</strong></p></td>
    <td width="475" valign="top"><p>https://pub.qa.orcid.org/v1.2/search/orcid-bio/?q=family-name:Sanchez<br />
      <em>Searches for ORCID records with the term &ldquo;sanchez&rdquo; in Family (Last) Name </em></p></td>
  </tr>
</table><br />&nbsp;
  <li>Leave the Request Body and Content-Type fields blank, and click <strong>Send the request</strong>.<br />&nbsp;</li>
  <li>XML for matching records appears in the <strong>Request/Response</strong> section on the right.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h3><a name="3.2.4"></a>3.2.4. More  searches to try!</h3>
<ol>
  <li><strong>Search for  records associated with the exact DOI 10.1087/20120404:</strong><br />
    https://pub.qa.orcid.org/v1.2/search/orcid-bio/?q=digital-object-ids:%2210.1087/20120404%22<br />&nbsp;</li>
  <li><strong>Search for  records modified between May 6, 2015 and today:</strong><br />
    https://pub.qa.orcid.org/search/orcid-bio?q=profile-last-modified-date:%5B2015-05-06T00:00:00Z%20TO%20NOW%5D</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h1><a name="4"></a>4. BONUS:  Public API: Getting Authenticated ORCID iDs</h1>
<p>When you need to collect a  user&rsquo;s ORCID iD in your web application, the best method is to use the ORCID  API to get an authenticated ORCID iD.</p>
<p>Rather than relying on  users to correctly type their ORCID iDs into a form, the API process prompts  users to log into their ORCID account and passes their ORCID iD to your system  automatically. This prevents typos and ensures that you get the correct ORCID  iD for each user.</p>
<h2><a name="4.1"></a>4.1 OAuth  Introduction</h2>
<p>Getting an authenticated  ORCID iD through the API depends on an authentication process called <a href="http://oauth.net/" target="_blank">OAuth</a>. With  OAuth, a user can authorize a third-party system to access their account in  another system without sharing their login information. </p>
<p> You&rsquo;ve likely encountered  OAuth many times before – it&rsquo;s the same technology that allows you to log into  other applications using your Google, Facebook, or Twitter account.</p>
<p> The OAuth process consists  of the following steps:</p>
<ol>
  <li>Get an <strong>Authorization Code</strong> from the user.<br />
  &nbsp;</li>
  <li>Exchange the Authorization Code for the user&rsquo;s <strong>ORCID iD</strong>.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="4.2"></a>4.2 Setting  up the OAuth Playground</h2>
<p>In a real-world situation,  API interactions are completed by your system using a programming language such  as PHP, Java, or Ruby on Rails. For this boot camp, however, we&rsquo;ll be using a  web-based tool, the Google OAuth Playground.</p>
<p> The first thing we need to  do is set up the OAuth Playground to work with the ORCID API. </p>
<ol>
  <li>Visit <a href="https://developers.google.com/oauthplayground" target="_blank">https://developers.google.com/oauthplayground</a><br />&nbsp;</li>
  <li>Click the gear icon in the upper right corner to open  the configuration form.<br />&nbsp;</li>
</ol>
<p><img src="http://alainna.org/orcid/clip_image019.jpg" alt="" width="557" height="63" border="0" /></p>
<ol>
  <li><img src="http://alainna.org/orcid/clip_image021.jpg" alt="" width="250" height="272" align="right" hspace="12" vspace="12" />In the configuration form, enter the following:<br />&nbsp;</li>
<table border="1" cellspacing="0" cellpadding="0" width="425">
  <tr>
    <td width="162" valign="top"><p><strong>OAuth flow</strong></p></td>
    <td width="263" valign="top"><p>Server-side</p></td>
  </tr>
  <tr>
    <td width="162" valign="top"><p><strong>OAuth endpoints</strong></p></td>
    <td width="263" valign="top"><p>Custom</p></td>
  </tr>
  <tr>
    <td width="162" valign="top"><p><strong>Authorization endpoint</strong></p></td>
    <td width="263" valign="top"><p>https://qa.orcid.org/oauth/authorize</p></td>
  </tr>
  <tr>
    <td width="162" valign="top"><p><strong>Token endpoint</strong></p></td>
    <td width="263" valign="top"><p>https://qa.orcid.org/oauth/token</p></td>
  </tr>
  <tr>
    <td width="162" valign="top"><p><strong>Access token location</strong></p></td>
    <td width="263" valign="top"><p>Authorization header w/Bearer prefix</p></td>
  </tr>
  <tr>
    <td width="162" valign="top"><p><strong>OAuth Client ID</strong></p></td>
    <td width="263" valign="top"><p>Your Public API client id (ex: APP-LTF7N2HTB31FMM3Z)</p></td>
  </tr>
  <tr>
    <td width="162" valign="top"><p><strong>OAuth Client Secret</strong></p></td>
    <td width="263" valign="top"><p>Your Public API client secret (ex: c7359b4c-b495-42cd-a63e-d5bde5b0221a)</p></td>
  </tr>
</table><br />&nbsp;
  <li>The configuration screen should look similar to the image at right. After you&rsquo;ve entered the settings, click Close in the lower-left corner of the configuration screen.<br />
  </li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="4.3"></a>4.3 Get an  Authorization Code</h2>
<p>To  get an Authorization Code, you&rsquo;ll need to prompt the user to log into their ORCID  account and grant permission to your application. In a real-world situation,  this is done using an authorization URL that you construct. With the OAuth  Playground, however, this step is done by configuring some additional settings  and clicking a button.</p>
<ol>
  <li><img width="287" height="187" src="http://alainna.org/orcid/clip_image023.gif" align="right" hspace="12" vspace="12" alt="pub-select-authorize.png" />First, we will specify the permission (scope) that we  wish to request from the user. </li>
<p>Do  not select any of the options from the list beneath <strong>Step 1: Select &amp; authorize APIs</strong>. Instead, type <strong>/authenticate</strong> in the text box.</p>
<p> <em>The /authenticate scope allows you to  retrieve a user&rsquo;s ORCID iD. This is the only scope available in the Public API.  The Member API, however, permits additional scopes, which we&rsquo;ll explore in the  next section.</em></p>
  <li>Click <strong>Authorize  APIs</strong>.<br />&nbsp;</li>
  <li><img src="http://alainna.org/orcid/clip_image025.jpg" alt="" width="275" height="235" align="right" hspace="12" vspace="12" />An ORCID OAuth  login screen will appear, requesting that the user grant the permissions  entered in the previous steps. When this screen appears, click <strong>Sign In</strong>, and sign  into your Sandbox account.<br />&nbsp;</li>
  <li>Click <strong>Authorize</strong> on the ORCID OAuth login screen and you  will be sent back to the OAuth Playground. A 6-character code will appear in  the <strong>Authorization Code</strong> field beneath <strong>Step  2: Exchange authorization codes for tokens</strong>.<br />&nbsp;</li>
</ol>
<br clear="all" />
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="4.4"></a>4.4 Exchange the  Authorization Code for the User&rsquo;s ORCID iD</h2>
<p>Once you have an  Authorization Code, you can exchange it for the user&rsquo;s ORCID iD. In a real-world  situation, this exchange would be done by your system, using a programming  language such as PHP, Java, or Ruby on Rails. With the OAuth Playground,  however, this step is done by clicking a button.</p>
<ol>
  <li><img src="http://alainna.org/orcid/clip_image027.gif" alt="" width="242" height="102" align="right" hspace="12" vspace="12" />Beneath the <strong>Authorization Code</strong> field, click <strong>Exchange authorization code for tokens</strong>. <br />&nbsp;
</li>
  <li>The user&rsquo;s name and ORCID iD will appear in the <strong>Request/Response</strong> section on the right  side of the screen.</li>
<p><img border="0" width="340" height="163" src="http://alainna.org/orcid/clip_image029.jpg" alt="name-orcid.png" /></p><br  />&nbsp;
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h1><a name="5"></a>5. Member  API: Access to Amend ORCID Records</h1>
<p>As discussed in section  1.1, the Public API can only be used to read and search ORCID records, and to  get authenticated ORCID iDs. The Member API, however, can be used to add new  information to ORCID records, as well as to update information previously  added.</p>
<h2><a name="5.1"></a>5.1  Accessing the Sandbox Member API</h2>
<p>As with the Public API,  client credentials consisting of a client ID and a client secret are needed in  order to access the Member API. Public API credentials cannot be used to access  the Member API, so we&rsquo;ll be using a different client ID and secret for the  remainder of this boot camp.</p>
<p>Client Credentials for the  Member APIs are issued by ORCID. For this boot camp, you can use the sample Sandbox Client Credentials, but we recommend that you obtain your own Sandbox Client Credentials using the request form at <a href="https://orcid.org/content/register-client-application" target="_blank">https://orcid.org/content/register-client-application</a></p>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="5.2"></a>5.2 Setting up the OAuth Playground</h2>
<p>We&rsquo;ll continue to use the  Google Developers&rsquo; OAuth Playground for the next exercises, but a few configuration  changes are needed in order to work with the Member API.</p>
<ol>
  <li>Visit <a href="https://developers.google.com/oauthplayground" target="_blank">https://developers.google.com/oauthplayground</a><br />&nbsp; </li>
  <li>Click the gear icon in the upper right corner to open  the configuration form.<br />&nbsp; </li>
<p><img src="http://alainna.org/orcid/clip_image030.jpg" alt="" width="530" height="60" border="0" /></p>
<p><img src="http://alainna.org/orcid/clip_image031.jpg" alt="" width="275" height="291" align="right" hspace="12" vspace="12" /></p>
  <li>Enter the following:
   <p><em>(Fields edited to work with the Member  API are highlighted; the rest remain the same.)</em></p>
<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td width="158" valign="top"><p><strong>OAuth flow</strong></p></td>
    <td valign="top"><p>Server-side</p></td>
  </tr>
  <tr>
    <td width="158" valign="top"><p><strong>OAuth endpoints</strong></p></td>
    <td valign="top"><p>Custom</p></td>
  </tr>
  <tr>
    <td width="158" valign="top"><p><strong>Authorization endpoint</strong></p></td>
    <td valign="top"><p>https://qa.orcid.org/oauth/authorize</p></td>
  </tr>
  <tr>
    <td width="158" valign="top"><p><strong>Token endpoint</strong></p></td>
    <td valign="top"><p><strong>https://qa.orcid.org/oauth/token</strong></p></td>
  </tr>
  <tr>
    <td width="158" valign="top"><p><strong>Access token location</strong></p></td>
    <td valign="top"><p>Authorization header    w/Bearer prefix</p></td>
  </tr>
  <tr>
    <td width="158" valign="top"><p><strong>OAuth Client ID</strong></p></td>
    <td valign="top"><p><strong>Your Member API client ID</strong> (ex: APP-VZTMFLZVBD5NSJQA)</p></td>
  </tr>
  <tr>
    <td width="158" valign="top"><p><strong>OAuth Client Secret</strong></p></td>
    <td valign="top"><p><strong>Your Member API client secret</strong> (ex: 448101b3-1618-4841-8c4f-b04ab9edac92)</p></td>
  </tr>
</table><br  />&nbsp;</li>
  <li>The configuration screen should look similar to the  image at right. After you&rsquo;ve entered the settings, click <strong>Close</strong> in the lower left corner of the configuration screen.</li>
</ol>
<br clear="all" />
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h1><a name="6"></a>6. Member  API: Getting permission to edit ORCID records </h1>
<h2><a name="6.1"></a>6.1  Obtaining Access Tokens</h2>
<p>To access an ORCID record  via the Member API, you first need to get permission from the owner of the  record in the form of an Access Token.</p>
<p> This process of granting  permission uses OAuth and is similar to the process used for obtaining an  authenticated ORCID iD described in <a href="#4">section 4</a>. </p>
<ol>
  <li>Get an <strong>Authorization  Code</strong>.<br />&nbsp; </li>
  <li>Exchange the Authorization Code for an <strong>Access Token</strong>.<br />&nbsp; </li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h3><img src="http://alainna.org/orcid/clip_image033.jpg" alt="" width="288" height="177" align="right" hspace="12" vspace="12" /><a name="h.uzsp2l9oif0z" id="h.uzsp2l9oif0z"></a>6.1.1 Get an Authorization Code</h3>
<p>To get an Authorization  Code, you&rsquo;ll need to prompt the user to log into his/her ORCID account and  grant permission to your application. In a real-world situation, this is done  using an authorization URL that you construct. With the OAuth Playground, however,  this step is done by configuring some additional settings and clicking a  button.</p>
<ol>
  <li>Beneath <strong>Step 1:  Select &amp; authorize APIs</strong> on the left side of the screen, type <strong>/activities/update</strong> in the text box (do  not select any of the options in the box above).<br />&nbsp; </li>
  <li>Click <strong>Authorize  APIs</strong>.<br />&nbsp; </li>
  <li><img src="http://alainna.org/orcid/clip_image035.gif" alt="" width="315" height="136" align="right" hspace="12" vspace="12" />An ORCID OAuth  login screen will appear. Click <strong>Sign In</strong> and sign into your Sandbox account.<br />&nbsp; </li>
  <li>Click <strong>Authorize </strong>on  the ORCID OAuth login screen and you will be sent back to the OAuth Playground.  A 6-character code will appear in the <strong>Authorization  Code </strong>field.<br />&nbsp; </li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h3><a name="6.1.2"></a>6.1.2  Exchange the Authorization Code for an Access Token</h3>
<p>Once you have an  Authorization Code, you can exchange it for an Access Token, which allows you  to read from/write to a user&rsquo;s ORCID record. In a real-world situation, this  exchange would be done by your system, using a programming language such as  PHP, Java, or Ruby on Rails. With the OAuth Playground, however, this step is  done by clicking a button.</p>
<ol>
  <li><img src="http://alainna.org/orcid/clip_image036.gif" alt="" width="336" height="111" align="right" hspace="12" vspace="12" />Beneath the <strong>Authorization Code</strong> field, click <strong>Exchange authorization code for tokens</strong>. <br />&nbsp; </li>
  <li>The token will appear in the <strong>Access Token </strong>field.<br />&nbsp; </li>
  <li>Note that you are provided with additional information  in the <strong>Request/Response </strong>section on  the right side of the screen, such as the name and ORCID iD of the user who  granted permission, the lifespan of the token (20 years), and the scope for  which the token is valid.</li>
<p><img src="http://alainna.org/orcid/clip_image038.jpg" alt="" width="340" height="103" border="0" /></p>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h1><a name="7"></a>7. Member  API: Writing to ORCID records via the API</h1>
<h2><a name="7.1"></a>7.1 Adding a  New Work to an ORCID Record</h2>
<ol>
  <li>Beneath <strong>Step 3:  Configure request to API</strong>, set <strong>HTTP  Method </strong>to <strong>POST</strong>.<br />&nbsp; </li>
  <li>Click <strong>Add  headers</strong> and enter the following values:</li>
  <ul>
    <li><strong>Header name:</strong> accept</li>
    <li><strong>Header value:</strong> application/vnd.orcid+xml<br />
    </li>
  </ul>
<p><img src="http://alainna.org/orcid/clip_image040.jpg" alt="" width="464" height="119" border="0" /></p>
  <li>Click <strong>Add</strong> to  add another header and enter the following values:</li>
  <ul>
    <li><strong>Header name:</strong> Content-type</li>
    <li><strong>Header value:</strong> application/vnd.orcid+xml<br />&nbsp; </li>
  </ul>
  <li>Click <strong>Add</strong> again, then click <strong>Close</strong>.<br />&nbsp; </li>
  <li>In the <strong>Request  URI</strong> field, enter https://api.qa.orcid.org/v1.2/[orcid-id]/orcid-works,  replacing [orcid-id] with the ORCID iD of the Sandbox record that you created earlier  (ex: https://api.qa.orcid.org/v1.2/0000-0002-3791-8427/orcid-works)<br />
    <br />
    <img src="http://alainna.org/orcid/clip_image042.jpg" alt="" width="392" height="232" border="0" /><br />&nbsp; </li>
  <li>Click <strong>Enter  request body</strong>. Here is where you&rsquo;ll enter the XML for the works you wish to  add.<br />&nbsp; </li>
  <li>Visit <a href="http://git.io/vITI9" target="_blank">http://git.io/vITI9</a> and copy the XML in the <strong>Sample Work </strong>section.<br />&nbsp; </li>
  <li>Paste the copied content into the <strong>Request Body </strong>text box and click <strong>Close</strong>.<br />
    <br />
    <img src="http://alainna.org/orcid/clip_image044.jpg" alt="" width="498" height="275" border="0" /></li><Br />&nbsp;
  <li>Click <strong>Send the  request</strong>.<br />&nbsp; </li>
  <li>The  results will appear in the <strong>Request/Response </strong>section on the right side of the screen. Scroll to the bottom – if you see <strong>HTTP/1.1 201 Created</strong>, the work was  successfully posted!<br />&nbsp; 
    <img src="http://alainna.org/orcid/clip_image046.jpg" alt="" width="483" height="224" border="0" /><br />&nbsp; </li>
  <li> Visit the <strong>public  view </strong>of your Sandbox record at http://sandbox.orcid.org/[Your sandbox iD]  to see the work that you added in the user interface.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="7.2"></a>7.2 Updating  a Work</h2>
<p>In the last section, we  asked the user for permission to add a new work to their ORCID record using the  /activities/update scope. To edit that same work, we need to request  permission using the /orcid-works/update scope. </p>
<p> In a real-world situation,  create and update permissions can be requested in the same step, resulting in  an Access Token that can be used to both add and edit works. When using the  OAuth Playground, however, we can only request permission for one scope at a  time, so we&rsquo;ll need to generate a new Access Token in order to edit the work  that we just added.</p>
<ol>
  <li>Beneath <strong>Step 1:  Select &amp; authorize APIs</strong>, type <strong>/orcid-works/update</strong> in the text box.<br />&nbsp; </li>
  <li>Click <strong>Authorize  APIs</strong>.<br />&nbsp; </li>
  <li>An ORCID OAuth login screen will appear. Click <strong>Sign In</strong>, and sign into your Sandbox  account.<br />&nbsp; </li>
  <li>Click <strong>Authorize </strong>on  the ORCID OAuth login screen and you will be sent back to the OAuth Playground.  A 6-character code will appear in the <strong>Authorization  Code </strong>field.<br />&nbsp; 
  </li>
  <li>Beneath the Authorization Code field, click <strong>Exchange authorization code for tokens</strong>.<br />&nbsp; </li>
  <li>The token will appear in the <strong>Access Token </strong>field.<br />&nbsp; </li>
  <li>Beneath <strong>Step 3:  Configure request to API</strong>, set <strong>HTTP  Method </strong>to <strong>PUT</strong>.<br />&nbsp; </li>
  <li>Click <strong>Add  headers</strong> and enter the following values:</li>
  <ul>
    <li><strong>Header name:</strong> Accept</li>
    <li><strong>Header value:</strong> application/vnd.orcid+xml<br />&nbsp; </li>
  </ul>
  <li>Click <strong>Add</strong> to  add another header and enter the following values:</li>
  <ul>
    <li><strong>Header name:</strong> Content-type</li>
    <li><strong>Header value:</strong> application/vnd.orcid+xml<br />&nbsp; </li>
  </ul>
  <li>Click <strong>Add</strong> again, then click <strong>Close</strong>.<br />&nbsp; </li>
  <li>In  the <strong>Request URI </strong>field, enter  https://api.qa.orcid.org/v1.2/[orcid-id]/orcid-works, replacing [orcid-id]  with the ORCID iD of your Sandbox record (ex:  https://api.qa.orcid.org/v1.2/0000-0002-1223-3173/orcid-works). <br />&nbsp; 
  </li>
  <li>Click <strong>Enter request body</strong>. This is where you&rsquo;ll  enter the XML for the work that you wish to edit.<br />&nbsp; </li>
  <li>Visit <a href="http://git.io/vITI9" target="_blank">http://git.io/vITI9</a> and copy the XML in the <strong>Sample Work  Updated </strong>section.<br />&nbsp; 
  </li>
  <li>Paste  the copied content into the <strong>Request Body</strong> field and click <strong>Close</strong>.<br />&nbsp; 
  </li>
  <li>Click <strong>Send the Request</strong>.<br />&nbsp; 
  </li>
  <li>The  results will appear in the <strong>Request/Response </strong>section on the right side of the screen. If the full XML of the user&rsquo;s  record appears, the work was successfully updated!<br />If you receive an error, be sure to check that the headers value under <b>Add headers</b> have not been changed to garbled text, e.g. "application%2Fvnd.orcid%2Bxml".<br />&nbsp; 
  </li>
  <li>Visit  the public view of your Sandbox record at http://sandbox.orcid.org/[Your  sandbox iD] to see the changes to the work in the user interface.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h1><a name="8"></a>8. BONUS: Member API: Creating New Records</h1>
<p>Organizations are often  interested in creating ORCID records on behalf of their faculty, staff, or  students. The ORCID API supports this through a create on demand process that  allows users to create a new record at any time, and to grant your system  read/write access to their record (via the API). Users who already have an  ORCID iD can use the same process to send their existing iD to your system and  grant your system read/write access.</p>
<p> See a demo of this process  at: <a href="https://orcid-createondemand.herokuapp.com/" target="_blank">https://orcid-createondemand.herokuapp.com</a></p>
<p>  In this section, we&rsquo;ll walk  through the basic steps to implement a create on demand process. For more  information, see <a href="https://members.orcid.org/create-records">https://members.orcid.org/create-records</a></p>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="8.1"></a>8.1  Construct the Authorization URL</h2>
<p>The create on demand  process begins with a special authorization URL that you construct. The URL includes your ORCID API client credentials and information about any read/write  permissions that you&rsquo;d like to request from the user.</p>
<h3><a name="8.1.1"></a>8.1.1 Base  URL</h3>
<p>Your authorization URL  begins with one of the following addresses, depending on the environment that  you&rsquo;re using.</p>
  <table border="1" cellspacing="0" cellpadding="0" width="613">
    <tr>
      <td width="158" valign="top"><p><strong>Sandbox API</strong></p></td>
      <td width="455" valign="top"><p> https://qa.orcid.org/oauth/authorize?</p></td>
    </tr>
    <tr>
      <td width="158" valign="top"><p><strong>Production API</strong></p></td>
      <td width="455" valign="top"><p>https://orcid.org/oauth/authorize?</p></td>
    </tr>
  </table>
<ol>
  <li>Open a text editor and copy/paste or type the base URL  into a new document. For this tutorial, we&rsquo;re using the Sandbox API, so our  base URL is:</li>
<p><strong>https://qa.orcid.org/oauth/authorize?</strong></p>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h3><a name="8.1.2"></a>8.1.2  Required Parameters</h3>
<p>After the base URL, we need  to include some additional bits of information – called &ldquo;parameters&rdquo; – that  identify your client app to the ORCID API and tell the API what permissions  you&rsquo;d like to request from the user. Each parameter is separated by an &amp;  character.</p>
  <table border="1" cellspacing="0" cellpadding="0" width="611">
    <tr>
      <td width="158" valign="top"><strong>client_id</strong></td>
      <td width="453" valign="top"><p>Your Member API client ID    (ex: APP-VZTMFLZVBD5NSJQA)</p></td>
    </tr>
    <tr>
      <td width="158" valign="top"><p><strong>scope</strong></p></td>
      <td width="453" valign="top"><p>The read/write    permission(s) you wish to request from the user, from the <strong><a href="https://members.orcid.org/api/orcid-scopes" target="_blank">ORCID Scopes list</a></strong>   </p>
        <p> If including multiple permissions, separate them with an HTML-encoded space (%20), ex:  /activities/update%20/read-limited</p>
        <p> <em>At minimum, /authenticate needs to be    included, which allows you to obtain the user&rsquo;s ORCID iD.</em></p></td>
    </tr>
    <tr>
      <td width="158" valign="top"><p><strong>response_type</strong></p></td>
      <td width="453" valign="top"><p>code </p></td>
    </tr>
    <tr>
      <td width="158" valign="top"><p><strong>redirect_uri</strong></p></td>
      <td width="453" valign="top"><p>The page on your site that the user should be sent to when the    authorization is complete, ex: http://yoursite/somepage.html<br />
        <em>This URL must be registered as part of    your API credential registration. </em><br />
        For this boot camp, use: <a href="https://developers.google.com/oauthplayground/" target="_blank">https://developers.google.com/oauthplayground/</a></p></td>
    </tr>
  </table>
<ol>
  <li>In your text editor, add the required parameters to  your base URL, as in the example below. Make sure to replace the Client ID with  your assigned Client ID!</li>
<p><strong>https://qa.orcid.org/oauth/authorize?<br />
  client_id=APP-VZTMFLZVBD5NSJQA&amp;<br />
  scope=/activities/update%20/read-limited&amp;<br />
  response_type=code&amp;<br />
  redirect_uri=https://developers.google.com/oauthplayground</strong></p>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h3><a name="8.1.3"></a>8.1.3  Optional Parameters</h3>
<p>In addition to the required  parameters, you can add any of the optional parameters below to customize the  ORCID authorization screen and pre-fill the registration form with information  from your system.</p>
<table border="1" cellspacing="0" cellpadding="0" width="624">
  <tr>
    <td width="107" valign="top"><br />
      <strong>state</strong></td>
    <td width="517" valign="top"><p>A random value used as a security tactic to prevent Cross-Site    Request Forgery (CSRF).</p>
    <p> <em>When ORCID sends the user back to your    redirect_uri, the state value will be included in the response.</em> </p>
    <p><a href="http://www.twobotechnologies.com/blog/2014/02/importance-of-state-in-oauth2.html">More about using the state parameter    to prevent CSRF</a>.</p></td>
  </tr>
  <tr>
    <td width="107" valign="top"><p><strong>family_names</strong></p></td>
    <td width="517" valign="top"><p>The user's family (last)    name, used to pre-fill the registration form.</p></td>
  </tr>
  <tr>
    <td width="107" valign="top"><p><strong>given_names</strong></p></td>
    <td width="517" valign="top"><p>The user's given    (first)  name, used to pre-fill the    registration form.</p></td>
  </tr>
  <tr>
    <td width="107" valign="top"><p><strong>email</strong></p></td>
    <td width="517" valign="top"><p>The researcher's email    address, used to pre-fill the sign-in or registration form. </p></td>
  </tr>
  <tr>
    <td width="107" valign="top"><p><strong>lang</strong></p></td>
    <td width="517" valign="top"><p>The language to display    the authorization page in, as a 2-letter <a href="http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes" target="_blank">ISO 639-1 code</a>.</p></td>
  </tr>
  <tr>
    <td width="107" valign="top"><p><strong>show_login</strong></p></td>
    <td width="517" valign="top"><p>Forces the login form to    display by default, set to true or false.</p></td>
  </tr>
</table>
<ol>
  <li><img width="195" height="119" src="http://alainna.org/orcid/clip_image047.gif" align="right" hspace="12" vspace="5" alt="Text Box: IMPORTANT!." />In your text editor, add some  optional parameters to pre-fill the registration form. Your final authorization  URL should like something like:</li>
<p><strong>https://qa.orcid.org/oauth/authorize?<br />
  client_id=APP-VZTMFLZVBD5NSJQA&amp;<br />
  scope=/activities/update%20/read-limited&amp;<br />
  response_type=code&amp;<br />
  redirect_uri=https://developers.google.com/oauthplayground&amp;<br />
  family_names=Orcidson&amp;<br />
  given_names=Orc&amp;<br />
  email=orcidson@mailinator.com</strong></p>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="8.2"></a>8.2 Build a Redirect Page/Application</h2>
<p>After clicking your  authorization URL and completing the ORCID registration or sign-in process,  users are sent to the page that you specified in the redirect_uri parameter. </p>
<p> When a user is sent to this  page, the ORCID API attaches an Authorization Code to the end of the URL for  the page. As we saw in the previous sections of this tutorial, an Authorization  Code can be exchanged for a user&rsquo;s ORCID iD and (optionally) an Access Token. </p>
<p> In this tutorial, we&rsquo;ve  been relying on the OAuth Playground to perform the authorization code  exchange. In a live application, this is done by your system via your specified  redirect page.</p>
<p> This step requires some  programming expertise, so you may need to enlist the help of a web developer. A  variety of languages can be used – code can be executed right in the redirect  page, or the redirect page can connect to an application living on your server.</p>
<p> Regardless of the language,  your redirect page (or any server application it connects to) needs to:</p>
<ol>
  <li>Capture  the <strong>Authorization Code</strong>.</li>
  <li>Exchange  the Authorization Code for an <strong>Access Token</strong>.</li>
  <li><strong>Store  </strong>the Access Token and ORCID iD  (e.g. in a database) for use in future use.</li>
</ol>
<p>See an example in PHP at: <a href="https://github.com/lizkrznarich/orcid-demo-app" target="_blank">https://github.com/lizkrznarich/orcid-demo-app</a></p>
<p>  For more examples  contributed by ORCID members, see: <a href="https://members.orcid.org/api/code-examples" target="_blank">https://members.orcid.org/api/code-examples</a></p>
<p><strong><em>Note:</strong> If you simply want to promote ORCID  creation, but don&rsquo;t need to collect users&rsquo; ORCID iDs or Access Tokens, you can  create a static HTML redirect page that does not perform an authorization code  exchange.</em></p>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="8.3"></a>8.3 Prompt  Users to Create or Connect their ORCID iD</h2>
<p>Once you&rsquo;ve created an  authorization URL and a redirect page, the next step is to prompt users to  click the authorization URL. To do this, you can:</p>
<ol>
  <li>Send each user an email with the authorization URL.
  <p> <em>URLs can easily be customized with  family_name, given_name, and email parameters using the mailmerge feature available  in many email programs.</em></p></li>
  <li>Create a page on your site with the authorization URL  included as a button or a link.
  <p>For this tutorial, simply  copy the link and paste it into your browser&rsquo;s address bar and press  Return/Enter.</p></li>
  <li>If you&rsquo;ve signed out of your Sandbox account since the  prior exercises, you should see the ORCID registration form with the name and  email address pre-filled – to finish creating your new sandbox account:</li>
  <ol>
    <li>Enter a <strong>password</strong> (twice).</li>
    <li>Click the checkbox beside <strong>I consent to the privacy policy…</strong></li>
    <li>Click <strong>Authorize</strong>.<br  />&nbsp;</li>
</ol>
  <li>You&rsquo;ll be sent to the  redirect URI (Google OAuth Playground), and you&rsquo;ll see the 6-character  <strong>Authorization Code</strong> in your browser&rsquo;s address bar. A confirmation email will also have also  been sent to the address that you specified in the registration form.<br />
    <br />
  <img src="http://alainna.org/orcid/clip_image049.jpg" alt="" width="410" height="81" border="0" /><br />&nbsp;</li>
  <li>Leave the OAuth Playground window open for the next  steps, but don&rsquo;t exchange the Authorization Code yet.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="8.4"></a>8.4 Obtain  Access Tokens and ORCID iDs</h2>
<p>In a live application, this  step would be completed via your redirect page, as discussed above. For this  tutorial, we&rsquo;ll continue to use the OAuth Playground.</p>
<p> Before we continue with the  Authorization Code exchange, we first need to make sure that the OAuth  Playground is still configured correctly.</p>
<ol>
  <li>Click the gear icon in the upper right corner to open  the configuration form.</li>
<p><img src="http://alainna.org/orcid/clip_image050.jpg" alt="" width="530" height="60" border="0" /></p>
  <li>In the configuration form, verify that the following  settings (which are the same as those used in sections 4.6 and 4.7) remain.  Re-enter any that are not set.<br  />&nbsp;</li>
  <table border="1" cellspacing="0" cellpadding="0" width="570">
    <tr>
      <td width="158" valign="top"><p><strong>OAuth flow</strong></p></td>
      <td width="412" valign="top"><p>Server-side</p></td>
    </tr>
    <tr>
      <td width="158" valign="top"><p><strong>OAuth endpoints</strong></p></td>
      <td width="412" valign="top"><p>Custom</p></td>
    </tr>
    <tr>
      <td width="158" valign="top"><p><strong>Authorization endpoint</strong></p></td>
      <td width="412" valign="top"><p>https://qa.orcid.org/oauth/authorize</p></td>
    </tr>
    <tr>
      <td width="158" valign="top"><p><strong>Token endpoint</strong></p></td>
      <td width="412" valign="top"><p>https://qa.orcid.org/oauth/token</p></td>
    </tr>
    <tr>
      <td width="158" valign="top"><p><strong>Access token location</strong></p></td>
      <td width="412" valign="top"><p>Authorization header w/Bearer prefix</p></td>
    </tr>
    <tr>
      <td width="158" valign="top"><p><strong>OAuth Client ID</strong></p></td>
      <td width="412" valign="top"><p>Your Member API client ID (ex: APP-VZTMFLZVBD5NSJQA)</p></td>
    </tr>
    <tr>
      <td width="158" valign="top"><p><strong>OAuth Client Secret</strong></p></td>
      <td width="412" valign="top"><p>Your Member API client secret (ex: 448101b3-1618-4841-8c4f-b04ab9edac92)</p></td>
    </tr>
  </table><br />&nbsp;
  <li>Click <strong>Close</strong> in the lower left corner of the configuration screen.<br  />&nbsp;</li>
  <li>Beneath the <strong>Authorization  Code</strong> field, click <strong>Exchange  authorization code for tokens</strong>.<br />&nbsp;</li>
  <li>The token will appear in the Access Token field and in  the <strong>Request/Response </strong>section on the  right side of the screen. The Request/Response section also includes the user&rsquo;s  name and ORCID iD, and the scope(s) for which token is valid. In your live app,  these are the pieces of information that your system should store.  </li>
<p><img src="http://alainna.org/orcid/clip_image052.jpg" alt="" width="624" height="317" border="0" /></p>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="8.5"></a>8.5 Read  from/Write to Users&rsquo; ORCID Records</h2>
<p>Once you have the user&rsquo;s  ORCID iD and Access Token, it can be used to make API calls that read  from/write to the user&rsquo;s ORCID record per the permissions requested, as we did  earlier in this tutorial.</p>
<p> Access Tokens are valid for 20 years by default. They can be used immediately  or at any point in the future.</p>
<p> For example, you can:</p>
<ul>
  <li>Read information from the user&rsquo;s ORCID record and copy  it into your system.<br />&nbsp;</li>
  <li>Add information from your system to the user&rsquo;s ORCID  record – affiliations, works, etc.<br />&nbsp;</li>
  <li>Update the user&rsquo;s ORCID record when new information is  available in your system.<br />&nbsp;</li>
  <li>Update your system when new information is added to the  user&rsquo;s ORCID record.<br />&nbsp;</li>
</ul>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h1><a name="9"></a>9. ORCID API Resources</h1>
<ul>
  <li>See example implementations and workflow guides <a href="https://members.orcid.org" target="_blank">https://members.orcid.org</a><br />&nbsp;</li>
  <li>Read technical documentation <a href="https://members.orcid.org/api" target="_blank">https://members.orcid.org/api</a><br />&nbsp;</li>
  <li>Join the ORCID API Users Group <a href="https://groups.google.com/group/orcid-api-users" target="_parent">https://groups.google.com/group/orcid-api-users</a><br />&nbsp;</li>
  <li>Sign up for a Technical Webinar <a href="https://members.orcid.org/event-list">https://members.orcid.org/event-list</a><br />&nbsp;</li>
  <li>Email ORCID Support <a href="mailto:support@orcid.org">support@orcid.org</a></li>
</ul>
