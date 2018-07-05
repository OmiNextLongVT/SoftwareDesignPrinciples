# SOLID

**O: Open-Closed principle**

>SOFTWARE ENTITIES (CLASSES, MODULES, FUNCTIONS...) SHOULD BE OPEN FOR EXTENSION, BUT CLOSED FOR MODIFICATION

>1. OPEN FOR EXTENSION:  
>Should be able to extend or change the behaviours of class without efforts.
>2. CLOSED FOR MODIFICATIONS:  
>Must extend a class without changing the implementation.

> Dễ dàng thay đổi class behaviours mà không cần sửa đổi class đó.

**Example:**  
```Swift
protocol Printable {
    func printDetails() -> String
}
 
class Logger {
 
    func printData() {
        let cars: [Printable] = [
            Car(name: "Batmobile", color: "Black"),
            Car(name: "SuperCar", color: "Gold"),
            Car(name: "FamilyCar", color: "Grey"),
            Bicycle(type: "BMX"),
            Bicycle(type: "Tandem")
        ]
 
        cars.forEach { car in
            print(car.printDetails())
        }
    }
}
 
class Car: Printable {
    let name: String
    let color: String
 
    init(name: String, color: String) {
        self.name = name
        self.color = color
    }
 
    func printDetails() -> String {
        return "I'm \(name) and my color is \(color)"
    }
}
 
class Bicycle: Printable {
    let type: String
 
    init(type: String) {
        self.type = type
    }
 
    func printDetails() -> String {
        return "I'm a \(type)"
    }
}
```