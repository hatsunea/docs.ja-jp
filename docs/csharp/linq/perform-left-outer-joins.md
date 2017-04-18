---
title: "左外部結合の実行"
description: "方法: 左外部結合を実行する。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6ba90a6fe16d4ba33e8b9e55c93f7365b6bc905b
ms.lasthandoff: 03/13/2017

---
# <a name="perform-left-outer-joins"></a>左外部結合の実行
左外部結合は、最初のコレクションの各要素を、2 つ目のコレクション内にある要素との相関関係の有無にかかわらず返す結合です。 LINQ を使用すると、グループ結合の結果に対して <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> メソッド呼び出すことで、左外部結合を実行できます。  
  
## <a name="example"></a>例  
 次の例は、グループ結合の結果に対して <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> メソッドを使用し、左外部結合を実行する方法を示しています。  
  
 2 つのコレクションの左外部結合を作成するための最初のステップは、グループ結合を使用して内部結合を実行することです。 (このプロセスの詳細については、「[内部結合の実行](perform-inner-joins.md)」参照してください。)この例では、`Pet.Owner` に一致する `Person` オブジェクトに基づいて、`Person` オブジェクトの一覧が `Pet` オブジェクトの一覧に内部結合されています。  
  
 2 つ目のステップは、最初 (左側) のコレクションの各要素を結果セットに含めることです。このとき、その要素と一致するものが右のコレクションにあるかどうかは考慮しません。 これを行うには、グループ結合内の一致する要素の各シーケンスに対して、<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> を呼び出します。 この例では、`Pet` オブジェクトに一致する各シーケンスに対して、<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> が呼び出されています。 このメソッドは、`Person` オブジェクトに対して一致する `Pet` オブジェクトのシーケンスが空である場合に、単一の既定値を含んだコレクションを返します。これにより、各 `Person` オブジェクトが結果コレクション内に表されることが保証されます。  
  
> [!NOTE]
>  参照型の既定値は `null` です。そのためこのコード例では、各 `Pet` コレクションの各要素にアクセスする前に Null 参照がチェックされます。  
  
 [!code-cs[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [内部結合の実行](perform-inner-joins.md)   
 [グループ化結合の実行](perform-grouped-joins.md)   
 [匿名型](../programming-guide/classes-and-structs/anonymous-types.md)   
 