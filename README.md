# serializeObject
Serializes a form (or a set of inputs) to an object. It uses FileReader and Deferred to serialize input[type="file"]

## Usage
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
			}).fail(function(e){
				// consider to handle FileReader error
			});
		});
	});
</script>
```
The result object is something like this
```
{
	inputName: inputValue,
	inputArray: [firstInputValue, secondInputValue, ...],
	checkedCheckboxWithValue: checkboxValue,
	checkedCheckboxWithoutValue: true,
	uncheckedCheckboxWithoutValue: false,
	fileInput: {
		name: fileName,
		type: mimeType,
		size: fileSize,
		data: dataBase64
	},
	fileInputArray: [{...}, {...}, ...]
}
```

## Serialization rules
- Only inputs with name attribute are serialized
- Inputs with same name becomes an array (if more then one appears)
- Inputs with name ends with "[]" are forced to be serialized as array, even if single occurance
- Checkboxes with value attribute are serialzed only if checked
- Checkboxes without value attribute are serialzed as boolean, depends on checked state
- File inputs are serialized as objects with name, mime type, size and data as base64
- Multiple file inputs are serialized as arrays if more then one file or input name ends with "[]"

### Requirements
- FileReader JavaScript API
- jQuery 1.5+

---
(c)2017 aleksandr.ru
