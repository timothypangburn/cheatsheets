# rsync files via ssh - assumes key is setup to target system
rsync -avz -e "ssh" --append --progress logger:~/fbi-1395/fbi-1395-201607.log .

# rsync files ignore existing files in targeted directory
rsync -avz --append --progress --ignore-existing /source-dir /dest-dir

# rsync with the use of sudo on destination system.
rsync -avz --append --progress --ignore-existing --rsync-path="sudo rsync" dest-server:/directory .
