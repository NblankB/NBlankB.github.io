---
layout: post
title:  "Kubernetes CKA 준비 - 1. AWS 기반 VM으로 H.A 구축"
date: 2022-10-17 20:55:49 +0900
category: Kubernetes
---
#  

블로그 이사 하면서 쓰는 첫 글  
언제 끝날지...
  
{: toc}  

## H.A(High Availavility, 고가용성)
- kubernetes.io - [HA Topology](https://kubernetes.io/ko/docs/setup/production-environment/tools/kubeadm/ha-topology/), RedHat - [High Availability Containers](https://www.redhat.com/ko/topics/containers/high-availability-containers)
- 인프라, 애플리케이션 등을 오랜 기간 지속적인 운영이 가능하도록 하는 구성
- 마스터의 HA 구성에는 1대 이상의 마스터가 필요하지만 etcd의 구조에 의해 3대 이상 홀수대의 노드로 구성하는 것이 좋다.  
![HACluster1](https://d33wubrfki0l68.cloudfront.net/d1411cded83856552f37911eb4522d9887ca4e83/b94b2/images/kubeadm/kubeadm-ha-topology-stacked-etcd.svg)  
![HACluster2](https://d33wubrfki0l68.cloudfront.net/ad49fffce42d5a35ae0d0cc1186b97209d86b99c/5a6ae/images/kubeadm/kubeadm-ha-topology-external-etcd.svg)[^1]
- 편의성을 위해 stacked etcd로 구성해보려 한다.

### 환경
- AWS Instances(t3.large-gp3-20gb, Ubuntu20.04), Calico network plugin, Kubernetes v1.24.0  

![Bench](https://miro.medium.com/max/720/1*zDiFQZVXuL923x0LbmXMaA.png)[^2]  
이전까지


---
### 각주
{: .no_toc}  
[^1]: google kubernetes  
[^2]: itnext  