# Démarrer avec l'api FHIR d'Iris Dp

Chaque appel à l'api doit être fait avec une clé d'api. La clé d'api peut se générer avec l'interface de [création de compte]().
Une fois votre clé obtenue vous aurez accès à l'api. 

## Votre premier appel Api

Pour cette section nous utilisons curl qui est un outil présent sur la pluspart des plateformes windows 10+, macos, linux.

Lancez la commande suivante pour récupérer le CapabilityStatement FHIR (liste des fonctionnalités du serveur) : 

``` bash
curl -H "E-SANTE-API: XXXX-XXXXX-XXXXX" https://ans.com/fhir/metadata
```

Si tout c'est bien passé, vous devriez avoir un résultat similaire à : 

``` json
{
    "type": "CapabilityStatement"
}
```

