---
title: '方法 : ファイル、フォルダー、およびドライブに関する情報を取得する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: c4f29cd2ae65fb05a2636ae3674c7ffd1613b0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338540"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>方法 : ファイル、フォルダー、およびドライブに関する情報を取得する (C# プログラミング ガイド)
.NET Framework では、次のクラスを使用して、ファイル システム情報にアクセスできます。  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo> クラスと <xref:System.IO.DirectoryInfo> クラスはファイルまたはディレクトリを表し、NTFS ファイル システムでサポートされるファイル属性の多くを公開するプロパティを含みます。 また、ファイルとフォルダーを開く、閉じる、移動する、および削除するためのメソッドも含まれます。 コンストラクターに、ファイル、フォルダー、またはドライブの名前を表す文字列を渡すことで、クラスのインスタンスを作成できます。  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 また、<xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>、<xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>、および <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType> の呼び出しを使用して、ファイル、フォルダー、またはドライブの名前を取得することもできます。  
  
 <xref:System.IO.Directory?displayProperty=nameWithType> クラスと <xref:System.IO.File?displayProperty=nameWithType> クラスは、ディレクトリとファイルに関する情報を取得するための静的メソッドを提供します。  
  
## <a name="example"></a>例  
 次の例では、ファイルとフォルダーに関する情報にアクセスするさまざまな方法を示します。  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ユーザー指定のパス文字列を処理する場合、次の条件の例外も処理する必要があります。  
  
-   ファイル名が不適切である。 たとえば、無効な文字が含まれている場合や、空白のみの場合です。  
  
-   ファイル名が NULL である。  
  
-   ファイル名の長さがシステムで定義された最大長を超えている。  
  
-   ファイル名にコロン (:) が含まれている。  
  
 指定したファイルの読み取りに必要なアクセス許可がアプリケーションに与えられていない場合、`Exists` メソッドは目的のパスが存在するかどうかに関係なく `false` を返します。ただし、例外はスローされません。  
  
## <a name="see-also"></a>参照  
 <xref:System.IO?displayProperty=nameWithType>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ファイル システムとレジストリ (C# プログラミング ガイド)](../../../csharp/programming-guide/file-system/index.md)
