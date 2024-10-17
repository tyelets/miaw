---
title: PAGE TITLE HERE
layout: template
filename: web_to_case.md
--- 
<html>
<head>
    <META HTTP-EQUIV="Content-type" CONTENT="text/html; charset=UTF-8">
<title>The best page ever</title>
</head>
<body>
<h1>web to case</h1>

<!--  ----------------------------------------------------------------------  -->
<!--  NOTE: Please add the following <META> element to your page <HEAD>.      -->
<!--  If necessary, please modify the charset parameter to specify the        -->
<!--  character set of your HTML page.                                        -->
<!--  ----------------------------------------------------------------------  -->



<!--  ----------------------------------------------------------------------  -->
<!--  NOTE: Please add the following <FORM> element to your page.             -->
<!--  ----------------------------------------------------------------------  -->

<form action="https://webto.salesforce.com/servlet/servlet.WebToCase?encoding=UTF-8&orgId=00Daj00000EAo59" method="POST">

<input type=hidden name="orgid" value="00Daj00000EAo59">
<input type=hidden name="retURL" value="https://tyelets.github.io/miaw/">

<!--  ----------------------------------------------------------------------  -->
<!--  NOTE: These fields are optional debugging elements. Please uncomment    -->
<!--  these lines if you wish to test in debug mode.                          -->
<!--  <input type="hidden" name="debug" value=1>                              -->
<!--  <input type="hidden" name="debugEmail"                                  -->
<!--  value="tatsiana.yelets@gmail.com">                                      -->
<!--  ----------------------------------------------------------------------  -->

<label for="name">Contact Name</label><input  id="name" maxlength="80" name="name" size="20" type="text" /><br>

<label for="email">Email</label><input  id="email" maxlength="80" name="email" size="20" type="text" /><br>

<label for="phone">Phone</label><input  id="phone" maxlength="40" name="phone" size="20" type="text" /><br>

<label for="subject">Subject</label><input  id="subject" maxlength="80" name="subject" size="20" type="text" /><br>

<label for="description">Description</label><textarea name="description"></textarea><br>

<input type="hidden"  id="external" name="external" value="1" /><br>

<input type="submit" name="submit">

</form>
</body>
</html>
