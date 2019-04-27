#Working with data


## JSON

### Pretty Printing JSON

```swift
func prettyPrintJson(json:Any) throws -> String{
    let d: Data = try JSONSerialization.data(withJSONObject: json, options: .prettyPrinted)
    return String(data: d, encoding: .utf8)!
}
```

Where 'json' is a json object from 'JSONSerialization.jsonObject'
