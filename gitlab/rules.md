```
 rules:
 - if: $FOO == "BAR"
   when: manual 
 - if: $CI_COMMIT_BRANCH == "dev" && $FOO =~ /^dev.*/
   when: always   
 - if: $CI_COMMIT_BRANCH == "main" && $FOO !~ /^dev.*/
   when: manual
 - when: never 
```