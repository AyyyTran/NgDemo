node {
    def nodeHome = tool name: 'node-18', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
    env.PATH = "${nodeHome}/bin:${env.PATH}"

    stage('Check Tools') {
        bat "node -v"
        bat "npm -v"
    }

    stage('Checkout') {
        checkout scm
    }

    stage('npm Install') {
        bat "npm install"
    }

    stage('Unit Tests') {
        bat "npm test -- --watch=false"
    }
  
    stage('Start Development Server') {
        bat "npm start"
    }

    stage('Run Cypress Tests') {
        bat "npm run cypress:run"
    }
}
