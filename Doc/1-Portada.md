[Index](1-Portada.md) - [Siguiente](2-Kube_simple.md)

---------------------------------

Kubernetes HA sobre OpenStack
=============================

Proyecto Celtic Kubernetes de fin de ciclo de ASIR (sysadmin) IES Gonzalo Nazareno (Dos Hermanas, España)

* [Contacto](Contacto.md)

El escenario tiene sus nombres tomados de los dioses Celtas de la siguiente entrada de la Wikipedia [enlace](https://es.wikipedia.org/wiki/Categor%C3%ADa:Dioses_celtas) donde podrás consultar su descripción.


Índice de contenido
-------------------
*******************
1. [Portada proyecto](1-Portada.md)
2. [Despliegue simple Kubernetes](2-Kube_simple.md)
3. [Despliegue Kubernetes cluster en HA masters y minions](3-Kube_HA_pcs.md)
4. [Addons para Kubernetes](4-Addons.md)
5. [Exponer servicios internos de Kubernetes](5-Exponer_svc.md)
6. [Almacenamiento persistente para Kubernetes](6-Almacenamiento.md)
7. [Explotando Kubernetes](7-Explotando_kubernetes.md)
8. [Kubernetes con Ansible](8-Kubernetes_ansible.md)

#### Los nombres elegidos son

| Nombre      | Función         | Numero  |
|-------------------|-----------------------|-----------|
| [**Taranis**](https://es.wikipedia.org/wiki/Taranis)    | Proxy         | 1     |
| [**Belenus**](https://es.wikipedia.org/wiki/Belenus)    | Proxy         | 2     |
| [**Morrigan**](https://es.wikipedia.org/wiki/Morrigan)    | KMaster         | 1     | 
| [**Balar**](https://es.wikipedia.org/wiki/Balar)      | KMaster         | 2     |
| [**Artio**](https://es.wikipedia.org/wiki/Artio)      | KMinion       | 1     |
| [**Esus**](https://es.wikipedia.org/wiki/Esus)    | KMinion         | 2     |
| [**Angus**](https://es.wikipedia.org/wiki/Angus_(mitología))      | Almacenamiento    | 1     |
| [**Dagda**](https://es.wikipedia.org/wiki/Dagda)      | Almacenamiento    | 2     | 

-----------------------------

## Definiendo Kubernetes

[![GoReportCard Widget]][GoReportCard] [![GoDoc Widget]][GoDoc] [![Travis Widget]][Travis] [![Coverage Status Widget]][Coverage Status]

[GoDoc]: https://godoc.org/k8s.io/kubernetes
[GoDoc Widget]: https://godoc.org/k8s.io/kubernetes?status.svg
[GoReportCard]: https://goreportcard.com/report/k8s.io/kubernetes
[GoReportCard Widget]: https://goreportcard.com/badge/k8s.io/kubernetes
[Travis]: https://travis-ci.org/kubernetes/kubernetes
[Travis Widget]: https://travis-ci.org/kubernetes/kubernetes.svg?branch=master
[Coverage Status]: https://coveralls.io/r/kubernetes/kubernetes
[Coverage Status Widget]: https://coveralls.io/repos/kubernetes/kubernetes/badge.svg


<hr>

Kubernetes es un orquestador de [contenedores](https://github.com/kubernetes/kubernetes/wiki/Why-Kubernetes%3F#why-containers) open source a través de múltiples hosts, proporcionar mecanismos básicos para el despliegue, mantenimiento y escalado de aplicaciones.

Kubernetes es:

* **liviano**: ligero, sencillo, accesible
* **portable**: publico, privado, hibrido, multi cloud
* **extensible**: modular
* **Autonomo**: gestion de contenedores de forma autonoma

Kubernetes se basa en una [década y media de experiencia en Google para ejecutar cargas de trabajo de producción](https://research.google.com/pubs/pub43438.html), combinado con las ideas y las mejores prácticas de la comunidad.

<hr>

## Conceptos

Kubernetes trabaja con los siguientes conceptos:

[**Cluster**](https://github.com/kubernetes/kubernetes/blob/master/docs/admin/README.md)
Un cluster es un conjunto de máquinas virtuales o físicas de infraestructura y otros recursos utilizados por Kubernetes para ejecutar los contenedores. 

[**Node**](https://github.com/kubernetes/kubernetes/blob/master/docs/admin/node.md)
Un nodo es un equipo físico o virtual con Kubernetes, en la que las pods pueden ejecutarse.

[**Pod**](https://github.com/kubernetes/kubernetes/blob/master/docs/user-guide/pods.md)
Los pods son un grupo contenedores de aplicaciones con volúmenes compartidos. Son las unidades de despliegue más pequeñas que se pueden crear, programadas y gestionadas con Kubernetes. Los pods se pueden crear de forma individual, pero se recomienda que utilice un controlador de replica incluso si la creación es de un sola pod.

[**Replication controller**](docs/user-guide/replication-controller.md)
Los controladores de replicación gestionar el ciclo de vida de los pods. Se aseguran de que un determinado número de pods están ejecutando en cualquier momento dado, creando o matando los pods que se definan.

[**Service**](https://github.com/kubernetes/kubernetes/blob/master/docs/user-guide/services.md)
Los servicios proporcionan un unico, nombre estable y dirección para un conjunto de pods.
Ellos actúan como balanceadores de carga entre los pods del servicio.

[**Label**](https://github.com/kubernetes/kubernetes/blob/master/docs/user-guide/labels.md)
Las etiquetas se utilizan para organizar y seleccionar grupos de objetos en función de clave: valor.