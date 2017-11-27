---
title: ICorDebugType Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType
helpviewer_keywords: ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9a25e72766e6647f820c9871e989d4b24db0bf26
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtype-interface1"></a><span data-ttu-id="f8634-102">ICorDebugType Interface1</span><span class="sxs-lookup"><span data-stu-id="f8634-102">ICorDebugType Interface1</span></span>
<span data-ttu-id="f8634-103">型、基本または複雑な (つまり、ユーザー定義) を表します。</span><span class="sxs-lookup"><span data-stu-id="f8634-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="f8634-104">型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="f8634-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8634-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f8634-105">Methods</span></span>  
  
|<span data-ttu-id="f8634-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="f8634-106">Method</span></span>|<span data-ttu-id="f8634-107">説明</span><span class="sxs-lookup"><span data-stu-id="f8634-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8634-108">EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="f8634-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="f8634-109">ジェネリックを参照する ICorDebugTypeEnum へのインターフェイス ポインターを取得<xref:System.Type>これによって参照されるクラスのパラメーター`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="f8634-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="f8634-110">GetBase メソッド</span><span class="sxs-lookup"><span data-stu-id="f8634-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="f8634-111">インターフェイス ポインターを取得、`ICorDebugType`これによって参照されるクラスの基底クラスを参照する`ICorDebugType`が存在する場合は、します。</span><span class="sxs-lookup"><span data-stu-id="f8634-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="f8634-112">GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="f8634-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="f8634-113">この型指定されたコンス トラクターを参照する ICorDebugClass へのインターフェイス ポインターを取得`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="f8634-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="f8634-114">GetFirstTypeParameter メソッド</span><span class="sxs-lookup"><span data-stu-id="f8634-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="f8634-115">インターフェイス ポインターを取得、`ICorDebugType`を参照する最初のジェネリック<xref:System.Type>これによって参照されるクラスのコンス トラクターのパラメーター`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="f8634-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="f8634-116">GetRank メソッド</span><span class="sxs-lookup"><span data-stu-id="f8634-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="f8634-117">配列型の次元数を取得します。</span><span class="sxs-lookup"><span data-stu-id="f8634-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="f8634-118">GetStaticFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="f8634-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="f8634-119">トークンを指定したスタック フレームに指定したフィールドによって参照される静的フィールドの値を含む ICorDebugValue にインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f8634-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="f8634-120">GetType メソッド</span><span class="sxs-lookup"><span data-stu-id="f8634-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="f8634-121">共通言語ランタイムのネイティブ型を記述する CorElementType 値を取得<xref:System.Type>これによって参照される`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="f8634-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8634-122">コメント</span><span class="sxs-lookup"><span data-stu-id="f8634-122">Remarks</span></span>  
 <span data-ttu-id="f8634-123">場合は、型がジェネリック、`ICorDebugClass`インスタンス化されていない型を表します。</span><span class="sxs-lookup"><span data-stu-id="f8634-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="f8634-124">`ICorDebugType`インターフェイスはジェネリック型のインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="f8634-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="f8634-125">ハッシュ テーブルなど、\<K, V > で表されます`ICorDebugClass`であるのに対し Hashtable\<Int32, String > で表されます`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="f8634-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="f8634-126">非ジェネリック型は型が両方によって表される`ICorDebugClass`と`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="f8634-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="f8634-127">後者のインターフェイスは、型のインスタンス化に対処するには、.NET Framework version 2.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="f8634-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8634-128">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f8634-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8634-129">要件</span><span class="sxs-lookup"><span data-stu-id="f8634-129">Requirements</span></span>  
 <span data-ttu-id="f8634-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8634-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8634-131">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8634-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8634-132">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8634-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8634-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8634-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8634-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8634-134">See Also</span></span>  
 [<span data-ttu-id="f8634-135">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8634-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)