
# Podman and Libvirt

---

# Software distribution


---

# Packages

 - RPM
 - yellow package (pkg)
 - Installshield installer (msi)
 - .war


---

# Containers and virtual machines

---

# Reasons

  - increased security*
  - ease of distribution
  - consistency in deployment
	  - software appliance

---

# Docker

```
$ alias docker=podman
```

---

# Podman

 _open platform for developing, shipping, and running applications_

---

# Podman

a runtime to run 'containers'


---
# Containerfile

Describes the environment the application runs in

---

# Syntax and commands

```dockerfile
FROM ...

RUN ...

COPY ...

CMD ...
```

---

# Build

```
$ podman build
```


---

# Apache container using Fedora

```dockerfile
FROM fedora:39

RUN dnf install -y httpd && \
    systemctl enable httpd.service

EXPOSE 80

#CMD ["/usr/sbin/init"]
CMD ["/usr/sbin/httpd"]
```

---

# Build

```
$ podman build -t httpd-example .
```

---

# Run

```
$ podman run -d --rm --systemd=always -p 8080:80 httpd-example
$ links http://localhost:8080
$ podman ps -a
```

---

# Interactive

```
$ podman run -it --rm fedora:39 bash
# uname -a
Linux ... x86_64 GNU/Linux
```

---

# Publishing

Container registry
```
$ podman pull
$ podman push
$ podman tag
```

---

# Libvirt

A virtualization API to control a _Hypervisor_

---

# KVM

_an open source virtualization technology built into Linux_

---

# Create a VM

```
$ virsh create rhel9vm.xml
```

...

---

# Virt-install

```
$ virt-install \
   -n RHEL9VM \
   --description "Test VM" \
   --os-type=Linux \
   --os-variant=rhel9 \
   --ram=4096 \
   --vcpus=2 \
   --disk path=/var/lib/libvirt/images/RHEL9VM.img,bus=virtio,size=10 \
   --graphics none \
   --cdrom /var/libvirt/images/rhel9.iso \
   --network bridge:br0
```
---

# Use Cockpit

...

---

# Let's leave at this ...

this is all you need to know about VMs

---
