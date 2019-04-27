# apple-dev-notes
Notes, tips and tricks when doing development on Apple platforms


## Swift

### Variables

#### Optional values

Variables can have optional values. These are noted by the use of '?'

```swift
var optional:String? = "Hello"
```

This means that the variable can potentially be nil.

You can check for a value inline using let:

var greeting:String = "Hello!";

```swift
if let name = optional {
  greeting = "Hello \(name)"
}```

If optional has a value the statement will return true and the block will be executed. If its nil, it will return false, and the block will not be executed.

#### Default values

You can use '??' to provide a default value when using a variable with an optional value.

```swift
let nickName:String? = "mesh"
let name:String = "Mike"
print("Hi! \(nickName ?? name)")
```

If nickName is nil, then the name variable value will be used.

When working with optional values, you can write a '?' before the operation. If the value is nil, everything after the '?' is ignored, and the returned value is nil.

let len = nickName?.length

### Control Flows

#### switch statements

```swift
let foo = "bar"

switch foo {
  case "bar":
    print("bar")
  case "bam":
    print ("bam")
  default:
    print ("dont know")
}
```

Note that statements do not fall through, and thus you do not need break statements.

cases support any kind of data, and can include comparison operators.

#### for-in iterating dictionaries

```swift
let values = [
  "firstName":"Mike",
  "lastName":"Chambers",
  "nickName":"mesh"
]

for (key, value) in values {
  print("\(key) is \(value)")
}
```

#### Looping with an index

```swift
var total = 0
for (i in 0..<4) {
  total += i
}
```

Note, '..<' omits upper value. '...' includes upper value.

### Functions and Closures

#### Defining a Function

```swift
func greet(person:String day:String) -> {
  return "Hello \(person), today is (day)"
}

greet(person:"Bob", day:"Tuesday")
```

By default, functions use their parameter names as their argument names (as above). You can specify custom labels before the parameter name:

```swift
func greet(person:String on day:String) -> {
  return "Hello \(person), today is (day)"
}

greet(person:"Bob", on:"Tuesday")
```

You can use '_' to to have no argument label.

```swift
func greet(_ person:String _ day:String) -> {
  return "Hello \(person), today is (day)"
}

greet("Bob", "Tuesday")
```

Good overview [here](https://stackoverflow.com/a/49350382)

#### Returning multiple values

You can use a tuple to return multimate values from a function:

```swift
func foo() -> (a:Int, b:Int, c:Int) {
  return (1, 2, 3)
}

let out = foo()
print(out.a)
print(out.1)
```

#### Passing a function as an argument

func callFunction(comparer : f:(Int) -> Bool) -> {
  return comparer(5)
}

func compare(number:Int) -> Bool {
  return number > 0
}

var value = callFunction(comparer:compare)

#### Defining a Closures

You can define a closure by wrapping the code in '{}'

Single statement enclosures implicitly return the value of their only statement:

```swift
let mappedNumbers = numbers.map({number in 3 * number})
```

When a closure if the only argument to a function, you can omit the parentheses:

```swift
let sortedNumbers = numbers.sorted { $0 > $1}

//or

let sortedNumbers = numbers.sorted ({ $0 > $1})
```

Note, function arguments can also be referenced by their argument position index (as above).

### Classes

Creating a custom class:

```swift
//NamedShape extends Shape
class NamedShaped : Shape {
  var _name:String

  //constructor
  init(_name:String) {
    self._name = _name
  }

  //deconstructor
  deinit() {

  }

  //getter / setter
  var name : String {
    get {
      return _name
    }
    set(value) {
      _name = value
    }
  }
}
```

Note, classes are always passed by references. structs are copied.

#### Errors

```swift
do {
  let response = foo()
  print (response)
} catch {
  print(error)
}
```

Error is any type that implements the [Error protocol](https://developer.apple.com/documentation/swift/error)

You can also use 'try?' to convert the result to an optional, and set result to nil if it fails.

```swift
let success = try? send()
```
