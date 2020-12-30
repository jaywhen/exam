# Exam

## 1:
>  Set **PC** ip: 192.168....
>  **Gateway**: 192.168...


```	bash
// create dir /nfs...
vim /etc/exports
/etc/init.d/nfs-server restart
```

```bash
// create dir /tftp...
chmod -R 777 /tftp...
vim /etc/xinetd.d/tftp
service xinetd restart

// uboot:
setenv serverip PCip
setenv ipaddr 192.168....
saveenv
```



## 2:

**uboot**:

```bash
set bootargs noinitrd console=ttySAC0 console=tty1 root=/dev/nfs nfsroot=192.168.9.96:/nfs996/fss ip=192.168.9.97:192.168.9.96:192.168.9.1:255.255.255.0::eth0:off
```

*action1*:

```bash
bootm 0x32000000
tftp 0x32000000 uImage
```



***modify /root/桌面/linux-2.6.22.6/arch/arm/plat-s3c24xx/common-smdk.c***

```c
static struct mtd_partition smdk_default_nand_part[] = {
	[0] = {
		.name	= "rsr",
		.size	= SZ_8M,
		.offset	= 0,
	},
	[1] = {
		.name	= "se",
		.offset    = MTDPART_OFS_APPEND,
		.size	= SZ_4M,
	},
	[2] = {
	       .name	= "cs",
	       .offset 	= MTDPART_OFS_APPEND,
	       .size		= SZ_16M,
	},
	[3] = {
		.name	= "cqnu",
		.offset 	= MTDPART_OFS_APPEND,
		.size	= MTDPART_SIZ_FULL,
	}
};
```



*make uImage->/tftp...*

**uboot:**
*action1*
waning: panic

## 3:
compile and install Busybox: 

in arm-linux/lib:

```bash
cp *.so* rootfs/lib -d
```



rootfs:
add /etc: 1:copy

```bash
chmod +x /etc/init.d/rcS
```

*make dev:*

```bash
mknod console c 5 1
mknod null c 1 3
mkdir proc mnt tmp sys root
```


copy fs -> /nfs...



## 4:

*! change /work/tslib/etx/ts.conf* 
*copy /work/tslib -> /nfs.../fss/usr/local*

```bash
$TSLIB_ROOT/bin/ts_calibrate
```





 


