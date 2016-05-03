---
author: joshbax-msft
title: Wlan L1 Test 02 - Query Interface Properties
description: Wlan L1 Test 02 - Query Interface Properties
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9ed6e464-94cd-4f0e-a307-50c3b058d1e7
---

# Wlan L1 Test 02 - Query Interface Properties


This automated test queries the interface for a variety of common properties.

## Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Associated requirements</strong></p></td>
<td><p>Device.Network.WLAN.Base.ConformToNDIS Device.Network.WLAN.CSBBase.ConformToNDIS</p>
<p>[See the device hardware requirements.](http://go.microsoft.com/fwlink/p/?linkid=254483)</p></td>
</tr>
<tr class="even">
<td><p><strong>Platforms</strong></p></td>
<td><p>Windows 7 (x64) Windows 7 (x86) Windows RT (ARM-based) Windows 8 (x64) Windows 8 (x86) Windows RT 8.1 Windows 8.1 x64 Windows 8.1 x86</p></td>
</tr>
<tr class="odd">
<td><p><strong>Expected run time</strong></p></td>
<td><p>~1 minutes</p></td>
</tr>
<tr class="even">
<td><p><strong>Categories</strong></p></td>
<td><p>Basic Certification</p></td>
</tr>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td><p>Automated</p></td>
</tr>
</tbody>
</table>

 

## Running the test


Before you run the test, complete the test setup as described in the test requirements: [Wireless LAN (802.11) Testing Prerequisites](wireless-lan--80211--testing-prerequisites.md).

This test queries the device for the following properties:

-   IsMediaStreamingEnabled

-   IsBackgroundScanEnabled

-   IsSafeModeSupported

-   sSafeModeCertified

-   GetCurrentOperationMode

-   GetInterfaceState

-   sManagementFrameProtectionSupported

-   IsHostedNetworkCapable

-   enumerate all radios and radio states

-   IsAutoConfigEnabled

-   enumerate all support infrastructure cipher pairs

-   devices without Connected Standby must enumerate supported adhoc cipher pairs

-   GetBSSMode

-   GetCountryList

-   GetConnectionAttributes

-   GetRSSi

-   GetChannel

Any returned failure in the WLAN service API from the device these capabilities are queried will result in a failure in the test

The test will fail if the following is true:

-   There are less than three infrastructure cipher pairs.

-   If DOT11\_AUTH\_ALGO\_RSNA\_PSK is not implemented.

## Troubleshooting


For troubleshooting information, see [Troubleshooting Wireless LAN (802.11) Tests](troubleshooting-wireless-lan--80211--tests.md).

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20Wlan%20L1%20Test%2002%20-%20Query%20Interface%20Properties%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



