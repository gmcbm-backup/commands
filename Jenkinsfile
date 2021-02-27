pipeline {
    agent none

    stages {
        stage('Build Java 8') {
            agent {
                docker {
                    image 'maven:3-openjdk-8'
                    args '-v /root/.m2:/root/.m2'
                }
            }
            steps {
                echo 'Building..'
                sh 'mvn -pl . clean install'
                dir('core') {
                    echo "Building Core..."
                    sh 'mvn clean install'
                }
                dir('bukkit') {
                    echo "Building Bukkit..."
                    sh 'mvn clean install'
                }
                dir('bungee') {
                    echo "Building Bungee..."
                    sh 'mvn clean package'
                }
                dir('brigadier') {
                    echo "Building Brigadier..."
                    sh 'mvn clean install'
                }
                dir('jda') {
                    echo "Building JDA..."
                    sh 'mvn clean package'
                }
                dir('paper') {
                    echo "Building Paper..."
                    sh 'mvn clean package'
                }
                dir('sponge') {
                    echo "Building Sponge..."
                    sh 'mvn clean package'
                }
                dir('velocity') {
                    echo "Building Velocity..."
                    sh 'mvn clean package'
                }
            }
            post {
                success {
                    archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
                }
            }
        }

        stage('Build Java 11') {
            agent {
                docker {
                    image 'maven:3-openjdk-11'
                    args '-v /root/.m2:/root/.m2'
                }
            }
            steps {
                echo 'Building..'
                sh 'mvn -pl . clean install'
                dir('core') {
                    echo "Building Core..."
                    sh 'mvn clean install'
                }
                dir('bukkit') {
                    echo "Building Bukkit..."
                    sh 'mvn clean install'
                }
                dir('bungee') {
                    echo "Building Bungee..."
                    sh 'mvn clean verify'
                }
                dir('brigadier') {
                    echo "Building Brigadier..."
                    sh 'mvn clean install'
                }
                dir('jda') {
                    echo "Building JDA..."
                    sh 'mvn clean verify'
                }
                dir('paper') {
                    echo "Building Paper..."
                    sh 'mvn clean verify'
                }
                dir('sponge') {
                    echo "Building Sponge..."
                    sh 'mvn clean verify'
                }
                dir('velocity') {
                    echo "Building Velocity..."
                    sh 'mvn clean verify'
                }
            }
        }
    }
}
