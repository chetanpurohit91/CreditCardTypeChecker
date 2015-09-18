# CreditCardTypeChecker
This library can be used in Swift iOS projects for finding credit card / debit card type.


Example :

import UIKit

class ViewController: UIViewController {

    @IBOutlet weak var textFieldCardNumber: UITextField!
    @IBOutlet weak var labelMessage: UILabel!
    @IBOutlet weak var labelValidate: UILabel!
    
    var cardValidator = CardValidator()
    
    var cardType = ""
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        self.labelMessage.font = UIFont.boldSystemFontOfSize(15)
    
        textFieldCardNumber.addTarget(self, action: "textFieldDidChange:", forControlEvents: UIControlEvents.EditingChanged)
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }

    func textFieldDidChange(textField: UITextField) {

        if count(self.textFieldCardNumber.text) <= 7 {
            
            var cardType: String = cardValidator.checkCardType(self.textFieldCardNumber.text)
            self.labelMessage.text = cardType
            
        }
        
    }
    
}
