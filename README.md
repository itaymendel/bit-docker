# Docker image for running remote Bit scope

To ease the process of using Bit, you can use this docker image to run a remote scope for developing
and testing changes in Bit.

Run remote scope with latest bit version:
=================================

    docker run --rm --name bit -d -P  --volume ~/.ssh/id_rsa.pub:/tmp/id_rsa.pub bitteam/bit-docker


developing bit and testing:
===========================

    docker run --rm --name bit -d -P  --volume <path to bit code>:/bit-bin  --volume ~/.ssh/id_rsa.pub:/tmp/id_rsa.pub --env 'DEVELOPMENT=true' bitteam/bit-docker


Get working port of docker container:
=====================================
    docker port bit 22

Then use port to add remote scope

    bit remote add ssh://root@localhost:<port>:/tmp/scope -g
      
    
Build image:
============

    docker build . -t bit
    
