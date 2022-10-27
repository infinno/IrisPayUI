# Release notes

## v1.18.0 (44)
- Labels containing HTML will now be rendered properly.

## v1.17.1 (43)
- The method `IrisPayUI.confirmPayment(withCode:webhookHash:delegate:)` shouldn’t have been deprecated. Sorry about that.
- Bug fixes and performance improvements.

## v1.17.0 (42)
- Added support for a new field type: `date`. Tapping it shows a date picker.
- Future new field types shouldn’t crash the framework any more.

## v1.16.0 (41)
- Exposed the public classes, methods, enums, etc. to Objective-C.

## v1.15.0 (40)
- Added a new method called `startDomesticOrSEPAPayment`. Use it to make payments to a local or SEPA IBAN.
- Added a new method called `startBudgetPayment`. Use it to make a budget payment.

## v1.14.2 (39)
- Added support for changing the font of the labels and navigation bar titles.

## v1.14.1 (38)
- Fixed possible multiple calling of the delegate methods for a single operation.

## v1.14 (37)
- Won’t do any automatic dismissal of the web view; instead we track the `closeWindow` property.
- Fixed the scrolling in the `IPUIFormControllers` when there are no visible fields.
- Deprecated the `IPUIPaymentDelegate.gotConsent(_:)` method.
- Bug fixes and performance improvements.

## v1.13 (34)
- Added a menu in the banks list to filter the banks by country.
- When the process is completed and we reach the “All done!” page, we’ll wait 4 seconds, dismiss the web view, and call an appropriate delegate method.  

## v1.12.2 (32)
- Added a missing translation.
- Added missing documentation for the new `IPUIEnvironment` options.

## v1.12.1 (31)
- The `irisInstanceURL` parameter specifying a custom IrisPayUI instance returns to the IrisPayUI init method. If a valid URL is provided the `environment` will be ignored so be careful!

## v1.12 (30)
- Introduced a new `environment` parameter to the IrisPayUI init with two options: `sandbox` and `production`. It controls the URLs IrisPayUI is calling.
- Added checks to the framework methods so that they cannot be used with an empty Iris hash.

## v1.11.2 (28)
- Updated the `PayPerClickResponse` struct.

## v1.11.1 (27)
- Updated the `payByClick` method.

## v1.11 (26)
- Added a new method called `payByClick` that starts the payment process by using payment hash generated through Pay by Click.

## v1.10.1 (25)
- Fixed a crash related to the new `startPaymentWithoutConsent` method.

## v1.10 (24)
- When adding an account, if only one bank is available, we won’t show the list but start the bank’s flow immediately.
- Added a new method called `startPaymentWithoutConsent` for making payments without having to obtain consent first.

## v1.9.2 (23)
- Added support for a new type of field `LABEL` which is read-only.
- Added support for configuring the text colour of disabled input fields.
- Added a dropdown icon to the dropdown fields.

## v1.9.1 (22)
- Text in the IBAN form fields should be UPPERCASE automatically (if allowed by the device settings).

## v1.9 (21)
- Added support for supplying an IBAN to the `startPayment` method.

## v1.8.2 (20)
- Showing an alert if an error occurs after form submission.

## v1.8.1 (19)
- All input fields are not automatically UPPERCASE any more.

## v1.8 (18)
- Added support for dark mode configuration in the `IPUIAppearance` class.

## v1.7.1 (17)
- Automatically closing the web view after a consent string arrives.

## v1.6 (15)
- Added a method `gotConsent(_ consent: String)` to the `IPUIPaymentDelegate` which may be called during the process of creating and confirming a payment. The `consent` string passed to the method is a JSON object.

## v1.5 (14)
- If the final step of a process returns anything in the `result` property, it will be passed to the delegate as a `String`.

## v1.4 (13)
- Added separate delegate methods called after successfully adding an IBAN and confirming a payment.
- Added support for handling universal links and custom URL schemes.
- Showing the bank logo and name (if provided) in the add IBAN form (if it’s not in a web view).
- Bugfixes.

## v1.3 (10)
- Bugfixes.

## v1.2 (9)
- You can now set the URL of the IRIS PAY instance you want the framework to use.
- Added support for supplying webhooks when adding IBANs and confirming payments.
- Added support for setting the language of the returned labels, messages, etc., when initializing the framework (supports Bulgarian and English).

## v1.1 (1)
- Completing a PSD2 payment (`confirmPayment(withCode: String)` method).
- Customisation of the Buttons.

## v1.0 (1)
- Original release.
- Adding IBANs (`addIBAN()` method).
- Beginning a PSD2 payment (`startPayment()` method).
- Customisation of the Lists and Forms.
