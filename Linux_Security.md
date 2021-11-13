# ACM
(Access control model)
- Discretionary Access Control (DAC)
A discreción del usuario (sudo, permisos, privilegios), con base a ficheros & usuarios. Modelo: Sujeto / Objeto.

- NDAC - Non-discretionary Access Control
- RBAC - Role-Based Access Control (Grupos)

- MAC - Mandatory Access Control 
Grupos y Sujetos/Accesos. Etiquetas de objetos en base a privilegios (Top Secret, etc.), "clearance". Ejemplo: SELinux

# SECURITY FRAMEWORKS
Frameworks, Software, Modules

- GrSecurity / AppArmor / SELinux

	Apparmor -> Per program & permissions.
Easiest to setup. Lightweight. 

	SELinux -> Implements MAC model
Limits permissions of programs/users. Fuerte administrativo. Para sistemas estáticos.

	GrSecurity -> Low configuration. Not default. 
Link: https://micahflee.com/2016/01/debian-grsecurity/ (Comprensivo)
Link: https://grsecurity.net/compare

Comparison: (OLD) https://www.cyberciti.biz/tips/selinux-vs-apparmor-vs-grsecurity.html

	PAX -> Patch 4 linux kernel. Least-privilege approach. PaX + Frameworks
Link: https://alpinelinux.org/downloads/

---

LSM (Linux Security Modules)
https://en.wikipedia.org/wiki/Linux_Security_Modules

Pentoo, Alpine (Security/lightweight), Arch Linu (Uses PaX & GrSecurity)

GrSecurity enabled kernels for debian: ColdKernel (Investigar)

