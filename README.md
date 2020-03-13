# CCTV

This is bash script to have simple and comfort cctv record server

## Installing

Install and config mail client and mutt to have e-mail notifications about errors

```
aptitude install exim4 mutt
dpkg-reconfigure exim4-config
```

Download cctv script

```
git clone https://github.com/nikita-pershukov/cctv.git
```

Add user and group for using cctv

```
adduser cctv
addgroup cctv-adm
usermod -a -G cctv-adm cctv
```

Add symlink to comfort use cctv

```
ln -s ./watchdog /usr/local/bin/cctv
```

Create "config" file for yourself with same stuff

```
local_dir           local_dir_path
records_dir         records_dir_path
logs_dir            logs_dir_path
cctv_config         cctv_config_name_in_local_dir
wait_file           wait_file_name_in_local_dir
force_file          force_file_name_in_local_dir
resolution          resolutioin
fps                 fps
script_command      $0 $*
script_params       $*
USER                user_2_execute_script
emails              emails_2_notify_about_errors
cctv_reboot_start   cctv_reboot_start_time
cctv_reboot_stop    cctv_reboot_stop_time
```

Create "config" file for yourself with same stuff

```
cam_name    rtsp_url    status
```

Add record in crontab (from user cctv) to use cctv

```
crontab -l > /tmp/mycron
echo "  * *  *   *   *     /usr/local/bin/cctv auto" >> /tmp/mycron
crontab /tmp/mycron
rm /tmp/mycron
```

## Version

alpha

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE.txt) file for details
