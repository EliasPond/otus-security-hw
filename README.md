# OTUS. Домашние задания по курсу "Безопасность Linux"


### hw_1 - Разворачиваем лабораторную среду на базе Kali Linux и CentOS с помощью Vagrant

Полезные ссылки:
* [Download Vagrant](https://www.vagrantup.com/downloads.html)
* [Образ CentOS 7](https://app.vagrantup.com/centos/boxes/7)
* [Образ Kali Linux](https://app.vagrantup.com/kalilinux/boxes/rolling)


### hw_2 - Освоение практических примеров использования chroot, apparmor, pam.d, polkit
#### polkit
Созданный policykit разрешает пользователю otus монтировать диски
#### pam.d
Пользователю otus2 запрещена авторизация через SSH
#### chroot
Для пользователя otus3 настроен chroot при логине через SSH

Полезныйе ссылки:
* [Vagrant provisioning](https://www.vagrantup.com/docs/provisioning/)
* [Конфигурации PAM](https://developer.ibm.com/articles/au-sshlocks/)
* [Конфигурация policykit](http://rus-linux.net/MyLDP/sec/PolicyKit_pr2.html)


### hw_3 - Исследование уязвимости уровня ядра Linux
Эксплуатация уязвимости dirtycow. На хосте создается исполняемый файл /tmp/dirtyc0w и файл для теста /tmp/cow_test с правами 0404 root:root. Эксплуатация уязвимости осуществляется выполнением команды:
`$ /tmp/dirtyc0w /tmp/cow_test 'insert_your_text_here'`

![alt text](https://github.com/EliasPond/otus-security-hw/blob/master/hw_3/Screenshot.png)

Полезные ссылки:
* [Исходный код dirtyc0w](https://github.com/dirtycow/dirtycow.github.io/wiki/PoCs)
* [Dirty COW CVE-2016-5195](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-5195)
* [Меры противодействия уязвимости](https://www.digitalocean.com/community/tutorials/how-to-protect-your-server-against-the-dirty-cow-linux-vulnerability)
