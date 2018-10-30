# To publish

Creds are found in lastpass. `VERSION` should be something like OS-OS_VERSION, for example, if building using alpine-3.8, use tag `ALPINE-3.8`.

```
docker login
docker build -t better/docker-scala:VERSION .
docker push better/docker-scala:VERSION
docker logout
```
