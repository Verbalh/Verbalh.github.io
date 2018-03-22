<!DOCTYPE html>
<html>
    <head>
        <title>HackWare.ru:::DOM XSS</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <div id="default"> An error occurred...</div>
		
		<script>alert("Pwned")</script>
 
        <script>
            function OnLoad() {
                var foundFrag = get_fragment();
                return foundFrag;
            }
 
            function get_fragment() {
                var r4c = '(.*?)';
                var results = location.hash.match('.*input=token(' + r4c + ');');
 
                if (results) {
                    document.getElementById("default").innerHTML = "";
                    return (unescape(results[2]));
                } else {
                    return null;
                }
            }
 
            display_session = OnLoad();
            document.write("Your session ID was: " + display_session + "<br><br>")
        </script>  
 
    </body>
</html>
