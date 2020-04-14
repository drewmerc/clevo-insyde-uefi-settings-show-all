# clevo-insyde-uefi-settings-show-all
Little guide on how to show all the settings in clevo insyde_h20 uefi.

# first things first
The operations in this guide will most likely unlock __ALL__ settings in this bios. Do __NOT__ do this if you don't have a good reason!
If you think something is wrongly set and you are unsure, just go to load the optimal defaults, or your device may even can't power on!

# values
+ NH50/NHxxRA
    + offset is 0x133
    + value is 0x01
      + tested on hasee_z7m-ct5na(~~oem modded bios~~)


# finding the offset

1. Download ### [UEFITool](https://github.com/LongSoft/UEFITool)  ### [Universal-IFR-Extractor](https://github.com/LongSoft/Universal-IFR-Extractor) and ### [InsydeH2OUVE_x86_WINx64_200.00.01.00](https://www.google.com/search?q=InsydeH2OUVE_x86_WINx64_200.00.01.00)
2.  Download the bios https://repo.palkeo.com/clevo-mirror/NH5x_70_RDx_RCx_RAx_RHx(Q)
3.  Open the bios (NHx0RC.13 or NHx0RC13.efi in this case) and open in H2OUVE the click Setup/Advanced/Advanced Chipset Control 
![rom files](https://i.imgur.com/xWOfZjk.png)
![H2OUVE ](https://i.imgur.com/lzspIFW.png)
4. Here you can change Setup Menu Insyde Full Show to show and browse around for the menu to find which menu you wish to unlock but for this guide i will unlock everything
5.  Open the bios rom in UEFITool and search for the text string "Setup Menu Insyde Full Show" from the action menu ![search](https://i.imgur.com/1bjthWJ.png)
6.  Double click "Unicode text "Setup Menu Insyde Full Show" in DriverSampleDxe/PE32 image section at header-offset 94B28h" once found in the bottom search tab, once found which will take you to the correct section once at the correct section right click and export as is ![export](https://i.imgur.com/DQ7lqOn.png)
7. Open the exported file "Section_PE32_image_DriverSampleDxe_SetupUtility.sct" in IRFExtractor and extract ![extract](https://i.imgur.com/Hc09jRU.png)
8. Open extracted text file "Section_PE32_image_DriverSampleDxe_SetupUtility IFR.txt" in notepad and search for "Setup Menu Insyde Full Show" ![notepad](https://i.imgur.com/SF4t4sH.png)
9. Setup Menu Insyde Full Show, VarStoreInfo (VarOffset/VarName): 0x133


# generic steps
1.  Download the modded "uefi shell" here https://github.com/datasone/grub-mod-setup_var ,and save it in a bootable device
2.  restart into uefi main menu(from windows advanced reboot or press f2 after power on),choose "Boot from file",then choose it.
3.  run "setup_var [offset]" "setup_var2 [offset]" "setup_var_3 [offset]",and find out which command can find a GUID that has a name of "Setup".(Just ignore the mismatch message and look for "Setup")
4. run that command multiple times,and write down all the current values of the offset of all GUID.
5. run "that_command [offset] [value]".If the command set the value on the right GUID,go ahead.If not,use the same command with values you previously saved to set them back.Try until you set in the right GUID and other GUID are still default.
6. Run "quit""exit" or other to exit to the uefi main menu.
7. Start the setup utility,and see if the magic happens.

# well
Please improve this if you find such values on other models。And sorry for my bad english,any contribution is welcome！

# other
You can find more informations here > https://www.bios-mods.com/forum/Thread-READ-FIRST-Access-Advanced-settings-through-EFI-shell?page=42
