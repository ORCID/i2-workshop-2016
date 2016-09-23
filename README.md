[//]: # (This document was created for the i2 TechEx Workshop on Sep 25, 2106 in Miami, Fl)

# i2-workshop-2016
### Internet 2 Tech Exchange, Sept 2016
## Hands on with the ORCID API: <br />Getting Authenticated ORCID iDs & Permissions Through Your IdP


_[see the full agenda](http://meetings.internet2.edu/2016-technology-exchange/detail/10004303/)_

_In February 2016, ORCID enabled IdP SSO for all eduGAIN member institutions, allowing the first direct connection between the systems. More recently, ORCID introduced a process that enables IdPs to request authenticated ORCID iDs and user permissions to access their ORCID record, using a process that requires little programming or custom code for institutions. In this hands-on tutorial each participant will set up such a connection in the ORCID test sandbox site (https://sandbox.orcid.org/signin)._

[//]: # (---------AGENDA---------)
<a name="top"></a>
##Workshop Agenda (4 hrs)
###[1. PRESENTATION](#1-what-is-orcid): WHAT IS ORCID? (30 min)
Learn about ORCID and ORCID iDs and how they work. Understand how organizations are using the ORCID registry to collect and display ORCID iDs, and connect and sync information between ORCID records and their own system.

###[2. ACTIVITY](#2-explore-registry): EXPLORE THE ORCID REGISTRY (20 min)
Set up an ORCID iD in our test environment, and explore signing in with your IdP. Understand ORCID’s provenance model and its implications. Learn about the components of an ORCID record, how they get populated, and how they get used.

###[3. PRESENTATION](#3-about-orcid-apis): ABOUT THE ORCID APIs (30 min)
Discover ORCID API types and features, and understand ORCID’s test environment and the technologies that ORCID uses.

###[4. ACTIVITY](#4-oauth-basics): OAUTH BASICS (30 min)
ORCID’s API uses OAuth 2.0 as its protocol for a system client to obtain user permission to access the information stored in his/her ORCID record. In this section you will obtain system client credentials, and execute basic commands to request permission using a basic OAuth 2.0 3-legged flow. (Don’t know what that is? don’t worry! It will be covered in the session.)

###[5. PRESENTATION](#5-cross-link-breakdown): THE CROSS-LINK BREAKDOWN (15 min)
Breakdown of the functionality that we are about setup.

###[6. ACTIVITY](#6-api-credentials): API CREDENTIAL SETUP (30 min)
Set up ORCID Member API credentials to enable IdP cross linking. We will try it out, using Google OAuth playground to simulate the IdP website.

###[7. ACTIVITY](#7-user-experience): THE USER EXPERIENCE (30 min)
The technical connection is only part of the overall solution. What should you display to users when they authorize your system to connect with their ORCID records? What you should tell them if they deny your request? Using an ORCID template as a starting point, workshop participants will work together to craft messages and customize templates that will resonate with their audiences.

###[8. ACTIVITY](#8-post-affiliation): POST AN AFFILIATION TO YOUR UNIVERSITY (50 min)
Format data about the person’s relationship to your institution and post it to his/her ORCID record. Update the data that you’ve already posted to simulate updating data when an affiliation relationship changes.

###[9. REFERENCE MATERIALS](#9-reference)

--

[//]: # (---------WHAT IS ORCID?---------)
<a name="1-what-is-orcid"></a>
#1. WHAT IS ORCID? (30 min) 
_PRESENTATION_ 

[Presented as a power point presentation](https://www.dropbox.com/s/t96571yrgygjzuu/20160925_TechExWorkshop-Paglione.pptx?dl=0)
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------EXPLORE THE ORCID REGISTRY---------)
<a name="2-explore-registry"></a>
#2. EXPLORE THE ORCID REGISTRY (20 min)
_ACTIVITY_

<h2><img width="194" height="336" src="http://alainna.org/orcid/clip_image002.gif" align="right" hspace="12" vspace="12" alt="Screen Shot: ORCID registration screen at https://sandbox.orcid.org/register" /><a name="2.1"></a>2.1 Create an ORCID iD</h2>
<p>In order to try out API calls, such as a reading a record and adding information to it, you will also  need to create a test ORCID record. This can be done through the  user interface, much like in the live ORCID registry.</p>
<ol>
  <li>Open a web browser and navigate to <a href="https://sandbox.orcid.org/signin" target="_blank">https://sandbox.orcid.org/signin</a><br />&nbsp;</li>
  <li>Click <strong>Register for an ORCID iD</strong>.<br />&nbsp;</li>
  <li>Complete the form with a name, email, and password. You will need to remember this information for future steps.</li>
<p><strong><em>IMPORTANT! </em></strong><em>Don&rsquo;t use a real email address! Instead, make up an address  ending in @mailinator.com (use any prefix, e.g. sgarcia@mailinator.com).</em></p>
  <li>Click the <strong>I consent…</strong> checkbox and click <strong>Register</strong>.<br />&nbsp;</li>
  <li>After completing the registration process, you will be  taken to your new testing ORCID record. Make note of the 16-digit ORCID iD for this record – you will need this in order to make API calls later during the workshop.<br />
    <img src="http://alainna.org/orcid/clip_image004.jpg" alt="Screen Shot: Top section of the my-orcid page, showing the ORCID iD in the left column under the name at https://sandbox.orcid.org/my-orcid" width="645" height="107" border="0" /><br />&nbsp;</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

<h2><a name="2.2"></a>2.2 Explore the ORCID record</h2>
<p>In this section we will learn about the parts of an ORCID record, and explore ORCID's provenance model.</p>
<ol>
  <li>Using the interface, add a sentence or two to serve as the biography for your test record. The biography section is located at the top of the right column, and the edit button is the pencil icon in the upper right corner of this section, next to the visibility selector.<br />&nbsp;</li>
  <li>In the <strong>Employment</strong> section, click <strong>Add employment</strong> > <strong>Add manually</strong> to add employment information.<br />&nbsp;</li>
  <li>After saving your employment information, notice the information on the bottom of the "card" you just created. There is a Source field (that matches your name because you added this information) and the date that you created this addition to your record. This provenance information is recorded for all infomration added to an ORCID record.<br />&nbsp;</li>
  <li>In the main menu at the top of the screen, click on the <strong>Account settings</strong> link to display your account preferences. Notice each section to see what iD holders can control with their ORCID accounts.<br />&nbsp;</li>
  <li>In the main menu at the top of the screen, click on the <strong>Developer tools</strong> link. In this section a user may obtain credentials to access the public API. Note that this API is different from the member API that we will be discussing today.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

<h2><a name="2.3"></a>2.3 Connect your new iD with your IdP</h2>
<p>Since there are over 2.5 million ORCID iDs, many people already have an ORCID iD when they link to their IdP. To experience this proces, we will sign out of your test record and start from the prospective of someone who has an iD, and notices that they can sign in with IdP credentials.</p>
<ol>
  <li>Sign out of the ORCID record you just created by clicking the <strong>Sign out</strong> button in the upper right corner. <em>Alternatively, you can navigate to the URL: <a href="https://sandbox.orcid.org/signout" target="_blank">https://sandbox.orcid.org/signout</a>.</em><br />&nbsp;</li>
  <li>On the Sign in page (<a href="https://sandbox.orcid.org/signin" target="_blank">https://sandbox.orcid.org/signin</a>), choose <strong>Sign in using your Institutional Account</strong> to see the list of supported eduGAIN institutions.<br />&nbsp;</li>
  <li>Enter your organization's name in the box, or choose to pick it from the list. If you do not have credentials at an eduGAIN-included institution, you may use <strong>United ID</strong> for this example. <em>(you will need 2-factor authentication to use United ID.)</em><br />&nbsp;</li>
  <li>After signing into your institution, you will be asked to finish linking the accounts by providing your ORICD sign in credentials. Type in the email address / ORCID iD and Password that you created in the previous step. Click <strong>Sign into ORCID</strong> to finish linking your accounts.<br />&nbsp;</li>
  <li>On the my-orcid page that appears, notice an orange alert box confirming that the accounts are linked, and suggesting that you connect to the university's account. This is an example, of the cross linking that we will be exploring further today. We will ignore this message for now.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------ABOUT THE ORCID APIs---------)
<a name="3-about-orcid-apis"></a>
#3. ABOUT THE ORCID APIs (30 min)
_PRESENTATION_

<h2><a name="3.1"></a>3.1 ORCID API types &amp; features</h2>
<p>ORCID offers several APIs (Application Programming Interfaces) that allow your systems to connect to the  ORCID registry, including reading from and writing to ORCID records. Some API  functions are freely available to anyone; others are available to organizations  that financially support ORCID with an annual membership subscription.</p>
<table border="1" cellspacing="0" cellpadding="0" width="680">
<tr>
  <td width="95" valign="top"><br />
    <strong>API Version</strong></td>
  <td width="200" valign="top"><p><strong>Access</strong></p></td>
  <td width="385" valign="top"><p><strong>Features</strong></p></td>
</tr>
<tr>
  <td width="95" valign="top"><p>Public API</p></td>
  <td width="200" valign="top"><p>Freely available to anyone</p></td>
  <td width="385" valign="top"><p><strong>Authenticate:</strong> Obtain a user&rsquo;s authenticated ORCID iD<br />
    <strong>Read (Public)</strong>:<strong> </strong>Search/retrieve public data<br />
    <strong>Create:</strong> Create new ORCID records on demand</p>
</td>
</tr>
<tr>
  <td width="95" valign="top"><p>Member API</p></td>
  <td width="200" valign="top"><p>Available to organizations that support ORCID with an annual membership subscription<br /><i>Sandbox Member API freely available to all for testing</i></p></td>
  <td width="385" valign="top"><p><strong>Read (Limited)</strong>: Search/retrieve limited-access data<br />
    <strong>Add</strong>: Post new items to a record (affiliations, works, etc.)<br />
    <strong>Update</strong>: Edit or delete items you previously added</p></td>
</tr>
</table>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="3.2"></a>3.2 Sandbox test environment</h2>
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
<h2><a name="3.3"></a>3.3 ORCID  API technologies</h2>
<p>All of the ORCID APIs are  based on the same set of technologies:</p>
<ol>
<li><strong>REST: </strong>ORCID APIs are &ldquo;RESTful&rdquo;, which  means that they use HTTP (hyper-text transfer) calls to transfer information.<br />&nbsp;</li>
<li><strong>OAuth:</strong> ORCID  APIs use the OAuth 2.0 authentication protocol in order to grant client  applications access to users&rsquo; ORCID records.<br />&nbsp;</li>
<li><strong>XML/JSON:</strong> ORCID APIs support data exchange in either XML or JSON format.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="3.4"></a>3.4 ORCID  API Tools</h2>
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
<p>For this workshop, we will  be using the online tool <a href="https://developers.google.com/oauthplayground/">Google OAuth Playground</a>.</p>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------OAUTH BASICS---------)
<a name="4-oauth-basics"></a>
#4. OAUTH BASICS (30 min)
_ACTIVITY_

<p>As discussed in [section 3.1](#3.1), the Public API can only be used to read and search ORCID records, and to  get authenticated ORCID iDs. The Member API, however, can be used to add new  information to ORCID records, as well as to update information previously added. To do these actions, one must obtain permission from the user/data subject. This section describes the standard OAuth process for requesting this permission.</p>
<h2><a name="4.1"></a>4.1  Accessing the Sandbox Member API</h2>
<p>Client credentials consisting of a client ID and a client secret are needed in order to access the Member API. Client Credentials for the Member APIs are issued by ORCID. For this workshop, you can use the sample Sandbox Client Credentials, but we recommend that you obtain your own Member API Sandbox Client Credentials using the request form at <a href="https://orcid.org/content/register-client-application" target="_blank">https://orcid.org/content/register-client-application</a> for experimintation and testing that you do outside of this workshop.</p>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

<h2><a name="4.2"></a>4.2 Setting up the OAuth Playground</h2>
<p>We&rsquo;ll use the Google Developers&rsquo; OAuth Playground for the next exercises. To get started, we will need to configure the environment to work with the ORCID Member API.</p>
<ol>
<li>Visit <a href="https://developers.google.com/oauthplayground" target="_blank">https://developers.google.com/oauthplayground</a><br />&nbsp; </li>
<li>Click the gear icon in the upper right corner to open the configuration form.<br />&nbsp; </li>
<p><img src="http://alainna.org/orcid/clip_image030.jpg" alt="Screen shot: Top of the screen at the Google OAuth plaground site, showing the gear icon in the upper right corner at https://developers.google.com/oauthplayground" width="530" height="60" border="0" /></p>
<li>Enter the following:
<table border="1" cellspacing="0" cellpadding="0">
<tr>
  <td width="158" valign="top"><p><strong>OAuth flow</strong></p></td>
  <td valign="top"><p>Server-side</p></td>
  <td width="275" rowspan="7"><img src="http://alainna.org/orcid/clip_image031.jpg" alt="Screen shot: The Google OAuth plaground configuration form expanded at https://developers.google.com/oauthplayground" width="275" height="291" /></td>
</tr>
<tr>
  <td valign="top"><p><strong>OAuth endpoints</strong></p></td>
  <td valign="top"><p>Custom</p></td>
</tr>
<tr>
  <td valign="top"><p><strong>Authorization endpoint</strong></p></td>
  <td valign="top"><p>https://qa.orcid.org/oauth/authorize</p></td>
</tr>
<tr>
  <td valign="top"><p><strong>Token endpoint</strong></p></td>
  <td valign="top"><p>https://qa.orcid.org/oauth/token</p></td>
</tr>
<tr>
  <td valign="top"><p><strong>Access token location</strong></p></td>
  <td valign="top"><p>Authorization header    w/Bearer prefix</p></td>
</tr>
<tr>
  <td valign="top"><p><strong>OAuth Client ID</strong></p></td>
  <td valign="top"><p>Your Member API client ID (ex: APP-VZTMFLZVBD5NSJQA)</p></td>
</tr>
<tr>
  <td valign="top"><p><strong>OAuth Client Secret</strong></p></td>
  <td valign="top"><p>Your Member API client secret (ex: 448101b3-1618-4841-8c4f-b04ab9edac92)</p></td>
</tr>
</table></li>
<li>The configuration screen should look similar to the image at right. After you&rsquo;ve entered the settings, click <strong>Close</strong> in the lower left corner of the configuration screen.</li>
</ol>
<div clear="all" />
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

<h2><a name="4.3"></a>4.3  Getting permission (an Access Token) to access ORCID records</h2>
<p>To access an ORCID record via the Member API, you first need to get permission from the owner of the record in the form of an Access Token. ORCID uses the standard protocol, OAuth 2.0, to obtain this permission. Generally there are two steps: </p>
<ol>
<li>Get an <strong>Authorization Code</strong>.<br />&nbsp; </li>
<li>Exchange the Authorization Code for an <strong>Access Token</strong>.<br />&nbsp;</li>
</ol>
<h3><img src="http://alainna.org/orcid/clip_image033.jpg" alt="Screen shot: Google OAuth Playground, Step 1 - adding the scope variable, and clicking the 'Authorize API' button." width="288" height="177" align="right" hspace="12" vspace="12" /><a name="h.uzsp2l9oif0z" id="h.uzsp2l9oif0z"></a>4.3.1 Get an Authorization Code</h3>
<p>To get an Authorization  Code, you&rsquo;ll need to prompt the user to sign into his/her ORCID account and  grant permission to your application. In a real-world situation, this is done  using an authorization URL that you construct. With the OAuth Playground, however, this step is done by configuring some additional settings and clicking a button.</p>
<ol>
<li>Beneath <strong>Step 1: Select &amp; authorize APIs</strong> on the left side of the Google OAuth Playground screen, type <strong>/activities/update</strong> in the text box (do not select any of the options presented in the box above).<br />&nbsp;</li>
<li>Click the <strong>Authorize APIs</strong> button.<br />&nbsp; </li>
<li><img src="http://alainna.org/orcid/clip_image035.gif" alt="Screen shot: Google OAuth Playground, Step 2 - exchanging the authorization code for tokens - the code is pre-filled after the previous step." width="315" height="136" align="right" hspace="12" vspace="12" />An ORCID OAuth permission screen will appear. If you are already signed into your test Sandbox account, click the <strong>Authorize</strong> button to grant permission. If you are not yet signed in, type in your test account sign in credentials, and click <strong>Sign In</strong> and sign into your Sandbox account and grant the permissions.<br />&nbsp; </li>
<li>Click <strong>Authorize</strong> on the ORCID OAuth login screen and you will be sent back to the OAuth Playground. A 6-character code will appear in the <strong>Authorization Code </strong>field.<br />&nbsp; </li>
</ol>

<h3><a name="4.3.2"></a>4.3.2  Exchange the Authorization Code for an Access Token</h3>
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
#5. THE CROSS-LINK BREAKDOWN (15 min)
_PRESENTATION_

**TO BE WRITTEN**: _As described in the agenda: Breakdown of the functionality that we are about setup. Suggest this be a power point slide that shows the flow._

The basic steps for crosslinking are:

1. The user creates an ORCID iD and links to the IdP (as we did in earlier in the workshop)
2. ORCID kicks off the OAuth permission based on information that the IdP has provided _(see the next section for this information)_
3. The user grants permission to the IdP (as we did earlier in the workshop)
4. The IdP processes the permission and provides feedback to the user, in the form of a webpage.
5. The IdP redirects the user back to the ORCID my-orcid page where (s)he started.


<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------API CREDENTIAL SETUP---------)
<a name="6-api-credentials"></a>
#6. API CREDENTIAL SETUP (30 min)
_ACTIVITY_

**TO BE WRITTEN**: _As described in the agenda: Set up ORCID Member API credentials to enable IdP cross linking. We will try it out, using Google OAuth playground to simulate the IdP website._

Originally I had thought that we'd have an interface for requesting credentials, setting up the pemissions one wants along with the redirect URI. I was then thinking that we could have them set up the redirect URI to execute the OAuth statements using their credentials, and then displaying the ORCID iD obtained on the page. i.e., they would have put in their credentials, and the pre-set code would display the ORCID iD. We just show them the token statement that converts the code into the ORCID iD. It woudl be great to have an alternate suggestion on how to handle this based on what we can do right now.

<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------THE USER EXPERIENCE---------)
<a name="7-user-experience"></a>
#7. THE USER EXPERIENCE (30 min)
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
#8. POST AN AFFILIATION TO YOUR UNIVERSITY (50 min)
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
#9. REFERENCE MATERIALS

<ul>
<li>See example implementations and workflow guides <a href="https://members.orcid.org" target="_blank">https://members.orcid.org</a><br />&nbsp;</li>
<li>Read technical documentation <a href="https://members.orcid.org/api" target="_blank">https://members.orcid.org/api</a><br />&nbsp;</li>
<li>Join the ORCID API Users Group <a href="https://groups.google.com/group/orcid-api-users" target="_parent">https://groups.google.com/group/orcid-api-users</a><br />&nbsp;</li>
<li>Sign up for a Technical Webinar <a href="https://members.orcid.org/event-list">https://members.orcid.org/event-list</a><br />&nbsp;</li>
<li>Email ORCID Support <a href="mailto:support@orcid.org">support@orcid.org</a></li>
</ul>
