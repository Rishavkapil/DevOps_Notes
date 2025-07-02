

A ConfigMap is an api object used to store non-confidential data in key-value pairs. Pods can consume configMaps as environment variables, command-line arguments, or as configuration files in a volume. 

A ConfigMap allows you to decouple environment-specific configuration from your container images, so that your applications are easily portable. 


NOTE : ConfigMap does not provide secrecy or encryption. If the data you want to store in confidential , then use a Secret rather than configMap