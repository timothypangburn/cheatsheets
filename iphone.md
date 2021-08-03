#iPhone Command when hooked to a Linux Machine

## Get udid
lsusb -v 2> /dev/null | grep -e "Apple Inc" -A 2
