# syntax=docker/dockerfile:1

## Build Image
FROM golang:1.18-bullseye as build

WORKDIR /evmos
COPY . /evmos

RUN BUILD_TAGS=muslc make build-e2e-chain-init

## Deploy image
FROM ubuntu

COPY --from=build /evmos/build/chain_init /bin/chain_init

ENV HOME /evmos
WORKDIR $HOME

ENTRYPOINT [ "chain_init" ]
