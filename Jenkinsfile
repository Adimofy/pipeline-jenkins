pipeline {
    agent any
    stages {
        stage('Erica Stage') {
            steps {
                sh '#!/bin/bash

					# Check operating system statistics
					echo "Operating system statistics:"
					echo "CPU usage: $(top -bn1 | grep load | awk '{printf "%.2f%%\n", $(NF-2)}')"
					echo "Memory usage: $(free | awk '/Mem/{printf "%.2f%%\n", $3/$2*100}')"
					echo "Disk usage: $(df -h / | awk '/\//{print $(NF-1)}')"

					# Check Jenkins status
					jenkins_status=$(systemctl is-active jenkins.service)
					if [ "$jenkins_status" = "active" ]; then
  						echo "Jenkins is running"
					else
  						echo "Jenkins is not running"
					fi'
                    sh 'lscpu'
            }
        }
    }
}
