node {
    checkout scm

    stage('todobackend deploy') {
        writeFile file: 'extra.json', text: "{'image_tag':'${IMAGE_TAG}', 'ecs_tasks':[${TASKS}]}"
        withEnv(["VALUT_PASSWORD=${VALUT_PASSWORD}"]) {
            sh 'ansible-playbook site.yml --valut-password-file valut.py -e "@extras.json"'
        }
    }
}