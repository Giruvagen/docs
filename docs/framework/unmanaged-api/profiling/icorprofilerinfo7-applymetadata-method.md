---
title: "ICorProfilerInfo7::ApplyMetaData Method"
ms.date: "02/15/2019"
dev_langs: 
  - "cpp"
api_name: 
  - "ICorProfilerInfo7.ApplyMetaData"
api_location: 
  - "mscorwks.dll"
api_type: 
  - "COM"
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
author: "rpetrusha"
ms.author: "ronpet"
---
# ICorProfilerInfo7::ApplyMetaData Method
[Supported in the .NET Framework 4.6.1 and later versions]  
  
 Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.  
  
## Syntax  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## Parameters  
 `moduleID`  
 [in] The identifier of the module whose metadata was changed.  
  
## Remarks  
 If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.  
  
 `ApplyMetaData` only supports adding the following types of metadata:  
  
-   `AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). method.  
  
-   `TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.  
  
-   `TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.  
  
-   `MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.  
  
-   `MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.  
  
-   `UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.  

Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:

- `TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.

- `MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method. However, adding virtual methods to an existing type is not supported. Virtual methods must be added before the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.

## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## See also

- [ICorProfilerInfo7 Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
