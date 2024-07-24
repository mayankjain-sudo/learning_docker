FROM alpine:3.18 AS build

ARG PACKER_VERSION="1.9.1"
ARG PACKER_VERSION_SHA256SUM="ed1ac407ec3ce421beb221f8869cdc0998fbefb96cb9b89e71e47f9a1421fdee"

RUN wget https://releases.hashicorp.com/packer/1.9.1/packer_1.9.1_linux_arm64.zip

#COPY packer_${PACKER_VERSION}_linux_amd64.zip .
RUN echo "${PACKER_VERSION_SHA256SUM}  packer_${PACKER_VERSION}_linux_arm64.zip" > checksum && sha256sum -c checksum

RUN /usr/bin/unzip packer_${PACKER_VERSION}_linux_arm64.zip


FROM gcr.io/google.com/cloudsdktool/cloud-sdk:slim
RUN apt-get -y update && apt-get -y install ca-certificates && rm -rf /var/lib/apt/lists/*
COPY --from=build packer /usr/bin/packer
ENTRYPOINT ["/usr/bin/packer"]