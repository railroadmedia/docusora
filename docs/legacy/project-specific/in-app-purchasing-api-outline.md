# Android & IOS In-App Purchasing

## Handling New Orders

### IOS

1. User submits a new order in the app
2. App send request to drumeo backend with the 'receipt' (base 64 encoded string) and account information
    - Request type: post
    - Request url: /laravel/public/mobile-app/apple/verify-receipt-and-process-payment
    - Request receipt param key: receipt
    - Request email param key: email
    - Request password param key: password
3. Drumeo backend sends receipt to apple store-kit API
    - Using this package: https://github.com/aporat/store-receipt-validator
4. If the payment was successful:
    - Drumeo backend creates user account if needed
    - Drumeo backend gives access level to the user
    - Drumeo backend stores data about the payment in the database
    - Drumeo backend logs in the user and returns an auth token to the app
5. If the payment fails:
    - Drumeo backend returns errors to the app
    
Docs: [https://developer.apple.com/documentation/storekit/in-app_purchase/validating_receipts_with_the_app_store](https://developer.apple.com/documentation/storekit/in-app_purchase/validating_receipts_with_the_app_store)

### Android

1. User submits a new order in the app
2. App send request to drumeo backend with the 'package_name', 'product_id', 'purchase_token' and account information
    - Request type: post
    - Request url: /laravel/public/mobile-app/google/verify-receipt-and-process-payment
    - Request package name param key: package_name
    - Request product id param key: product_id
    - Request purchase token param key: purchase_token
    - Request email param key: email
    - Request password param key: password
3. Drumeo backend sends receipt to google play store API
    - Using this package: https://github.com/aporat/store-receipt-validator
4. If the payment was successful:
    - Drumeo backend creates user account if needed
    - Drumeo backend gives access level to the user
    - Drumeo backend stores data about the payment in the database
    - Drumeo backend logs in the user and returns an auth token to the app
5. If the payment fails:
    - Drumeo backend returns errors to the app
    
Docs: [https://developer.android.com/google/play/billing/billing_library_overview](https://developer.android.com/google/play/billing/billing_library_overview)
    

<!-- --- -->

## Handling Subscription Events

### IOS

1. Apple store-kit API sends request to our server using a configured endpoint
    - Request url: /laravel/public/mobile-app/apple/handle-server-notification
2. Drumeo backend uses data in request to process the renewal or cancellation and adjusts the users access
3. Drumeo returns empty 200 response to store-kit API

Docs: [https://developer.apple.com/documentation/storekit/in-app_purchase/enabling_server-to-server_notifications](https://developer.apple.com/documentation/storekit/in-app_purchase/enabling_server-to-server_notifications)

### Android

1. Google play RTDN API sends request to our server using a configured endpoint
    - Request url: /laravel/public/mobile-app/google/handle-server-notification
2. Drumeo backend uses data in request to process the renewal or cancellation and adjusts the users access
3. Drumeo returns empty 200 response to RTDN API

Docs: [https://developer.android.com/google/play/billing/realtime_developer_notifications](https://developer.android.com/google/play/billing/realtime_developer_notifications)
Helpful Guide: [https://medium.com/androiddevelopers/subscriptions-101-for-android-apps-b7005a7e93a6](https://medium.com/androiddevelopers/subscriptions-101-for-android-apps-b7005a7e93a6)