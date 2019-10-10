

### mod + Shift + 减号 隐藏窗口
### mod + 减号 显示窗口
bindsym $mod+minus move scratchpad
bindsym $mod+plus  scratchpad show

### 打开文件管理器
> bindsym Ctrl+Mod1+f exec pcmanfm &>/dev/null&
bindsym Ctrl+Mod1+f exec thunar &>/dev/null&
### 打开PDF 阅读器
bindsym Ctrl+Mod1+d exec evince &>/dev/null&


###  Bind your audio keyboard keys to change volume and pause/play
```
bindsym XF86AudioRaiseVolume exec amixer -q set Master 5%+ unmute  
bindsym XF86AudioLowerVolume exec amixer -q set Master 5%- unmute  
bindsym XF86AudioMute exec amixer -q set Master mute  
bindsym XF86AudioPlay exec playerctl play-pause  
bindsym XF86AudioNext exec playerctl next  
bindsym XF86AudioPrev exec playerctl previous  
```


################################
### 在指定的工作区间打开应用
################################
### assign [class="URxvt"] $ws1
```
assign [class="netease-cloud-music"] $ws8
assign [class="wechat"] $ws9
assign [class="youdao-dict"] $ws10
```

### 新窗口的默认布局
> for_window [class="URxvt"] layout tabbed
```
for_window [class="wechat"] floating enable 
for_window [class="netease-cloud-music"] floating enable 
for_window [class="youdao-dict"] floating enable 
```




##################################
###   i3_bar config
##################################
```
bar {
    # status_command i3status
    status_command i3status --config ~/.config/i3/i3status.conf
    # 显示模式  dock|hide|invisible
    # dock:一直停靠，hide:通过按键显示和隐藏,invisible:强制隐藏
    mode dock
    # hidden_state hide
    # modifier $mod
    # 显示位置 top|buttom
    # position top
    # 分隔符
    separator_symbol "|"
    # 托盘输出显示 none|primary|<output>
    # tray_output HDMI2
    tray_output primary
    # 托盘内容之间的间距
    tray_padding 3
    i3bar_command /usr/bin/i3bar
    # 设置字体
    font pango:Monaco 10
    # 显示工作区安妮
    workspace_buttons yes
    height 28
    colors {
        background #010101
        statusline #ffffff
        separator #ffffff
        
        # colorclass        border      background     text
        focused_workspace   #9D6A47      #9D6A47     #ffffff
        active_workspace    #333333      #787878     #ffffff
        inactive_workspace  #333333      #787878     #ffffff
        urgent_workspace    #2f343a      #787878     #ffffff
        binding_mode        #2f343a      #787878     #ffffff
    }
}
```

exec --no-startup-id compton --config ~/.config/i3/compton.conf -bc  
exec --no-startup-id ss-qt5  
exec --no-startup-id fcitx  
