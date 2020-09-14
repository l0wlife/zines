<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# hooking functions
Algumas funções são capazes de detectar e remover a hidden storage, porém para evitar isso, o Win32/gapz faz um hook nessas funcionalidades<br>
Sendo elas `IRP_MJ_INTERNAL_DEVICE_CONTROL` e `IRP_MJ_DEVICE_CONTROL`, são handlers do miniport driver. no `IRP_MJ_DEVICE_CONTROL` é feito um hook nessas funções:
* IOCTL_SCSI_PASS_THROUGH
* IOCTL_SCSI_PASS_THROUGH_DIRECT
* IOCTL_ATA_PASS_THROUGH
* IOCTL_ATA_PASS_THROUGH_DIRECT
<br><br>
esses hooks impedem que algumas determinadas regiões da memória seja descoberta incluindo o boot record, a partir do momento que esses hooks são feitos, impede qualquer tipo de overwrite também<br><br>

[pwn](../README.md)<br>
[home](../../README.md)
