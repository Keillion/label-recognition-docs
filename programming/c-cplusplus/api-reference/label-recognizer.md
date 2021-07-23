---
layout: default-layout
title: Dynamsoft Label Recognizer C++ API Reference - CLabelRecognizer Class
description: This page shows CLabelRecognizer methods of Dynamsoft Label Recognizer for C++ API Reference.
keywords: api reference, c++
needAutoGenerateSidebar: true
needGenerateH3Content: true
---


# class dynamsoft::dlr::CLabelRecognizer


## Initialization
  
  | Method               | Description |
  |----------------------|-------------|
  | [`InitLicense`](#initlicense) | Sets the license and activates the SDK. |
  | [`InitDLSConnectionParameters`](#initdlsconnectionparameters) | Initializes a DM_DLSConnectionParameters struct with default values. |
  | [`InitLicenseFromDLS`](#initlicensefromdls) | Initializes the label recognizer license and connects to the specified server for online verification. |



### InitLicense
Sets product key and activate the SDK.

```cpp
int InitLicense (const char *license)
```   

**Parameters**
`[in]	license`	The product key.

**Return value**
Returns error code. Returns 0 if the function completed successfully, otherwise call [`GetErrorString`](#geterrorstring) to get detailed message. 

Possible returns are:
`DLR_OK`;

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
delete recognizer;
```

### InitDLSConnectionParameters
Initializes a DM_DLSConnectionParameters struct with default values.

```cpp
static int InitDLSConnectionParameters (DM_DLSConnectionParameters *pDLSConnectionParameters)
```   

**Parameters**
`[in, out] pDLSConnectionParameters` The struct of [`DM_DLSConnectionParameters`](dm-lts-connection-parameters.md).   

**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
char errorBuf[512];
DM_DLSConnectionParameters paramters;
CLabelRecognizer::InitDLSConnectionParameters(&paramters);
paramters.organizationID = "Your organization ID";
CLabelRecognizer::InitLicenseFromDLS(&paramters, errorBuf, 512);
```



### InitLicenseFromDLS
Initializes the label recognizer license and connects to the specified server for online verification.

```cpp
static int InitLicenseFromDLS(DM_DLSConnectionParameters *pDLSConnectionParameters, char errorMsgBuffer[], const int errorMsgBufferLen)
```   

**Parameters**
`[in] pDLSConnectionParameters` The struct [`DM_DLSConnectionParameters`](dm-lts-connection-parameters.md) with customized settings.   
`[in, out] errorMsgBuffer` The buffer is allocated by caller and the recommending length is 256. The error message will be copied to the buffer.  
`[in]	errorMsgBufferLen` The length of allocated buffer.  

**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
char errorBuf[512];
DMDLSConnectionParameters paramters;
CLabelRecognizer::InitDLSConnectionParameters(&paramters);
paramters.organizationID = "Your organization ID";
CLabelRecognizer::InitLicenseFromDLS(&paramters, errorBuf, 512);
```

 

## Settings

  | Method               | Description |
  |----------------------|-------------|
  | [`GetRuntimeSettings`](#getruntimesettings) | Gets the current settings and saves it into a struct. |
  | [`UpdateRuntimeSettings`](#updateruntimesettings) | Updates runtime settings with a given struct. |
  | [`ResetRuntimeSettings`](#resetruntimesettings) | Resets the runtime settings. |
  | [`AppendSettingsFromString`](#appendsettingsfromstring) | Appends LabelRecognizerParameter settings in a string to the SDK object. |
  | [`AppendSettingsFromFile`](#appendsettingsfromfile) | Appends LabelRecognizerParameter settings in a file to the SDK object. |
  | [`OutputSettingsToFile`](#outputsettingstofile) | Outputs LabelRecognizerParameter settings into a file (JSON file). |
  | [`ClearAppendedSettings`](#clearappendedsettings) | Clear all appended LabelRecognizerParameter settings in the SDK object. |
  | [`UpdateReferenceRegionFromBarcodeResults`](#updatereferenceregionfrombarcoderesults) | Updates reference region which is defined with source type LST_BARCODE. |
  | [`GetModeArgument`](#getmodeargument) | Get argument value for the specified mode parameter. |
  | [`SetModeArgument`](#setmodeargument) | Set argument value for the specified mode parameter. |



### GetRuntimeSettings
Get current settings and save them into a [`DLR_RuntimeSettings`](dlr-runtime-settings.md) struct.

```cpp
int GetRuntimeSettings (DLR_RuntimeSettings* settings)
```   
   
**Parameters**
`[in,out]	settings` The struct of runtime settings.  

**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
DLR_RuntimeSettings settings;
int errorCode = recognizer->GetRuntimeSettings(&settings);
delete recognizer;
```



### UpdateRuntimeSettings
Update runtime settings with a given [`DLR_RuntimeSettings`](dlr-runtime-settings.md) struct.

```cpp
int UpdateRuntimeSettings (DLR_RuntimeSettings* settings, char errorMsgBuffer[] = NULL, const int errorMsgBufferLen = 0)
```   
   
**Parameters**
`[in]	settings` The struct of runtime settings.  
`[in,out]	errorMsgBuffer` <sub>Optional</sub> The buffer is allocated by caller and the recommended length is 256.The error message will be copied to the buffer.  
`[in]	errorMsgBufferLen` <sub>Optional</sub> The length of the allocated buffer.  

**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
DLR_RuntimeSettings settings;
int errorCode = recognizer->GetRuntimeSettings(&settings);
settings.linesCount = 1;
char errorMessage[256];
recognizer->UpdateRuntimeSettings(&settings, errorMessage, 256);
delete recognizer;
```



### ResetRuntimeSettings
Reset all runtime settings to default values.

```cpp
int ResetRuntimeSettings ()
```   
   
**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
DLR_RuntimeSettings settings;
int errorCode = recognizer->GetRuntimeSettings(&settings);
settings.linesCount = 1;
recognizer->UpdateRuntimeSettings(&settings);
recognizer->ResetRuntimeSettings();
delete recognizer;
```





### AppendSettingsFromString
Append a new template string to the current label recognizer instance.

```cpp
int AppendSettingsFromString (const char* content, char errorMsgBuffer[] = NULL, const int errorMsgBufferLen = 0)
```   
   
**Parameters**
`[in] content` A JSON string that represents the content of the settings.   
`[in,out] errorMsgBuffer` <sub>Optional</sub> The buffer is allocated by caller and the recommending length is 256. The error message will be copied to the buffer.  
`[in] errorMsgBufferLen` <sub>Optional</sub> The length of allocated buffer.


**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
char errorMessage[256];
recognizer->AppendSettingsFromString("{\"LabelRecognizerParameter\":{\"Name\":\"P1\", \"RegionPredetectionModes\":[{\"Mode\":\"RPM_GENERAL_HSV_CONTRAST\"}], \"ReferenceRegionNameArray\": [\"R1\"]},\"ReferenceRegion\":{\"Name\":\"R1\",\"Localization\":{\"SourceType\":\"LST_PREDETECTED_REGION\",\"RegionPredetectionModesIndex\":0},\"TextAreaNameArray\":[\"T1\"]},\"TextArea\":{\"Name\":\"T1\",\"CharacterModelName\":\"Number\"}}", errorMessage, 256);
delete recognizer;
```



### AppendSettingsFromFile
Appends LabelRecognizerParameter settings in a file to the SDK object.

```cpp
int AppendSettingsFromFile (const char* filePath, char errorMsgBuffer[] = NULL, const int errorMsgBufferLen = 0)
```   
   
**Parameters**
`[in] filePath` The settings file path.   
`[in,out] errorMsgBuffer` <sub>Optional</sub> The buffer is allocated by caller and the recommending length is 256. The error message will be copied to the buffer.  
`[in] errorMsgBufferLen` <sub>Optional</sub> The length of allocated buffer.


**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
char errorMessage[256];
recognizer->AppendSettingsFromString("your file path", errorMessage, 256);
delete recognizer;
```




### OutputSettingsToFile
Outputs runtime settings and save them into a settings file (JSON file).  

```cpp
int OutputSettingsToFile (const char* filePath, const char* templateName)
```   
   
**Parameters**
`[in]	filePath` The path of the output file which stores current settings.  
`[in]	templateName` A unique name for declaring current runtime settings.  


**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
char errorMessageAppend[256];
recognizer->AppendSettingsFromString("{\"LabelRecognizerParameter\":{\"Name\":\"P1\", \"RegionPredetectionModes\":[{\"Mode\":\"RPM_GENERAL_HSV_CONTRAST\"}], \"ReferenceRegionNameArray\": [\"R1\"]},\"ReferenceRegion\":{\"Name\":\"R1\",\"Localization\":{\"SourceType\":\"LST_PREDETECTED_REGION\",\"RegionPredetectionModesIndex\":0},\"TextAreaNameArray\":[\"T1\"]},\"TextArea\":{\"Name\":\"T1\",\"CharacterModelName\":\"Number\"}}", errorMessageAppend, 256);
recognizer->OutputSettingsToFile("C:\\Program Files (x86)\\Dynamsoft\\{Version number}\\Templates\\CurrentRuntimeSettings.json", "currentRuntimeSettings");
delete recognizer;
```




### ClearAppendedSettings
Clear all appended parameter settings of the current label recognizer instance.

```cpp
void ClearAppendedSettings ()	
```   
   
**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
recognizer->ClearAppendedSettings();
```

### UpdateReferenceRegionFromBarcodeResults
Updates reference region which is defined with source type LST_BARCODE.  

```cpp
int UpdateReferenceRegionFromBarcodeResults (const BarcodeResultArray* barcodeResults, const char* templateName)
```   
   
**Parameters**
`[in]	barcodeResults` The barcode results used to localize reference region.  See also [`BarcodeResultArray`](barcode-result-array.md).
`[in]	templateName` The template name. A template name is the value of key LabelRecognizerParameter.Name defined in JSON formatted settings. If no template name is specified, current runtime settings will be used.


**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
char errorMessageAppend[256];
recognizer->AppendSettingsFromString("{\"LabelRecognizerParameter\":{\"Name\":\"P1\", \"RegionPredetectionModes\":[{\"Mode\":\"RPM_GENERAL_HSV_CONTRAST\"}], \"ReferenceRegionNameArray\": [\"R1\"]},\"ReferenceRegion\":{\"Name\":\"R1\",\"Localization\":{\"SourceType\":\"LST_BARCODE\"},\"TextAreaNameArray\":[\"T1\"]},\"TextArea\":{\"Name\":\"T1\",\"CharacterModelName\":\"Number\"}}", errorMessageAppend, 256);
//Get barcodeResults from Dynamsoft Barcode Reader SDK
recognizer->UpdateReferenceRegionFromBarcodeResults(barcodeResults, "P1");
delete recognizer;
```



### SetModeArgument

Set argument value for the specified mode parameter.


```cpp
int SetModeArgument (const char* modesName, const int index, const char* argumentName, const char* argumentValue, char errorMsgBuffer[] = NULL,  const int errorMsgBufferLen = 0)	
```   
**Parameters**
`[in]	modesName` The mode parameter name to set argument.  
`[in]	index` The array index of mode parameter to indicate a specific mode.  
`[in]	argumentName` The name of the argument to set.  
`[in]	argumentValue` The value of the argument to set.  
`[in,out]	errorMsgBuffer`<sub>Optional</sub> The buffer is allocated by the caller and the recommended length is 256. The error message will be copied to the buffer.  
`[in]	errorMsgBufferLen`<sub>Optional</sub> The length of the allocated buffer.  

**Return value**
Returns error code (returns 0 if the function operates successfully).  
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

#### Remark
Check follow link for available modes and arguments:
- [`RegionPredetectionModes`]({{ site.parameters-reference }}label-recognizer-parameter/region-predetection-modes.html#regionpredetectionmodes)

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
DLR_RuntimeSettings settings;
int errorCode = recognizer->GetRuntimeSettings(&settings);
settings.regionPredetectionModes[0] = RPM_GENERAL_RGB_CONTRAST;
char errorMessage[256];
recognizer->UpdateRuntimeSettings(&settings, errorMessage, 256);
recognizer->SetModeArgument("RegionPredetectionModes", 0, "AspectRatioRange", "100", errorMessage, 256);
delete recognizer;
```




### GetModeArgument

Get argument value for the specified mode parameter.

```cpp
int GetModeArgument (const char* modesName, const int index, const char* argumentName, char valueBuffer[], const int valueBufferLen, char errorMsgBuffer[] = NULL, const int errorMsgBufferLen = 0)	
```   
   
**Parameters**  
`[in]	modesName` The mode parameter name to get argument.  
`[in]	index` The array index of mode parameter to indicate a specific mode.  
`[in]	argumentName` The name of the argument to get.  
`[in,out]	valueBuffer` The buffer is allocated by caller and the recommended length is 480. The argument value would be copied to the buffer.  
`[in]	valueBufferLen` The length of allocated buffer.  
`[in,out]	errorMsgBuffer`<sub>Optional</sub> The buffer is allocated by the caller and the recommended length is 256. The error message will be copied to the buffer.  
`[in]	errorMsgBufferLen`<sub>Optional</sub> The length of the allocated buffer.  

**Return value**
Returns error code (returns 0 if the function operates successfully).  
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

#### Remark
Check follow link for available modes and arguments:
- [`RegionPredetectionModes`]({{ site.parameters-reference }}label-recognizer-parameter/region-predetection-modes.html#regionpredetectionmodes)

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
DLR_RuntimeSettings settings;
int errorCode = recognizer->GetRuntimeSettings(&settings);
settings.regionPredetectionModes[0] = RPM_GENERAL_RGB_CONTRAST;
char errorMessage[256];
char argumentValue[480];
recognizer->UpdateRuntimeSettings(&settings, errorMessage, 256);
recognizer->SetModeArgument("RegionPredetectionModes", 0, "AspectRatioRange", "100", errorMessage, 256);
recognizer->GetModeArgument("RegionPredetectionModes", 0, "AspectRatioRange", argumentValue, 480, errorMessage, 256);
delete recognizer;
```

 
   
## Recognizing
   
  | Method               | Description |
  |----------------------|-------------|
  | [`RecognizeByBuffer`](#recognizebybuffer) | Recognizes text from memory buffer containing image pixels in defined format. |
  | [`RecognizeByFile`](#recognizebyfile) | Recognizes text from a specified image file. |
   
### RecognizeByBuffer
Recognizes text from the memory buffer containing image pixels in defined format.

```cpp
int RecognizeByBuffer(const ImageData* imageData, const char* templateName)
```   
   
**Parameters**
`[in]	imageData` A struct of [`ImageData`](image-data.md) that represents an image.  
`[in]	templateName` The template name. A template name is the value of key LabelRecognizerParameter.Name defined in JSON formatted settings. If no template name is specified, current runtime settings will be used.

**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
//Generate imageData from somewhere else
int errorCode = recognizer->RecognizeByBuffer(imageData, "");
delete recognizer;
```




### RecognizeByFile
Recognizes text from a specified image file.

```cpp
int RecognizeByFile (const char* fileName, const char* templateName)	
```   
   
**Parameters**
`[in]	fileName` A string defining the file name.  
`[in]	templateName` The template name. A template name is the value of key LabelRecognizerParameter.Name defined in JSON formatted settings. If no template name is specified, current runtime settings will be used.

**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
int errorCode = recognizer->RecognizeByFile("C:\\Program Files (x86)\\Dynamsoft\\{Version number}\\Images\\AllSupportedBarcodeTypes.tif", "");
delete recognizer;
```

 
   
## Result
   
  | Method               | Description |
  |----------------------|-------------|
  | [`GetAllResults`](#getallresults) | Gets all recognized results. |
  | [`FreeResults`](#freeresults) | Frees memory allocated for recognized results. |

### GetAllResults
Get all recognized results.

```cpp
int GetAllResults (DLR_ResultArray** results)	
```   
   
**Parameters**
`[out] results`	Recognized results returned by last calling function [`RecognizeByBuffer`](#recognizebybuffer) / [`RecognizeByFile`](#recognizebyfile). The results is allocated by SDK and should be freed by calling function [`FreeResults`](#freeresults).

**Return value**
Returns error code (returns 0 if the function operates successfully).    
*You can call [`GetErrorString`](#geterrorstring) to get detailed error message.*

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
DLR_ResultArray * results;
int errorCode = recognizer->RecognizeByFile("C:\\Program Files (x86)\\Dynamsoft\\{Version number}\\Images\\AllSupportedBarcodeTypes.tif", "");
recognizer->GetAllResults(&results);
dynamsoft::dlr::CLabelRecognizer::FreeResults(&results);
delete recognizer;
```



### FreeResults
Free memory allocated for text results.

```cpp
static void FreeResults (DLR_ResultArray ** results)	
```   
   
**Parameters**
`[in]	results` Recognized results.

**Code Snippet**
```cpp
CLabelRecognizer* recognizer = new CLabelRecognizer();
recognizer->InitLicense("t0260NwAAAHV***************");
DLR_ResultArray * results;
int errorCode = recognizer->RecognizeByFile("C:\\Program Files (x86)\\Dynamsoft\\{Version number}\\Images\\AllSupportedBarcodeTypes.tif", "");
recognizer->GetAllResults(&results);
dynamsoft::dlr::CLabelRecognizer::FreeResults(&results);
delete recognizer;
```

 


## General
   
  | Method               | Description |
  |----------------------|-------------|
  | [`GetErrorString`](#geterrorstring) | Returns the error string. |
  | [`GetVersion`](#getversion) | Returns the version number string for the SDK. |


### GetErrorString

Get error message by error code.

```c++
static const char* GetErrorString (const int errorCode)	
```   
   
**Parameters**

`[in]	errorCode` The error code.
 

**Return value**

The error message.

**Code Snippet**

```c++
const char* errorString = GetErrorString(errorCode);
```



### GetVersion

Get version information of SDK.

```c++
static const char* GetVersion ()
```   

**Return value**
The version information string.

**Code Snippet**

```c++
const char* versionInfo = GetVersion();
```

 