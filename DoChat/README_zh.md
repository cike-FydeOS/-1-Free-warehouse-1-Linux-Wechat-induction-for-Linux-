# DoChat /d����?t??t/ ��װ΢��

[![Docker](https://github.com/huan/docker-wechat/workflows/Docker/badge.svg)](https://github.com/huan/docker-wechat/actions?query=workflow%3ADocker)
[![Powered By Wine](https://img.shields.io/badge/Powered%20By-Wine-red)](https://www.winehq.org/)

[![dockeri.co](https://dockeri.co/image/zixia/wechat)](https://hub.docker.com/r/zixia/wechat/tags)

DoChat����װ΢�ţ���һ������Linux��΢��PC Windows�ͻ��ˡ�

![DoChat](https://huan.github.io/docker-wechat/images/dochat.png)

> ͼƬ��Դ: [Docker 101](https://www.docker.com/blog/docker-101-introduction-docker-webinar-recap/) + [Icon Finder](https://www.iconfinder.com/icons/4539886/application_chat_communication_wechat_wechat_logo_icon), Ps-ed by Ruoxin Song

## ����

- [����](https://twitter.com/newsycombinator/status/1231489594765594625) by Y Combinator [Hacker News](https://news.ycombinator.com/item?id=22395507)
- [����](https://huan.github.io/docker-wechat/images/oschina-feb-25-2020.png) by [OS China](https://www.oschina.net/)

## ��������

�����Ѿ��յ��û����棬���ǵ�΢���˺���ʹ�ñ���Ŀ���ѱ����ã���������ге�ʹ�÷��գ�

1. [��������һ�����°��docker��������΢�žͱ����� #55](https://github.com/huan/docker-wechat/issues/55)

## �÷� ![Powered Linux](https://img.shields.io/badge/WeChat-Linux-brightgreen)

΢��PC��ͨ����������������Linux����������

```sh
curl -sL https://raw.githubusercontent.com/huan/docker-wechat/master/dochat.sh | bash
```

ֻ�轫�����һ�������/ճ�����նˣ�Ȼ�󰴻س�������ô΢��PC�ܿ�ͻ���������XWindows�����ϡ�

![DoChat �ն�����](https://huan.github.io/docker-wechat/images/term-dochat.png)

## �ص�

��ֻ��Ҫһ��shell����Ϳ��Կ��伴�ã�

1. ����������/��ʾ���֡�
1. ʹ�á�Ctrl+V�������Ƶ�ͼ��ճ����΢��`

![DoChat ��ͼ](https://huan.github.io/docker-wechat/images/screenshot-dochat.png)

## Ҫ��

1. ����ʹ��Linux Ubuntu���а棨DoChat����UbuntuDesktop19.10�����ģ�
    1. Debian֧��ȷ�� ([#9](https://github.com/huan/docker-wechat/issues/9))
    1. OpenSUSE֧��ȷ�� ([#16](https://github.com/huan/docker-wechat/issues/16))
    1. ��ȷ�ϼܹ�֧�� ([#26](https://github.com/huan/docker-wechat/issues/26))
    1. Ubuntu(19.04/18.10/18.04) Ӧ���ܹ�֧��
    1. ����Linux���а棺����֧��
1. Docker (���� `sudo apt update && apt install docker.io` ΪUbuntu�û���װDocker)

## ��������

### `DOCHAT_DPI`

ͼ����Ļ�ֱ��ʵ�DPI������

| DPI  | ���� |
| ---: | :---: |
|  96 | 100% |
| 120 | 125% |
| 144 | 150% |
| 192 | 200% |

Ĭ��ֵ: `120`

Ҫ�Ŵ󴰿������С����ִ�����²���:

```sh
curl -sL https://raw.githubusercontent.com/huan/docker-wechat/master/dochat.sh \
  | DOCHAT_DPI=192 bash
```

### `DOCHAT_SKIP_PULL`

���ÿ������ʱ������Ϊ���°汾��ȡdockerͼ�񣬿������� `DOCHAT_SKIP_PULL` ��������.

```sh
curl -sL https://raw.githubusercontent.com/huan/docker-wechat/master/dochat.sh \
  | DOCHAT_SKIP_PULL=true bash
```

����������� `dochat.sh`:

```sh
DOCHAT_SKIP_PULL=true ./dochat.sh
```

### `DOCHAT_����`

��ʾ���������־��Ϣ.

```sh
curl -sL https://raw.githubusercontent.com/huan/docker-wechat/master/dochat.sh \
  | DOCHAT_DEBUG=true bash
```

### `DOCHAT_΢�Ű汾`

ʹ��΢�ŵ��ض��汾.

�������� <https://hub.docker.com/r/zixia/wechat/tags>

����:

```sh
curl -sL https://raw.githubusercontent.com/huan/docker-wechat/master/dochat.sh \
  | DOCHAT_WECHAT_VERSION=2.7.1.85 bash
```

## ���ڳ���Ա��˵

��������Լ�����һ�У������������ϴ򿪶��΢��PC�ͻ��ˣ���ô���������鿴���Ǵ洢���е� [dochat.sh](https://github.com/huan/docker-wechat/blob/master/dochat.sh) ����������docker����:

```sh
docker run \
  --name DoChat \
  --rm \
  -i \
  \
  -v "$HOME/DoChat/WeChat Files/":'/home/user/WeChat Files/' \
  -v "$HOME/DoChat/Applcation Data":'/home/user/.wine/drive_c/users/user/Application Data/' \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  \
  -e DISPLAY \
  \
  -e XMODIFIERS=@im=fcitx \
  -e GTK_IM_MODULE=fcitx \
  -e QT_IM_MODULE=fcitx \
  -e GID="$(id -g)" \
  -e UID="$(id -u)" \
  \
  --ipc=host \
  --privileged \
  \
  zixia/wechat
```

���������Ҫ�޸���.

## �汾����

dockerӳ���������汾����ģʽ:

1. `X.Y.Z.a`: This is for the WeChat PC Windows Client version
    1. `zixia/wechat:2.7.1.85`: WeChat 2.7.1.85
    1. `zixia/wechat:2.8.0.112`: WeChat 2.8.0.112
1. `x.y`: ����docker����汾�ġ�.
    1. `zixia/wechat:0.2`: docker-wechat version 0.2

�����汾��ģʽ�����໥�ص�

����: the `zixia/wechat:0.2` ������ `zixia/wechat:2.8.0.112` ��ͼ����ͬ.

## ��֪����

- [ ] ΢��2.8.0.x���ܷ��ʹ�ͼƬ/�ļ� ([#341](https://github.com/huan/docker-wechat/issues/31))
  - �������: ���� [2.7.1.85](https://hub.docker.com/layers/zixia/wechat/2.7.1.85/images/sha256-e6e9d21c7cd1dfae0484e697f12f5f3c401de2f02e771d061868740e0d26549d) instead. (`DOCHAT_WECHAT_VERSION=2.7.1.85`)
- [ ] ��΢��������в������� ([#2](https://github.com/huan/docker-wechat/issues/2))

## ���������б�

- [x] ΢��PC��¼������Ϣ���ô洢 ([#3](https://github.com/huan/docker-wechat/issues/3))
- [ ] ����Dockerfileʱ���Զ���.exe��װ����װ΢��PC (������Ҫ�����Զ�������)
- [ ] ���΢��PC�������Ա����ǿ��Է�����dockerͼ����ͬ�İ汾��.

## FAQ

### ����Gnome�����ϵͳ����ͼ��

��װ Gnome ��չ: [Top Icons Plus Git](https://extensions.gnome.org/extension/2311/topicons-plus/) by bijignome

> Note 1: ������������TopIcons����չ���ǳ����ƣ�TopIcons��TopIcons Redux��TopIcons Plus��**TopIcons Plus Git**��TopIconsFix��ʹ��**TopIcons Plus Git**��������ȷ�ġ�  
>
> Note 2: ��TopIcons Plus����һ��bug�����¡�wine����������������ʾһ�����ڡ� ([#19](https://github.com/huan/docker-wechat/issues/19))

### ��openSUSE Leap��ʹ�ô���5�˳�

������openSUSE Leap����������Ϊ5��Ӧ�ó����˳�������ʱ������Ҫ����X���������ʿ����������κ��û�������Ӧ�ó���֮ǰ���ӵ�X��������ʹ��������������:  

`$ xhost +`

### ����2���������������ú�û��������

�����������' wine '����һ���ɵ�ȱ�ݺͶ��������������ɵġ����������ʹ�õ�����������������Ȼ���л������������

����Ϊ���ܻᵼ����ʹ��������ʾģʽʱ��ͼ��ʧ�������Ҫ��Ӧ�ó�������ʱ��ģʽ����Ϊ���񣬴˽ű������а���:

```Bash
#bin/bash
xrandr --output HDMI-1-2 --same-as eDP-1-1

curl -sL https://raw.githubusercontent.com/huan/docker-wechat/master/dochat.sh \
  | DOCHAT_SKIP_PULL=true bash &

sleep 5
xrandr --output HDMI-1-2 --right-of eDP-1-1
```

��HDMI-1-2����Ϊ�ⲿ��ʾ���ƣ���eDP-1-1����Ϊ������ʾ���ơ���ʾ�������ϣ������� [����](http://www.mikewootc.com/wiki/linux/usage/set_x_reso.html).<br/>***Notice***: ��������5ʱ�����뽫��¼�Ի����ϵ�������ʾ�ˣ�������ͼ���ܿ����ⲿ��ʾ��. 

## ����

- [ʹ��X11Forwardʱ���뷨��������](https://ubuntuforums.org/showthread.php?t=913752)
- [�����뷽����صĻ�������](https://fcitx-im.org/wiki/Input_method_related_environment_variables)
- [Docker GUI���ʵ��](https://github.com/zjZSTU/Containerization-Automation/blob/982d54458b05ef75fe6436f4ea72bbb66c4cb931/docs/docker/gui/%5BDocker%5DGUI���ʵ��.md)
- [Linux �� �������� wechat ΢��](https://www.kpromise.top/run-wechat-in-linux/)
- [WeChat Linux�����](https://ferrolho.github.io/blog/2018-12-22/wechat-desktop-on-linux)

## ��ʷ

### �汾

### v0.10 (2020��3��12��)

1. ��wine��v4.0������v5.0
1. ͨ�������Զ�΢�Ű汾�ŵ�GitHub��������Docker Hub.

### v0.8 (2020��3��3��)

1. ����µ����û���������DOCHAT_WECHAT_VERSION����ѡ��΢�Ű汾��
1. ��� ΢�� v2.8.0.112
    1. �������ĺ����
    1. ����IPv6����֧��
    1. ������һ����ѡ����
    1. ������������С������Ϣ
    1. ������С������ʹ��΢��֧��
    1. ���������ļ���壬�ɲ鿴�͹������������ļ�

```sh
curl -sL https://raw.githubusercontent.com/huan/docker-wechat/master/dochat.sh \
  | DOCHAT_WECHAT_VERSION=2.8.0.112 bash
```

### v0.5 (2020��2��24��)

1. ��ӻ���������DOCHAT_DPI��������ͼ����Ļ�ֱ��ʵ�DPI������
1. �����Զ�����.

### v0.4 (2020��2��21��)

���ҵ�������������������õ���һ���ܰ��ı�־��.

1. �޸����� ([#1](https://github.com/huan/docker-wechat/issues/1))
1. �޸����������в��˳�������.

### v0.2 (2020��2��18��)

��һ�������汾���ɱ���

### v0.1 (2020��2��17��)

��Ŀ������

## ��л

1. [΢��Linux�����](https://ferrolho.github.io/blog/2018-12-22/wechat-desktop-on-linux) - by [@ferrolho](https://github.com/ferrolho)
1. [Wine HQ Ӧ�����ݿ�-΢��](https://appdb.winehq.org/objectManager.php?sClass=application&iId=16931)
1. [������Ȳ���ϵͳ��΢�� docker ����](https://github.com/bestwu/docker-wechat) by [@bestwu](https://github.com/bestwu)
1. ���ҵ���������ܰ��Ƶ�DoChat��־��

## �����Ŀ

1. [DoWork /d����?w??k/ ��װ��ҵ΢��](https://github.com/huan/docker-wxwork): Dockerized WeChat Work (��ҵ΢��) PC Windows Client for Linux

## ����

[Huan LI](https://github.com/huan) ([��׿��](http://linkedin.com/in/zixia)) Tencent TVP of Chatbot zixia@zixia.net

[![Profile of Huan LI (��׿��) on StackOverflow](https://stackexchange.com/users/flair/265499.png)](https://stackexchange.com/users/265499)

## ��Ȩ & ���֤

- Code & Docs ? 2020-now Huan LI \<zixia@zixia.net\>
- Code released under the Apache-2.0 License
- Docs released under Creative Commons
