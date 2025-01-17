---
aliases:
- /fr/continuous_integration/setup_tests/containers
kind: documentation
title: Tests au sein de conteneurs
---

{{< site-region region="gov" >}}
<div class="alert alert-warning">La solution CI Visibility n'est pas encore disponible pour le site que vous avez sélectionné ({{< region-param key="dd_site_name" >}}).</div>
{{< /site-region >}}

## Présentation

Si vous exécutez vos tests à l'intérieur d'un conteneur que vous lancez vous-même dans le build (par exemple, en utilisant [`docker run`][1] ou [`docker-compose`][2]), transmettez les variables d'environnement suivantes au conteneur en fonction de votre fournisseur de CI. Le traceur Datadog pourra ainsi détecter automatiquement les informations sur le build.

En outre, vous devez passer les variables d'environnement requises pour configurer le traceur telles que décrites dans les [instructions d'instrumentation de test pour chaque langage][3] (telles que `DD_SERVICE`, `DD_ENV` et une `DD_TRACE_AGENT_URL` valide qui est accessible au sein du conteneur).

{{< tabs >}}
{{% tab "AppVeyor" %}}

- `APPVEYOR`
- `APPVEYOR_BUILD_ID`
- `APPVEYOR_BUILD_NUMBER`
- `APPVEYOR_BUILD_FOLDER`
- `APPVEYOR_REPO_PROVIDER`
- `APPVEYOR_REPO_NAME`
- `APPVEYOR_REPO_BRANCH`
- `APPVEYOR_REPO_COMMIT`
- `APPVEYOR_REPO_TAG_NAME`
- `APPVEYOR_PULL_REQUEST_HEAD_REPO_BRANCH`
- `APPVEYOR_REPO_COMMIT_MESSAGE`
- `APPVEYOR_REPO_COMMIT_MESSAGE_EXTENDED`
- `APPVEYOR_REPO_COMMIT_AUTHOR`
- `APPVEYOR_REPO_COMMIT_AUTHOR_EMAIL`

[Liste complète des variables d'environnement de build fournies par AppVeyor][1]


[1]: https://www.appveyor.com/docs/environment-variables/
{{% /tab %}}
{{% tab "Azure Pipelines" %}}

- `TF_BUILD`
- `BUILD_DEFINITIONNAME`
- `BUILD_BUILDID`
- `BUILD_SOURCESDIRECTORY`
- `BUILD_REPOSITORY_URI`
- `BUILD_SOURCEBRANCH`
- `BUILD_SOURCEVERSION`
- `BUILD_SOURCEVERSIONMESSAGE`
- `BUILD_REQUESTEDFORID`
- `BUILD_REQUESTEDFOREMAIL`
- `SYSTEM_TEAMFOUNDATIONSERVERURI`
- `SYSTEM_TEAMPROJECTID`
- `SYSTEM_JOBID`
- `SYSTEM_TASKINSTANCEID`
- `SYSTEM_PULLREQUEST_SOURCEREPOSITORYURI`
- `SYSTEM_PULLREQUEST_SOURCEBRANCH`
- `SYSTEM_PULLREQUEST_SOURCECOMMITID`
- `SYSTEM_STAGEDISPLAYNAME`
- `SYSTEM_JOBDISPLAYNAME`

[Liste complète des variables d'environnement de build fournies par Azure Pipelines][1]


[1]: https://docs.microsoft.com/en-us/azure/devops/pipelines/build/variables?view=azure-devops
{{% /tab %}}
{{% tab "Bitbucket Pipelines" %}}

- `BITBUCKET_PIPELINE_UUID`
- `BITBUCKET_BUILD_NUMBER`
- `BITBUCKET_CLONE_DIR`
- `BITBUCKET_REPO_FULL_NAME`
- `BITBUCKET_GIT_SSH_ORIGIN`
- `BITBUCKET_COMMIT`
- `BITBUCKET_BRANCH`
- `BITBUCKET_TAG`

[Liste complète des variables d'environnement de build fournies par Bitbucket Pipelines][1]


[1]: https://support.atlassian.com/bitbucket-cloud/docs/variables-and-secrets/
{{% /tab %}}
{{% tab "Bitrise" %}}

- `BITRISE_BUILD_SLUG`
- `BITRISE_TRIGGERED_WORKFLOW_ID`
- `BITRISE_BUILD_NUMBER`
- `BITRISE_BUILD_URL`
- `BITRISE_SOURCE_DIR`
- `GIT_REPOSITORY_URL`
- `BITRISE_GIT_COMMIT`
- `GIT_CLONE_COMMIT_HASH`
- `BITRISEIO_GIT_BRANCH_DEST`
- `BITRISE_GIT_BRANCH`
- `BITRISE_GIT_TAG`
- `BITRISE_GIT_MESSAGE`
- `BITRISE_APP_TITLE`
- `GIT_CLONE_COMMIT_MESSAGE_SUBJECT`
- `GIT_CLONE_COMMIT_MESSAGE_BODY`
- `GIT_CLONE_COMMIT_AUTHOR_NAME`
- `GIT_CLONE_COMMIT_AUTHOR_EMAIL`
- `GIT_CLONE_COMMIT_COMMITER_NAME`
- `GIT_CLONE_COMMIT_COMMITER_EMAIL`

[Liste complète des variables d'environnement de build fournies par Bitrise][1]


[1]: https://devcenter.bitrise.io/en/references/available-environment-variables.html
{{% /tab %}}
{{% tab "Buildkite" %}}

- `BUILDKITE`
- `BUILDKITE_PIPELINE_SLUG`
- `BUILDKITE_JOB_ID`
- `BUILDKITE_BUILD_ID`
- `BUILDKITE_BUILD_NUMBER`
- `BUILDKITE_BUILD_URL`
- `BUILDKITE_BUILD_CHECKOUT_PATH`
- `BUILDKITE_REPO`
- `BUILDKITE_COMMIT`
- `BUILDKITE_BRANCH`
- `BUILDKITE_TAG`
- `BUILDKITE_MESSAGE`
- `BUILDKITE_BUILD_AUTHOR`
- `BUILDKITE_BUILD_AUTHOR_EMAIL`
- `BUILDKITE_BUILD_CREATOR`
- `BUILDKITE_BUILD_CREATOR_EMAIL`
- `BUILDKITE_AGENT_ID`
- `BUILDKITE_AGENT_META_DATA_*`

[Liste complète des variables d'environnement de build fournies par Buildkite][1]


[1]: https://buildkite.com/docs/pipelines/environment-variables
{{% /tab %}}
{{% tab "CircleCI" %}}

- `CIRCLECI`
- `CIRCLE_PROJECT_REPONAME`
- `CIRCLE_BUILD_NUM`
- `CIRCLE_BUILD_URL`
- `CIRCLE_WORKFLOW_ID`
- `CIRCLE_WORKING_DIRECTORY`
- `CIRCLE_REPOSITORY_URL`
- `CIRCLE_SHA1`
- `CIRCLE_BRANCH`
- `CIRCLE_TAG`
- `CIRCLE_JOB`

[Liste complète des variables d'environnement de build fournies par CircleCI][1]


[1]: https://circleci.com/docs/2.0/env-vars/#built-in-environment-variables
{{% /tab %}}
{{% tab "Codefresh" %}}

- `CF_BUILD_ID`
- `CF_PIPELINE_NAME`
- `CF_BUILD_URL`
- `CF_STEP_NAME`
- `CF_BRANCH`
- `CF_REVISION`

[Liste complète des variables d'environnement de build fournies par Codefresh][1]


[1]: https://codefresh.io/docs/docs/pipelines/variables/
{{% /tab %}}
{{% tab "GitHub Actions" %}}

- `GITHUB_ACTION`
- `GITHUB_SERVER_URL`
- `GITHUB_RUN_ID`
- `GITHUB_RUN_NUMBER`
- `GITHUB_RUN_ATTEMPT`
- `GITHUB_WORKFLOW`
- `GITHUB_WORKSPACE`
- `GITHUB_REPOSITORY`
- `GITHUB_SHA`
- `GITHUB_HEAD_REF`
- `GITHUB_REF`
- `GITHUB_JOB`

[Liste complète des variables d'environnement de build fournies par GitHub Actions][1]


[1]: https://docs.github.com/en/free-pro-team@latest/actions/reference/environment-variables#default-environment-variables
{{% /tab %}}
{{% tab "GitLab CI" %}}

- `GITLAB_CI`
- `CI_PIPELINE_ID`
- `CI_PIPELINE_URL`
- `CI_PIPELINE_IID`
- `CI_PROJECT_PATH`
- `CI_PROJECT_DIR`
- `CI_JOB_STAGE`
- `CI_JOB_NAME`
- `CI_JOB_URL`
- `CI_JOB_ID`
- `CI_RUNNER_ID`
- `CI_RUNNER_TAGS`
- `CI_REPOSITORY_URL`
- `CI_COMMIT_SHA`
- `CI_COMMIT_REF_NAME`
- `CI_COMMIT_BRANCH`
- `CI_COMMIT_TAG`
- `CI_COMMIT_AUTHOR`
- `CI_COMMIT_MESSAGE`
- `CI_COMMIT_TIMESTAMP`

[Liste complète des variables d'environnement de build fournies par GitLab CI][1]


[1]: https://docs.gitlab.com/ee/ci/variables/predefined_variables.html
{{% /tab %}}
{{% tab "Jenkins" %}}

- `JENKINS_URL`
- `BUILD_TAG`
- `BUILD_NUMBER`
- `BUILD_URL`
- `WORKSPACE`
- `JOB_NAME`
- `JOB_URL`
- `GIT_URL`
- `GIT_URL_1`
- `GIT_COMMIT`
- `GIT_BRANCH`
- `NODE_NAME`
- `NODE_LABELS`
- `DD_CUSTOM_TRACE_ID` (variable personnalisée définie par le [plug-in Jenkins Datadog][2])
- `DD_CUSTOM_PARENT_ID` (idem)

[Liste complète des variables d'environnement de build fournies par Jenkins][1]


[1]: https://wiki.jenkins.io/display/JENKINS/Building+a+software+project
[2]: https://github.com/jenkinsci/datadog-plugin
{{% /tab %}}
{{% tab "TeamCity" %}}

- `TEAMCITY_VERSION`
- `TEAMCITY_BUILDCONF_NAME`
- `BUILD_URL`
- `DATADOG_BUILD_ID` (variable personnalisée définie par l'[intégration Datadog/TeamCity][2])

[Liste complète des variables d'environnement de build fournies par TeamCity][1]


[1]: https://www.jetbrains.com/help/teamcity/predefined-build-parameters.html
[2]: https://plugins.jetbrains.com/plugin/20852-datadog-ci-integration
{{% /tab %}}
{{% tab "Travis CI" %}}

- `TRAVIS`
- `TRAVIS_BUILD_ID`
- `TRAVIS_BUILD_NUMBER`
- `TRAVIS_BUILD_WEB_URL`
- `TRAVIS_BUILD_DIR`
- `TRAVIS_JOB_WEB_URL`
- `TRAVIS_REPO_SLUG`
- `TRAVIS_COMMIT`
- `TRAVIS_BRANCH`
- `TRAVIS_TAG`
- `TRAVIS_PULL_REQUEST_SLUG`
- `TRAVIS_PULL_REQUEST_BRANCH`
- `TRAVIS_COMMIT_MESSAGE`

[Liste complète des variables d'environnement de build fournies par Travis CI][1]


[1]: https://docs.travis-ci.com/user/environment-variables/#default-environment-variables
{{% /tab %}}
{{% tab "Buddy CI" %}}

- `BUDDY`
- `BUDDY_SCM_URL`
- `BUDDY_EXECUTION_REVISION`
- `BUDDY_EXECUTION_BRANCH`
- `BUDDY_EXECUTION_TAG`
- `BUDDY_PIPELINE_ID`
- `BUDDY_EXECUTION_ID`
- `BUDDY_PIPELINE_NAME`
- `BUDDY_EXECUTION_URL`
- `BUDDY_EXECUTION_REVISION_MESSAGE`
- `BUDDY_EXECUTION_REVISION_COMMITTER_NAME`
- `BUDDY_EXECUTION_REVISION_COMMITTER_EMAIL`

[Liste complète des variables d'environnement de build fournies par Buddy CI][1]


[1]: https://buddy.works/docs/pipelines/environment-variables#default-environment-variables
{{% /tab %}}
{{< /tabs >}}

[1]: https://docs.docker.com/engine/reference/run/
[2]: https://docs.docker.com/compose/reference/
[3]: /fr/continuous_integration/tests/