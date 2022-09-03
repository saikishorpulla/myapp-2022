pipeline {
    parameters {
  choice choices: ['master', 'develop', 'qa'], description: 'choose a branch to build', name: 'branchname'
}
    agent any
 stages {
      stage("Only for master") {
         when {
             expression {
                 params.branchname == "master"
             }
         }
         steps {
             echo "this only work for master branch"
         }
     }
     stage("Demo") {
         steps {
             git url:"https://github.com/saikishorpulla/myapp-2022", branch:params.branchname
             echo params.branchname
             echo "welcome to params job"
         }
     }
 }
}
