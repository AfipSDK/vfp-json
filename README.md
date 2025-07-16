# Visual FoxPro - JSON 

Library to use JSON in Visual FoxPro

## Functions

`json_encode(xExpr)`

Transform la expresion a un string en formato JSON

`json_decode(cJson)`

Transforma un string JSON a un objeto.

`json_getErrorMsg()`

Retorna el mensaje de error de la ultima decdificacion.


### Examples

### Encoding
```cs
SET PROCEDURE "C:\\path\\to\\json.prg" ADDITIVE

LOCAL loTestObject

loTestObject = CREATEOBJECT("JSONObject")
loTestObject.set("foo", "var")
loTestObject.set("jhon", "doe")
loTestObject.set("number_prop", 12345)

* Add a JSONArray
LOCAL loArrayProp
loArrayProp = CREATEOBJECT("JSONArray")
loTestObject.set("array_property", loArrayProp)

	* Add a JSONObject to the array
	LOCAL loArrayItem
	loArrayItem = CREATEOBJECT("JSONObject")
	loArrayProp.add(loArrayItem)

	loArrayItem.set("item_boolean_prop", .T.)

LOCAL cJsonString

cJsonString =  json_encode(oSmtp)
```

### Decoding
```cs
obj = oJson.decode('{"jsonrpc":"1.0", "id":1, "method":"sumArray", "params":[3.1415,2.14,10],"version":1.0}')
? obj.get('jsonrpc'), obj._jsonrpc
? obj.get('id'), obj._id
? obj.get('method'), obj._method
? obj._Params.array[1], obj._Params.get(1)


cJson = ' {"server":"imap.gmail.com", "user":"billgates", "password":"melinda" , "port":895, "auth":false, "ssl":false, "timeout":20, "error":404}' 
? cJson
oSmtp = json_decode(cJson)
cJson =  json_encode(oSmtp)


```
