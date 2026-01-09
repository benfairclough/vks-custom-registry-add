Perform this before building the VKS cluster:

You will need the cert in its raw base64 encoded form, you then need to double base64 encode it:
Example.

From a terminal with base64 installed:
base64 my-cert-1.crt | base64


When creating the VKS cluster call the secret in the VKS YAML  - Sample below:

Key parts are the array -name: osConfiguration and then the below snippet

    variables:
      - name: vmClass
        value: guaranteed-medium
      - name: storageClass
        value: storage-profile
      - name: osConfiguration
        value:
          trust:
            additionalTrustedCAs:
              - caCert:
                  secretRef:
                    key: my-cert-1
                    name: VKS-CLUSTER-trusted-ca-secret
