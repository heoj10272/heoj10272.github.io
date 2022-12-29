---
layout: post
title: "[Ansible] 오류 SSH auth method: private key Timed out"
subtitle: Ansible
date: '2022-12-07 1:30:00 +0900'
category: study
tags: ansible ansible-error
image:
  path: /assets/img/study_Ansible/2022-12-07-[Ansible]_오류_SSH_auth_method_private_key_Timed_out_while_waiting_for_the_machine_to_boot/1.png
---

`Ansible` 오류 정리<br>
SSH auth method: private key Timed out while waiting for the machine to boot

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>

# 1. 오류
---

![1](/assets/img/study_Ansible/2022-12-07-[Ansible]_오류_SSH_auth_method_private_key_Timed_out_while_waiting_for_the_machine_to_boot/1.png)

```shell
iac-node1: SSH auth method: pivate key 
Timed out while waiting for the machine to boot. This means that
Vagrant was unable to communicate with the guest machine within
the configured ("config.vm.boot_timeout" value) time period.
```

# 2. 오류 원인
---

```
vagrant up
```

이전에 `vagrant halt` 로 VM을 정상종료 하지 않고 꺼버렸더니, `vagrant up` 을 할 때 이와 같은 문제가 발생했다.<br>
정상 종료하지 않으면 다음 번 접속 때 문제가 발생할 수 있다는 것을 처음 알게 되었다 ...

# 3. 해결 방법
---

우선 `VirtualBox` 를 켜준다.<br>

![2](/assets/img/study_Ansible/2022-12-07-[Ansible]_오류_SSH_auth_method_private_key_Timed_out_while_waiting_for_the_machine_to_boot/2.png)

이제 각 VM의 `시작(T)` - `일반 시작(N)` 을 눌러 접속한다.<br>
만약에 이미 켜져있으면, 전원을 종료한 뒤 다시 시작해주자.

![3](/assets/img/study_Ansible/2022-12-07-[Ansible]_오류_SSH_auth_method_private_key_Timed_out_while_waiting_for_the_machine_to_boot/3.png)

모든 VM이 정상적으로 전원이 켜지고, 주루루룩 줄이 내려가다가 유저 로그인 화면까지 출력되면 다시 터미널로 넘어가자.<br>

```
vagrant halt
```

![4](/assets/img/study_Ansible/2022-12-07-[Ansible]_오류_SSH_auth_method_private_key_Timed_out_while_waiting_for_the_machine_to_boot/4.png)

`halt` 로 VM을 정상 종료해준다.

![5](/assets/img/study_Ansible/2022-12-07-[Ansible]_오류_SSH_auth_method_private_key_Timed_out_while_waiting_for_the_machine_to_boot/5.png)

종료가 확인되었으면, 이제 다시 켜주자.

```
vagrant up
```

이 때 만약 `SSH auth method: private key` 단계에서 멈춘다면, `VirtualBox` 에서 켜는 중인 VM을 클릭해주자.<br>
그러면 미리보기에서 로그가 주루룩 내려가면서, 터미널에서도 제대로 연결이 된다.<br>
슈뢰딩거의 VM도 아니고 ... 이 단계에서 10분을 기다렸는데 안되어서 직접 보고자 들어갔더니 그제서야 되길래 황당했다 ...