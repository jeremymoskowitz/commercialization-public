---
Description: 'Split a Windows image file (.wim) to span across multiple DVDs'
MS-HAID: 'p\_adk\_online.split\_a\_windows\_image\_\_wim\_\_file\_to\_span\_across\_multiple\_dvds'
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'Split a Windows image file (.wim) to span across multiple DVDs'
---

# Split a Windows image file (.wim) to span across multiple DVDs


Split .wim files into .swm files for DVDs or FAT32 file systems. Use this procedure when the split .swm files do not fit in into a single medium, such as these cases:

-   Deploying Windows using DVDs. (A standard single-sided DVD stores 4.7GB).
-   Deploying your Windows image from a Windows PE USB key. (The standard Windows PE installation uses the FAT32 file system, which has a maximum file size of 4GB.) For more information, see [WinPE: Store or split images to deploy Windows using a single USB key](winpe--use-a-single-usb-key-for-winpe-and-a-wim-file---wim-.md).

After the files are split, you can copy them onto separate DVDs, or onto USB key(s).

Note, before you can apply the image, you must first put all of the split files into the same folder, for example, by copying them to a temporary folder on the destination computer. Then use DISM to apply the image, while specifying the split .swm files location and file pattern. DISM does not support applying the files from separate folders or DVDs.

By default, this option creates new split .wim files with a .swm extension. The first file name is based on the specified file name, and each of the following files receives a number after it. For example, when you split "Install.wim", the default filenames are "Install.swm", "Install2.swm", "Install3.swm", and so on.

**Important**  
-   Windows Setup doesn't support installing from a split .swm file for Windows 10.
-   You cannot modify a split .swm file.

 

## <span id="Scenario__Deploy_Windows_using_DVDs"></span><span id="scenario__deploy_windows_using_dvds"></span><span id="SCENARIO__DEPLOY_WINDOWS_USING_DVDS"></span>Scenario: Deploy Windows using DVDs


1.  On your technician PC, open the **Deployment and Imaging Tools Environment** as an administrator.
2.  Split the Windows image:

    ``` syntax
    Dism /Split-Image /ImageFile:C:\images\install.wim /SWMFile:C:\images\install.swm /FileSize:4700
    ```

    where:

    -   `C:\images\install.wim` is the name and the location of the image file that you want to split.

    -   `C:\images\install.swm` is the destination name and the location for the split .swm files.

    -   `4700` is the maximum size in MB for each of the split .swm files to be created.

    In this example, the */split* option creates an install.swm file, an install2.swm file, an install3.swm file, and so on, in the C:\\images directory.

3.  Copy the files to individual DVDs. For example, insert the first DVD and type:
    ```
    copy C:\images\install.swm D:\*
    ```

    Then insert the second DVD and type:
    ```
    copy C:\images\install2.swm D:\*
    ```

    And so on until all .swm files are copied to DVDs.
4.  Boot your destination computer to Windows Preinstallation Environment (WinPE). For more information, see [WinPE: Create a Boot CD, DVD, ISO, or VHD](winpe-create-a-boot-cd-dvd-iso-or-vhd.md).
5.  Configure and format your hard drive partitions, as shown in [Capture and Apply Windows, System, and Recovery Partitions](capture-and-apply-windows-system-and-recovery-partitions.md).
6.  Copy the files to a single temporary folder. For example, insert the first DVD and type:
    ```
    md C:\temp
    copy d:\install.swm c:\TempDVDFolder\*
    ```

    Then insert the second DVD and type:
    ```
    copy d:\install2.swm c:\TempDVDFolder\*
    ```

    And so on until all .swm files are copied.
7.  Apply your image using the DISM /Apply-image /swmfile option:
    ```
    Dism /apply-image /imagefile:c:\temp\install.swm /swmfile:c:\temp\install*.swm /index:1 /applydir:D:\
    ```

8.  Remove the temp folder:
    ```
    rd c:\TempDVDFolder /s /q
    ```

9.  Set up your system and recovery partitions, as shown in [Capture and Apply Windows, System, and Recovery Partitions](capture-and-apply-windows-system-and-recovery-partitions.md).

## <span id="related_topics"></span>Related topics


[Capture and Apply Windows, System, and Recovery Partitions](capture-and-apply-windows-system-and-recovery-partitions.md)

[WinPE: Use a single USB key for WinPE and a WIM file (.wim)](winpe--use-a-single-usb-key-for-winpe-and-a-wim-file---wim-.md)

[DISM Image Management Command-Line Options](dism-image-management-command-line-options-s14.md)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_adk_online\p_adk_online%5D:%20Split%20a%20Windows%20image%20file%20%28.wim%29%20to%20span%20across%20multiple%20DVDs%20%20RELEASE:%20%284/11/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



