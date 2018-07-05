# SOLID

**INTERFACE SEGREGATION PRINCIPLE (ISP)**

> CLIENT SHOULD NOT BE FORCES TO DEPEND UPON INTERFACES THAT THEY DO NOT USE

example:

```Swift
protocol TapProtocol {
    func didTap()
}
 
protocol DoubleTapProtocol {
    func didDoubleTap()
}
 
protocol LongPressProtocol {
    func didLongPress()
}
 
class SuperButton: TapProtocol, DoubleTapProtocol, LongPressProtocol {
    func didTap() {
        // send tap action
    }
 
    func didDoubleTap() {
        // send double tap action
    }
 
    func didLongPress() {
        // send long press action
    }
}
 
class PoorButton: TapProtocol {
    func didTap() {
        // send tap action
    }
}
```