# Introducción a la infraestructura virtual: concepto y soporte físico

## **Ejercicio 1**. Consultar en el catálogo de alguna tienda de informática el precio de un ordenador tipo servidor y calcular su coste de amortización a cuatro y siete años.

Se ha elegido como servidor la siguiente máquina [HP ProLiant ML110 Gen10 Intel Xeon 4108/16GB](https://www.pccomponentes.com/hp-proliant-ml110-gen10-intel-xeon-4108-16gb).

Para calcular el coste de amortización aplicamos el método lineal, es decir, todos los años contables tendrás una parte X igual de amortización. El precio sin IVA es 1156,20€.

* Para cuatro años: 1156,20€ * 4 / 100 = 289,05€/año (que representa el 25% de amortización al año, coincidiendo con el máximo permitido por hacienda en España)
* Para siete años: 1156,20€ * 7 / 100 = 165,17€/año (0,1429% al año)

## **Ejercicio 2**. Usando las tablas de precios de servicios de alojamiento en Internet “clásicos”, es decir, que ofrezcan Virtual Private Servers o servidores físicos, y de proveedores de servicios en la nube, comparar el coste durante un año de un ordenador con un procesador estándar (escogerlo de forma que sea el mismo tipo de procesador en los dos vendedores) y con el resto de las características similares (tamaño de disco duro equivalente a transferencia de disco duro) en el caso de que la infraestructura comprada se usa solo el 1% o el 10% del tiempo.

Para el servicio de VPS se ha usado [vpsserver](https://www.vpsserver.com/virtual-private-server/) y como proveedor de servicio en la nube [AWS-EC2](https://aws.amazon.com/es/ec2/pricing/on-demand/).

Se ha elegido la siguiente configuración del ordenador:

* vCPU->2Cores
* Memoria->2GiB
* Disco -> 50GB

Esta configuración tiene un coste de 9,99€ al mes en vpsserver y un coste de 0,0236 USD por hora en AWS.

Por tanto, con un uso del 1% anual sería:

* AWS: 2,06736USD
* vpsserver: 1,1988€

Y para un uso del 10% anual:

* AWS: 20,6736USD
* vpsserver: 11,988€

## **Ejercicio 3**. En general, cualquier ordenador con menos de 5 o 6 años tendrá estos flags.¿Qué modelo de procesador es? ¿Qué aparece como salida de esa orden? Si usas una máquina virtual, ¿qué resultado da? ¿Y en una Raspberry Pi o, si tienes acceso, el procesador del móvil?

``` bash
$ grep -E '^flags.*(vmx|svm)' /proc/cpuinfo
flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d
```

Modelo de procesador

``` bash
$ inxi
CPU: Quad Core Intel Core i5-7300HQ (-MCP-) speed/min/max: 800/800/3500 MHz Kernel: 4.15.0-64-generic x86_64 Up: 1d 9h 53m
Mem: 2817.2/7862.7 MiB (35.8%) Storage: 1.13 TiB (2.4% used) Procs: 240 Shell: zsh 5.4.2 inxi: 3.0.32
```

## **Ejercicio 4**

### 1. Comprobar si el núcleo instalado en tu ordenador contiene este módulo del kernel usando la orden kvm-ok. Alternativamente (o además), usar lscpu como se indica arriba

En mi máquina no se encuentra instalado el módulo del kérnel kvm.

``` bash
    $ LC_ALL=C lscpu | grep Virtualization
    Virtualization:      VT-x
```

### 2. Instalar un hipervisor para gestionar máquinas virtuales, que más adelante se podrá usar en pruebas y ejercicios

Hipervisor tipo 2 instalado: **VirtualBox**

## **Ejercicio 5**. Darse de alta en servicios de nube usando ofertas gratuitas o cupones que pueda proporcionar el profesor

Usando las ventajas y ofertas que proporciona *GitHub Developer Student Pack* me he registrado en todos los servicios que se ofertan en la plataforma, Heroku, Digital Ocean, Microsoft Azure. Por otro lado, me he registrado en la plataforma de Oracle que se pasó por el grupo de Telegram de la asignatura.

## **Ejercicio 6**. Darse de alta en una web que permita hacer pruebas con alguno de los sistemas de gestión de nube anteriores
