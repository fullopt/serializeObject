# serializeObject
Serializes a form (or a set of inputs) to an object. It uses FileReader and Deferred to serialize input[type="file"]

Usage:
```
<script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
<script src="jquery.serializeObject.js"></script>
<script>			
	$(function(){
		$('form').on('submit', function(e) {
			e.preventDefault();
			$(this).serializeObject().done(function(o){
				if(window.console) console.log(o);
				// see the object in console
			});
		});
	});
</script>
```

(c)2017 aleksandr.ru
