Linode VPS ��װGnome VNC (CentOS 6)

��װGnome

1. ��װGnome���滷����ִ���������
	# yum groupinstall "X Window System" "Desktop Platform" Desktop
2. ��װ��Ӧ�������Լ�������
	# yum -y groupinstall "Graphical Administration Tools"
	# yum -y groupinstall "Internet Browser"
	# yum -y groupinstall "General Purpose Desktop"
	# yum -y groupinstall "Office Suite and Productivity"
	# yum -y groupinstall "Graphics Creation Tools"
3. �޸�ϵͳĬ����������Ĭ���������У��ָĳ�����
	�༭ /etc/inittab���� id:3:initdefault: ��Ϊ id:5:initdefault:��
4. ����ϵͳ
	# reboot

��װVNC

1. �����װ
	# yum install tigervnc-server
	# yum install xorg-x11-fonts-Type1
	# yum install vnc(��ѡ)
2. ���ÿ�������
	# chkconfig vncserver on
3. ��������(VNC��¼ʱ������)
	# vncpasswd
	Password:
	Verify:
4. �༭VNC�����ļ�
	# vim /etc/sysconfig/vncservers
	���ļ�ĩβ������£�
	VNCSERVERS="1:root"
	VNCSERVERARGS[1]="-geometry 1920x1080"
5. ����VNC
	# service vncserver start
6. �༭xstartup�ļ�
	vim ~/.vnc/xstartup
	�������
	# twm &
	exec gnome-session &
7. ��������VNC
	# service vncserver restart
8. ����VNC Viewer���ӷ�����
	IP��ַ:1
	����

���������������

1. ��װ�������԰�
	# yum -y groupinstall chinese-support
2. ������Ӧ���ַ�������
	2.1 ��ʱ��Ч
	# export LANG="zh_CN.UTF-8"    # ����Ϊ����
 
	2.2 ������Ч
	�༭/etc/sysconfig/i18n�����rebootһ�£�
	LANG="zh_CN.UTF-8"
	���߱༭ /etc/profile �����ļ����������һ��
	export LANG="zh_CN.UTF-8"
	��������
	# . /etc/profile
	�鿴��ǰ���ַ���
	# echo $LANG
	
	
	
[�ο�����]
https://cnzhx.net/blog/centos-yum-install-desktop/
https://rbgeek.wordpress.com/2012/06/26/how-to-install-vnc-server-on-centos-6/
http://www.ha97.com/4634.html
http://www.centoscn.com/image-text/install/2015/0211/4687.html
http://skypegnu1.blog.51cto.com/8991766/1545449


























