<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1">
<title>The best page ever</title>
</head>
<body>
<h1>The best page ever!!!</h1>
<p>Cat ipsum dolor sit amet, jump launch to pounce upon little yarn mouse, bare fangs at toy run hide in litter box until treats are fed. Go into a room to decide you didn't want to be in there anyway. I like big cats and i can not lie kitty ipsum dolor sit amet, shed everywhere shed everywhere stretching attack your ankles chase the red dot, hairball run catnip eat the grass sniff. Meow i could pee on this if i had the energy for slap owner's face at 5am until human fills food dish yet scamper. Knock dish off table head butt cant eat out of my own dish scratch the furniture. Make meme, make cute face. Sleep in the bathroom sink chase laser but pee in the shoe. Paw at your fat belly licks your face and eat grass, throw it back up kitty ipsum dolor sit amet, shed everywhere shed everywhere stretching attack your ankles chase the red dot, hairball run catnip eat the grass sniff.</p>

BEFORE CONTAINER
<div id="lightning-container"></div>	

<script src="https://daj00000eao59ead-dev-ed.develop.my.site.com/lightning/lightning.out.js"></script>
<script>
    $Lightning.use(
        "c:ChatApp", // Replace with your Aura App's name
        function() {
            $Lightning.createComponent(
                "c:customChatWidget", // Replace with your LWC's name
                {}, // Attributes for the component
                "lightning-container", // The ID of the container element
                function(component) {
                    console.log("Chat widget loaded!");
                }
            );
        },
        "https://daj00000eao59ead-dev-ed.develop.my.site.com/ESWTestGitChat1729181444275vforcesite" // Replace with your Salesforce instance URL
    );
</script>
</body>

</html>
