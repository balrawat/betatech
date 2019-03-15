---
layout: post
title: How To Convert Virtual Machines Between VirtualBox and VMware
date: '2013-01-31T21:36:00.000+05:30'
author: Balvinder Rawat
tags:
  - virtualbox
  - vmware
  - windows
modified_time: '2014-01-07T12:52:36.003+05:30'
thumbnail: >-
  http://2.bp.blogspot.com/-WnhAHSpqmxk/UQqUjoVWkrI/AAAAAAAAAOE/maGY8XPjxFA/s72-c/image.png
blogger_id: 'tag:blogger.com,1999:blog-6814921223515313000.post-4776281782227908972'
blogger_orig_url: >-
  https://www.linuxtechtips.com/2013/01/how-to-convert-virtual-machines-between.html
---
[![](http://2.bp.blogspot.com/-WnhAHSpqmxk/UQqUjoVWkrI/AAAAAAAAAOE/maGY8XPjxFA/s1600/image.png)][1]

  

  

  

Migrating to another virtual machine program can be intimidating. if you already have your virtual machines set up they way you like them, you don’t necessarily have to install them from scratch – you can migrate your existing virtual machines.

  

VirtualBox and VMware use different virtual machine formats, but each supports the standard Open Virtualization Format. Convert your existing virtual machine to OVF or OVA and you’ll be able to import it into another virtual machine program.

Unfortunately, this may not always work perfectly, as VirtualBox and VMware both seem to use slightly different OVA/OVF implementations that aren’t entirely compatible. If this doesn’t work, you may want to reinstall your virtual machine’s guest operating system from scratch.

### VirtualBox to VMware

Before migrating a virtual machine from VirtualBox to VMware, ensure it’s “powered off” in VirtualBox – not suspended. If it’s suspended, launch the virtual machine and shut it down.

  

[![](http://3.bp.blogspot.com/-yqMn8ddxq9E/UQqUhl4ZljI/AAAAAAAAAN0/YZ_eE9dDpeI/s1600/image1.png)][2]

  

  

  

Click the File menu in VirtualBox and select Export Appliance.

  

  

[![](http://1.bp.blogspot.com/-ojvpo9D_OVU/UQqUevRH2HI/AAAAAAAAANs/tsVR9YbwoRs/s1600/image2.png)][3]

  

Select the virtual machine you want to export and provide a location for it.

  

[![](http://2.bp.blogspot.com/-4Zo_sutvfmU/UQqUjUSPYrI/AAAAAAAAAN8/yPU3vaV0rGI/s1600/image3.png)][4]

  

  

  

  

VirtualBox will create a nOpen Virtualization Format Archive (OVA file) that VMware can import. This may take some time, depending on the size of your virtual machine’s disk file.

  

  

[![](http://3.bp.blogspot.com/-bOHsa3HqSSA/UQqUkLKMi6I/AAAAAAAAAOI/tjVaT8W1pWM/s1600/image4.png)][5]

  

To import the OVA file in VMware, click the Open a Virtual Machine option and browse to your OVA file.

  

[![](http://3.bp.blogspot.com/-5rzqZFZoV9E/UQqUlbqizuI/AAAAAAAAAOU/oGn6QcfrbW4/s1600/image5.png)][6]

  

VirtualBox and VMware aren’t perfectly compatible, so you’ll probably receive a warning message saying the the file “did not pass OVF specification performance” – but if you click Retry, the virtual machine should import and function properly.

  

[![](http://1.bp.blogspot.com/-pwswTV4fpkw/UQqUnWTGk0I/AAAAAAAAAOc/UIa4mGtA_jg/s1600/image6.png)][7]

[  
][8]

  

After the process completes, you can boot the virtual machine in VMware, uninstall VirtualBox Guest Additions from the Control Panel inside the virtual machine, and install VMware Tools from the virtual machine’s menu.

### VMware to VirtualBox

Before migrating a virtual machine from VMware to VirtualBox, ensure it’s “powered off” in VMware – not suspended. If it’s suspended, launch the virtual machine and shut it down.

  

[![](http://1.bp.blogspot.com/-xB4Rsy1FYqY/UQqUnRprrFI/AAAAAAAAAOk/MhtqWyYJbn0/s1600/image5_thumb.png)][9]

[  
][10]

  

Next, browse to the OVFTool folder. If you’re using VMware Player, you’ll find it at C:\\Program Files (x86)\\VMware\\VMware Player\\OVFTool. Hold Shift, right-click inside the OVFTool folder, and select Open command window here.

  

[![](http://4.bp.blogspot.com/-InSxBVnETy0/UQqUo6hMfFI/AAAAAAAAAOs/dw7WAYn1Ixg/s1600/image7.png)][11]

  

  

  

  

Run ovftool with the following syntax:

  

> ovftool source.vmx export.ovf

For example, if we wanted to convert the virtual machine located at C:\\Users\\NAME\\Documents\\Virtual Machines\\Windows 7 x64\\Windows 7 x64.vmx and create a new OVF file at C:\\Users\\NAME\\export.ovf, we’d run the following command:

> ovftool “C:\\Users\\NAME\\Documents\\Virtual Machines\\Windows 7 x64\\Windows 7 x64.vmx” C:\\Users\\NAME\\export.ovf

If you receive a “failed to open disk” error, it’s likely that the virtual machine is still running or wasn’t shut down properly – boot the virtual machine and perform a shut down.

  

[![](http://3.bp.blogspot.com/-xkolRYuFFck/UQqUqZwDp0I/AAAAAAAAAO0/jb_kyatVQNI/s1600/image8.png)][12]

  

Once the process is complete, you can import the .ovf file into VirtualBox. Use the Import Appliance option in the File menu.

  

[![](http://1.bp.blogspot.com/-ARNpdGtM3lA/UQqUrPmWxCI/AAAAAAAAAO8/FDrgyhD9Yhk/s1600/image9.png)][13]

  

After the process completes, you can boot the virtual machine, uninstall VMware Tools, and install VirtualBox’s Guest Additions.

[1]: http://2.bp.blogspot.com/-WnhAHSpqmxk/UQqUjoVWkrI/AAAAAAAAAOE/maGY8XPjxFA/s1600/image.png
[2]: http://3.bp.blogspot.com/-yqMn8ddxq9E/UQqUhl4ZljI/AAAAAAAAAN0/YZ_eE9dDpeI/s1600/image1.png
[3]: http://1.bp.blogspot.com/-ojvpo9D_OVU/UQqUevRH2HI/AAAAAAAAANs/tsVR9YbwoRs/s1600/image2.png
[4]: http://2.bp.blogspot.com/-4Zo_sutvfmU/UQqUjUSPYrI/AAAAAAAAAN8/yPU3vaV0rGI/s1600/image3.png
[5]: http://3.bp.blogspot.com/-bOHsa3HqSSA/UQqUkLKMi6I/AAAAAAAAAOI/tjVaT8W1pWM/s1600/image4.png
[6]: http://3.bp.blogspot.com/-5rzqZFZoV9E/UQqUlbqizuI/AAAAAAAAAOU/oGn6QcfrbW4/s1600/image5.png
[7]: http://1.bp.blogspot.com/-pwswTV4fpkw/UQqUnWTGk0I/AAAAAAAAAOc/UIa4mGtA_jg/s1600/image6.png
[8]: http://1.bp.blogspot.com/-xB4Rsy1FYqY/UQqUnRprrFI/AAAAAAAAAOk/MhtqWyYJbn0/s1600/image5_thumb.png
[9]: http://1.bp.blogspot.com/-xB4Rsy1FYqY/UQqUnRprrFI/AAAAAAAAAOk/MhtqWyYJbn0/s1600/image5_thumb.png
[10]: http://1.bp.blogspot.com/-pwswTV4fpkw/UQqUnWTGk0I/AAAAAAAAAOc/UIa4mGtA_jg/s1600/image6.png
[11]: http://4.bp.blogspot.com/-InSxBVnETy0/UQqUo6hMfFI/AAAAAAAAAOs/dw7WAYn1Ixg/s1600/image7.png
[12]: http://3.bp.blogspot.com/-xkolRYuFFck/UQqUqZwDp0I/AAAAAAAAAO0/jb_kyatVQNI/s1600/image8.png
[13]: http://1.bp.blogspot.com/-ARNpdGtM3lA/UQqUrPmWxCI/AAAAAAAAAO8/FDrgyhD9Yhk/s1600/image9.png

