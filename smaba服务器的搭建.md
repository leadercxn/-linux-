# samba �������Ĵ

## ���ӽ���
1. [samba�������Ĵ������](https://www.linuxidc.com/Linux/2018-11/155466.htm)


## ����
1. ���µ�ǰ���
    ```
        sudo apt-get upgrade 
        sudo apt-get update 
        sudo apt-get dist-upgrade
    ```
2. ��װsamba������
    ```
        sudo apt-get install samba samba-common
    ```
3. ѡ�������samba�ļ�Ŀ¼
    /home/cxn
4. ����û�cxn����������123456
    sudo smbpasswd -a cxn

5. ����samba�������ļ�
    sudo nano /etc/samba/smb.conf

    ```
        [cxn]
        comment = cxn folder
        browseable = yes
        path = /home/cxn
        create mask = 0700
        directory mask = 0700
        valid users = cxn
        force user = cxn
        force group = cxn
        public = yes
        available = yes
        writable = yes
    ```
6. samba ����������
    sudo service smbd restart

7. ��win�µ�,���ҵĵ�����������·����\\192.168.1.101\cxn ���˺� cxn ������(���趨�� 123456)
    ������window�²鿴����Ӧ�Ĺ����ļ�Ŀ¼

8. ���ҵĵ������� ӳ������������������Ӷ�Ӧ�������ڵ�·��
    \\192.168.1.101\cxn