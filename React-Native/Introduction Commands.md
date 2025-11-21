`npx @react-native-community/cli@latest init NATE_App` ->  To start or initialise the react-native application
> Output must be like this after this command : 
> 
```
Need to install the following packages:
@react-native-community/cli@20.0.2
Ok to proceed? (y) y

                                                          
               ######                ######               
             ###     ####        ####     ###             
            ##          ###    ###          ##            
            ##             ####             ##            
            ##             ####             ##            
            ##           ##    ##           ##            
            ##         ###      ###         ##            
             ##  ########################  ##             
          ######    ###            ###    ######          
      ###     ##    ##              ##    ##     ###      
   ###         ## ###      ####      ### ##         ###   
  ##           ####      ########      ####           ##  
 ##             ###     ##########     ###             ## 
  ##           ####      ########      ####           ##  
   ###         ## ###      ####      ### ##         ###   
      ###     ##    ##              ##    ##     ###      
          ######    ###            ###    ######          
             ##  ########################  ##             
            ##         ###      ###         ##            
            ##           ##    ##           ##            
            ##             ####             ##            
            ##             ####             ##            
            ##          ###    ###          ##            
             ###     ####        ####     ###             
               ######                ######               
                                                          

              Welcome to React Native 0.81.4!                
                 Learn once, write anywhere               

✔ Downloading template
✔ Copying template
✔ Processing template
✔ Installing dependencies
✔ Initializing Git repository

  
  Run instructions for Android:
    • Have an Android emulator running (quickest way to get started), or a device connected.
    • cd "/root/AndroidStudioProjects/react-native-projects/NATE_App" && npx react-native run-android
```

`npx react-native start` -> Run this on another terminal and then another one on Android's Terminal
`npx react-native run-android` -> To start the Application on Emulator


**Generating an Application :** 
In your react native project root, run:
```
cd android 
./gradlew assembleRelease`
```

This will generate an unsigned APK in:
`android/app/build/outputs/apk/release/app-release-unsigned.apk`

Clean your build cache and node modules for a fresh start:
`cd android ./gradlew clean cd .. rm -rf node_modules npm install`


Sorting the Icons using this  : 
For Android, add the following line in your `android/app/build.gradle` under `dependencies` section if fonts are not bundled properly:
`apply from: "../../node_modules/react-native-vector-icons/fonts.gradle"`
Then rebuild the app.
