---
title: "スレッド セーフなコレクション | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, overview
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
caps.latest.revision: 24
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: b35c47a7d77038cc6a213b221e0081a4d83c8dae
ms.contentlocale: ja-jp
ms.lasthandoff: 04/08/2017

---
# <a name="thread-safe-collections"></a>スレッド セーフなコレクション
[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] では、スレッド セーフかつスケーラブルなコレクション クラスをいくつか含む <xref:System.Collections.Concurrent?displayProperty=fullName> 名前空間が導入されています。 ユーザー コードで同期を追加することなく、複数のスレッドでこのようなコレクションの項目を安全かつ効率的に追加または削除できます。 新しいコードを記述するときに、コレクションが複数のスレッドに同時に書き込みを行う場合は、常に同時実行コレクション クラスを使用します。 共有コレクションの読み取りのみを行う場合は、<xref:System.Collections.Generic?displayProperty=fullName> 名前空間のクラスを使用できます。 .NET Framework 1.1 以前のランタイムを対象にする必要がない場合は、1.0 コレクション クラスを使用しないことをお勧めします。  
  
## <a name="thread-synchronization-in-the-net-framework-10-and-20-collections"></a>.NET Framework 1.0 と 2.0 のコレクションのスレッドの同期  
 .NET Framework 1.0 で導入されたコレクションは、<xref:System.Collections?displayProperty=fullName> 名前空間にあります。 一般的に使用される <xref:System.Collections.ArrayList> や <xref:System.Collections.Hashtable> を含むこのコレクションは、コレクションのスレッド セーフ ラッパーを返す `Synchronized` プロパティを通じてスレッド セーフを確保します。 このラッパーは、すべての追加操作または削除操作でコレクション全体をロックすることで機能します。 したがって、コレクションにアクセスしようとする各スレッドは、ロックを取得する順番を待機する必要があります。 これはスケーラブルではなく、大規模なコレクションの場合はパフォーマンスが大幅に低下するおそれがあります。 また、競合状態を完全に防ぐことはできません。 詳細については、MSDN Web サイトの「[Synchronization in Generic Collections](http://go.microsoft.com/fwlink/?LinkID=161130)」 (ジェネリック コレクションでの同期) を参照してください。  
  
 .NET Framework 2.0 で導入されたコレクション クラスは、<xref:System.Collections.Generic?displayProperty=fullName> 名前空間にあります。 これには、<xref:System.Collections.Generic.List%601>、<xref:System.Collections.Generic.Dictionary%602> などがあります。 これらのクラスを使用すると、.NET Framework 1.0 クラスと比較して、タイプ セーフおよびパフォーマンスが向上します。 ただし、.NET Framework 2.0 コレクション クラスではスレッドの同期は行われません。複数のスレッドで同時に項目を追加または削除する場合は、ユーザー コードですべての同期を行う必要があります。  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] の同時実行コレクション クラスを使用することをお勧めします。このクラスは、.NET Framework 2.0 コレクション クラスのタイプ セーフを確保するだけでなく、[!INCLUDE[net_v10_short](../../../../includes/net-v10-short-md.md)] コレクションよりも効率的で完全なスレッド セーフも確保します。  
  
## <a name="fine-grained-locking-and-lock-free-mechanisms"></a>粒度の細かいロック機構とロック制御の不要な機構  
 同時実行コレクション型には、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] の新機能である <xref:System.Threading.SpinLock>、<xref:System.Threading.SpinWait>、<xref:System.Threading.SemaphoreSlim>、および <xref:System.Threading.CountdownEvent> などの軽量な同期機構を使用するものもあります。 これらの同期型では、通常、スレッドを実際の待機状態にする前の短期間に*ビジー スピン*が使用されます。 待機時間が非常に短くなると予測される場合は、スピンを使用すると、負荷がかかるカーネル遷移を伴う待機を行うよりも負荷が格段に小さくなります。 スピンを使用するコレクション クラスでは、この効率性は、複数のスレッドで項目を高速で追加および削除できることを意味します。 スピンとブロッキングの詳細については、「[SpinLock](../../../../docs/standard/threading/spinlock.md)」および「[SpinWait](../../../../docs/standard/threading/spinwait.md)」を参照してください。  
  
 <xref:System.Collections.Concurrent.ConcurrentQueue%601> クラスと <xref:System.Collections.Concurrent.ConcurrentStack%601> クラスでは、ロックは使用されません。 代わりに、<xref:System.Threading.Interlocked> 操作によってスレッド セーフを確保します。  
  
> [!NOTE]
>  同時実行コレクション クラスでは、<xref:System.Collections.ICollection> をサポートしているので、<xref:System.Collections.ICollection.IsSynchronized%2A> プロパティと <xref:System.Collections.ICollection.SyncRoot%2A> プロパティが無関係であっても、これらのプロパティの実装を提供します。 `IsSynchronized` は常に `false` を返し、`SyncRoot` は常に `null` (Visual Basic の場合は `Nothing`) になります。  
  
 次の表は、<xref:System.Collections.Concurrent?displayProperty=fullName> 名前空間のコレクション型を示しています。  
  
|型|説明|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601> を実装する任意の型に境界ブロッキング機能を提供します。 詳細については、「[BlockingCollection の概要](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)」を参照してください。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|キーと値のペアのディクショナリのスレッド セーフな実装。|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|先入れ先出し (FIFO: First In First Out) キューのスレッド セーフな実装。|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|後入れ先出し (LIFO: Last In First Out) スタックのスレッド セーフな実装。|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|要素の順序付けられていないコレクションのスレッド セーフな実装。|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|`BlockingCollection` で使用するために型が実装する必要があるインターフェイス。|  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[BlockingCollection の概要](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)|<xref:System.Collections.Concurrent.BlockingCollection%601> 型で提供される機能について説明します。|  
|[方法: ConcurrentDictionary の項目を追加および削除する](../../../../docs/standard/collections/thread-safe/how-to-add-and-remove-items.md)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602> の要素を追加および削除する方法について説明します。|  
|[方法: BlockingCollection の項目を個別に追加および取得する](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)|読み取り専用の列挙子を使用せずにブロッキング コレクションの項目を追加および取得する方法について説明します。|  
|[方法: 境界ブロッキング機能をコレクションに追加する](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)|任意のコレクション クラスを <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> コレクションの基になるストレージ機構として使用する方法について説明します。|  
|[方法: ForEach を使用して BlockingCollection 内の項目を削除する](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)|`foreach` (Visual Basic の場合は `For Each`) を使用してブロッキング コレクションのすべての項目を削除する方法について説明します。|  
|[方法: パイプラインでブロッキング コレクションの配列を使用する](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)|複数のブロッキング コレクションを同時に使用してパイプラインを実装する方法について説明します。|  
|[方法: ConcurrentBag を使用してオブジェクト プールを作成する](../../../../docs/standard/collections/thread-safe/how-to-create-an-object-pool.md)|新しいオブジェクトを頻繁に作成する代わりにオブジェクトを再利用できるシナリオで、同時実行バッグを使用してパフォーマンスを向上させる方法について説明します。|  
  
## <a name="reference"></a>参照  
 <xref:System.Collections.Concurrent?displayProperty=fullName>