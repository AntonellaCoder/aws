# Some tips and configuration

## How to increase volume size of an instance.

Go to aws amazon webpage.

Select your instance and then your volume, then modify.

You could choose gp3 and the size of what you want.

Then ssh to your instance.

List the files to work with.

```df -h```

List the blocks to work with.

```lsblk```

Increase the partition. (the path could be different, see the list of previous steps)

```sudo growpart /dev/xvda 1```

Increase the file system. (the path could be different, see the list of previour steps)

```sudo resize2fs /dev/xvda1```

Check if it worked.

```df -h```
