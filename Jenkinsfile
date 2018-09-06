#!groovy
import java.text.*

// pod utilisé pour la compilation du projet
podTemplate(label: 'meltingpoc-run-pod', containers: [

  // le slave jenkins
  containerTemplate(name: 'jnlp', image: 'jenkinsci/jnlp-slave:alpine'),

  // montage nécessaire pour que le conteneur docker fonction (Docker In Docker)
  volumes: [hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock')]
) {

        node('meltingpoc-run-pod') {

            properties([parameters([
                    text(defaultValue: '', description: '', name: 'env'),

                    string(defaultValue: '', description: '', name: 'api_gateway', trim: true),
                    string(defaultValue: '', description: '', name: 'evenement_parcours_integration', trim: true),
                    string(defaultValue: '', description: '', name: 'evenement_rappel', trim: true),
                    string(defaultValue: '', description: '', name: 'gestion_evenement', trim: true),
                    string(defaultValue: '', description: '', name: 'gestion_images', trim: true),
                    string(defaultValue: '', description: '', name: 'gestion_personnes', trim: true),
                    string(defaultValue: '', description: '', name: 'parcours_integration', trim: true),
                    string(defaultValue: '', description: '', name: 'referentiel_personnes_api', trim: true),
                    string(defaultValue: '', description: '', name: 'referentiel_personnes_ui', trim: true)
            ])

            stage('Deploy') {

                if (params.api_gateway != '')
                    build job: '/SOFTEAMOUEST/chart-run/master', parameters: [
                            string(name: 'image', value: params.api_gateway),
                            string(name: 'chart', value: "api-gateway"),
                            string(name: 'env', value: params.env)], wait: false

                if (params.evenement_parcours_integration != '')
                    build job: '/SOFTEAMOUEST/chart-run/master', parameters: [
                            string(name: 'image', value: params.evenement_parcours_integration),
                            string(name: 'chart', value: "evenement-parcours-integration"),
                            string(name: 'env', value: params.env)], wait: false

                if (params.evenement_rappel != '')
                    build job: '/SOFTEAMOUEST/chart-run/master', parameters: [
                            string(name: 'image', value: params.evenement_rappel),
                            string(name: 'chart', value: "evenement-rappel"),
                            string(name: 'env', value: params.env)], wait: false

                if (params.gestion_evenement != '')
                    build job: '/SOFTEAMOUEST/chart-run/master', parameters: [
                            string(name: 'image', value: params.gestion_evenement),
                            string(name: 'chart', value: "gestion-evenement"),
                            string(name: 'env', value: params.env)], wait: false

                if (params.gestion_images != '')
                    build job: '/SOFTEAMOUEST/chart-run/master', parameters: [
                            string(name: 'image', value: params.gestion_images),
                            string(name: 'chart', value: "gestion-images"),
                            string(name: 'env', value: params.env)], wait: false

                if (params.gestion_personnes != '')
                    build job: '/SOFTEAMOUEST/chart-run/master', parameters: [
                            string(name: 'image', value: params.gestion_personnes),
                            string(name: 'chart', value: "gestion-personnes"),
                            string(name: 'env', value: params.env)], wait: false

                if (params.parcours_integration != '')
                    build job: '/SOFTEAMOUEST/chart-run/master', parameters: [
                            string(name: 'image', value: params.parcours_integration),
                            string(name: 'chart', value: "parcours-integration"),
                            string(name: 'env', value: params.env)], wait: false

                if (params.referentiel_personnes_api != '')
                    build job: '/SOFTEAMOUEST/chart-run/master', parameters: [
                            string(name: 'image', value: params.referentiel_personnes_api),
                            string(name: 'chart', value: "referentiel-personnes-api"),
                            string(name: 'env', value: params.env)], wait: false

                if (params.referentiel_personnes_ui != '')
                    build job: '/SOFTEAMOUEST/chart-run/master', parameters: [
                            string(name: 'image', value: params.referentiel_personnes_ui),
                            string(name: 'chart', value: "referentiel-personnes-ui"),
                            string(name: 'env', value: params.env)], wait: false
            }
        }
}

