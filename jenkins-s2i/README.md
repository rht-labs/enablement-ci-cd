# jenkins-s2i
This repo contains a sample s2i for jenkins used by the Red Hat Open Innovation Labs.

## Adding plugins
Add plugins to the `plugins.txt` file by including them in the form of `<plugin-id>:<version>`. Eg `email-ext:2.11`.

To get a list of all plugins and their version on an existing Jenkins in this format run this command in the Groovy console.

```groovy
Jenkins.instance.pluginManager.plugins.each{
  plugin ->
    println ("${plugin.getShortName()}:${plugin.getVersion()}")
}
```
## Adding seed jobs
The JENKINS created by this s2i is loaded with a seed for creating a react app and golang pipeline. Additional seeds can be created by including them in `configuration/jobs/`. Create a new folder (for the jenkins job name) and add a `config.xml`. The example seeds point to a DSL stored with sample apps.

## Slack Integration
Edit the `configuration/jenkins.plugins.slack.SlackNotifier.xml` and replace `YOUR_TOKEN_GOES_HERE` with the slack endpoint token. Edit the domain name to match your team one too.

## Git Credentials Generation
The `init.groovy` contains some code run on launch. When deploying Jenkins, set the `GIT_USERNAME` and `GIT_PASSWORD` env variables to have them read in my this config generator
