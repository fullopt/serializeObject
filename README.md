# serializeObject
Serializes a form (or a set of inputs) to an object. It uses FileReader and Deferred to serialize input[type="file"]

Usage:
```
<script>			
	$(function(){
		$('form').on('submit', function(e) {
			e.preventDefault();
			$(this).serializeObject().done(function(o){
				if(window.console) console.log(o);
				// the object see console
			});
		});
	});
</script>
```

(c)2017 aleksandr.ru
