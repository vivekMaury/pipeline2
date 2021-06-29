pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Build') {
            steps {
                echo 'Building'
                bat 'build.bat'
                
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
                bat '''@echo off'
                md Realease_Timestamp'''
                bat '''@echo off
                move SomeName.exe Realease_Timestamp'''
 
            }
        }
        stage('Test') {
            steps {
                echo 'Testing '
                bat '''echo on
                for /f "tokens=3,2,4 delims=/- " %%x in ("%date%") do set d=%%y%%x%%z
                set data=%d%
                for /f "tokens=1,2 delims=:. " %%x in ("%time%") do set t=%%x%%y
                set time=%t%
                Echo zipping...
                "C:\\Program Files\\7-Zip\\7z.exe" a -tzip "D:\\JenkinsHome\\workspace\\PipelineOne\\Test_Zipping_%d%_%t%.zip" "D:\\JenkinsHome\\workspace\\PipelineOne\\Realease_Timestamp"
                echo Done!'''
            }
        }
        stage('Release') {
            steps {
                echo 'Releasing'
                 bat '''echo on
                for /f "tokens=3,2,4 delims=/- " %%x in ("%date%") do set d=%%y%%x%%z
                set data=%d%
                for /f "tokens=1,2 delims=:. " %%x in ("%time%") do set t=%%x%%y
                set time=%t%
                Echo moving...
                move Test_Zipping_%d%_%t%.zip [REALEASE]
                echo Done!'''
                bat '''@echo off
                del /q Realease_Timestamp
                rmdir Realease_Timestamp  /q'''
             
                
            }
        }
    }
}
