pipeline {
   agent any
      environment {
        
         PATH='/usr/local/bin:/usr/bin:/bin'
         //PATH='/usr/local/bin:/usr/bin:/bin/ANDROID_HOME'
         //PATH='/Users/Shared/Jenkins/ANDROID_HOME'
      }
   stages {
      stage('NPM Setup') {
      steps {
        //sh 'npm install'
        echo "Prueba npm"
         sh 'nvm use 10.9.0'
         
      }
   }

   stage('IOS Build') {
   steps {
      sh 'ionic cordova build ios --release'
     //sh 'node --max-old-space-size=8192 ./node_modules/@ionic/app-scripts/bin/ionic-app-scripts.js build --prod && cordova build ios'
     } 
  }

   stage('Android Build') {
   steps {
      sh 'sudo su'
      sh 'Mac@2018\n'
      sh 'mkdir prueba'
     echo "Android falta agregar al path android"
      //sh 'ionic cordova build android --release'
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
