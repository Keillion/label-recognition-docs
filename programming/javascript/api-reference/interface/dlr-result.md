---
layout: default-layout
title: Dynamsoft Label Recognizer JavaScript Interface - DLRResult
description: This page shows the DLRResult interface of Dynamsoft Label Recognizer for JavaScript.
keywords: DLRResult, javascript, interface
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# DLRResult

Stores the recognized result.

## Attributes
  
| Attribute | Type |
|---------- | ---- |
| [`referenceRegionName`](#referenceregionname) | *string* |
| [`textAreaName`](#textareaname) | *string* |
| [`location`](#location) | [`Quadrilateral`](quadrilateral.md) |
| [`confidence`](#confidence) | *number* |
| [`lineResultsCount`](#lineresultscount) | *number* |
| [`lineResults`](#lineresults) | *[`DLR_LineResult`](dlr-line-result.md)* |
| [`pageNumber`](#pagenumber) | *number* |

### referenceRegionName

The name of the reference region which is used to recognize the current result.

### textAreaName

The name of the text area used to recognize current result.

### location

The location of current recognized text.

### confidence

The confidence of the result. It ranges from 0 to 100.

### lineResultsCount

The line result count.

### lineResults

The line results array.

### pageNumber

The page number the result located in. The index is 0-based.