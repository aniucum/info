### Introduction to heredocs in Dockerfiles
- https://www.docker.com/blog/introduction-to-heredocs-in-dockerfiles/

```
RUN <<EOF
echo "Hello" >> /hello
echo "World!" >> /hello
EOF
```