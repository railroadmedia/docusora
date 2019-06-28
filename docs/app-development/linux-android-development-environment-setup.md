# Ubuntu

## Getting You OS Ready
- install java 8
    - sudo apt-get install openjdk-8-jdk
- install android studio using snap (install snap if you dont have it) 
    - sudo snap install android-studio --classic
- run android studio app and install sdk:
    - go through install steps, use the 'Standard' setup
    - choose the dark dracula mode!
    - finish the step (it will download and install everything)

- install nvm: 
    - sudo apt-get update
    - sudo apt-get install build-essential libssl-dev
    - sudo curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
    - source ~/.bashrc
    - nvm --version
- install node:
    - nvm install node
    - nvm alias default node
    - node -v
    - npm -v
- setup env vars
    - export ANDROID_HOME=$HOME/Android/Sdk
    - export PATH=$PATH:$ANDROID_HOME/emulator
    - export PATH=$PATH:$ANDROID_HOME/tools
    - export PATH=$PATH:$ANDROID_HOME/tools/bin
    - export PATH=$PATH:$ANDROID_HOME/platform-tools
    - alias run-emu="$ANDROID_HOME/tools/emulator @pixel2"
    - source ~/.bashrc
- fix java
    - export JAVA_OPTS='-XX:+IgnoreUnrecognizedVMOptions --add-modules java.se.ee'
- generate and run emulator
    - touch ~/.android/repositories.cfg
    - sdkmanager "system-images;android-27;google_apis;x86"
    - sdkmanager --licenses
    - avdmanager create avd -n doo1 -k "system-images;android-27;google_apis;x86" --device 'Nexus 5X'
    - emulator -avd doo1
    
- install react native
    - npm install -g react-native-cli
    
- get repo files from dev and chmod 777 -R /app-folder


## Compiling/Developing Drumeo App