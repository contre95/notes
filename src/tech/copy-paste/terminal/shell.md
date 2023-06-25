# Shell useful commands

## Decompressing a file

Script for decompressing different kind of files
```shell
#!/bin/bash
if [ -f $1 ]; then
	case $1 in
	*.tar.bz2) tar xjf $1 ;;
	*.tar.gz) tar xzf $1 ;;
	*.bz2) bunzip2 $1 ;;
	*.rar) unrar x $1 ;;
	*.gz) gunzip $1 ;;
	*.tar) tar xf $1 ;;
	*.tar.xz) tar xf $1 ;;
	*.tbz2) tar xjf $1 ;;
	*.tgz) tar xzf $1 ;;
	*.zip) unzip $1 ;;
	*.Z) uncompress $1 ;;
	*.7z) 7z x $1 ;;
	*) echo "'$1' cannot be extracted via ex()" ;;
	esac
else
	echo "'$1' is not a valid file"
fi
```

Remove all python package under pip freeze
```shell
 pip freeze | xargs -I {} pip uninstall -y {}
```

## Get certs from website 

```shell
openssl s_client -showcerts -verify 5 -connect contre.lucas:443 < /dev/null | awk '/BEGIN CERTIFICATE/,/END CERTIFICATE/{ if(/BEGIN CERTIFICATE/){a++}; out="cert"a".pem"; print >out}'
```
