# Setting Up Development Environment for React Native

1. Go to [this guide](https://reactnative.dev/docs/environment-setup) and follow the provided instructions for you development OS. 
    - Our apps are _not_ expo managed! Therefore, ensure you are following the **React Native CLI Quickstart** section in the link provided.
    - If you are using a Mac, please set up the Target OS for both Android and iOS. Else, you can only develop for Android :(

    <br>

2. Once you are done setting up all of the required dependencies, pull the desired app repository and checkout the current up-to-date branch.
    - Our current up-to-date branch is **forum**.
    - Link to Drumeo repository: [Drumeo Repository](https://github.com/railroadmedia/drumeo-app)
    - Link to Pianote repository: [Pianote Repository](https://github.com/railroadmedia/Pianote2)

    <br>
   
# Running the Apps

## Pianote

1. Open the terminal at the project root directory, i.e. ~/Pianote2 ( where ever you pulled the repository! )

2. Run `npm install` and wait for completion

### Running on iOS

3. Navigate to the **ios** folder in the terminal, `cd ios` from root directory

4. Run `pod install`, wait for completion

5. Open **Xcode** -> Open project **Pianote2.xcworkspace** located in the ios folder

6. Select **NotificationServiceExtension** and select any iOS device

![](https://github.com/railroadmedia/docusora/blob/master/docs/images/pianote_xcode_gif.gif "Pianote Xcode")

7. Run the app by pressing the play button
    - The React Native Metro JS Bundler _should_ start automatically. If it does not, open it by running `npm start` in the project root directory.
    - If the build fails, ensure you followed all of the above steps correctly. 
    - If you are running Mac OS on Silicon instead of Intel and the above steps are not working for you, Csilla may be able to help you.

<br>

### Running on Android

3. Run `npm start` in the project root directory, i.e. ~/Pianote2

4. Open **Android Studio** -> Open the "**android**" folder that is in the project root directory

5. Choose a device and run the project!
    - Note: Android Studio may need to load for some time when the project is first opened

![](https://github.com/railroadmedia/docusora/blob/master/docs/images/pianote_android_gif.gif "Pianote Android")

<br>

## Drumeo

1. Open the terminal at the project root directory, i.e. ~/drumeo-app ( where ever you pulled the repository! )

2. Run `npm install` and wait for completion

### Running on iOS

3. Navigate to the **ios** folder in the terminal, `cd ios` from root directory

4. Run `pod install`, wait for completion

5. Navigate back to the project root directory `cd ..` and run `npm start` to start the Metro JS Bundler

5. Open **Xcode** -> Open project **Drumeo.xcworkspace** located in the ios folder

6. Select **NotificationServiceExtension** and select any iOS device

![](https://github.com/railroadmedia/docusora/blob/master/docs/images/drumeo_xcode_gif.gif "Drumeo Xcode")

7. Run the app by pressing the play button
    - If the build fails, ensure you followed all of the above steps correctly. 
    - If you are running Mac OS on Silicon instead of Intel and the above steps are not working for you, Csilla may be able to help you.

<br>

### Running on Android

3. Run `npm start` in the project root directory, i.e. ~/drumeo-app

4. Open **Android Studio** -> Open the "**android**" folder that is in the project root directory

5. Choose a device and run the project!
    - Note: Android Studio may need to load for some time when the project is first opened

![](https://github.com/railroadmedia/docusora/blob/master/docs/images/drumeo_android_gif.gif "Drumeo Android")

<br>

# Switching Between Production and Staging DB

### Pianote

Open the file **common.service.js** and change the rootUrl to:
| DB | rootUrl |
| :---: | :---: |
| Staging | ![](https://github.com/railroadmedia/docusora/blob/master/docs/images/pianote_staging.png "Pianote Staging Settings") |
| Production | ![](https://github.com/railroadmedia/docusora/blob/master/docs/images/pianote_prod.png "Pianote Prod Settings") |

<br>

### Drumeo

Open the file **auth.service.js** and change the rootUrl to:
| DB | rootUrl |
| :---: | :---: |
| Staging | ![](https://github.com/railroadmedia/docusora/blob/master/docs/images/drumeo_staging.png "Drumeo Staging Settings") |
| Production | ![](https://github.com/railroadmedia/docusora/blob/master/docs/images/drumeo_prod.png "Drumeo Prod Settings") |

