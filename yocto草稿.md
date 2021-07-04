repo init -u https://github.com/STMicroelectronics/oe-manifest.git -b refs/tags/openstlinux-5.10-dunfell-mp1-21-03-31

DISTRO=fsl-imx-x11 MACHINE=imx6ull14x14evk source fsl-setup-release.sh -b build

DISTRO=openstlinux-weston MACHINE=stm32mp1 source layers/meta-st/scripts/envsetup.sh

bitbake st-image-weston

# yacto

## yocto �������̵�һ�㲽�� ��ubuntu������
1. ��װ��Ҫ������
    ```shell
        sudo apt-get update
        sudo apt-get upgrade
        sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3 pylint xterm
        sudo apt-get install make xsltproc docbook-utils fop dblatex xmlto
        sudo apt-get install libmpc-dev libgmp-dev
        sudo apt-get install libncurses5 libncurses5-dev libncursesw5-dev libssl-dev linux-headers-generic u-boot-tools device-tree-compiler bison flex g++ libyaml-dev libmpc-dev libgmp-dev
        sudo apt-get install coreutils bsdmainutils sed curl bc lrzsz corkscrew cvs subversion mercurial nfs-common nfs-kernel-server libarchive-zip-perl dos2unix texi2html diffstat libxml2-utils

        git config --global user.name "Your Name"
        git config --global user.email "you@example.com"
        git config --list
    ```
    or
    ```shell
        sudo apt-get install gawk wget git-core
        sudo apt-get install diffstat unzip texinfo gcc-multilib
        sudo apt-get install build-essential chrpath socat libsdl1.2-dev
        sudo apt-get install libsdl1.2-dev
        sudo apt-get install xterm sed cvs
        sudo apt-get install subversion coreutils texi2html
        sudo apt-get install docbook-utils python-pysqlite2
        sudo apt-get install help2man make gcc g++
        sudo apt-get install desktop-file-utils
        sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev mercurial
        sudo apt-get install autoconf automake groff
        sudo apt-get install curl lzop asciidoc
        sudo apt-get install u-boot-tools
    ```
2. ��װ repo
    ```
        curl https://mirrors.tuna.tsinghua.edu.cn/git/git-repo -o repo
        chmod +x repo

        vim repo
    ```
        ������ ��google�� �ؼ��֣��Ѷ�Ӧ�и�Ϊ����
        ```shell
            REPO_URL='https://mirrors.tuna.tsinghua.edu.cn/git/git-repo'
        ```
        ���޸� .bashrc �ļ�����repo·����ӵ�����������

3. ����һ������ yocto ����Ŀ¼
    ``` 
        mkdir yocto_project && cd yocto_project
    ```
4. repo init ��ʼ���ֿ�
    ```shell
        repo init  -u  [github-url]
            example1: repo init -u https://github.com/STMicroelectronics/oe-manifest.git -b refs/tags/openstlinux-5.10-dunfell-mp1-21-03-31
            example2: repo init -u git://git.freescale.com/imx/fsl-arm-yocto-bsp.git -b imx-4.1-krogoth
    ```
5. repo �ֿ�ͬ��
    ```shell
        repo sync
    ```

* ��ע����������������Ҫ�󶼱Ƚϸߣ���Ϊ��Щ�ֿ��ڹ��⣬������Ҫ��ǽ

6. ���û�������
    ```
        DISTRO=<distro name> MACHINE=<machine name> source fsl-setup-release.sh -b <build dir>
            example1:DISTRO=fsl-imx-x11 MACHINE=imx6ulevk source fsl-setup-release.sh -b ./fsl_build_x11
            exampke2:DISTRO=openstlinux-weston MACHINE=stm32mp1 source layers/meta-st/scripts/envsetup.sh
    ```
    ����� DISTRO �� MACHINE �Ӳ�ͬSoc�ٷ��������ֲ����
7. ����
    ```
        bitbake [image]
            example1:bitbake core-image-minimal
            example2:bitbake st-image-weston
    ```
    ����� image �Ӳ�ͬSoc�ٷ��������ֲ����

## yocto ������Ŀ¼�ܹ�
1. ��������Ŀ¼
    ```
        <yocto project>/<build dir>/tmp/deploy/images/imx6ulevk
    ```

2. ����������uboot��kernel�����ļ�ϵͳĿ¼
    1. uboot ·���� ��������
        `<yocto project>/<build dir>/tmp/work/imx6ulevk-poky-linux-gnueabi/u-boot-imx/2016.03-r0/git`
    2. Linux ·���� ��������
        `<yocto project>/<build dir>/tmp/work-shared/imx6ulevk/kernel-source`
    3. ���ļ�ϵͳĿ¼
        `<yocto project>/<build dir>/tmp/deploy/images/imx6ulevk/core-image-minimal-imx6ulevk-          20190621012322.rootfs.tar.bz2`
    
    һ�㹤��������
    ������3�����ó�����������