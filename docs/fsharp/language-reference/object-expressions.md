---
title: オブジェクト式 (F#)
description: 名前付きの種類を追加のコードと、新規作成に必要なオーバーヘッドを回避するときに、f# オブジェクト式を使用する方法を学習します。
ms.date: 05/16/2016
ms.openlocfilehash: fed78e2be52838eedf55759b195696f1210a8a20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564392"
---
# <a name="object-expressions"></a>オブジェクト式

*式をオブジェクト*は動的に作成された、匿名のオブジェクトの種類の新しいインスタンスを作成する式が既存の基本型、インターフェイス、またはインターフェイスのセットに基づいて。


## <a name="syntax"></a>構文

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>コメント
前の構文では、 *typename*既存のクラス型またはインターフェイス型を表します。 *型 params*省略可能なジェネリック型パラメーターについて説明します。 *引数*コンス トラクターのパラメーターを必要とするクラス型に対してのみ使用します。 *メンバー定義*は基本クラスのメソッドをオーバーライドまたは基底クラスまたはインターフェイスのいずれかの抽象メソッドの実装です。

次の例は、さまざまな種類のオブジェクトの式を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>オブジェクト式を使用します。
余分なコードと名前付きの種類を新規作成に必要なオーバーヘッドを回避する場合は、オブジェクト表現を使用します。 プログラムで作成された型の数を最小限に抑えるには、オブジェクト表現を使用する場合のコード行の数を削減し、型の不要な急増を回避できます。 特定の状況に対処するためだけの多くの種類を作成するには、代わりに、既存の種類をカスタマイズまたは特定の状況にインターフェイスの適切な実装を提供するオブジェクト式を使用することができます。


## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)
