# Fix Fedora 44 / Cinnamon

Si on arrive pas à se connecter:

    $ sudo dnf install slick-greeter
    $ sudo systemctl disable gdm
    $ sudo systemctl enable lightdm
    $ sudo systemctl reboot

Il faut un nom de machine statique, sinon en utiliser un:

    $ hostnamectl
    Static hostname: leigh-pc
    ...

    $ sudo hostnamectl set-hostname <choose hostname>

Source: https://discussion.fedoraproject.org/t/cant-login-using-cinnamon-after-upgrade-to-fedora-44/190236/8
