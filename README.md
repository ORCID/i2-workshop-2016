[//]: # (This document was created for the i2 TechEx Workshop on 2016.09.25 in Miami, Fl. It was updated on 2017.05.08 to support [v2.0 of the ORCID API schema](https://github.com/ORCID/ORCID-Source/tree/master/orcid-model/src/main/resources/record_2.0).)

# i2-workshop-2016
### Internet 2 Tech Exchange, Sept 2016
## Hands on with the ORCID API: <br />Getting Authenticated ORCID iDs & Permissions Through Your IdP


_[see the full agenda](http://meetings.internet2.edu/2016-technology-exchange/detail/10004303/)_

_In February 2016, ORCID enabled IdP SSO for all eduGAIN member institutions, allowing the first direct connection between the systems. More recently, ORCID introduced a process that enables IdPs to request authenticated ORCID iDs and user permissions to access their ORCID record, using a process that requires little programming or custom code for institutions. In this hands-on tutorial each participant will set up such a connection in the ORCID test sandbox site (https://sandbox.orcid.org/signin)._

[//]: # (---------AGENDA---------)
<a name="top"></a>
##Workshop Agenda (4 hrs)
###[1. PRESENTATION](#1-what-is-orcid): WHAT IS ORCID? (30 min)
<p>Learn about ORCID and ORCID iDs and how they work. Understand how organizations are using the ORCID registry to collect and display ORCID iDs, and connect and sync information between ORCID records and their own system.</p>

###[2. ACTIVITY](#2-explore-registry): EXPLORE THE ORCID REGISTRY (20 min)
<p>Set up an ORCID iD in our test environment, and explore signing in with your IdP. Understand ORCID’s provenance model and its implications. Learn about the components of an ORCID record, how they get populated, and how they get used.</p>

###[3. PRESENTATION](#3-about-orcid-apis): ABOUT THE ORCID APIs (30 min)
<p>Discover ORCID API types and features, and understand ORCID’s test environment and the technologies that ORCID uses.</p>

###[4. ACTIVITY](#4-oauth-basics): OAUTH BASICS (30 min)
<p>ORCID’s API uses OAuth 2.0 as its protocol for a system client to obtain user permission to access the information stored in their ORCID record. In this section you will obtain system client credentials, and execute basic commands to request permission using a basic OAuth 2.0 3-legged flow. (Don’t know what that is? don’t worry! It will be covered in the session.)</p>

###[5. PRESENTATION](#5-cross-link-breakdown): THE CROSS-LINK BREAKDOWN (15 min)
<p>Breakdown of the cross-link functionality.</p>

###[6. PRESENTATION](#6-api-credentials): API CREDENTIAL SETUP (30 min)
<p>Set up ORCID Member API credentials to enable IdP cross linking. We will try it out, using Google OAuth playground to simulate the IdP website.</p>

###[7. ACTIVITY](#7-user-experience): THE USER EXPERIENCE (30 min)
<p>The technical connection is only part of the overall solution. What should you display to users when they authorize your system to connect with their ORCID records? What you should tell them if they deny your request? Using an ORCID template as a starting point, workshop participants will work together to craft messages and customize templates that will resonate with their audiences.</p>

###[8. ACTIVITY](#8-post-affiliation): POST AN AFFILIATION TO YOUR UNIVERSITY (50 min)
<p>Format data about the person’s relationship to your institution and post it to their ORCID record. Update the data that you’ve already posted to simulate updating data when an affiliation relationship changes.</p>

###[9. REFERENCE MATERIALS](#9-reference)

--

[//]: # (---------WHAT IS ORCID?---------)
<a name="1-what-is-orcid"></a>
#1. WHAT IS ORCID? (30 min) 
_PRESENTATION_ 

[Presented as a power point presentation](https://github.com/ORCID/i2-workshop-2016/blob/master/20160925_TechExWorkshop-Paglione.pdf)
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
  <li>Choose the green <b>anyone</b> visibility setting so you'll be able to see any new items added on your public record.<br />&nbsp;</li> 
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
  <li>After saving your employment information, notice the information on the bottom of the "card" you just created. There is a Source field (that matches your name because you added this information) and the date that you created this addition to your record. This provenance information is recorded for all information added to an ORCID record.<br />&nbsp;</li>
  <li>In the main menu at the top of the screen, click on the <strong>Account settings</strong> link to display your account preferences. Notice each section to see what iD holders can control with their ORCID accounts.<br />&nbsp;</li>
  <li>In the main menu at the top of the screen, click on the <strong>Developer tools</strong> link. In this section a user may obtain credentials to access the public API. Note that this API is different from the member API that we will be discussing today.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

<h2><a name="2.3"></a>2.3 Connect your new iD with your IdP</h2>
<p>Since there are over 2.5 million ORCID iDs, many people already have an ORCID iD when they link to their IdP. To experience this process, we will sign out of your test record and start from the prospective of someone who has an iD, and notices that they can sign in with IdP credentials.</p>
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
<p>ORCID offers two APIs (Application Programming Interfaces) that allow your systems to connect to the  ORCID registry, including reading from and writing to ORCID records. Some API functions are freely available to anyone; others are available to organizations that financially support ORCID with an annual membership subscription.</p>
<table border="1" cellspacing="0" cellpadding="0" width="680">
<tr>
  <td width="95" valign="top"><p><strong>API Version</strong></p></td>
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
    <strong>Update</strong>: Edit or delete items you previously added<br /><br />Register 1 API application</p></td>
</tr>
<tr>
  <td width="95" valign="top"><p>Premium Member API</p></td>
  <td width="200" valign="top"><p>Available to organizations that support ORCID with an annual membership subscription<br /><i>Premium Sandbox Member API freely available to all for testing</i></p></td>
  <td width="385" valign="top"><p><strong>Webhook notifications</strong>: Receive a notice every time a user's ORCID record is updated<br />
   Register 5 API applications</p></td>
</tr>
</table>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>
<h2><a name="3.2"></a>3.2 Sandbox test environment</h2>
<p>In addition to the  production Registry and APIs, ORCID also offers a testing environment, the ORCID Sandbox, which we will be using for this boot camp. The Sandbox is open  to all users and provides a place to develop and test applications without affecting data in the live ORCID registry.</p>
<p> The Sandbox includes:</p>
<ul>
<li><strong><a href="https://sandbox.orcid.org/signin" target="_blank">Sandbox Registry</a></strong>: Simulates the ORCID Registry <br />&nbsp;</li>
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

As discussed in [section 3.1](#3.1), the Public API can only be used to read and search ORCID records, and to  get authenticated ORCID iDs. The Member API, however, can be used to add new  information to ORCID records, as well as to update information previously added. To do these actions, one must obtain permission from the user/data subject. This section describes the standard OAuth process for requesting this permission.
<h2><a name="4.1"></a>4.1  Accessing the Sandbox Member API</h2>
<p>Client credentials consisting of a client ID and a client secret are needed in order to access the Member API. Client Credentials for the Member APIs are issued by ORCID. For this workshop, you can use the sample Sandbox Client Credentials, but we recommend that you obtain your own Member API Sandbox Client Credentials using the request form at <a href="https://orcid.org/content/register-client-application" target="_blank">https://orcid.org/content/register-client-application</a> for experimentation and testing that you do outside of this workshop.</p>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

<h2><a name="4.2"></a>4.2 Setting up the OAuth Playground</h2>
<p>We&rsquo;ll use the Google Developers&rsquo; OAuth Playground for the next exercises. To get started, we will need to configure the environment to work with the ORCID Member API.</p>
<ol>
<li>Visit <a href="https://developers.google.com/oauthplayground" target="_blank">https://developers.google.com/oauthplayground</a><br />&nbsp; </li>
<li>Click the gear icon in the upper right corner to open the configuration form.<br />&nbsp; </li>
<p><img src="http://alainna.org/orcid/clip_image030.jpg" alt="Screen shot: Top of the screen at the Google OAuth playground site, showing the gear icon in the upper right corner at https://developers.google.com/oauthplayground" width="530" height="60" border="0" /></p>

<li>Enter the following:
<table border="1" cellspacing="0" cellpadding="0">
<tr>
  <td width="158" valign="top"><p><strong>OAuth flow</strong></p></td>
  <td valign="top"><p>Server-side</p></td>
  <td width="275" rowspan="7"><img src="http://alainna.org/orcid/clip_image031.jpg" alt="Screen shot: The Google OAuth playground configuration form expanded at https://developers.google.com/oauthplayground" width="275" height="295" /></td>
</tr>
<tr>
  <td valign="top"><p><strong>OAuth endpoints</strong></p></td>
  <td valign="top"><p>Custom</p></td>
</tr>
<tr>
  <td valign="top"><p><strong>Authorization endpoint</strong></p></td>
  <td valign="top"><p>https://sandbox.orcid.org/oauth/authorize</p></td>
</tr>
<tr>
  <td valign="top"><p><strong>Token endpoint</strong></p></td>
  <td valign="top"><p>https://sandbox.orcid.org/oauth/token</p></td>
</tr>
<tr>
  <td valign="top"><p><strong>Access token location</strong></p></td>
  <td valign="top"><p>Authorization header w/Bearer prefix</p></td>
</tr>
<tr>
  <td width="158" valign="top"><p><strong>OAuth Client ID</strong></p></td>
  <td valign="top"><p>Your Sandbox Member API client ID (e.g. APP-E422WM33OPZWKKMQ)</p></td>
</tr>
<tr>
  <td width="158" valign="top"><p><strong>OAuth Client Secret</strong></p></td>
  <td valign="top"><p>Your Sandbox Member API client secret (e.g. ae857cfb-446b-4c3f-8a09-55436bf602dc)</p></td>
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
<h3><a name="h.uzsp2l9oif0z" id="h.uzsp2l9oif0z"></a>4.3.1 Get an Authorization Code</h3>
<p>To get an Authorization Code, you&rsquo;ll need to prompt the user to sign into their ORCID account and  grant permission to your application. In a real-world situation, this is done using an authorization URL that you construct using your <b>client ID</b>, your required access permission <b>scopes</b>, and your <b>redirect uri</b> -- the landing page users will go to after they authorize the connection. This URL looks something like</p>

```
https://sandbox.orcid.org/oauth/authorize?client_id=[your client ID]&response_type=code&scope=/activities/update%20/read-limited&redirect_uri=https%3A%2F%2Fyourdomain.edu%2Fyourlandingpage
```

<img src="http://alainna.org/orcid/clip_image033.jpg" alt="Screen shot: Google OAuth Playground, Step 1 - adding the scope variable, and clicking the 'Authorize API' button." width="288" height="142"  style="float: right; margin: 2px 2px 2px 2px;" vspace="12" /><p>With the OAuth Playground, however, this step is done by configuring some additional settings and clicking a button.</p>
<ol>
<li>Beneath <strong>Step 1: Select &amp; authorize APIs</strong> on the left side of the Google OAuth Playground screen, type "<strong>/activities/update /read-limited</strong>" in the text box (do not select any of the options presented in the box above).<br />&nbsp;</li>
<li>Click the <strong>Authorize APIs</strong> button.<br />&nbsp; <br />&nbsp; </li>
<li>An ORCID OAuth permission screen will appear. If you are already signed into your test Sandbox account, click the <strong>Authorize</strong> button to grant permission. If you are not yet signed in, type in your Sandbox test account sign in credentials, and click <strong>Authorize</strong> to grant the permissions.<br />&nbsp; </li>
<li>Clicking <strong>Authorize</strong> will send the user back to the OAuth Playground. A 6-character code will appear in the <strong>Authorization Code </strong>field.<br />&nbsp;</li>
</ol>

<h3><a name="4.3.2"></a>4.3.2  Exchange the Authorization Code for an Access Token</h3>
<p><img style="float: right; margin: 2px 2px 2px 2px;" src="http://alainna.org/orcid/clip_image035.png" alt="Screen shot: Google OAuth Playground, Step 2 - exchanging the authorization code for tokens - the code is pre-filled after the previous step." width="288" height="120"  />Once you have an  Authorization Code, you can exchange it for an Access Token, which allows you  to read from/write to a user&rsquo;s ORCID record. In a real-world situation, this  exchange would be done by your system, using a programming language such as  PHP, Java, or Ruby on Rails. This call is a RESTful call with information similar to the following</p>

<br style="clear:both" />

<p><img src="http://alainna.org/orcid/clip_image036.png" alt="Screen shot: Google OAuth Playground, Step 2 - exchanging the authorization code for tokens - after exchanging the code, the access and refresh tokens are visible." width="288" height="167" style="float: right; margin: 2px 2px 2px 2px;"  /></p>

```
HTTP method: GET
Header:   Accept: application/json 
Data:     client_id=[your client ID]&
          client_secret=[your client secret]&
          grant_type=authorization_code&
          code=[the authorization code]&
          redirect_uri=https://developers.google.com/oauthplayground
Endpoint: https://sandbox.orcid.org/oauth/token"
```

<p>With the OAuth Playground, however, this step is done by clicking a button.</p>
<ol>
<li>Beneath the <strong>Authorization Code</strong> field, click <strong>Exchange authorization code for tokens</strong>. <br />&nbsp; </li>
<li>The token will appear in the <strong>Access Token </strong>field.<br  style="clear:both"  />&nbsp; </li>
<img src="http://alainna.org/orcid/clip_image038.png" alt="Screen shot: the request/response section on the right side of the screen displays access token details." width="288" height="82" style="float: right; margin: 2px 2px 2px 2px;" border="0" />
<li>Note that you are provided with additional information in the <strong>Request/Response </strong>section on the right side of the screen, such as the name and ORCID iD of the user who granted permission, the lifespan of the token (20 years), and the scope for  which the token is valid.<br />&nbsp; <br />&nbsp; </li>
</ol>
<div clear="all" />
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------THE CROSS-LINK BREAKDOWN---------)
<a name="5-cross-link-breakdown"></a>
#5. THE CROSS-LINK BREAKDOWN (15 min)
_PRESENTATION_

<p>The basic steps for cross linking are:</p>
<ol>
<li>The user creates an ORCID iD and links to the IdP (as we did in earlier in the workshop)</li>
<li>ORCID kicks off the OAuth permission based on information that the IdP has provided <em>(see the next section for this information)</em></li>
<li>The user grants permission to the IdP (as we did earlier in the workshop)</li>
<li>The IdP processes the permission and provides feedback to the user, in the form of a webpage.</li>
<li>The IdP redirects the user back to the ORCID /my-orcid page where they started.</li>
</ol>

<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------API CREDENTIAL SETUP---------)
<a name="6-api-credentials"></a>
#6. API CREDENTIAL SETUP (30 min)
_PRESENTATION_

<p>To get started setting up the <b>institutional sign-in cross-link</b> process described in the previous section, you'll need to:</p>

<ol>
<li><b>Get ORCID Member API credentials</b>. Not a member? Everyone can use the Sandbox Member API for testing. On the production (live) server, you can use the <a href="https://members.orcid.org/api/introduction-orcid-public-api" target="_blank">ORCID Public API</a> to obtain users' authenticated ORCID iDs, but you won't be able to update their ORCID records to display their institutional affiliation, works, or other data.</li>
<li><b>Configure your identity provider settings for your API credentials</b>.
</ol>

##6.1 Get ORCID Member API Credentials

<p>To use the ORCID Member API, you'll need credentials consisting of a Client ID (consumer KEY) and Client Secret (consumer SECRET). These work like a username and password that allow your application to access the API.</p>

<p>We require that all new Member API applications be built and tested using our <a href="https://sandbox.orcid.org/signin" target="_blank">Developers Sandbox</a>, which mirrors production environment behavior, but does not contain production data. <a href="https://support.orcid.org/knowledgebase/articles/166623" target="_blank">Learn more about the Developers Sandbox</a>.</p>

<p><a href="https://orcid.org/content/register-client-application-0">Fill in the ORCID Sandbox Member API Client Application form</a> to get Sandbox API credentials. <b>Note</b>: The process is not automated. ORCID staff will usually issue your credentials within 24 hours.</p>

<p>When requesting credentials, you'll be asked for the following information:</p>
<ol>
<li><strong>Notes for ORCID Staff</strong>: let us know if you're using a <a href="https://members.orcid.org/orcid-enabled-systems" target="_blank">vendor system</a>, need additional redirect URIs, or have any other questions or notes.</li>
<li><strong>Name of your organization</strong> </li>
<li><strong>Contact email address</strong> Use a valid email &ndash; we send your credentials to this address!</li>
<li><strong>Name of your client application</strong>: Name displayed on authorization screen and list of trusted organizations in users' records </li>
<li><strong>Short description of your client application</strong>: Displayed on authorization screen when users click the question mark icon</li>
<li><strong>URL of the home page of your application</strong>: Displayed on the list of trusted organizations in users' records </li>
<li><strong>Redirect URIs</strong>: URL(s) in your web application where users should be returned to after they authorize access to their ORCID record data. (<b>Note</b>: All Redirect URIs must be HTTPS on the production server, however HTTP is fine for the Developers Sandbox.)</li>
<li><strong>Type of credentials</strong>: Basic allows you to read from/write to records, while premium allows read/write access and also lets you register webhooks. We recommend that all Sandbox clients apply for premium credentials</li>
</ol>

##6.2 Configure identity provider settings for your API credentials
<p>The process for adding identity provider settings to your API credentials currently is not automated.</p>

<p>Please send <a href="mailto:support@orcid.org">ORCID a request</a> with the following information:</p>

<ul>
<li>Client ID
<li>Your identity provider entity ID (e.g. https://idp.example.org/idp/shibboleth)
<li>Your Redirect URI: The page on your site that users should be directed to after they complete the cross-link process. This can be different from the redirect URI you use for other ORCID API applications.
<li>The permission scope(s) that you would like. We support the following scopes:
    <ul>
    <li><b>/authenticate</b>: obtain the authenticated ORCID iD (public API)</li>
    <li><b>/read-limited</b>: read limited data on the ORCID record and obtain the authenticated ORCID iD (member API)</li>
    <li><b>/activities/update</b>: add/update an affiliation for your organization in the <b>employment</b> or <b>education</b> section of the ORCID record</li>
    <li><b>/person/update</b>: add/update a unique identifier for your organization in the <b>other IDs</b> section, or a link to the user's faculty webpage in the <b>websites</b> section of the of the ORCID record</li>
	</ul>
</li>
</ul>
<p><em>For new API credential requests, you can also include this info in the notes section of the request form.</em></p>


<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------THE USER EXPERIENCE---------)
<a name="7-user-experience"></a>
#7. THE USER EXPERIENCE (30 min)
_ACTIVITY_

<p>So far, we've spent most of this tutorial focused on technical aspects of building an ORCID integration. The technical nuts and bolts are important, but the user experience is just as critical in a successful integration. </p>

<p>In this section, we'll switch directions and discuss some of the key considerations in making sure that users can connect their ORCID iD to your institution quickly and easily, and that they understand the value of doing so, including:</p>

* [Redirect pages](redirect-pages)
*  [Local support resources](local-support-resources)
*  [User communication](communication)

##7.1 Redirect pages<a id="redirect-pages"></a>
<p>While much of the cross-link interaction takes place on the ORCID site, there are (minimally) 2 pages or response messages that you'll need to create on your own site:</li>
<ol>
<li><b>Redirect page/message &ndash; user authorized the connection</b>: this is the URL that you provide in your API credential registration.</li>
<li><b>Redirect page &ndash; user denied permission</b>: </li>
</ol>
<p>It's important to include messaging and graphics on these pages that help users understand what's happening, and to provide them with resources in case they have questions or run into trouble.</p>

###7.1.1 Redirect page - user authorized the connection

* Confirmation message, customized with the user's name/ORCID iD
* Link/button back to user's ORCID record; use https://orcid.org/my-orcid to send the user to their personal ORCID record
* Contact information at your institution for help/questions about ORCID and your IdP
* Link to resources about how your institution uses ORCID iDs and how it has integrated with ORCID
* Link to contact [ORCID Support](https://orcid.org/help/contact-us)
* Link to [information about ORCID](https://orcid.org/about)
* Link to the [ORCID user Knowledge Base](https://support.orcid.org)
* [ORCID branding/graphics](https://members.orcid.org/logos-web-graphics)

###7.1.2 Redirect page - user denied permission

* Message describing what happened: The user can sign into ORCID using their institutional account, but your institution doesn't know their ORCID iD and can't update their record
* Message listing the benefits of connecting an ORCID iD to your institution
* ORCID-branded button with custom OAuth link to complete the ORCID authorization
* Contact information at your institution for help/questions about ORCID
* Link to resources about how your institution uses ORCID
* [ORCID branding/graphics](https://members.orcid.org/logos-web-graphics)

##7.2 Local support resources <a id="local-support-resources"></a>
<p>ORCID's support team can help your users with general ORCID questions and issues, but for help related to your institution's ORCID integration you'll need to create some resources of your own for your users. These can include:</p>

* Knowledge Base/help articles
* [LibGuides](https://members.orcid.org/resources)
* Tutorials
* Videos<


<p>You should also provide users with contact information for someone at your institution who can provide assistance with ORCID-related questions.</p>

###7.2.1 Example resources

* [HKBU iD connect tutorial video](https://www.youtube.com/watch?v=Zd5r0PflZE4&feature=youtu.be)
* [University of Michigan LibGuide](http://guides.lib.umich.edu/orcid)
* [King Abdullah University of Science and Technology LibGuide](http://libguides.kaust.edu.sa/orcid)
* [More resources](https://members.orcid.org/resources#sec4)

##7.3 Communications<a id="communications"></a>

* Plan a communication timeline: make sure that users are aware of your ORCID project and plans well before you launch!
* Get high-level buy-in: send communications from dean/provost-level channels if possible<
* Promote your ORCID project at libraries, faculty/staff/TA trainings and orientations, campus events, etc.
* Make it an ongoing effort: ensure that new faculty/staff/TAs are in the loop

###7.3.1 Outreach resources
<p>We're here to help! Find logos, fliers, videos, presentation, and other downloadable templates that you use to help get the word out about ORCID at: <a href="https://members.orcid.org/outreach-resources">ORCID Outreach Resources</a></p>.


##7.4 Activity: Build your own redirect pages!
<p>Use the samples provided to create your own custom redirect pages.</p>

1. Download [sample-redirect-pages.zip](sample-redirect-pages.zip) to your computer.
2. Unzip the files.
3. Open redirect-success.html and redirect-deny.html in a browser to view their current content.
4. Using a text editor, edit redirect-success.html and redirect-deny.html to customize the messages, links, graphics, etc. Make sure to keep the files inside the sample-redirect-pages folder, so that the style sheets remain linked!
5. Save your changes and refresh the pages in your browser to see the results.

<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------POST AN AFFILIATION TO YOUR INSTITUTION---------)
<a name="8-post-affiliation"></a>
#8. POST AN AFFILIATION TO YOUR INSTITUTION (50 min)
_ACTIVITY_

<p>In this section we will add and update an employment affiliation to your Sandbox test ORCID record using the permission that you have already received from the earlier exercise. Note: It is also possible to post an education affiliation using [different slightly different XML and endpoints](sample-education-affiliation.xml).</p>

<h2><a name="8.1"></a>8.1 Post an employment affiliation to your ORCID record</h2>
<ol>
<li>Beneath <strong>Step 3: Configure request to API</strong>, set <strong>HTTP Method</strong> to <strong>POST</strong>.<br />&nbsp; </li>
<li>Click <strong>Add headers</strong> and enter the following values:</li>
<ul>
  <li><strong>Header name:</strong> accept</li>
  <li><strong>Header value:</strong> application/vnd.orcid+xml<br />
  </li>
</ul>
<p><img src="http://alainna.org/orcid/clip_image040.jpg" alt="configure headers" width="464" height="119" border="0" /></p>
<li>Click <strong>Add</strong> to add another header and enter the following values:</li>
<ul>
  <li><strong>Header name:</strong> Content-type</li>
  <li><strong>Header value:</strong> application/vnd.orcid+xml<br />&nbsp; </li>
</ul>
<li>Click <strong>Add</strong> again, then click <strong>Close</strong>.<br />&nbsp; </li>
<li>In the <strong>Request URI</strong> field, enter https://api.sandbox.orcid.org/v2.0/[orcid-id]/employment,  replacing [orcid-id] with the ORCID iD of the Sandbox record that you created earlier (e.g. https://api.sandbox.orcid.org/v2.0/0000-0002-3791-8427/employment)<br />
  <br />
  <img src="http://alainna.org/orcid/clip_image042.jpg" alt="configure request URI" width="350" height="195" border="0" border="0" /><br />&nbsp; </li>
<li>Click <strong>Enter request body</strong>. Here is where you&rsquo;ll enter the XML for the works you wish to  add.<br />&nbsp; </li>
<li>Go to [sample-employment-affiliation.xml](sample-employment-affiliation.xml) and copy the XML.<br />&nbsp; </li>
<li>Paste the copied content into the <strong>Request Body </strong>text box.<br />&nbsp; </li>
<li>Customize the text to reflect your institution. For the disambiguated-organization-identifier, replace XXXXXX with the <a href="http://ido.ringgold.com" target="_blank">Ringgold identifier</a> for your institution.<br />&nbsp; </li>
<li>Click <strong>Close</strong>.<br />
  <br />
  <img src="http://alainna.org/orcid/clip_image044.jpg" alt="" width="500" height="332" border="0" /></li><Br />&nbsp;
<li>Click <strong>Send the  request</strong>.<br />&nbsp; </li>
<li>The  results will appear in the <strong>Request/Response</strong> section on the right side of the screen. Scroll to the bottom &ndash; if you see <strong>HTTP/1.1 201 Created</strong>, the affiliation was successfully posted!<br /> &nbsp; 
  <img src="http://alainna.org/orcid/clip_image046.jpg" alt="HTTP response" width="499" height="280"  border="0" /><br />&nbsp; </li>
<li>Each item added to the ORCID record has a unique <b>put-code</b> that can be used to read the full metadata of the item, or to edit or delete the item using the client that has added it to the record. The put-code is displayed in the response following <b>Location</b>: https://api.sandbox.orcid.org/v2.0/[orcid-id]/employment/[put-code]. In a real-world situation, your system would store this put-code along with the affiliation data in your database. <br style="clear: all;" /></li>
<li>Visit the <strong>public view</strong> of your Sandbox record at https://sandbox.orcid.org/[Your sandbox iD] to see the work that you added in the user interface.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

<h2><a name="8.2"></a>8.2 Updating an affiliation</h2>
<p>In a real-world situation, you may need to update a researcher's affiliation when they finish a degree, change departments, or finish a contract. To update an affiliation, you will require the unique <b>put-code</b> for the affiliation.</p>
<ol>
<li>Beneath <strong>Step 3: Configure request to API</strong>, set <strong>HTTP Method </strong>to <strong>PUT</strong>, which is required to update the item.<br />&nbsp; </li>
<li>At the end of the request URI, add the <b>put-code</b> of the affiliation you just created, e.g. https://api.sandbox.orcid.org/v2.0/0000-0002-3791-8427]/employment/employment/26651. Without the put-code, you cannot update the affiliation.<br />&nbsp; </li>
<li>Click <strong>Enter request body</strong>. This is where you&rsquo;ll  enter the XML for the work that you wish to edit.<br />&nbsp; </li>
<li>Go to [sample-employment-affiliation-edit.xml](sample-employment-affiliation-edit.xml) and copy the XML.<br />&nbsp; </li>
<li>Paste the XML in the <strong>Request Body</strong> field and amend to reflect your institution.<br />
Tip: The amended area are lines 1 (edit) and lines 13-11 (new data). You can copy line one and use it to replace the first line of your data; enter the unique <b>put-code</b> in place of "put-code="XXXXX"". The new data begins begins with &lt;common:end-date&gt;, and you can can paste it after the &lt;/common:start-date&gt; in the active Request Body.)<br />
  <img src="http://alainna.org/orcid/clip_image051.jpg" alt="HTTP response" width="500" height="415"  border="0" /><br />&nbsp; </li>
<li>Click <strong>Close</strong>.<br />&nbsp; </li>
<li>Click <strong>Send the Request</strong>.<br />&nbsp; </li>
<li>The  results will appear in the <strong>Request/Response </strong>section on the right side of the screen.  Scroll down &ndash; if you see <b>HTTP/1.1 200 OK</b>, the affiliation was successfully posted!<br />If you receive an error, be sure to check that the headers value under <b>Add headers</b> have not been changed to garbled text, e.g. "application%2Fvnd.orcid%2Bxml".<br />
  <img src="http://alainna.org/orcid/clip_image053.jpg" alt="HTTP response" width="500" height="170"  border="0" /><br />&nbsp;
</li>
<li>Visit  the public view of your Sandbox record at https://sandbox.orcid.org/[Your  sandbox iD] to see the changes to the work in the user interface.</li>
</ol>
<p align="right" style="font-size:9px"><a href="#top">-top-</a></p>

[//]: # (---------REFERENCE MATERIALS---------)
<a name="9-reference"></a>
#9. REFERENCE MATERIALS

<ul>
<li>See example implementations and workflow guides at our <a href="https://members.orcid.org" target="_blank">Member Support Center</a><br />&nbsp;</li>
<li>Read our <a href="https://members.orcid.org/api" target="_blank">API technical documentation</a><br />&nbsp;</li>
<li>Find sample calls and XML in the <a href="https://github.com/ORCID/ORCID-Source/tree/master/orcid-model/src/main/resources/record_2.0" target="_blank">ORCID Github repository</a><br />&nbsp;</li>
<li>Join the  <a href="https://groups.google.com/group/orcid-api-users" target="_parent">ORCID API Users Group</a><br />&nbsp;</li>
<li>Sign up for a  <a href="https://members.orcid.org/event-list">Technical Webinar</a><br />&nbsp;</li>
<li><a href="https://orcid.org/help/contact-us">Contact us for help</a></li>
</ul>
