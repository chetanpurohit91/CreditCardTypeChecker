# CreditCardTypeChecker
This library can be used in Swift iOS projects for finding credit card / debit card type.


    //
    //  CardValidator.swift
    //  CreditCard 
    //
    //  Created by Chetan Purohit on 18/09/15.
    //  Copyright (c) 2015 Chetan Purohit. All rights reserved.
    //

    import Foundation

    class CardValidator: NSObject {

    var cardType = ""
    
    var inputNumbers = 0
    
    
    func checkCardType(var cardNumber: String) -> String {
        
        cardNumber = cardNumber.stringByReplacingOccurrencesOfString("-", withString: "", options: NSStringCompareOptions.LiteralSearch, range: nil)
        
            //for converting cardNumber string to integer if it is not empty
            if !cardNumber.isEmpty {
                
                inputNumbers = cardNumber.toInt()!
                
            }
            
            //if card number is empty then it should return blank
            if cardNumber.isEmpty {
                
                cardType = ""
                
            } else if count(cardNumber) == 1 {
                
                //This block checks for card type if there is only 1 digit inserted
                
                if inputNumbers == 1 {
                    
                    cardType = "UATP"
                    
                } else if inputNumbers == 4 {
                    
                    cardType = "Visa"
                    
                }
                
            } else if count(cardNumber) == 2 {
                
                //This block checks for card type if there are 2 digits inserted
                
                if inputNumbers == 34 || inputNumbers == 37 {
                    
                    cardType = "American Express"
                    
                } else if inputNumbers == 62 {
                    
                    cardType = "China UnionPay"
                    
                } else if inputNumbers == 36 || inputNumbers == 38 || inputNumbers == 39 {
                    
                    cardType = "Diners Club International"
                    
                } else if inputNumbers == 54 || inputNumbers == 55 {
                    
                    cardType = "Diners Club"
                    
                } else if inputNumbers == 65 {
                    
                    cardType = "Discover Card"
                    
                } else if inputNumbers == 50 || (inputNumbers >= 56 && inputNumbers <= 69) {
                    
                    cardType = "Maestro"
                    
                } else if (inputNumbers >= 51 && inputNumbers <= 55) {
                    
                    cardType = "MasterCard"
                    
                }
                
            } else if count(cardNumber) == 3 {
                
                //This block checks for card type if 3 digits are inserted
                
                if (inputNumbers >= 300 && inputNumbers <= 305) || inputNumbers == 309 {
                    
                    cardType = "Diners Club"
                    
                } else if (inputNumbers >= 644 && inputNumbers <= 649) {
                    
                    cardType = "Discover Card"
                    
                } else if inputNumbers == 636 {
                    
                    cardType = "InterPayment"
                    
                } else if (inputNumbers > 637 && inputNumbers <= 639) {
                    
                    cardType = "InstaPayment"
                    
                }
                
            } else if count(cardNumber) == 4 {
                
                //This block checks for card type if 4 digits are inserted
                
                if inputNumbers == 5610 {
                    
                    cardType = "Bankcard"
                    
                } else if (inputNumbers == 2014 || inputNumbers == 2149) {
                    
                    cardType = "Diners Club enRoute"
                    
                } else if inputNumbers == 6011 {
                    
                    cardType = "Discover Card"
                    
                } else if inputNumbers >= 3528 && inputNumbers <= 3589 {
                    
                    cardType = "JCB"
                    
                } else if inputNumbers == 6304 || inputNumbers == 6706 || inputNumbers == 6771 || inputNumbers == 6709 {
                    
                    cardType = "Laser"
                    
                } else if inputNumbers >= 2221 && inputNumbers <= 2720 {
                    
                    cardType = "MasterCard"
                    
                } else if inputNumbers == 6334 || inputNumbers == 6767 {
                    
                    cardType = "Solo"
                    
                } else if inputNumbers == 4903 || inputNumbers == 4905 || inputNumbers == 4911 || inputNumbers == 4936 || inputNumbers == 6333 || inputNumbers == 6759 {
                    
                    cardType = "Switch"
                    
                }
                
            } else if count(cardNumber) == 6 {
                
                //This block checks for card type if 6 digits are inserted
                
                if inputNumbers >= 560221 && inputNumbers <= 560225 {
                    
                    cardType = "Bankcard"
                    
                } else if inputNumbers >= 622126 && inputNumbers <= 622925 {
                    
                    cardType = "Discover Card"
                    
                } else if inputNumbers == 564182 || inputNumbers == 633110 {
                    
                    cardType = "Switch"
                        
                }
                
            }
            
            return cardType
            
        }
    
    }
