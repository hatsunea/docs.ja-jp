---
title: "CorNotificationForTokenMovement 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNotificationForTokenMovement
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNotificationForTokenMovement
helpviewer_keywords: CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60d6c56394952fca84b45ba042f7d45a1dec6b1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="b3f92-102">CorNotificationForTokenMovement 列挙型</span><span class="sxs-lookup"><span data-stu-id="b3f92-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="b3f92-103">トークンの再マップが発生したときに、メタデータ API クライアントに送信される通知を指定します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f92-104">構文</span><span class="sxs-lookup"><span data-stu-id="b3f92-104">Syntax</span></span>  
  
```  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a><span data-ttu-id="b3f92-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b3f92-105">Members</span></span>  
  
|<span data-ttu-id="b3f92-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b3f92-106">Member</span></span>|<span data-ttu-id="b3f92-107">説明</span><span class="sxs-lookup"><span data-stu-id="b3f92-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="b3f92-108">通知のタイミング`mdTypeRef`、 `mdMethodDef`、 `mdMemberRef`、または`mdFieldDef`トークン移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="b3f92-109">任意のトークンを動かしたときに通知します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="b3f92-110">トークンの移動時に通知しません。</span><span class="sxs-lookup"><span data-stu-id="b3f92-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="b3f92-111">通知のタイミング、`mdMethodDef`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="b3f92-112">通知のタイミング、`mdMemberRef`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="b3f92-113">通知のタイミング、`mdFieldDef`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="b3f92-114">通知のタイミング、`mdTypeRef`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="b3f92-115">通知のタイミング、`mdTypeDef`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="b3f92-116">通知のタイミング、`mdParamDef`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="b3f92-117">通知のタイミング、`mdInterfaceImpl`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="b3f92-118">通知のタイミング、`mdProperty`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="b3f92-119">通知のタイミング、`mdEvent`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="b3f92-120">通知のタイミング、`mdSignature`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="b3f92-121">通知のタイミング、`mdTypeSpec`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="b3f92-122">通知のタイミング、`mdCustomAttribute`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="b3f92-123">通知のタイミング、`mdSecurityValue`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="b3f92-124">通知のタイミング、`mdPermission`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="b3f92-125">通知のタイミング、`mdModuleRef`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="b3f92-126">通知のタイミング、`mdNameSpace`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="b3f92-127">通知のタイミング、`mdAssemblyRef`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="b3f92-128">通知のタイミング、`mdFile`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="b3f92-129">通知のタイミング、`mdExportedType`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="b3f92-130">通知のタイミング、`mdManifestResource`トークンを移動します。</span><span class="sxs-lookup"><span data-stu-id="b3f92-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3f92-131">コメント</span><span class="sxs-lookup"><span data-stu-id="b3f92-131">Remarks</span></span>  
 <span data-ttu-id="b3f92-132">トークンが再マップされる (移動) メタデータのマージ中にします。</span><span class="sxs-lookup"><span data-stu-id="b3f92-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3f92-133">要件</span><span class="sxs-lookup"><span data-stu-id="b3f92-133">Requirements</span></span>  
 <span data-ttu-id="b3f92-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b3f92-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3f92-135">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b3f92-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b3f92-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3f92-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f92-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3f92-137">See Also</span></span>  
 [<span data-ttu-id="b3f92-138">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="b3f92-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)