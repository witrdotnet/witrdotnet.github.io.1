---
author: admin
comments: false
date: 2015-04-01 11:01:46+00:00
layout: post
link: https://witr.net/quotation/?p=719
slug: vt-x-is-being-used-by-another-hypervisor-please-disable-the-kvm
title: VT-x is being used by another hypervisor .. Please disable the KVM
wordpress_id: 719
categories:
- linux
---


while starting my VM using vagrant, I have following error :


<blockquote>
The guest machine entered an invalid state while waiting for it
to boot. Valid states are 'starting, running'. The machine is in the
'poweroff' state. Please verify everything is configured
properly and try again.

**If the provider you're using has a GUI that comes with it,
it is often helpful to open that and watch the machine**, since the
GUI often has more helpful error messages than Vagrant can retrieve.
For example, if you're using VirtualBox, run `vagrant up` while the
VirtualBox GUI is open.
</blockquote>



So, I edit my Vagrantfile and uncomment gui

    
    
       config.vm.provider "virtualbox" do |vb|
         vb.gui = true
       end
    



Then I start my vm using VirtualBox. I have the following error :
VT-x is being used by another hypervisor ... Please disable the KVM

**what to do ?**
1. see if kvm is running and is used


<blockquote>
witr@serv:~$ lsmod | grep kvm
kvm_intel             143592  3 
kvm                   459835  1 kvm_intel
</blockquote>


here kvm is used by one consumer (kvm_intel) and kvm_intel is used by 3 consumers.

2. stop kvm consumers
In my case it's the android emulator i have launched from AndroidStudio which causes problem. I stop emulator.

3. restart vm
that's all


