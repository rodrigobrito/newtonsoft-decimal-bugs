﻿# Newtonsoft, decimal deserialize inconsistency between versions 10 and 11

 ```csharp
var v = 15.1200m;

var v10Serialized = Newtonsoft10x::Newtonsoft.Json.JsonConvert.SerializeObject(v);
var v10Deserialized = Newtonsoft10x::Newtonsoft.Json.JsonConvert.DeserializeObject<decimal>(v10Serialized);

var v11Serialized = Newtonsoft11x::Newtonsoft.Json.JsonConvert.SerializeObject(v);
var v11Deserialized = Newtonsoft11x::Newtonsoft.Json.JsonConvert.DeserializeObject<decimal>(v11Serialized);

Assert.AreEqual(v10Serialized, "15.1200");
Assert.AreEqual(v10Deserialized.ToString(CultureInfo.InvariantCulture), "15.12"); // Inconsistency between versions

Assert.AreEqual(v11Serialized, "15.1200");
Assert.AreEqual(v11Deserialized.ToString(CultureInfo.InvariantCulture), "15.1200"); //Inconsistency between versions
```
