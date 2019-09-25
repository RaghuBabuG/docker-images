# Copyright (c) 2019 Oracle and/or its affiliates. All rights reserved.
#
# Licensed under the Universal Permissive License v 1.0 as shown at http://oss.oracle.com/licenses/upl.
#
# ORACLE DOCKERFILES PROJECT
# --------------------------
# This is the Dockerfile for Remote Data Gateway V2 installer
# 
# REQUIRED FILES TO BUILD THIS IMAGE
# ----------------------------------
# (1) bi_rdc_client-<version>.bin
#     Download the above installer file from https://www.oracle.com/middleware/technologies/oac-downloads.html
#
# HOW TO BUILD THIS IMAGE
# -----------------------
# Put all downloaded files in the same directory as this Dockerfile
# Run: 
#      $ docker build -t oracle/rdc:v2 . 
#
# Pull base image
# ---------------
FROM oraclelinux:6-slim

#Common ENV - if not passed user default values
ENV username admin
ENV pwd welcome1

#Create RDC home and add 'oracle' as user
RUN useradd -b /rdc -d /rdc -m -s /bin/bash oracle && \
    mkdir -p /rdc && \
    mkdir -p /rdc/oraInventory && \
    cd /rdc

WORKDIR /rdc

# Copy packages
COPY bi_rdc_client.bin /rdc
COPY rdc-response-file.rsp /rdc
COPY oraInst.loc /rdc
COPY runJetty /rdc

RUN chmod 777 /rdc/*

# Install
USER oracle

# prepare for config
EXPOSE 8080

CMD ["sh", "-c", "/rdc/runJetty ${username} ${pwd}"]
