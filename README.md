import UIKit
import OHHTTPStubs

class ViewController: UIViewController {

  override func viewDidLoad() {
    super.viewDidLoad()

    // Stub a network request
    stub(condition: isHost("api.example.com") && isPath("/users")) { _ in
      // Return a stub response
      return OHHTTPStubsResponse(
        fileAtPath: Bundle.main.path(forResource: "users", ofType: "json")!,
        statusCode: 200,
        headers: ["Content-Type": "application/json"]
      )
    }

    // Make a network request (using Alamofire or URLSession)
    // ... your network request code ...

    // Remove the stub (optional)
    // OHHTTPStubs.removeAllStubs()
  }
}
