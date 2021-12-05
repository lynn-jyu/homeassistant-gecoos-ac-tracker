# Home Assistant Gecoos AC-Controller Device Tracker
[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/custom-components/hacs)

适用于集客AC控制器(非集客网关)

## HA的yaml配置
```python
device_tracker:
  - platform: gecoos_ac_controller_tracker 
    host: !secret jike_gateway_ac_host            # 必填项，集客网关AC的IP地址
    username: !secret jike_gateway_ac_username    # 必填项，集客网关AC的登录账号
    password: !secret jike_gateway_ac_password    # 必填项，集客网关AC的登录密码
    include:
      - K2P                                       # 可选项，值为AP的设备名称，用于过滤AP
      - RM2100

    # latitude: !secret home_latitude
    # longitude: !secret home_longitude

    consider_home: 30                             #设备离线延时
    interval_seconds: 15                          #扫描间隔时间
    new_device_defaults:
      track_new_devices: true
```
## 插件使用说明
把文件夹放到HA的config/custom_components目录下，并按以上的yaml配置后，重启HA就可以了。

## 备注
网关AC默认是一分钟同步一次，所以扫描间隔时间不要设置太低了，没啥用，浪费资源。
按以上配置测试过，基本上90秒左右，HA里有反馈

![截图](https://raw.githubusercontent.com/xz0609/JiKe_GateWay_AC_HA/main/image-4085187.jpg)


## Credits

[xz0609](https://github.com/xz0609/JiKe_GateWay_AC_HA)(forked from)

