# Ajax-Text-File
Display a simple text file in a web page using AJAX.

Initially, I wrote the script to work inside a content management system but it will work for any web page. You will need to set the url variable to the folder that has your text files then add this code to your web page. The script is looking for the name of the text file as a url parameter.

For example, to open test.txt in test.html use the following address: test.html?file=test.txt

```
<script>
$.urlParam = function(name){
	var results = new RegExp('[\?&]' + name + '=([^&#]*)').exec(window.location.href);
	if (results == null){
       return null;
    }
    else{
       return results[1] || 0;
    }
}
 
url = '/source/pathname'+ $.urlParam('file');

</script>
<pre id="data">

&nbsp;</pre>
<script>
$.ajax({
   url: url,
   dataType:"text",
   success:function(data)
   {
    
    $("#data").html(data);

   },
   error: function() 
   {
    $('#error').html('<p>An error has occurred</p>');
   }

});

</script>
```
