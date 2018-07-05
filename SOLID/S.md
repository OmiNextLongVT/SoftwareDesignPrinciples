# SOLID

1. S : **Single responsibility principle**
    > There should never be more than one reason for a class to change  
    > (Một class chỉ nên có một nhiệm vụ duy nhất)

    **Wrong:**
    ```swift
    class Handler {
 
        func handle() {
            let data = requestDataToAPI()
            let array = parse(data: data)
            saveToDB(array: array)
        }
    
        private func requestDataToAPI() -> Data {
            // send API request and wait the response
        }
    
        private func parse(data: Data) -> [String] {
            // parse the data and create the array
        }
    
        private func saveToDB(array: [String]) {
            // save the array in a database (CoreData/Realm/...)
        }
    }
    ```

    **Right:**  
    ```Swift
    class Handler {
 
        let apiHandler: APIHandler
        let parseHandler: ParseHandler
        let dbHandler: DBHandler
    
        init(apiHandler: APIHandler, parseHandler: ParseHandler, dbHandler: DBHandler) {
            self.apiHandler = apiHandler
            self.parseHandler = parseHandler
            self.dbHandler = dbHandler
        }
    
        func handle() {
            let data = apiHandler.requestDataToAPI()
            let array = parseHandler.parse(data: data)
            dbHandler.saveToDB(array: array)
        }
    }
 
class APIHandler {
 
    func requestDataToAPI() -> Data {
        // send API request and wait the response
    }
}
 
class ParseHandler {
 
    func parse(data: Data) -> [String] {
        // parse the data and create the array
    }
}
 
class DBHandler {
 
    func saveToDB(array: [String]) {
        // save the array in a database (CoreData/Realm/...)
    }
}
    ```