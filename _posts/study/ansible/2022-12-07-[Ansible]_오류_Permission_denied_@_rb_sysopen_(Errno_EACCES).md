---
layout: post
title: "[Ansible] 오류 Permission denied @ rb_sysopen (Errno::EACCES)"
subtitle: Ansible
date: '2022-12-07 1:30:00 +0900'
category: study
tags: ansible ansible-error
image:
  path: /assets/img/study_Ansible/2022-12-07-[Ansible]_오류_Permission_denied_@_rb_sysopen_(Errno_EACCES)/1.png
---

`Ansible` 오류 정리<br>
C:/HashiCorp/Vagrant/embedded/gems/2.3.2/gems/vagrant-2.3.2/plugins/providers/virtualbox/action/set_name.rb:46:in `initialize': Permission denied @ rb_sysopen - C:/Windows/System32/vagrant/iac/.vagrant/machines/iac-control1/virtualbox/action_set_name (Errno::EACCES)

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>

# 1. 오류
---

![1](/assets/img/study_Ansible/2022-12-07-[Ansible]_오류_Permission_denied_@_rb_sysopen_(Errno_EACCES)/1.png)

```shell
C:/HashiCorp/Vagrant/embedded/gems/2.3.2/gems/vagrant-2.3.2/plugins/providers/virtualbox/action/set_name.rb:46:in `initialize': Permission denied @ rb_sysopen - C:/Windows/System32/vagrant/iac/.vagrant/machines/iac-control1/virtualbox/action_set_name (Errno::EACCES)
```

# 2. 오류 원인
---

```
vagrant up
```

`vagrant up` 실행 시 오류 발생.<br>
터미널을 계속 켜두고 작업을 하던지라 깜빡했는데, 터미널을 킬 때 반드시 관리자 권한으로 실행해야한다.<br>

# 3. 해결 방법
---

우선 `VirtualBox` 를 켜준다.<br>

![2](/assets/img/study_Ansible/2022-12-07-[Ansible]_오류_Permission_denied_@_rb_sysopen_(Errno_EACCES)/2.png)

관리자 권한으로 실행해주자.
