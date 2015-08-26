  This is a simple role which rebuilds a docker container, this may be necessary sometimes if you are building a local image and need the containers which use that image to be rebuilt using continuous integration, below is a sample playbook that you could work off of :) Feel free to PR and fork :D
  
    ---
    - hosts: local
      vars:
      - volumes:
        - "/home/code/postgresdesign:/usr/local/apache2/htdocs/nerdsville/postgresdesign"
      - ports:
        - "80:80"
      roles:
        - role: rebuild_docker_container
          container_name: apache-proxy-1
          image_name: apache-reverse-proxy
