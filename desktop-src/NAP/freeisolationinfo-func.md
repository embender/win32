---
title: FreeIsolationInfo function (NapUtil.h)
description: Frees an IsolationInfo data structure.
ms.assetid: 639cfa74-0823-4a19-9cbe-dd6f0a38e7eb
keywords:
- FreeIsolationInfo function NAP
topic_type:
- apiref
api_name:
- FreeIsolationInfo
api_location:
- qutil.dll
api_type:
- DllExport
ms.topic: reference
ms.date: 05/31/2018
---

# FreeIsolationInfo function

> [!Note]  
> The Network Access Protection platform is not available starting with Windows 10

 

The **FreeIsolationInfo** function frees an [**IsolationInfo**](/windows/win32/api/naptypes/ns-naptypes-isolationinfo) data structure.

## Syntax


```C++
NAPAPI VOID WINAPI FreeIsolationInfo(
  _In_ IsolationInfo *isolationInfo
);
```



## Parameters

<dl> <dt>

*isolationInfo* \[in\]
</dt> <dd>

A pointer to the [**IsolationInfo**](/windows/win32/api/naptypes/ns-naptypes-isolationinfo) data structure to free.

</dd> </dl>

## Remarks

All the COM interfaces supported by the NAP system use standard COM memory management rules and the COM memory allocators (**CoTaskMemAlloc** and **CoTaskMemFree**):

-   **In** parameters are allocated and freed by the caller.
-   **Out** parameters are allocated by the callee and freed by the caller using **CoTaskMem**.
-   **In/out** parameters are allocated by the caller, freed and reallocated by the callee, and ultimately freed by the caller, using **CoTaskMem**.

All NAP functions for freeing memory also free all embedded pointers.

## Requirements



|                                     |                                                                                      |
|-------------------------------------|--------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista \[desktop apps only\]<br/>                                       |
| Minimum supported server<br/> | Windows Server 2008 \[desktop apps only\]<br/>                                 |
| Header<br/>                   | <dl> <dt>NapUtil.h</dt> </dl> |
| DLL<br/>                      | <dl> <dt>Qutil.dll</dt> </dl> |



 

 





