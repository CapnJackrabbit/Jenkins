pipeline
{
    agent
    {
        docker
        {
            image 'python:3.7'
        }
    }

    stages
    {
        stage ('Primeiro pipeline')
        {
            steps
            {
                sh 'python3 -V'
            }
        }

        stage ('Instalando itens do requirements.txt')
        {
            steps
            {
                sh 'pip install -r reqirements.txt --disable-pip-version-check'
            }
        }
    }
}