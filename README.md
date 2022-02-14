# keyword-script

<!DOCTYPE html>
<html>
    <head> 
      
 
    </head>
    <body>
      <div id="tfheader">
  	    <input type="text" id="srch_term" size="21" maxlength="120">
  	    <input type="submit" value="search" id="srch_btn">
	    </div>
    </body>
<html>

<script> 


    // This returns th element object for 'srch_button', Then it adds a click event to 
    // the button which will work when the user presses the button.
    document.getElementById('srch_btn').addEventListener('click', query_db);
    
    // Fetching the url
    function query_db() {
        var query = document.getElementById('srch_term').value;
        fetch(`https://security.snyk.io/api/listing?q=${query}`)
          .then(resp => resp.json())
          .then(data => console.log(data))
          .catch(error => console.error('FETCH ERROR:', error));
      
      }
    
    function appendData(data) {
      var mainContainer = document.getElementById("tfheader");
      for (var i = 0; i < data.length; i++) {
        var div = document.createElement("div");
        div.innerHTML = 'Vulnerability: ' + data[i].title + ' ' + 'Package:' + data[i].packageName + ' ' + 'Criticality:' + data[i].severity;
        mainContainer.appendChild(div);
      }
    }

</script>
