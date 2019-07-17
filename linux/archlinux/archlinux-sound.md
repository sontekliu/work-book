# Archlinux 无声音

### 1. 安装 alsa-utils

首先确认是否已安装 `alsa-utils`

```shell
$ sudo pacman -S alsa-utils
```

### 2. 运行 alsamixer 调试音量

```shell
$ alsamixer
```

左右键选择调哪个，将Master和PCM按“m”解除静音（下边MM变成00,MM表示静音），使用上下键调大音量。


```
在 alsamixer 中，下方标有 MM 的声道是静音的，而标有 00 的通道已经启用。 使用 ← 和 → 方向键，选中 
Master 和 PCM 声道。按下 m 键解除静音。使用 ↑ 方向键增加音量，直到增益值为0。该值显示在左上方 Item:
字段后。过高的增益值会导致声音失真。 要想得到完整的 5.1 或 7.1 环绕立体声，还得解除 Front、 
Surround、 Center、LFE (subwoofer) 和 Side 这些声道的静音（上述名称是 Intel HD Audio 声卡使用的声道
名，可能因设备不同而有所差异）。注意，仅有这些设置，系统不会自动将立体声源（多数音乐）提升（upmix）成环绕立
体声。 要启用麦克风，切换至 Capture 选项卡，按下 F4，按下 空格 启用其中一个声道即可。 按下 Esc 
键退出 alsamixer。左右键选择调哪个，将Master和PCM按“m”解除静音（下边MM变成00,MM表示静音），使用上下
键调大音量。
```

### 3. ESC 退出，保存设置
```shell
$ sudo alsactl store
```

### 4. reboot

重启之后，检查是否有声音，刚才的配置是否存在。

### 5. 重启之后还是没有声音

使用命令获取声卡的ID和设备ID

```shell
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Device [USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

card 之后是声卡id，device 之后是设备ID

### 6. 配置音频

```shell
$ amixer -c 1 scontrols
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958',1
```

> -c --card N " select the card

### 7. 配置默认声卡

把下列配置添加到系统级别的 /etc/asound.conf 或用户级别的 ~/.asoundrc 文件。如果文件不存在，可以手动创建。其中的各个ID，请根据实际情况调整：

```
defaults.pcm.card 0
defaults.pcm.device 0
defaults.ctl.card 0
```

`pcm` 选项决定用来播放音频的设备，而 `ctl` 选项决定那个声卡能够由控制工具（如 alsamixer）使用。

### 8. 重启生效

```shell
$ sudo reboot
```









