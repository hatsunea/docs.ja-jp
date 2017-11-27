---
title: "GetCurrentApartmentType 関数 (アンマネージ API リファレンス)"
description: "GetCurrentApartmentType 関数では、呼び出し元を実行しているアパートメントの種類を取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetCurrentApartmentType
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetCurrentApartmentType
helpviewer_keywords: GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b250913b55ba59261a666760cc15466b6f9d096e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="d6c52-103">GetCurrentApartmentType 関数</span><span class="sxs-lookup"><span data-stu-id="d6c52-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="d6c52-104">呼び出し元を実行しているアパートメントの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="d6c52-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d6c52-105">構文</span><span class="sxs-lookup"><span data-stu-id="d6c52-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="d6c52-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6c52-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d6c52-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="d6c52-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d6c52-108">[in]ポインター、 [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="d6c52-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="d6c52-109">[out]ポインター、 [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx)を呼び出し元のアパートメントを示す列挙値。</span><span class="sxs-lookup"><span data-stu-id="d6c52-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="d6c52-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="d6c52-110">Return value</span></span>


|<span data-ttu-id="d6c52-111">定数</span><span class="sxs-lookup"><span data-stu-id="d6c52-111">Constant</span></span>  |<span data-ttu-id="d6c52-112">値</span><span class="sxs-lookup"><span data-stu-id="d6c52-112">Value</span></span>  |<span data-ttu-id="d6c52-113">説明</span><span class="sxs-lookup"><span data-stu-id="d6c52-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="d6c52-114">0</span><span class="sxs-lookup"><span data-stu-id="d6c52-114">0</span></span> | <span data-ttu-id="d6c52-115">関数が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="d6c52-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="d6c52-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="d6c52-116">0x80000008</span></span> | <span data-ttu-id="d6c52-117">呼び出し元はアパートメントで実行していません。</span><span class="sxs-lookup"><span data-stu-id="d6c52-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d6c52-118">コメント</span><span class="sxs-lookup"><span data-stu-id="d6c52-118">Remarks</span></span>

<span data-ttu-id="d6c52-119">この関数への呼び出しをラップする、 [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d6c52-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6c52-120">要件</span><span class="sxs-lookup"><span data-stu-id="d6c52-120">Requirements</span></span>  
 <span data-ttu-id="d6c52-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6c52-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c52-122">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d6c52-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d6c52-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c52-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c52-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6c52-124">See also</span></span>  
[<span data-ttu-id="d6c52-125">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d6c52-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)