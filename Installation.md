## Installation

[The official website](https://support.touchgfx.com/4.18/docs/introduction/installation) is suggest two different way to install the files. I am going to explain second way that I follow and install personally. You can prefer which way you wish.
1. First thing first, Open your CubeMX (I assume you already installed. If not, installed before-hand.)

![Picture](/Pics/1.png "STM32CubeMX Main Screen")

1. Press "Help" tab
1. In opening sesion, press "Manage embedded software packages"

![Picture](/Pics/2.png "STM32CubeMX Help Section")

1. There will  be new window opened called "Embedded Software Packages Manager"
1. Select the tab called "STMicroelectronics"

![Picture](/Pics/3.png "Embedded Software Packages Manager Main Screen")

1. You will see list of programs/tools that could be added/downloaded from STMicroelectronics.
1. In opening screen, scroll-down an find the section called "X-CUBE-TOUCHGFX"

![Picture](/Pics/5.png "TouchGFX Generator Section in ESPM Screen")

1. When you oppening that section, you will see the TouchGFX Generator with versions. I highly recommend installing the latest version. But, there might be slight differences between what I show and the version you guys using.
1. Click the box, and press install button. It will install the files, but it is not end there. You have to find files and install the TouchGFX manually. This operation just download the necessarry file, __installation must be completed!__
1. You should track your program to find wherever it installed the files. Probably, it's installed in <br> "__C:\Users\\\<user>\STM32Cube\Repository\Packs\STMicroelectronics\X-CUBE-TOUCHGFX\\\<version>\Utilities\PC_Software\TouchGFXDesigner__" path. You will find a __TouchGFX-\<version>.msi__ installer. Rest is easy, just press next, next, done. I am suggesting tick the section "create a desktop shortcut".
<hr>
This section is over in here. If you have trouble through installation, search online. Probably going to find the answer anyway.