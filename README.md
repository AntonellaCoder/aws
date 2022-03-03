# Increase Swap file, Increase Storage of EC2.

## Optimizing the instance by adding swap file.

See if you have file swap with htop

```htop```

Check before and after if this file is there. ( /swapfile )

```ls -la /```

Create the swapfile of 1G (for other size, this lis is diff).

```sudo fallocate -l 1G /swapfile```


Wipe the file out for 1G (for other size, this line is diff).

```sudo dd if=/dev/zero of=/swapfile bs=1024 count=1048576```

Give it root privileges.

```sudo chmod 600 /swapfile```

Make the swapfile

```sudo mkswap /swapfile```

Turn on the swapfile

```sudo swapon /swapfile```

Open this file with vim or nano

```sudo vim /etc/fstab```

Add this line to the file mentioned before

```/swapfile swap swap defaults 0 0```

Run this command to see if any errors.

```sudo mount -a```

Verified that you have the swapfile running.

```htop```

That's it, it is done.

If you want to know your static Ip while in your terminal then do this.

```curl ifconfig.me```

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
