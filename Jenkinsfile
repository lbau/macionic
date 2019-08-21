pipeline {
   agent any
      environment {
         // path de Mac
         PATH='/usr/local/bin:/usr/bin:/bin:/Users/DCos/.nvm:/Users/DCos:.nvm'
         //path de whindows
         //PATH='/Users/lesba_3nkrzb1/AppData/Local/Programs/Microsoft~1/bin:%NVM_HOME%:%NVM_SYMLINK%:%windir%/system32:%HOMEDRIVE%:%HOMEPATH%'
         //PATH='/usr/local/bin:/usr/bin:/bin/ANDROID_HOME'
         //PATH='/Users/Shared/Jenkins/ANDROID_HOME'
         JENKINS='true'
         INSNPM='echo "Mac@2018" | sudo -S npm install'
         PS='Mac@2018'
      }
   stages {

      stage('NPM Setup') {
      steps {
         echo "node --version"
         echo "nvm list"
         echo "nvm use 10.13.0"
         /*
         sh "echo sudo su"
         sh "echo ${PS}"
         sh "npm install"
         sh "echo nvm list"
         sh "echo nvm use 10.9.0"*/
         //sh 'nvm.sh list'
         
      }
   }
      

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

      echo 'ionic cordova build android --release'
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
