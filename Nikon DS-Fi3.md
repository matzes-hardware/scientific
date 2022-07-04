## Nikon DS-Fi3 camera for microscopy

* 5.9 megapixels:
  * 2880x2048 pixels @ 15fps
  * 1440x1024 pixels @ 30fps
* USB 3.0
* C mount
* suitable e.g. for Nikon Eclipse TE2000-U microscope

### Links

* Homepage: https://www.microscope.healthcare.nikon.com/en_EU/products/cameras/ds-fi3
* Brochure: https://d33b8x22mym97j.cloudfront.net/phase4/literature/Brochures/DS_series_2CE-MPAK-4_3.pdf
* Required software: NIS Elements: https://www.microscope.healthcare.nikon.com/en_EU/products/software/nis-elements

### Linux support

* enumerates, but no driver module is loaded (as of march 2022; linux kernel v5.14.9)

~~~
usb 1-1.2: new high-speed USB device number 81 using ehci-pci
usb 1-1.2: New USB device found, idVendor=04b0, idProduct=7014, bcdDevice= 0.01
usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 1-1.2: Product: DS-Fi3
usb 1-1.2: Manufacturer: Nikon Corporation
~~~

~~~
Bus 001 Device 080: ID 04b0:7014 Nikon Corp. DS-Fi3
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04b0 Nikon Corp.
  idProduct          0x7014 
  bcdDevice            0.01
  iManufacturer           1 Nikon Corporation
  iProduct                2 DS-Fi3
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0027
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength       0x0016
  bNumDeviceCaps          2
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000002
      HIRD Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000c
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   2
      Lowest fully-functional device speed is High Speed (480Mbps)
    bU1DevExitLat          10 micro seconds
    bU2DevExitLat        2047 micro seconds
Device Status:     0x0001
  Self Powered
~~~
