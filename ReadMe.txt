Installation QuestaSim 10.4c Linux On UBUNTU 16.04 LTS 64 bit

[0] Update sources 
    sudo apt-get update
    sudo apt-get upgrade

[1] Install 32 bit libraries
    sudo apt-get install lib32ncurses5
    sudo apt-get install lib32z1

[2] Put libstdc++.so.5 in the /usr/lib
    sudo mv libstdc++.so.5 /usr/lib

[3] Change the "enp2s0","enp3s0" name
    sudo gvim /etc/default/grub 
    change:: GRUB_CMDLINE_LINUX=”net.ifnames=0 biosdevname=0”
    sudo grub-mkconfig -o /boot/grub/grub.cfg

[4] Change "install.linux" authority
    chmod 777 install.linux

[5] Install "libgcc_s_so.1"
    sudo apt-cache search libgcc\*
    sudo apt-get install lib32gcc-4.7-dev
Test whether the lib is right setup
    cd /usr 
    sudo find ./ -name libgcc\*
The list has 
    "./libx32/libgcc_s.so.1" That means ok

[6] Install Mentor Graphics Questasim 10.4c 
    sudo ./install.linux64

[7] run sfk to crack the Questasim 10.4c
    cp -rf sfk /opt/tool/mentor/questasim10_4c/questasim/linux_x86_64/mgls/lib 
    cp -r run_sfk /opt/tool/mentor/questasim10_4c/questasim/linux_x86_64/mgls/lib
    cd /opt/tool/mentor/questasim10_4c/questasim/linux_x86_64/mgls/lib
    chmod 777 sfk
    ./run_sfk 

    How to check the result ?
    Answer::The result should display as this list
        total hits/matching patterns/non-matching patterns]
        error: failed to read+write: sfk - skipping
        [001/1/2] mgcld
        [001/1/2] mgls_asynch
        4 files checked, 2 changed.
        1 errors occurred.
[8] Setup the license file
    The same to the QuestaSim10_2b tool 

[9] ./vsim

[10] enjoy yourself!
