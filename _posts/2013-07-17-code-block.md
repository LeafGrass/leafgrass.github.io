---
layout: post
title: "Such A Fresh Trial"
tagline: "A bunch of hipster ipsum for ya head."
description: "OK, wish I am not lazy, write it manually."
category: articles
tags: [sample post, readability, test]
image:
  feature: texture-feature-04.jpg
---

## Code Block

This is sample of code block.

{% include 2011-03-10-sample-post.md %}

{% highlight cpp %}
/*
 * @brief   create a process
 * @param   pcb -i- pointer of process control block
 *          pentry -i- process main function entry
 *          name -i- process name
 *          args -i- process main function args
 *          stack_base -i- start address of stack
 *          stack_sz -i- process private stack size
 * @return  pid if create success
 */
int32 __os_process_create(void *pentry, char *name, void *args, uint32 stack_sz)
{
	struct _pcb_t *new_pcb = NULL;
	uint8 *stk = NULL;
	static unsigned int cnt = 0;

	if (pentry == NULL || !VALIDATE_SIZE(stack_sz))
		return -OS_EFAIL;

	new_pcb = (struct _pcb_t *)czalloc(sizeof(struct _pcb_t));
	if (new_pcb == NULL)
		goto err_pcb;

	stk = (uint8 *)czalloc(stack_sz);
	if (stk == NULL)
		goto err_stk;

#if (OUSIA_PORT_STACK_TYPE == OUSIA_PORT_STACK_DEC)
	/* FIXME ARCH_BIT can only be 32, hard code here :( */
	stk = stk + stack_sz - 4;
#endif

	new_pcb->stack_ptr = port_context_init(pentry, args, (void *)stk);
	new_pcb->pentry = pentry;
	new_pcb->name = name;
	new_pcb->pid = ++cnt;
	new_pcb->stack_sz = stack_sz;
	new_pcb->tcb.deadline = 0;
	new_pcb->tcb.ticks_sleeping = 0;
	new_pcb->tcb.ticks_running = 0;
	new_pcb->stat = PSTAT_READY;

	__pcb_enqueue(new_pcb);
	os_printk(LOG_DEBUG, "==> new: %s (%u)\n", name, new_pcb->pid);
	return new_pcb->pid;

err_stk:
	cfree(new_pcb);
err_pcb:
	return -OS_EFAIL;
}
{% endhighlight %}
