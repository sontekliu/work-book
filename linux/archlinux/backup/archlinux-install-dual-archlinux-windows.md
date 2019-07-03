# ArchLinux Install 

https://lampjs.wordpress.com/2014/09/01/arch-linux-easy-install-with-with-windows-dual-boot-for-beginners/

https://xiaix.me/arch-zhe-teng-xiao-ji-2-an-zhuang-arch-he-win7-shuang-xi-tong/
https://xiaix.me/records/

http://rackpull.com/linux/dual-boot-arch-linux-windows/

http://rackpull.com/linux/dual-boot-arch-linux-windows/

```
pacman -S grub
pacman -S ntfs-3g    #  否则 os-prober 发现不了 win
pacman -S os-prober

# os-prober # 测试是否发现 windows 系统

# grub-install --target=i386-pc /dev/sda
# grub-mkconfig -o /boot/grub/grub.cfg
```

