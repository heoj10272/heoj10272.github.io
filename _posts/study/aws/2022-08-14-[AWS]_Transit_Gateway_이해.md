---
layout: post
title: "[AWS] Transit Gateway 이해"
subtitle: AWS
date: '2022-08-14 18:00:00 +0900'
category: study
tags: aws aws-base
image:
  path: /assets/img/study_AWS/2022-08-14-[AWS]_Transit_Gateway_이해/logo.png
---

AWS의 Transit Gateway를 이해해보자.

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<br>

# 1. Transit Gateway 개요
---

>`Transit Gateway`는 가상 사설 클라우드(VPC)와 온프레미스 네트워크를 상호 연결하는 데 사용할 수 있는 네트워크 전송 허브입니다.<br>
>클라우드 인프라가 전 세계적으로 확장됨에 따라 리전 간 피어링은 AWS 글로벌 인프라를 사용하여 `Transit Gateway`를 함께 연결합니다. <br>
>데이터는 자동으로 암호화되며 퍼블릭 인터넷을 통해 전송되지 않습니다.
>
> AWS `Transit Gateway` Docs

즉 `Transit Gateway`는 네트워크 전송 허브(라우터)로서, 서로 다른 VPC간의 통신을 가능하게 하는 서비스이다.<br>
기존의 `VPC Peering`의 경우 1대 1 VPC 연결만 지원함에 따라 직접적으로 연결되지 않은 VPC에 바로 접근할 수 없었다면(전이적 피어링) `Transit Gateway`는 중앙 집중 허브를 통해 여러개의 VPC간 연결 정책을 중앙에서 관리할 수 있고, VPN을 통해 VPC와 온프레미스 네트워크를 연결할 수 있다.

# 2. Transit Gateway 특징
---

+ 여러 VPC와 연결 가능
+ 중앙 허브와 VPN을 통해 VPC와 온프레미스 네트워크 연결 가능
+ 복잡한 피어링 관계를 제거하여 네트워크 간소화
+ 다른 리전간의 `Transit Gateway`와 피어링 연결 가능
+ 새로운 네트워크를 한 번의 연결을 통해 추가 가능
+ 향상된 보안
    - 공용 네트워크에 노출되지 않음, 암호화
    - `DDos`, `SQL Injection`, `Cross Site Scripting` 등 방지
+ 온디맨드, 멀티캐스트 대역폭

# 3. VPC Peering의 한계
---

`Transit Gateway`에 대해 자세히 알기 전에 `VPC Peering`에 대해 먼저 알아보자. <br>
원활한 이해를 위한 빌드업이다.<br>
그림을 통해 살펴보자.

![archi](/assets/img/study_AWS/2022-08-14-[AWS]_Transit_Gateway_이해/vpc_peering_arch.png)

위 그림은 `VPC Peering`과 `VPN`을 사용한 `AWS Region 1`-`AWS Region 2`, `AWS Cloud`-`On-Premise` 연결을 나타낸 구조도이다.

이 때 구현된 연결은 다음과 같다.

1. `Amazon VPC A` - `Amazon VPC B`
2. `Amazon VPC B` - `Amazon VPC D`
3. `Amazon VPC C` - `Amazon VPC D`
4. `Amazon VPC C` - `Amazon VPC E`
5. `Amazon VPC D` - `Amazon VPC E`
6. `Amazon VPC B` - `On-Premise`

## VPC Peering - 전이적 피어링
---

1, 2번 연결을 보자.<br>

![archi](/assets/img/study_AWS/2022-08-14-[AWS]_Transit_Gateway_이해/vpc_peering_a_to_d.png)

`Amazon VPC A`에서 `Amazon VPC D`는 사이에 `Amazon VPC B`를 끼고 연결되어 있는 것 처럼 보인다.<br>
하지만 `전이적 피어링` 제한으로 인해 `Amazon VPC A`에서 `Amazon VPC D`로의 직접적인 접근(패킷 라우팅)은 불가능하다.

![archi](/assets/img/study_AWS/2022-08-14-[AWS]_Transit_Gateway_이해/transitive-peering-diagram.png)

위 그림은 `전이적 피어링` 제한을 나타낸다.<br>
`VPC A`는 각각 `VPC B`와 `VPC C`로 연결되어 있기 때문에, `VPC B`에서 `VPC A`를 통해 `VPC C`로 접근 할 수 있다고 생각하기 쉽지만, 이는 불가능하다.<br>
즉, 다음과 같은 연결은 직접적으로 이루어지지 않는다.

> `VPC B` - `VPC A` - `VPC C`

때문에 아까 봤던 구조도에서의 다음 연결은 이루어지지 않는다.

> `Amazon VPC A` - `Amazon VPC B` - `Amazon VPC D`

## VPC Peering - 엣지 간 라우팅
---

1, 6번 연결을 보자.

![archi](/assets/img/study_AWS/2022-08-14-[AWS]_Transit_Gateway_이해/vpc_peering_a_to_onpremise.png)

`Amazon VPC A`와 `Amazon VPC B`는 `VPC Peering`으로 연결되어 있으며, `Amazon VPC B`와 `On-Premise`는 `VPN Connection`으로 연결되어 있는데, 이 때 `VPN Connection`은 `Direct Connect`, `Site-to-Site`의 경우를 포함한다.<br>

위 경우와 마찬가지로 `Amazon VPC A`는 `Amazon VPC B`를 통해 `On-Premise`에 접근할 수 있을 것 처럼 보이지만, 이는 `엣지 간 라우팅` 제한으로 인해 불가능하다.

![archi](/assets/img/study_AWS/2022-08-14-[AWS]_Transit_Gateway_이해/edge-to-edge-vpn-diagram.png)

위 그림은 `엣지 간 라우팅` 제한을 나타낸다.<br>
`On-Premise` 네트워크에서의 트래픽은 `VPC A`에 대한 VPN 연결 또는 `AWS Direct Connect` 연결을 사용하여 `VPC B`에 직접 액세스할 수 없으며, 그 반대의 경우에도 불가능하다.

비단 `On-Premise`에 대한 피어링 뿐만이 아니라, 다음의 경우도 불가능하다.

+ 인터넷 게이트웨이를 통한 엣지 간 라우팅

![archi](/assets/img/study_AWS/2022-08-14-[AWS]_Transit_Gateway_이해/edge-to-edge-igw-diagram.png)

`VPC A`와 `VPC B` 사이(`pcx-abababab`)에 `VPC Peering` 연결이 있다.<br> 
`VPC A`에는 `인터넷 게이트웨이`가 있지만, `VPC B`에는 없다. <br>
`엣지 간 라우팅`은 지원되지 않으므로, `VPC A`를 사용하여 피어링 관계를 확장함으로써 `VPC B`와 인터넷 사이에 피어링 관계가 존재하도록 할 수 없다. <br>

예를 들어 인터넷에서의 트래픽은 `VPC A`에 대한 `인터넷 게이트웨이` 연결을 사용하여 `VPC B`에 직접 액세스할 수 없다.<br>
`인터넷 게이트웨이`가 아닌 `NAT 게이트웨이(또는 디바이스)`의 경우에도 마찬가지다.<br>

+ VPC 게이트웨이 엔드포인트를 통한 엣지 간 라우팅

![archi](/assets/img/study_AWS/2022-08-14-[AWS]_Transit_Gateway_이해/edge-to-edge-s3-diagram.png)

`VPC A`와 `VPC B` 사이(`pcx-aaaabbbb`)에 `VPC Peering` 연결이 있다. <br>
`VPC A`에는 `Amazon S3`에 연결하는 `VPC 게이트웨이 엔드포인트`가 있다. <br>
`엣지 간 라우팅`은 지원되지 않으므로 `VPC A`로 피어링 관계를 확장하여 `VPC B`와 `Amazon S3` 사이에 피어링 관계가 존재하도록 할 수는 없다.

예를 들어 `VPC B`는 `VPC A`에 대한 `VPC 게이트웨이 엔드포인트` 연결을 사용하여 `Amazon S3`에 직접 액세스할 수 없다.


# 4. Transit Gateway 사용
---

위 `VPC Peering`의 한계는 모두 `Transit Gateway`를 사용함으로서 극복할 수 있다.<br>
그림을 통해 살펴보자.

![archi](/assets/img/study_AWS/2022-08-14-[AWS]_Transit_Gateway_이해/transit_gateway_arch.png)

위 그림은 `Transit Gateway`를 사용한 구조도이다.

`VPC Peering`만을 통한 구현보다 훨씬 깔끔해진게 느껴진다.

각 `Amazon VPC`는 `Transit Gateway`을 통해 연결되며, `Transit Gateway - Route Table`을 통해 연결되어 있다면 어떤 대상이든 접근할 수 있다.

또한 불필요한 통신을 막기 위해 `Association`을 지정하여 리소스를 분리하고 차단할 수 있다.

확장성이 필요한 워크로드의 경우, `VPC Peering + VPN`만을 사용하여 네트워크를 구성한다면 `VPC`를 하나 추가할 때 마다 수 많은 연결이 필요할 수 있지만, `Transit Gateway`를 사용하면 한 번의 추가로 해결된다.

# 5. Transit Gateway 차이점, 단점
---

`Transit Gateway`가 장점만 있는 것은 아니다.<br>
`VPC Peering`과의 차이점을 알아보자.

## 서비스 갯수 한도(장점)
---

AWS 서비스에는 `Hard Limit`과 `Soft Limit` 개념이 있다. 

`Hard Limit`은 말그대로 더이상 수용할 수 없는 최대한도를 말하며 `Soft Limit`은 요청하여 증설할 수 있는 한도를 말한다.

`VPC Peering`의 `Hard limit`은 VPC당 125개 이며, `Transit Gateway`는 `Transit Gateway`당 5000개의 VPC 연결이 가능하다.

## 대역폭(단점)
---

`VPC Peering`은 대역폭에 제한이 없으며, `Transit Gateway`는 최대 대역폭이 50Gbps이다.

따라서 만약 50Gbps 이상의 대역폭을 요구하는 서비스의 경우 `Transit Gateway`를 사용한 네트워크 구축은 제한된다.

## 비용(단점)
---

비용을 같은 조건으로 비교해보면 `VPC Peering` 대비 `Trasit Gateway` 가 약 1.5배 더 비싸다. 

`데이터 전송 비용`은 두 서비스가 동일하지만, `Transit Gateway`는 사용하는 동안의 `연결 비용`, `VPN 비용`이 추가로 발생한다.

`Transit Gateway`의 기능을 생각하면 당연하다고 볼 수 있다.

하지만 만약 비용 효율적인 워크로드를 구성해야 하는 경우, `Transit Gateway`는 제한될 수 있다.

# Ref
---

[AWS Docs - Transit Gateway란 무엇입니까?](https://docs.aws.amazon.com/ko_kr/vpc/latest/tgw/what-is-transit-gateway.html)

[AWS Docs - 지원되지 않는 VPC 피어링 구성](https://docs.aws.amazon.com/ko_kr/vpc/latest/peering/invalid-peering-configurations.html#edge-to-edge-vgw)

[Transit Gateway란](https://yoo11052.tistory.com/170)

[VPC Peering 과 Transit Gateway 어떻게 다를까](https://dev.classmethod.jp/articles/different-from-vpc-peering-and-transit-gateway/)

[Transit Gateway?(1) - 개념 및 비용비교](https://junhyeong-jang.tistory.com/25)

[Transit Gateway 소개](https://whchoi98.gitbook.io/aws-hybrid/1.transit-gwatway/1.1.tgw-overview)

[VPC Peering과 Transit Gateway 비교](https://kim-dragon.tistory.com/178)