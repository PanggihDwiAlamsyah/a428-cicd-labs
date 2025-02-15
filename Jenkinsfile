pipeline {
    agent {
        docker {
            image 'node:lts-buster-slim'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the website? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        } 
    }
}


// jika erorr dimasa depan pada npm bisa pake 
// pipeline {
//     agent any  
    
//     environment {
//         CI = 'true'
//     }
    
//     stages {
//         stage('Build') {
//             agent {
//                 docker {
//                     image 'node:lts-buster-slim'  // Gunakan container Node.js
//                     args '-p 3000:3000'
//                 }
//             }
//             steps {
//                 sh 'npm install'
//             }
//         }

//         stage('Test') {
//             agent {
//                 docker {
//                     image 'node:lts-buster-slim'  // Gunakan container yang sama untuk test
//                     args '-p 3000:3000'
//                 }
//             }
//             steps {
//                 sh 'chmod +x ./jenkins/scripts/test.sh'  // Pastikan file bisa dieksekusi
//                 sh './jenkins/scripts/test.sh'
//             }
//         }

//         stage('Deliver') {
//             steps {
//                 sh 'chmod +x ./jenkins/scripts/deliver.sh ./jenkins/scripts/kill.sh'
//                 sh './jenkins/scripts/deliver.sh'
//                 input message: 'Finished using the website? (Click "Proceed" to continue)'
//                 sh './jenkins/scripts/kill.sh'
//             }
//         } 
//     }
// }


// pipeline {
//     agent any // Tidak menghentikan container setelah Test
//     stages {
//         stage('Build') {
//             agent {
//                 docker {
//                     image 'node:16-buster-slim'
//                     args '--network=host -p 3000:3000'
//                 }
//             }
//             steps {
//                 sh 'npm install'
//             }
//         }
//         stage('Test') {
//             steps {
//                 sh './jenkins/scripts/test.sh'
//             }
//         }
//         stage('Deploy') {
//             steps {
//                 sh './jenkins/scripts/deliver.sh'
//                 input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
//                 sh './jenkins/scripts/kill.sh'
//             }
//         }
//     }
// }