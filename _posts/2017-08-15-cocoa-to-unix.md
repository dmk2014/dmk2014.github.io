---
layout: post
title: Cocoa to Unix Timestamp Conversion Using Go
---

Core Data is a storage framework which is part of the Cocoa API for macOS and iOS application development. Within this framework, timestamps are stored as the number of seconds that have elapsed since midnight on January 1st 2001, GMT.

Therefore, a Cocoa timestamp of **524518502** represents the datetime **Tuesday 15 August 2017 19:35:02**, plus or minus your GMT offset.

If assumed to be a Unix timestamp, this value incorrectly respresents the datetime **Friday 15 August 1986 19:35:02**. To produce the correct result, the difference between the Unix and Cocoa Epochs must be considered.

Conversion from a Cocoa to Unix timestamp is trivial, as shown in the below sample using Go.

```go
// Coca Epoch, expressed as a Unix Timestamp
cocoaEpochTimestamp := time.Date(2001, 01, 01, 0, 0, 0, 0, time.UTC).Unix()

// Cocoa Timestamp (Tuesday 15 August 2017 19:35:02)
var cocoaTimestamp int64 = 524518502

// Unix Timestamp = Cocoa Epoch Timestamp + Cocoa Timestamp
unixTimestamp := cocoaEpochTimestamp + cocoaTimestamp

// Prints Unix Timestamp: 1502825702 - Tuesday 15 August 2017 19:35:02
fmt.Println(unixTimestamp)
```
