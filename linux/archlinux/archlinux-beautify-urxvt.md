# Archlinux 美化 urxvt 

### 1. 首先安装 `urxvt`

```
$ sudo pacman -S rxvt-unicode
$ sudo pacman -S urxvt-perls
$ yaourt font-size
$ yaourt urxvt-fullscreen
使配置生效
$ xrdb -load ~/.Xresources
```

### 2. 编辑 `~/.Xresources` 配置文件

```
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!!!    urxvt 配置文件
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

!urxvt 配置
!!$HOME/.Xresources
URxvt.preeditType:Root
! Sogou入法设置
! URxvt.inputMethod:fcitx
URxvt.termName: rxvt-unicode
URxvt.geometry: 95x35+200+120
URxvt.visualBell: false
URxvt.title:sontek-urxvt-unicode

!! coding
URxvt.multichar_encoding:   UTF-8
URxvt.imLocale:             zh_CN.UTF-8

! 透明设置
URxvt.transparent: True
URxvt.transparency: 255
URxvt.inheritPixmap: True
URxvt.shading: 100
!! 括号内表示透明度
URxvt.depth:32
URxvt.background:[80]#2E3436
URxvt.foreground: #FFFFFF
URxvt.colorBD: #ffffff
URxvt.colorUL: #00FF00
URxvt.tintColor:white
URxvt.cursorColor: #FFFFFF
URxvt.underlineColor:cyan
!! black
!URxvt.color0: #353535
!URxvt.color8: #666666
!! red
!URxvt.color1: #d14646
!URxvt.color9: #ee6363
!! green
!URxvt.color2: #7c984c
!URxvt.color10:#9acd32
!! brown/yellow
!URxvt.color3: #daa520
!URxvt.color11: #ffc125
!! blue
!URxvt.color4: #6f99b4
!URxvt.color12:#7c96b0
!! magenta
!URxvt.color5: #993b99
!URxvt.color13:#da4eda
!! cyan
!URxvt.color6:  #a7a15e
!URxvt.color14: #f0e68c
!! white
!URxvt.color7: #bbbbbb
!URxvt.color15:#eeeeee

! black
URxvt.color0: #2E3436
URxvt.color8: #555753
! red
URxvt.color1: #CC0000
URxvt.color9: #EF2929
! green
URxvt.color2: #4E9A06
URxvt.color10:#8AE234
! brown/yellow
URxvt.color3: #C4A000
URxvt.color11: #FCE94F
! blue
URxvt.color4: #3465A4
URxvt.color12:#729FCF
! magenta
URxvt.color5: #75507B
URxvt.color13:#AD7FA8
! cyan
URxvt.color6:  #06989A
URxvt.color14: #34E2E2
! white
URxvt.color7: #D3D7CF
URxvt.color15:#EEEEEC

!! 字体设置
Xft.dpi:96
URxvt.font:             xft:Monospace:size=14:antialias=true:style=Regular
URxvt.boldFont:         xft:Monospace:bold:size=14:antialias=true:style=Regular
! URxvt.font:             xft:Monaco:size=12:antialias=true:style=Regular
! URxvt.boldFont:         xft:Monaco:bold:size=12:antialias=true:style=Regular
URxvt.letterSpace:              0
URxvt.lineSpace:                1
!!滚动条设置，不显示滚动条
URxvt.scrollBar:                False
URxvt.scrollBar_right:          True
URxvt.scrollBar_floating:       False
URxvt.scrollstyle:              plain
!!滚屏设置
URxvt.mouseWheelScrollPage:     True
URxvt.scrollTtyOutput:          False
URxvt.scrollWithBuffer:         True
URxvt.scrollTtyKeypress:        True
!!光标闪烁
URxvt.cursorBlink:              True
! 光标以下划线显示,默认是 box 形式
! URxvt.cursorUnderline: true
! 在回滚缓冲区中保存的行数,默认值是 64
URxvt.saveLines:                3000
!!边框
URxvt.borderLess:               False

!! Perl extensions
URxvt.perl-ext-common: default,matcher,font-size,clipboard,url-select,keyboard-select,tabbed,fullscreen
!! Open urls in browser with Control-Click
URxvt.urlLauncher:              google-chrome-stable
URxvt.matcher.button:           1
URxvt.url-select.lanucher:      google-chrome-stable
URxvt.url-select.underline:     true
URxvt.keysym.C-u:               perl:url-select:select_next
URxvt.keysym.C-Escape:          perl:keyboard-select:activate
URxvt.keysym.C-s:               perl:keyboard-select:search

!   Key	            Description
! Shift+Down	    New tab
! Shift+Left	    Go to left tab
! Shift+Right	    Go to right tab
! Ctrl+Left	    Move tab to the left
! Ctrl+Right	    Move tab to the right
! Ctrl+d	    Close tab
! URxvt 选项卡配置
URxvt.tabbed.tabbar-fg:         2
URxvt.tabbed.tabbar-bg:         0
URxvt.tabbed.tab-fg:            3
URxvt.tabbed.tab-bg:            0

! F11 toggle fullscreen 
URxvt.keysym.F11:               perl:fullscreen:switch

! Ctrl + +  increase font size
URxvt.keysym.C-Plus:            perl:font-size:increase
! Ctrl + -  decrease font size
URxvt.keysym.C-Minux:           perl:font-size:decrease
! Ctrl + =  reset font size
URxvt.keysym.C-equal:           perl:font-size:reset
! Ctrl + /  show font style
URxvt.keysym.C-slash:           perl:font-size:show

!! Colorscheme

! special
! *.foreground: #93a1a1
! *.background: #141c21
! *.cursorColor: #afbfbf
!  
! ! black
! *.color0: #263640
! *.color8: #4a697d
!  
! ! red
! *.color1: #d12f2c
! *.color9: #fa3935
!  
! ! green
! *.color2: #819400
! *.color10: #a4bd00
!  
! ! yellow
! *.color3: #b08500
! *.color11: #d9a400
!  
! ! blue
! *.color4: #2587cc
! *.color12: #2ca2f5
!  
! ! magenta
! *.color5: #696ebf
! *.color13: #8086e8
!  
! ! cyan
! *.color6: #289c93
! *.color14: #33c5ba
!  
! ! white
! *.color7: #bfbaac
! *.color15: #fdf6e3

! 内边距，类似 padding
URxvt.internalBorder:3
URxvt.urgentOnBell: True
!URxvt.iso14755: false
!
!!! Common Keybinds for Navigations
!URxvt.keysym.Shift-Up: command:\033]720;1\007
!URxvt.keysym.Shift-Down: command:\033]721;1\007
!URxvt.keysym.Control-Up: \033[1;5A
!URxvt.keysym.Control-Down: \033[1;5B
!URxvt.keysym.Control-Right: \033[1;5C
!URxvt.keysym.Control-Left: \033[1;5D
!
!!! Copy Paste & Other Extensions
!URxvt.perl-ext-common: default,clipboard,url-select,keyboard-select
!URxvt.copyCommand: xclip -i -selection clipboard
!URxvt.pasteCommand: xclip -o -selection clipboard
!URxvt.keysym.M-c: perl:clipboard:copy
!URxvt.keysym.M-v: perl:clipboard:paste
!URxvt.keysym.M-C-v: perl:clipboard:paste_escaped
!URxvt.keysym.M-Escape: perl:keyboard-select:activate
!URxvt.keysym.M-s: perl:keyboard-select:search
!URxvt.keysym.M-u: perl:url-select:select_next
!URxvt.urlLauncher: firefox
!URxvt.underlineURLs: true
!URxvt.urlButton: 1
```

### 3. 透明启动 urxvt

* 3.1 首先安装 `compton`。
```
$ sudo pacman -S compton
```
* 3.2 i3 中配置开机启动
```
exec --no-startup-id compton -b
```
* 3.3 配置 urxvt 透明参数
```
bindsym $mod + Return exec urxvt -sh 40  # 1-100 透明参数
```

### Rofi 菜单设置

```
##################### Rofi config ################################
rofi.color-enabled: true
rofi.color-window: #272827, #13bf9d, #13bf9d
rofi.color-normal: #272827, #657b83, #272827, #272827, #13bf9d
rofi.color-active: #272827, #657b83, #272827, #272827, #13bf9d
rofi.color-urgent: #272827, #657b83, #272827, #272827, #13bf9d

rofi.separator-style: solid
rofi.sidebar-mode: false
rofi.lines: 5
rofi.font: Monaco 12
rofi.bw: 1
rofi.columns: 2
rofi.padding: 5
rofi.fixed-num-lines: true
rofi.hide-scrollbar: true
```
