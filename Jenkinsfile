pipeline {
	agent any 
		stages {
			stage('git-clone'){
				steps{
					checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'token', url: 'https://github.com/noelleflo/second-multibranch.git']]])
				}
			}
			stage('parallel-level'){
				parallel {
					stage('sub-job1'){
						steps{
							echo "sub-job1 task"
						}
					}
					stage('sub-job2'){
						steps{
							echo "sub-job2 task"
							echo "testing second multi"
						}
					}
					stage('user checkout'){
						steps{
							sh 'cat /etc/passwd |grep jenkins'
						}
					}
					stage('2-parallel'){
						parallel{
							stage('to-test-multi-builds'){
								steps{
									sh 'lscpu'
								}
							}
						}
					}
				}
			}
			stage('version-check'){
				steps{
					echo "end of parallel job"
				}
			}
		}
}
