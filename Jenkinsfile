pipeline {
    agent any

    stages {
        stage('Docker构建') {
            steps {
                sh "docker rm -f Excalidraw"
                sh "docker image rm xujiaji/excalidraw"
                sh "docker build -t xujiaji/excalidraw ."
            }
        }
        stage('部署') {
            steps {
                sh "docker run --name 'Excalidraw' -d  --net='bridge' --pids-limit 2048 -e TZ=\"Asia/Shanghai\" -e HOST_OS=\"Unraid\" -e HOST_HOSTNAME=\"Babay\" -e HOST_CONTAINERNAME=\"Excalidraw\" -l net.unraid.docker.managed=dockerman -l net.unraid.docker.webui='http://[IP]:[PORT:5000]/' -l net.unraid.docker.icon='https://raw.githubusercontent.com/Olprog59/unraid-templates/main/excalidraw/excalidraw.ico' -p '5000:80/tcp' xujiaji/excalidraw"
            }
        }
    }
}
