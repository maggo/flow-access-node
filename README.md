## Setup

### Download boot-tools

> See https://docs.onflow.org/node-operation/node-bootstrap/

If not on linux start an alpine linux shell and run the commands there (boot-tools are linux only)

```
$ docker run --rm -it -v "$(pwd):/access" -w /access alpine:latest
```

### Generate your node keys

Replace `NODE_HOST` with your public host eg `example.dev:3569`

```
$ ./boot-tools/bootstrap key \
  --address NODE_HOST \
  --role access \
  -o ./bootstrap
```

### Upload your public keys

Replace `TOKEN` with your token name, should be `mainnet-$CURRENT_MAINNET-$ID` eg. `mainnet-11-yourname`

```
$ ./boot-tools/transit push -b ./bootstrap -t TOKEN -r access
```

### Have your keys included in the next spork

Fill out the node operator application @ https://www.onflow.org/node-validators

and wait for the next spork.

## Run your node

### Pull the latest genesis info

Replace `TOKEN` with the token found at https://docs.onflow.org/node-operation/node-bootstrap/#step-4---start-your-flow-node

```
$ ./boot-tools/transit pull -b ./bootstrap -t TOKEN  -r access
```

### Boot your node

```
$ FLOW_GO_NODE_VERSION=latest FLOW_GO_NODE_ID=$(cat ./bootstrap/public-root-information/node-id) docker-compose up
```
