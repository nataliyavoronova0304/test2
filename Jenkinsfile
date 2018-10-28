node() {
stage("Clone"){
    git url: 'https://github.com/nataliyavoronova0304/test2.git'
}

stage("Build"){
 bat "java -jar mta.jar --build-target=CF --mtar=shine_cf.mtar build"
    
}
stage("Deploy"){
    withCredentials([usernamePassword(credentialsId: 'Demo123', passwordVariable: 'CF_PASSWD', usernameVariable: 'CF_USER')]) {
        bat "cf api https://api.cf.eu10.hana.ondemand.com"
        bat "cf login -u $CF_USER -p $CF_PASSWD"
        bat "cf deploy shine_cf.mtar"
        bat "cf apps"
    }

}
}
