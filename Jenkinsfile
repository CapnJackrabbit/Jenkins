pipeline
{
    agent
    {
        docker
        {
            image 'python:3.7'
            args '-u root:root'
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
                sh 'pip install -r requirements.txt --disable-pip-version-check'
            }
        }

        stage ('Validação do código')
        {
            steps
            {
                sh 'find . -name \\*.py | xargs pylint -f parseable | tee pylint.log'
                sh 'find . -name \\*.py | xargs pycodestyle | tee pep8.log'
            }
            post
            {
                always
                {
                    recordIssues(
                        tool: pyLint(pattern: '**/pylint.log'),
                        unstableTotalAll: 50,
                        failedTotalAll: 500
                    )

                    recordIssues(
                        tool: pylint(pattern: '**/pep8.log'),
                        unstableTotalAll: 50,
                        failedTotalAll: 500
                    )
                }
            }
        }
    }
}