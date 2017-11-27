---
title: "CeeSectionAttr 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CeeSectionAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CeeSectionAttr
helpviewer_keywords: CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f0c87c0e5703f13cf843ca5a4213440af71bd12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="7530c-102">CeeSectionAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="7530c-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="7530c-103">使用するセクションの属性を指定する値を提供、 [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="7530c-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7530c-104">構文</span><span class="sxs-lookup"><span data-stu-id="7530c-104">Syntax</span></span>  
  
```  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="7530c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="7530c-105">Members</span></span>  
  
|<span data-ttu-id="7530c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="7530c-106">Member</span></span>|<span data-ttu-id="7530c-107">説明</span><span class="sxs-lookup"><span data-stu-id="7530c-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="7530c-108">セクションには、属性がありません。</span><span class="sxs-lookup"><span data-stu-id="7530c-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="7530c-109">セクションには、読み取りのみ可能で、更新されない初期化されたデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7530c-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="7530c-110">セクションには、読み取りまたは更新が可能な初期化済みデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7530c-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="7530c-111">セクションには、読み取りし、実行が許可されている実行可能コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7530c-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7530c-112">要件</span><span class="sxs-lookup"><span data-stu-id="7530c-112">Requirements</span></span>  
 <span data-ttu-id="7530c-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7530c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7530c-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7530c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7530c-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="7530c-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7530c-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7530c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7530c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7530c-117">See Also</span></span>  
 [<span data-ttu-id="7530c-118">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="7530c-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)