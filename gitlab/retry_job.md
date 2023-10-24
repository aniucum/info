https://forum.gitlab.com/t/retry-a-job-multiple-times/58245/5
```
stage: run
image: ruby:2.7
before_script:
    - bundle install --path vendor/bundle
script:
    - |
      set +o errexit
      END=10
      for i in $(seq 1 $END); do
          echo "run $i time"
          bundle exec ... && exit 0
      done
      exit 1
```