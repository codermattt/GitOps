# Application workflow
- the application containers in the helm charts were taken off my docker hub repo https://hub.docker.com/repositories/devopper000 and
  the rest of the servies (memcache, rabbitmq) were taken off their original docker containers
- the application was then uploaded to aws ecr, and the helm charts deployed on the eks cluster
