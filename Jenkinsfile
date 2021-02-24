pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'mvn -pl . clean install'
                dir('core') {
                    echo "Building Core..."
                    sh 'mvn clean install -Djar.finalName=ACF_Core-${GIT_BRANCH#*/}-#${BUILD_NUMBER}'
                }
                dir('bukkit') {
                    echo "Building Bukkit..."
                    sh 'mvn clean install -Djar.finalName=ACF_Bukkit-${GIT_BRANCH#*/}-#${BUILD_NUMBER}'
                }
                dir('bungee') {
                    echo "Building Bungee..."
                    sh 'mvn clean package -Djar.finalName=ACF_Bungee-${GIT_BRANCH#*/}-#${BUILD_NUMBER}'
                }
                dir('brigadier') {
                    echo "Building Brigadier..."
                    sh 'mvn clean install -Djar.finalName=ACF_Brigadier-${GIT_BRANCH#*/}-#${BUILD_NUMBER}'
                }
                dir('jda') {
                    echo "Building JDA..."
                    sh 'mvn clean package -Djar.finalName=ACF_JDA-${GIT_BRANCH#*/}-#${BUILD_NUMBER}'
                }
                dir('paper') {
                    echo "Building Paper..."
                    sh 'mvn clean package -Djar.finalName=ACF_Paper-${GIT_BRANCH#*/}-#${BUILD_NUMBER}'
                }
                dir('sponge') {
                    echo "Building Sponge..."
                    sh 'mvn clean package -Djar.finalName=ACF_Sponge-${GIT_BRANCH#*/}-#${BUILD_NUMBER}'
                }
                dir('velocity') {
                    echo "Building Velocity..."
                    sh 'mvn clean package -Djar.finalName=ACF_Velocity-${GIT_BRANCH#*/}-#${BUILD_NUMBER}'
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
                }
            }
        }
    }
}
