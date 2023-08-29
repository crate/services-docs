# Technical Details


## About CPU units

CrateDB Cloud operates on Virtual Machines hosted on Azure and AWS. These VMs
are equipped with vCPUs. In most instances, 1 vCPU corresponds to 1 thread of
a multithreaded CPU. However, there are situations where 1 vCPU equates to 1
core. Portions of these VMs are designated for a CrateDB Node, which has
specific CPU requests and limits.

These requests are denoted in terms of milliCPUs, where 1000 milliCPUs is
approximately equal to 1 vCPU. For [CR1 to CR4](#cr1-cr4), both the requests
and limits are consistent, ranging from 1750 milliCPUs to 14000 milliCPUs,
translating to roughly 1.75 to 14 vCPUs. On the other hand, for [CR0](#cr0)
and [CRFREE](#crfree), the requests and limits vary: a 500 milliCPU request
with a 2000 milliCPU limit, which means they can utilize between 0.5 to
2 vCPUs based on the VM’s overall workload.

So, typically, 2 CPUs in the context of CrateDB Cloud would roughly equate
to 2 vCPUs on an Intel based Azure / AWS machine.
