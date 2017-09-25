# check_certificate_file
Nagios plugin for checking expiration of ssl certificate file

## Usage

```sh
# /usr/lib64/nagios/plugins/check_certificate_file
Check expiration date of ssl certification file plugin for Nagios
Usage: check_certificate_file --crt-file crtfile.crt -w WARNING_DAYS -c CRITICAL_DAYS
Usage: check_certificate_file --crt-file crtfile.crt -w WARNING_DAYS
Usage: check_certificate_file --help
Usage: check_certificate_file --version
```

## NRPE settings examples

```conf
command[check_certificate_file]=/usr/lib64/nagios/plugins/check_certificate_file --crt-file $ARG1$ -w $ARG2$ -c $ARG3$
```

## Nagios Host settings examples


```conf
define host{
        host_name host01
        ...
        _CRT_FILE /path/to/certfile.crt
}
```

```conf
define service{
        service_description             Certificate Expiration
        check_command                   check_nrpe!check_certificate_file!$_CRT_FILE 60 30
}
```
