# KeyVault

Secure key management is essential to protect data in the cloud. Use Azure Key Vault to encrypt keys and small secrets like passwords that use keys stored in hardware security modules (HSMs). For more assurance, import or generate keys in HSMs, and Microsoft processes your keys in FIPS validated HSMs (hardware and firmware) - FIPS 140-2 Level 2 for vaults and FIPS 140-2 Level 3 for HSM pools. With Key Vault, Microsoft doesn’t see or extract your keys. Monitor and audit your key use with Azure logging—pipe logs into Azure HDInsight or your security information and event management (SIEM) solution for more analysis and threat detection.

## Version 1.0.0.0

```
{
	"type": "Microsoft.Resources/deployments",
	"apiVersion": "2020-06-01",
	"name": "[concat(deployment().name, '-', variables('keyVaultName'))]",
	"properties": {
		"mode": "Incremental",
		"templateLink": {
			"id": "[resourceId('ComponentSpecs', 'Microsoft.Resources/templateSpecs/versions', 'KeyVault', '1.0.0.0')]"
		},
		"parameters":{
			"name" :{
				"value": "[variables('keyVaultName')]"
			}
		}
	}
}
```

### Parameters

Name | Mandatory | Type | Default Value
------------ | ------------- | ------------- | -------------
name | yes | string |
location | no | string| [resourceGroup().location]
enabledForDeployment | no | bool | false
enabledForTemplateDeployment | no | bool | false
enabledForDiskEncryption | no | bool | false

### Outputs

Name | Type 
------------ | ------------- 
resourceId | string 
