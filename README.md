# Docker Images

A set of custom docker images for CI.

# Test locally

As an example, in order to build the `php70` image, run

    $ docker build gridonic/php70 php70
    
Then, you might want to start a basic shell in your container

    $ docker run -t -i gridonic/php70 /bin/bash
