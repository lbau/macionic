pipeline {
   agent any
      environment {
         // path de Mac
         PATH='/usr/local/bin:/usr/bin:/bin:/Users/DCos/.nvm:/Users/DCos:.nvm:/var/lib/jenkins/.nvm'
         //path de whindows
         //PATH='/Users/lesba_3nkrzb1/AppData/Local/Programs/Microsoft~1/bin:%NVM_HOME%:%NVM_SYMLINK%:%windir%/system32:%HOMEDRIVE%:%HOMEPATH%'
         //PATH='/usr/local/bin:/usr/bin:/bin/ANDROID_HOME'
         //PATH='/Users/Shared/Jenkins/ANDROID_HOME'
         JENKINS='true'
         INSNPM='echo "Mac@2018" | sudo -S npm install'
         PS='Mac@2018'
 }

   
        
   stages {
 stage("Build") {
      steps {
         sh "echo sudo su"
         sh "echo ${PS}"
         sh "echo nvm use 10.9.0"
         nvm(nvmInstallURL: 'https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh', 
             nvmIoJsOrgMirror: 'https://iojs.org/dist',
             nvmNodeJsOrgMirror: 'https://nodejs.org/dist', 
             version: '10.9.0') {
                    sh "npm install"

                        
                    sh "npm install ionic@4.0.6"
                    sh 'npm config get prefix'
                  //sh 'ionic cordova build ios --release'
      echo "test ios"
                    echo "Build main site distribution"
                    //sh "npm run build:dist"

              }
         }
    }
      withEnv([
  "PATH+LOCAL=/usr/local/bin"
]) {
  stage('IOS Build') {
    steps {
      sh 'ionic cordova build ios --prod --release'
    } 
  }
}

 /*     stage('NPM Setup') {
      steps {
         echo "node --version"
         echo "nvm list"
         echo "nvm use 10.13.0"
         
         sh "echo sudo su"
         sh "echo ${PS}"
        // sh "export > env.txt"
        // sh "NVM_DIR=$HOME/.nvm && source $NVM_DIR/nvm.sh --no-use && NVM_NODEJS_ORG_MIRROR=https://nodejs.org/dist nvm install v10.9.0 && nvm use v10.9.0 && export > env.txt"
     
        // sh "npm install"
         sh "echo nvm list"
         sh "echo nvm use 10.9.0"
         //sh 'nvm.sh list'
         
      }
   }*/
      

   stage('IOS Build') {
   steps {
      //nvm 'use 10.9.0'
      sh 'ionic cordova build ios --release'
      echo "test ios"
     //sh 'node --max-old-space-size=8192 ./node_modules/@ionic/app-scripts/bin/ionic-app-scripts.js build --prod && cordova build ios'
     } 
  }

   stage('Android Build') {
   steps {

      sh 'ionic cordova build android --release'
     //sh 'node --max-old-space-size=8192 ./node_modules/@ionic/app-scripts/bin/ionic-app-scripts.js build --prod && cordova build android --release'
   }
  }

   stage('APK Sign') {
   steps {
      echo "Datos de tienda solo con los datos funciona, falta probar"
      //sh 'jarsigner -storepass your_password -keystore keys/yourkey.keystore platforms/android/app/build/outputs/apk/release/app-release-unsigned.apk nameApp'
   }
   }

   stage('Stage Web Build') {
      steps {
        sh 'npm run build --prod'
        echo "Web"
    }
  }

   stage('Publish Firebase Web') {
      steps {
      //sh 'firebase deploy --token "test01"'
        echo "Comando firebase not found revisar error"
   }
  }

   stage('Publish iOS') {
      steps {
        echo "Publish iOS Action"
    }
   }

   stage('Publish Android') {
     steps {
        echo "Publish Android API Action"
   }
  }

 }
}
