# Archlinux 美化 urxvt 

urxvt 的安装

```
# sudo pacman -S rxvt-unicode
```

配置如下：

```
!!$HOME/.Xdefaults
URxvt.preeditType:Root
!!!input method
URxvt.inputMethod:fcitx
URxvt.depth: 32
URxvt.inheritPixmap: True


!! Colorscheme

! special
*.foreground: #93a1a1
*.background: #141c21
*.cursorColor: #afbfbf
 
! black
*.color0: #263640
*.color8: #4a697d
 
! red
*.color1: #d12f2c
*.color9: #fa3935
 
! green
*.color2: #819400
*.color10: #a4bd00
 
! yellow
*.color3: #b08500
*.color11: #d9a400
 
! blue
*.color4: #2587cc
*.color12: #2ca2f5
 
! magenta
*.color5: #696ebf
*.color13: #8086e8
 
! cyan
*.color6: #289c93
*.color14: #33c5ba
 
! white
*.color7: #bfbaac
*.color15: #fdf6e3

!!!scrollbar
! 不显示滚动条
URxvt.scrollBar:False
URxvt.scrollBar_right:False
URxvt.scrollBar_floating:False
URxvt.scrollstyle:plain

!!!滚屏设置
URxvt.mouseWheelScrollPage:True
URxvt.scrollTtyOutput:False
URxvt.scrollWithBuffer:True
URxvt.scrollTtyKeypress:True

!!!光标闪烁
URxvt.cursorBlink:True
! 光标以下划线显示,默认是 box 形式
! URxvt.cursorUnderline: true
! 在回滚缓冲区中保存的行数,默认值是 64
URxvt.saveLines:1000

!!!边框
URxvt.borderLess: False

!!!字体设置
Xft.dpi:96
URxvt.font:xft:Monospace:size=14:style=Regular:antialias=true,xft:WenQuanYi Bitmap Song:size=14:style=Regular:antialias=true
URxvt.boldfont:xft:Monospace:size=14:style=Bold:antialias=true,xft:WenQuanYi Bitmap Song:size=14:style=Bold:antialias=true

!! URxvt Appearance
URxvt.letterSpace: -1
URxvt.lineSpace: 0
URxvt.geometry: 92x24
URxvt.title: URxvt
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
