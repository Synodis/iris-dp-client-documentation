---
layout: default
title: Démarrer avec l'api FHIR d'Iris Dp
---

Chaque appel à l'api doit être fait avec une clé d'api. La clé d'api peut se générer avec l'interface de [création de compte]().
Une fois votre clé obtenue vous aurez accès à l'api. 

## Votre premier appel Api

Pour cette section nous utilisons curl qui est un outil présent sur la pluspart des plateformes windows 10+, macos, linux.

Lancez la commande suivante pour récupérer le CapabilityStatement FHIR (liste des fonctionnalités du serveur) : 

```bash
curl -H "E-SANTE-API: XXXX-XXXXX-XXXXX" https://ans.com/fhir/metadata?_pretty=true&_format=json
```

Si tout c'est bien passé, vous devriez avoir un résultat similaire à : 

```json
{
  "resourceType": "CapabilityStatement",
  "fhirVersion": "4.0.1",
  "format": [ "application/fhir+xml", "xml", "application/fhir+json", "json" ],
  "rest": [ {
    "mode": "server",
    "resource": [ {
      "type": "Device",
      "profile": "https://apifhir.annuaire.sante.fr/ws-sync/exposed/structuredefinition/Device-rass",
      "interaction": [ {
        "code": "create"
      }, {
        "code": "read"
      }, {
        "code": "search-type"
      }, {
        "code": "update"
      } ],
      "searchInclude": [ "*", "Device:organization" ],
      "searchRevInclude": [ "Device:location", "Device:organization", "HealthcareService:organization", "Organization:endpoint", "Organization:partof", "PractitionerRole:organization", "PractitionerRole:partof", "PractitionerRole:practitioner" ],
      "searchParam": [ {
        "name": "_id",
        "type": "token",
        "documentation": "Recherche sur l'id de la ressource Device"
      }, {
        "name": "_lastUpdated",
        "type": "date",
        "documentation": "Renvoie uniquement les ressources qui ont été mises à jour pour la dernière fois comme spécifié par la periode donnée"
      }, {
        "name": "device-name",
        "type": "string",
        "documentation": "The device name"
      },
    ...
```

NOTE| Le capability statement permet de connaitre les fonctionnalités disponible sur le serveur FHIR (paramètres, ressources...).


Vous pouvez lancer la même requête sur une ressource par exemple pour récupérer les Practitioner:

```bash
curl -H "E-SANTE-API: XXXX-XXXXX-XXXXX" https://ans.com/fhir/Practitioner?_pretty=true&_format=json
```

La réponse devrait ressembler à cela :

```json
{
  "resourceType": "Bundle",
  "id": "fa4acb34-0a58-4a29-8d37-7d7768c1d4fd",
  "meta": {
    "lastUpdated": "2022-07-16T15:04:07.141+02:00"
  },
  "type": "searchset",
  "total": 10000,
  "link": [ {
    "relation": "self",
    "url": "..."
  }, {
    "relation": "next",
    "url": "..."
  } ],
  "entry": [ {
    "fullUrl": "https://.../fhir/v1/Practitioner/pra-59",
    "resource": {
      "resourceType": "Practitioner",
      "id": "pra-59",
      "meta": {
        "versionId": "1",
        "lastUpdated": "2022-07-16T12:40:56.316+02:00",
        "profile": [ "https://apifhir.annuaire.sante.fr/ws-sync/exposed/structuredefinition/practitioner-rass" ]
      },
    }
  }, {
    "fullUrl": "https://.../fhir/v1/Practitioner/pra-57",
    "resource": {
      "resourceType": "Practitioner",
      "id": "pra-57",
      "meta": {
        "versionId": "1",
        "lastUpdated": "2022-07-16T12:40:56.318+02:00",
        "profile": [ "https://apifhir.annuaire.sante.fr/ws-sync/exposed/structuredefinition/practitioner-rass" ]
      },
      ...
    }
  }
  ...
  ]
}
```



## Aller plus loins 


### Ressources interne 

<div class="wysiwyg" markdown="1">
* [Documentation détaillée par ressource]({{ '/pages/documentation/resources/practitioner.html' | relative_url }})
* [Use case de synchronisation]({{ '/pages/use-cases/full/index' | relative_url }})
* [Use d'appels unitaires]({{ '/pages/use-cases/practitioner-detail/index' | relative_url }})
</div>

### Ressources externes

<div class="wysiwyg" markdown="1">
* [Site officiel de FHIR](https://www.hl7.org/fhir/){:target="_blank"}
* [Librairie Java FHIR](https://hapifhir.io/){:target="_blank"}
* [Profils de l'annuaire santé](TODO){:target="_blank"}
</div>
