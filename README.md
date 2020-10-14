Paytabs iOS SDK Samples
========
![Paytabs-ios-library-v4.0.10](https://img.shields.io/badge/Paytabs%20IOS%20library-v4.0.10.rc.1-green.svg)
![xcode-v10.1](https://img.shields.io/badge/xcode-v10.1-green.svg)

For more information please see [the website][1].


## Installation

### CocoaPods

Simply add the following line to your `Podfile`:

```ruby
pod 'PayTabsSDK', '~> 4.0.10.rc.1'
```

### Manual

Download [SDK v4.0.10 Lite version](https://github.com/paytabscom/paytabs-ios-library-sample/raw/cocoapods_support/sdk/ios_sdk-v4.0.10-lite.zip)

Download [SDK v4.0.10 OCR version](https://github.com/paytabscom/paytabs-ios-library-sample/raw/cocoapods_support/sdk/ios_sdk-v4.0.10-ocr.zip)

Read the documentation to know how to integrate your application with the library
[documentation](https://dev.paytabs.com/docs/ios/)


Static framework requires at minimum deployment target 9.0.

You have to include the following dependencies in your  `Podfile:
```ruby
    # Paytabs dependencies
    pod 'BIObjCHelpers'
    pod 'IQKeyboardManager', '~> 4.0.2'
    pod 'AFNetworking', '-> 4.0.1'
    pod 'Mantle'
    pod 'Reachability'
    pod 'Lockbox'
    pod 'SBJson'
    pod 'PINCache'
    pod 'MBProgressHUD', '~> 1.1.0'
    pod 'ActionSheetPicker-3.0'

    # In case if you are using OCR version 
    pod 'PayCardsRecognizer'
```

You might face an issue when you try installing the sdk manualy while "ENABLE_BITCODE" flag enabled, you will have to include the following script to your `Podfile`:

```ruby
post_install do |installer|
    installer.pods_project.targets.each do |target|
        target.build_configurations.each do |config|
            config.build_settings['BITCODE_GENERATION_MODE'] = 'bitcode'
            config.build_settings['ENABLE_BITCODE'] = 'YES'
        end
    end
end
```
## Usage

### Pay now

```Swift
let bundle = Bundle(url: Bundle.main.url(forResource: "Resources", withExtension: "bundle")!)
self.initialSetupViewController = PTFWInitialSetupViewController.init(
    bundle: bundle,
    andWithViewFrame: self.view.frame,
    andWithAmount: 1.0,
    andWithCustomerTitle: "PayTabs Sample App",
    andWithCurrencyCode: "SAR",
    andWithTaxAmount: 0.0,
    andWithSDKLanguage: "en",
    andWithShippingAddress: "Manama",
    andWithShippingCity: "Manama",
    andWithShippingCountry: "BHR",
    andWithShippingState: "Manama",
    andWithShippingZIPCode: "123456",
    andWithBillingAddress: "Manama",
    andWithBillingCity: "Manama",
    andWithBillingCountry: "BHR",
    andWithBillingState: "Manama",
    andWithBillingZIPCode: "12345",
    andWithOrderID: "12345",
    andWithPhoneNumber: "0097333109781",
    andWithCustomerEmail: "test@paytabs.com",
    andIsTokenization: FALSE,
    andIsPreAuth: FALSE,
    andWithMerchantEmail: "",
    andWithMerchantSecretKey: "",
    andWithAssigneeCode: "SDK",
    andWithThemeColor:UIColor.red,
    andIsThemeColorLight: TRUE)


self.initialSetupViewController.didReceiveBackButtonCallback = {

}

self.initialSetupViewController.didStartPreparePaymentPage = {
  // Start Prepare Payment Page
  // Show loading indicator
}
self.initialSetupViewController.didFinishPreparePaymentPage = {
  // Finish Prepare Payment Page
  // Stop loading indicator
}

self.initialSetupViewController.didReceiveFinishTransactionCallback = {(responseCode, result, transactionID, tokenizedCustomerEmail, tokenizedCustomerPassword, token, transactionState) in
  print("Response Code: \(responseCode)")
  print("Response Result: \(result)")
  
  // In Case you are using tokenization
  print("Tokenization Cutomer Email: \(tokenizedCustomerEmail)");
  print("Tokenization Customer Password: \(tokenizedCustomerPassword)");
  print("TOkenization Token: \(token)");
}

```

Paytabs
-------
[Support][2] | [Terms of Use][3] | [Privacy Policy][4]




 [1]: https://dev.paytabs.com/docs/ios/
 [2]: https://www.paytabs.com/en/support/
 [3]: https://www.paytabs.com/en/terms-of-use/
 [4]: https://www.paytabs.com/en/privacy-policy/
