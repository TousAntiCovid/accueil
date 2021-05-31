# Conventions Kafka

## Objet

Fixer les conventions d'usage kafka. Elles s'inspirent de [ce post sur devshawn.com](https://devshawn.com/blog/apache-kafka-topic-naming-conventions/).

## Nommage des topic

Les noms des topics :

- sont en minuscules
- ne contiennent que les caractères `a-z`, `0-9`, `-` et `.`
- `.` est un caractère réservé pour séparer les termes qui structurent le nom du topic
- si un terme est composé de plusieurs mots, il utilise le _kebab-base_
- sont structurés de la manière suivante :

      <environnement>.<domaine>.<classification>.<description>(.<version>)?

      environnement:  [ "int" | "preprod" | "prod" ]
      domaine:        mots
      classification: [ "fct" | "cdc" | "cmd" | "sys" ]
      description:    mots
      version:        nombre
      mot:            [a-z0-9]+
      nombre:         [0-9]+

### Domaine

Le domaine métier de la donnée.

### Types de classification

Extrait de [devshawn.com](https://devshawn.com/blog/apache-kafka-topic-naming-conventions/) :

> The classification of data within a Kafka topic tells an end-user how it should be interpreted or used. This should not tell us about data format or contents. I typically use the following classifications:
> - fct: Fact data is information about a thing that has happened. It is an immutable event at a specific point in time. Examples of this include data from sensors, user activity events, or notifications.
> - cdc: Change data capture (CDC) indicates this topic contains all instances of a specific thing and receives all changes to those things. These topics do not capture deltas and can be used to repopulate data stores or caches. These are commonly found as compacted topics within Kafka.
> - cmd: Command topics represent operations that occur against the system. This is typically found as the request-response pattern, where you have a verb and a statement. Examples might include update-user and user-updated.
> - sys: System topics are used for internal topics within a single service. They are operational topics that do not contain any relevant information outside of the owning system. These topics are not meant for public consumption.

### Description

Nom d'évènement décrivant la donnée transportée dans le topic.

### Version

Numéro de version du topic.

