# SOLID

**LISKOV SUBSTITUION PRINCIPLE (LSP)**

> Functions that use pointers or references to base classes must be able to use objects of derived classed without knowing it

> Explain: Nếu class S là kế thừa của class T, objects của T có thể thay thế objects của S mà chương trình vẫn hoạt động bình thường.

Example: 

1. Preconditions changes

**Wrong:**
```Swift
class Handler {
 
    func save(string: String) {
        // Save string in the Cloud
    }
}
 
class FilteredHandler: Handler {
 
    override func save(string: String) {
        guard string.characters.count > 5 else { return }
 
        super.save(string: string)
    }
}
```

**Right:**
```Swift
class Handler {
 
    func save(string: String, minChars: Int = 0) {
        guard string.characters.count >= minChars else { return }
 
        // Save string in the Cloud
    }
}

class FilteredHandler: Handler {
 
    override func save(string: String) {
        guard string.characters.count > 5 else { return }
 
        super.save(string: string)
    }
}
```

2. Postconditions changes

