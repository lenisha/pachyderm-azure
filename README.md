## Run Pachctl tool in separate cluster

- Run docker image containing the `pachctl` tool in the container (as published in Dockerfile.pachctl )

```
kubectl run -it --rm pachctl --image=lenisha/pachctl --generator=run-pod/v1
```


- To point `pachctl` tool to API in different cluster use

```
   pachctl config update context default --pachd-address "xxxxxx:30750"
   pachctl version
```

Where xxxxxx - is address for the API LoadBalancer exposed for pachd service

- Verify

```
  pachctl config get context default
  or
  cat ~/.pachyderm/config.json
```

## Access PACHD Dashboard

- Expose dash-lb service `kubectl apply -f dash.yaml`

- Check IP of LoadBalancer `kubectl get svc`

- Access Dashboard

```
http://<dash-host>:8080/app?port=8081
```

where `port` parameter points to exposed grpc port for websocket communication



## References
[https://github.com/pachyderm/pachyderm/issues/3232](https://github.com/pachyderm/pachyderm/issues/3232)
[https://docs.pachyderm.io/en/latest/pachctl/pachctl_config_update_context.html?highlight=address](https://docs.pachyderm.io/en/latest/pachctl/pachctl_config_update_context.html?highlight=address)
[https://docs.pachyderm.io/en/latest/reference/config_spec.html](https://docs.pachyderm.io/en/latest/reference/config_spec.html)
