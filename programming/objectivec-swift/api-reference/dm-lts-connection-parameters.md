---
layout: default-layout
title: Dynamsoft Core Objective-C & Swift Class - iDMDLSConnectionParameters
description: This page shows the iDMDLSConnectionParameters class of Dynamsoft Core for iOS SDK.
keywords: iDMDLSConnectionParameters, class, objective-c, oc, swift
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---


# iDMDLSConnectionParameters
Defines a class to configure the parameters to connect to license tracking server.  


## Attributes
    
| Attribute | Type |
|---------- | ---- |
| [`mainServerURL`](#mainserverurl) | *NSString\** |
| [`standbyServerURL`](#standbyserverurl) | *NSString\** |
| [`handshakeCode`](#handshakecode) | *NSString\** |
| [`sessionPassword`](#sessionpassword) | *NSString\** |
| [`chargeWay`](#chargeway) | *EnumDMChargeWay* |
| [`UUIDGenerationMethod`](#uuidgenerationmethod) | *EnumDMUUIDGenerationMethod* |
| [`maxBufferDays`](#maxbufferdays) | *NSInteger* |
| [`limitedLicenseModules`](#limitedlicensemodules) | *NSArray\** |
| [`organizationID`](#organizationid) | *NSString\** |
| [`products`](#products) | *NSInteger* |


### mainServerURL
The URL of the license tracking server.
```objc
NSString*  mainServerURL
```
- **Value range**   
    Any string value   
      
- **Default value**   
    ""

- **Remarks**   
    If you choose "Dynamsoft-hosting", then no need to change the value of MainServerURL and StandbyServerURL. When both are set to null (default value), it will connect to Dynamsoft's license tracking servers for online verification.   


### standbyServerURL
The URL of the standby license tracking server.
```objc
NSString*  standbyServerURL
```
- **Value range**   
    Any string value   
      
- **Default value**   
    ""

- **Remarks**   
    If you choose "Dynamsoft-hosting", then no need to change the value of MainServerURL and StandbyServerURL. When both are set to null (default value), it will connect to Dynamsoft's license tracking servers for online verification.   


### handshakeCode
The handshake code.
```objc
NSString*  handshakeCode
```
- **Value range**   
    Any string value   
      
- **Default value**   
    ""

### sessionPassword
The session password of the handshake code set in license tracking server.
```objc
NSString*  sessionPassword
```
- **Value range**   
    Any string value   
      
- **Default value**   
    ""

### chargeWay
Sets the charge way.
```objc
EnumDMChargeWay chargeWay
```
- **Value range**   
    A value of [`EnumDMChargeWay`]({{ site.enumerations }}dm-charge-way.html) Enumeration items.
      
- **Default value**   
    `EnumDMChargeWayAuto`
    
- **See also**  
    [`EnumDMChargeWay`]({{ site.enumerations }}dm-charge-way.html)
      

### UUIDGenerationMethod
Sets the method to generate UUID.
```objc
EnumDMUUIDGenerationMethod UUIDGenerationMethod
```
- **Value range**   
    A value of [`EnumDMUUIDGenerationMethod`]({{ site.enumerations }}dm-uuid-generation-method.html) Enumeration items.
      
- **Default value**   
    `EnumDMUUIDGenerationMethodRandom`
    
- **See also**  
    [`EnumDMUUIDGenerationMethod`]({{ site.enumerations }}dm-uuid-generation-method.html)
      

### maxBufferDays
Sets the max days to buffer the license info.
```objc
NSInteger maxBufferDays
```
- **Value range**   
    [0,0x7fffffff]   
      
- **Default value**   
    7

### limitedLicenseModules
Sets the license modules to use.
```objc
NSArray*  limitedLicenseModules
```
- **Value range**   
    Each array item can be any one of the [`EnumDMLicenseModule`]({{ site.enumerations }}dm-license-module.html) Enumeration items.   
      
- **Default value**   
    nil
    
- **See also**  
    [`EnumDMLicenseModule`]({{ site.enumerations }}dm-license-module.html)    
      
### organizationID
The organization ID got from Dynamsoft.
```objc
NSString* organizationID
```
- **Value range**   
    Any string value   
      
- **Default value**   
    ""

### products
Sets the products to get the license for. Product values can be combined.
```objc
NSInteger products
```
- **Value range**   
    A combine value of [`EnumProduct`]({{ site.enumerations }}product.html) Enumeration items.
      
- **Default value**   
    `EnumProductALL`
    
- **See also**  
    [`EnumProduct`]({{ site.enumerations }}product.html)
  