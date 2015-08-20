<html>
<head>
    <SCRIPT type="text/javascript" lang="javascript"
    src="http://cdn.gigya.com/JS/socialize.js?apikey=3_mK2cmEzLkzhqe4MUrtPncxbv4wKsYAhsew0iVwhVUls3c_Jx_HLX434jAVpq5M_W">
    </SCRIPT>
</head>
<body>
<div id="runningCodeExample" style="border: 1px solid skyblue; padding: 15px; width: 400px; display: block; height: auto;">
    <h3 >Who is Your Favorite Superhero?</h3>
    <DIV id="reactionsDiv"></DIV> <!-- Reactions Plugin DIV Container -->
    <br />
    <h4 >Status:</h4>
    <div id="status"></div>
    <br/>
    <div id="results"></div>
    <script language="javascript">
         
        // UserAction
        var UA = new gigya.socialize.UserAction();
        UA.setLinkBack("http://www.gigya.com");  
         
        // Reaction buttons
        var buttons=[
        {
            ID: 'Superman',
            text: 'Superman',
            noButtonBorders:'true',
            iconImgUp:'http://wikifiles.gigya.com/images/checkbox.png',
            iconImgDown:'http://wikifiles.gigya.com/images/checkbox_selected.png',
            feedMessage: 'Superman is my favorite superhero!',
            tooltip:'Superman is my favorite superhero'
        }
         
        ,{
            ID: 'Batman',
            text: 'Batman',
            noButtonBorders:'true',
            iconImgUp:'http://wikifiles.gigya.com/images/checkbox.png',
            iconImgDown:'http://wikifiles.gigya.com/images/checkbox_selected.png',
            feedMessage: 'Batman is my favorite superhero!',
            tooltip:'Batman is my favorite superhero'       
        }
        ,{
            ID: 'Wonder Woman',
            text: 'Wonder Woman',
            noButtonBorders:'true',
            iconImgUp:'http://wikifiles.gigya.com/images/checkbox.png',
            iconImgDown:'http://wikifiles.gigya.com/images/checkbox_selected.png',     
            feedMessage: 'Wonder Woman is my favorite superhero!',
            tooltip:'Wonder Woman is my favorite superhero'
        }
        ,{
            ID: 'The Flash',
            text: 'The Flash',
            noButtonBorders:'true',
            iconImgUp:'http://wikifiles.gigya.com/images/checkbox.png',
            iconImgDown:'http://wikifiles.gigya.com/images/checkbox_selected.png',
            feedMessage: 'The Flash is my favorite superhero!',
            tooltip:'The Flash is my favorite superhero'   
        }
        ,{
            ID: 'Spider-man',
            text: 'Spider-man',
            noButtonBorders:'true',
            iconImgUp:'http://wikifiles.gigya.com/images/checkbox.png',
            iconImgDown:'http://wikifiles.gigya.com/images/checkbox_selected.png',
            feedMessage: 'Spider-man is my favorite superhero!',
            tooltip:'Spider-man is my favorite superhero'  
        }
        ,{
            ID: 'Wolverine',
            text: 'Wolverine',
            noButtonBorders:'true',
            iconImgUp:'http://wikifiles.gigya.com/images/checkbox.png',
            iconImgDown:'http://wikifiles.gigya.com/images/checkbox_selected.png',
            feedMessage: 'Wolverine is my favorite superhero!',
            tooltip:'Wolverine is my favorite superhero'   
        }
        ,{
            ID: 'Iron Man',
            text: 'Iron Man',
            noButtonBorders:'true',
            iconImgUp:'http://wikifiles.gigya.com/images/checkbox.png',
            iconImgDown:'http://wikifiles.gigya.com/images/checkbox_selected.png',
            feedMessage: 'Iron Man is my favorite superhero!',
            tooltip:'Iron Man is my favorite superhero'
        }
        ,{
            ID: 'The Incredible Hulk',
            text: 'The Incredible Hulk',
            noButtonBorders:'true',
            iconImgUp:'http://wikifiles.gigya.com/images/checkbox.png',
            iconImgDown:'http://wikifiles.gigya.com/images/checkbox_selected.png',
            feedMessage: 'The Incredible Hulk is my favorite superhero!',
            tooltip:'The Incredible Hulk is my favorite superhero' 
        }
        ];
         
        function printResponse(response) {
            if ( response.errorCode == 0 ) {           
                var myCounts = response['counts'];        
                if ( null!=myCounts && myCounts.length>0) {      
                    var msg = 'Poll Results: <br><br>';      
                    for (var index in myCounts) {
                        msg += myCounts[index].buttonId + ': ' + myCounts[index].count + '<br>';
                    }
                    document.getElementById('results').innerHTML = msg;
                }
                else {
                    alert('No Counts were returned');
                }
            }
            else {
                alert('Error :' + response.errorMessage);
            }
        }
         
        var countParams ={
            barID:'superheropoll',
            buttonIDs:'Superman,Batman,Wonder Woman,The Flash,Spider-man,Wolverine,Iron Man,The Incredible Hulk',
            callback:printResponse
        };
        var reactionsParams ={
            barID: 'superheropoll',
            containerID:'reactionsDiv',
            layout:'vertical',
            reactions:buttons,
            bodyText:'Share it on your favorite social networks:',
            cid: '',
            userAction:UA, // The userAction must be defined, even though it is overriden in each reaction button
            multipleReactions:'false', //
            onSendDone:function(a){document.getElementById('status').innerHTML = "Reaction Published!";},
            onReactionClicked :function(a){document.getElementById('status').innerHTML = "Reaction Clicked!";},
            onReactionClicked: function(a){gigya.socialize.getReactionsCount(countParams);}
        };
         
        gigya.socialize.showReactionsBarUI(reactionsParams);
    </script>
</div>
</body>
</html>
