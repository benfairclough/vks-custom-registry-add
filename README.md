Perform this before building the VKS cluster:

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
                    key: additional-ca-1
                    name: clustera-user-trusted-ca-secret
