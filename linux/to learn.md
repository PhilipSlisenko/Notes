find /home/shared/dvc-cache -type d -exec chmod 0775 {} \;  
isort  

umask, Access control list (ACL), setfacl https://unix.stackexchange.com/questions/75972/give-default-write-permission-to-group-to-any-newly-created-files-and-folders
 https://stackoverflow.com/questions/580584/setting-default-permissions-for-newly-created-files-and-sub-directories-under-a

highlight src/prepare.py \
    -O xterm256 | less -r

https://unix.stackexchange.com/questions/5642/what-if-kill-9-does-not-work
kill -9
fuser -v /dev/nvidia*
fuser -k /dev/nvidia*