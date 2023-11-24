### How to enable maven artifact caching for GitLab CI runner?
- https://stackoverflow.com/questions/37785154/how-to-enable-maven-artifact-caching-for-gitlab-ci-runner
```
cache:
  paths:
    - .m2/repository

variables:
  MAVEN_OPTS: "-Dmaven.repo.local=$CI_PROJECT_DIR/.m2/repository"

maven_job:
  script:
    - mvn clean install
```