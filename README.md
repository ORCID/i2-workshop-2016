[//]: # (This document was created for the i2 TechEx Workshop on Sep 25, 2106 in Miami, Fl)

# i2-workshop-2016
### Internet 2 Tech Exchange, Sept 2016
## Hands on with the ORCID API: <br />Getting Authenticated ORCID iDs & Permissions Through Your IdP


_[see the full agenda](http://meetings.internet2.edu/2016-technology-exchange/detail/10004303/)_

_In February 2016, ORCID enabled IdP SSO for all eduGAIN member institutions, allowing the first direct connection between the systems. More recently, ORCID introduced a process that enables IdPs to request authenticated ORCID iDs and user permissions to access their ORCID record, using a process that requires little programming or custom code for institutions. In this hands-on tutorial each participant will set up such a connection in the ORCID test sandbox site (https://sandbox.orcid.org/signin)._

[//]: # (---------AGENDA---------)
<a name="top"></a>
##Workshop Agenda (4 hrs)
###[PRESENTATION](#1-what-is-orcid): WHAT IS ORCID? (30 min)
Learn about ORCID and ORCID iDs and how they work. Understand how organizations are using the ORCID registry to collect and display ORCID iDs, and connect and sync information between ORCID records and their own system.

###[ACTIVITY](#2-explore-registry): EXPLORE THE ORCID REGISTRY (20 min)
Set up an ORCID iD in our test environment, and explore signing in with your IdP. Understand ORCID’s provenance model and its implications. Learn about the components of an ORCID record, how they get populated, and how they get used.

###[PRESENTATION](#3-about-orcid-apis): ABOUT THE ORCID APIs (30 min)
Discover ORCID API types and features, and understand ORCID’s test environment and the technologies that ORCID uses.

###[ACTIVITY](#4-oauth-basics): OAUTH BASICS (30 min)
ORCID’s API uses OAuth 2.0 as its protocol for a system client to obtain user permission to access the information stored in his/her ORCID record. In this section you will obtain system client credentials, and execute basic commands to request permission using a basic OAuth 2.0 3-legged flow. (Don’t know what that is? don’t worry! It will be covered in the session.)

###[PRESENTATION](#5-cross-link-breakdown): THE CROSS-LINK BREAKDOWN (15 min)
Breakdown of the functionality that we are about setup.

###[ACTIVITY](#6-api-credentials): API CREDENTIAL SETUP (30 min)
Set up ORCID Member API credentials to enable IdP cross linking. We will try it out, using Google OAuth playground to simulate the IdP website.

###[ACTIVITY](#7-user-experience): THE USER EXPERIENCE (30 min)
The technical connection is only part of the overall solution. What should you display to users when they authorize your system to connect with their ORCID records? What you should tell them if they deny your request? Using an ORCID template as a starting point, workshop participants will work together to craft messages and customize templates that will resonate with their audiences.

###[ACTIVITY](#8-post-affiliation): POST AN AFFILIATION TO YOUR UNIVERSITY (50 min)
Format data about the person’s relationship to your institution and post it to his/her ORCID record. Update the data that you’ve already posted to simulate updating data when an affiliation relationship changes.

###[REFERENCE MATERIALS](#9-reference)

--

[//]: # (---------WHAT IS ORCID?---------)
<a name="1-what-is-orcid"></a>
#WHAT IS ORCID? (30 min) 
_PRESENTATION_ 

[Presented as a power point presentation](https://www.dropbox.com/s/t96571yrgygjzuu/20160925_TechExWorkshop-Paglione.pptx?dl=0)
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------EXPLORE THE ORCID REGISTRY---------)
<a name="2-explore-registry"></a>
#EXPLORE THE ORCID REGISTRY (20 min)
_ACTIVITY_

**TO BE WRITTEN**: _Set up an ORCID iD in our test environment, and explore signing in with your IdP. Understand ORCID’s provenance model and its implications. Learn about the components of an ORCID record, how they get populated, and how they get used._
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------ABOUT THE ORCID APIs---------)
<a name="3-about-orcid-apis"></a>
#ABOUT THE ORCID APIs (30 min)
_PRESENTATION_

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

[//]: # (---------OAUTH BASICS---------)
<a name="4-oauth-basics"></a>
#OAUTH BASICS (30 min)
_ACTIVITY_

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


[//]: # (---------THE CROSS-LINK BREAKDOWN---------)
<a name="5-cross-link-breakdown"></a>
#THE CROSS-LINK BREAKDOWN (15 min)
_PRESENTATION_

**TO BE WRITTEN**: _As described in the agenda: Breakdown of the functionality that we are about setup. Suggest this be a power point slide that shows the flow._
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------API CREDENTIAL SETUP---------)
<a name="6-api-credentials"></a>
#API CREDENTIAL SETUP (30 min)
_ACTIVITY_

**TO BE WRITTEN**: _As described in the agenda: Set up ORCID Member API credentials to enable IdP cross linking. We will try it out, using Google OAuth playground to simulate the IdP website._

Originally I had thought that we'd have an interface for requesting credentials, setting up the pemissions one wants along with the redirect URI. I was then thinking that we could have them set up the redirect URI to execute the OAuth statements using their credentials, and then displaying the ORCID iD obtained on the page. i.e., they would have put in their credentials, and the pre-set code would display the ORCID iD. We just show them the token statement that converts the code into the ORCID iD. It woudl be great to have an alternate suggestion on how to handle this based on what we can do right now.

<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------THE USER EXPERIENCE---------)
<a name="7-user-experience"></a>
#THE USER EXPERIENCE (30 min)
_ACTIVITY_

**TO BE WRITTEN**: _As described in the agenda: The technical connection is only part of the overall solution. What should you display to users when they authorize your system to connect with their ORCID records? What you should tell them if they deny your request? Using an ORCID template as a starting point, workshop participants will work together to craft messages and customize templates that will resonate with their audiences._

Originally I envisioned we'd take what was done in the step above, and have them edit HTML pages to fill in the text of a simple accept and a simple deny display page (i.e., they just write the body text - keeping these as stand-alone files that they could edit themselves and upload so that they could see the result when going through the IdP round trip flow. the emphasis would be on the content of the page, not the technology.)

Suggestions for discussion topics
* Demo application
* Discussion about the two screens that they would write - when granted and denied permission - what should they say. 
* Imagry
* Inclusion of a link back to the registry...

<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------POST AN AFFILIATION TO YOUR UNIVERSITY---------)
<a name="8-post-affiliation"></a>
#POST AN AFFILIATION TO YOUR UNIVERSITY (50 min)
_ACTIVITY_

**TO BE UPDATED**: _Update this text to be specific to posting a university affiliation as part of the IdP Cross Link. From the agenda: Format data about the person’s relationship to your institution and post it to his/her ORCID record. Update the data that you’ve already posted to simulate updating data when an affiliation relationship changes._

Suggestions:
* update the XML to include affiliation specific to their own affiliation
* use the access token to post the XML to their own record
* Review the record - notice the source - explain the user's ability to create a copy with differences.
* If time, review updating the post using the same access token.

<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

<h2><a name="7.1"></a>7.1 Adding a New Work to an ORCID Record</h2>
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


[//]: # (---------POST AN AFFILIATION TO YOUR UNIVERSITY---------)
<a name="8-post-affiliation"></a>
#POST AN AFFILIATION TO YOUR UNIVERSITY (50 min)
_ACTIVITY_


[//]: # (---------REFERENCE MATERIALS---------)
<a name="9-reference"></a>
#REFERENCE MATERIALS

<ul>
<li>See example implementations and workflow guides <a href="https://members.orcid.org" target="_blank">https://members.orcid.org</a><br />&nbsp;</li>
<li>Read technical documentation <a href="https://members.orcid.org/api" target="_blank">https://members.orcid.org/api</a><br />&nbsp;</li>
<li>Join the ORCID API Users Group <a href="https://groups.google.com/group/orcid-api-users" target="_parent">https://groups.google.com/group/orcid-api-users</a><br />&nbsp;</li>
<li>Sign up for a Technical Webinar <a href="https://members.orcid.org/event-list">https://members.orcid.org/event-list</a><br />&nbsp;</li>
<li>Email ORCID Support <a href="mailto:support@orcid.org">support@orcid.org</a></li>
</ul>
