## Run Pachctl tool

- Run docker image containing the `pachctl` tool in the container (as published in Dockerfile.pachctl )

```
kubectl run -it --rm pachctl --image=lenisha/pachctl --generator=run-pod/v1
```


- To point `pachctl` tool to API in different cluster use

```
   pachctl config update context default --pachd-address "13.71.186.168:30750"
   pachctl version
```

- Verify

```
  pachctl config get context default
  or
  cat ~/.pachyderm/config.json
```
