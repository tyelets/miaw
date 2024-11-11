<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1">
<title>The best page ever</title>
</head>
<body>
<h1>The best page ever!!!</h1>
<p>Cat ipsum dolor sit amet, jump launch to pounce upon little yarn mouse, bare fangs at toy run hide in litter box until treats are fed. Go into a room to decide you didn't want to be in there anyway. I like big cats and i can not lie kitty ipsum dolor sit amet, shed everywhere shed everywhere stretching attack your ankles chase the red dot, hairball run catnip eat the grass sniff. Meow i could pee on this if i had the energy for slap owner's face at 5am until human fills food dish yet scamper. Knock dish off table head butt cant eat out of my own dish scratch the furniture. Make meme, make cute face. Sleep in the bathroom sink chase laser but pee in the shoe. Paw at your fat belly licks your face and eat grass, throw it back up kitty ipsum dolor sit amet, shed everywhere shed everywhere stretching attack your ankles chase the red dot, hairball run catnip eat the grass sniff.</p>
<div>
        Before iframe
    </div>
    <div>
        <iframe src="https://www.w3schools.com" title="W3Schools Free Online Web Tutorials"></iframe>

    </div>
	<script type='text/javascript'>
	function initEmbeddedMessaging() {
		try {
			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'
			console.log("before");
			window.addEventListener("onEmbeddedMessagingReady", e => {
			  embeddedservice_bootstrap.prechatAPI.setVisiblePrechatFields({
			    // List the pre-chat field names with the value and whether
			    // it's editable in the pre-chat form.
			    "_firstName": {
			      "value": "Jane",
			      "isEditableByEndUser": false
			    },
			    "dropdown_prechat": {
			      "value": "A2",
			      "isEditableByEndUser": false
			    },
			    "checkbox_prechat": {
			      "value": false,
			      "isEditableByEndUser": false
			    }
			  });
});

    console.log("after");

			embeddedservice_bootstrap.init(
				'00Daj00000EAo59',
				'Test_Git_Chat',
				'https://daj00000eao59ead-dev-ed.develop.my.site.com/ESWTestGitChat1729181444275',
				{
					scrt2URL: 'https://daj00000eao59ead-dev-ed.develop.my.salesforce-scrt.com'
				}
			);
   
  
		} catch (err) {
			console.error('Error loading Embedded Messaging: ', err);
		}
	};
</script>
<script type='text/javascript' src='https://daj00000eao59ead-dev-ed.develop.my.site.com/ESWTestGitChat1729181444275/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>

</body>
</html>
