#!/usr/bin/groovy
@Library('github.com/pradeepitm12/osio-pipeline@staging')_
osio {
    config runtime: 'node'

    ci {
        def app = processTemplate(
          params: [ release_version: "1.0.${env.BUILD_NUMBER}" ]
        )
        build resources: app
    }

    cd {
        def app = processTemplate(
          params: [ release_version: "1.0.${env.BUILD_NUMBER}" ]
        )
        build resources: app
        def service = loadResources(file: './.openshiftio/service.yaml')
        deploy resources: [service,app], env: 'stage'
    }
}
