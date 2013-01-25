*************
httpauth  
*************

Fork of httpauth a mon sensor from Ross of virtualgeek ( `<http://www.virtualgeek.net/2011_09_01_archive.html>`__ ) 

Add some enhancement:

* add disable proxy argument
* display human readable requested url on error message
* remove "use LWP::Authen::Ntlm;" cause error on current Debian version (6)

Help
##############

.. code-block:: 

	httpauth.monitor - ross.net
	This is a MON [http://mon.wiki.kernel.org] monitor.

	Standard Http Poll Usage:
	        perl ./httpauth.monitor [-U mydomain\my.user -P mypassword -t 10] http://www.mywebsite.com/about.php

	This checks for a 200 response from the specified urls and will work with either NTLM or basic auth.
	Note: Multiple target websites can be specified, space seperated, on the cli.

	Host Header Http Poll Usage:
	         perl ./httpauth.monitor [-U mydomain\my.user -P mypassword -t 10  -u /translate/ ] -h http://mywebsite.com 10.1.1.1 10.1.1.2 10.1.1.3

	As above, except for use in checking the health of individual servers in a web server farm
	eg using standard http poll usage described at the top would simply request the website from wherever DNS pointed
	this enables you to check the health of host headered sites on each individual web server, without modifying DNS
	or your hosts files.

	Parameters:
	-U Username - if using NTLM, use mydomain\\my.user (NOTE the 2x \\).
	-P Password
	-u Virtual directory or file name URL section eg /translate/ or /healthcheck.php
	-h Host Header eg domain name including http:// eg http://www.google.com
	-p Port if not port 80.
	-t Timeout for http requests - defaults to 10 seconds.
	-d Dump retrieved page contents (useful for debugging).
	-s Should exist - as in this text string should exist in the retrieved page eg -s OK
	-S Should NOT exist - as in this text string should NOT exist in the retrieved page eg -S ERROR
	-H Show this help
	-c Direct connexion without proxy

	NOTE:  When used with mon, the final list of hosts or URL's are the host groups supplied by MON.
