## Setup

### Download boot-tools

> See https://docs.onflow.org/node-operation/node-bootstrap/

### Generate your node keys

```
$ FLOW_GO_HOST=example.dev:3569
$ ./boot-tools/bootstrap key \
  --address "${FLOW_GO_HOST}" \
  --role access \
  -o ./bootstrap
```

If on mac, just run via docker

```
$ FLOW_GO_HOST=example.dev:3569
$ docker run --rm -it -v "$(pwd):/access" -w /access alpine:latest \
  ./boot-tools/bootstrap key \
  --address "${FLOW_GO_HOST}" \
  --role access \
  -o ./bootstrap
```
