pipeline {
  agent any

  environment {
    MY_VARIABLE = "Hello, World!"
  }

  stages {
    stage("Build") {
      steps {
        echo "Building..."
      }
    }

    stage("Test") {
      steps {
        echo "Running tests..."
      }
    }

    stage("Push") {
      steps {
        withCredentials([usernamePassword(credentialsId: "github-token", usernameVariable: "GITHUB_USERNAME", passwordVariable: "GITHUB_PERSONAL_ACCESS_TOKEN")]) {
          sh """
            echo ${GITHUB_USERNAME}
            echo ${GITHUB_PERSONAL_ACCESS_TOKEN}
          """
        }
      }
    }

    stage("Deploy") {
      steps {
        echo "Deploying..."
      }
    }
  }

  post {
    success {
      echo "Pipeline executed successfully!"
    }

    failure {
      echo "Pipeline execution failed!"
    }
  }
}
