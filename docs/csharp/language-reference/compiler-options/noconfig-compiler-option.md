---
title: -noconfig (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 96321de5982a79cb073b658a84e0e580dd466539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214443"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (C# コンパイラ オプション)
**-noconfig** オプションは、csc.exe ファイルと同じディレクトリにあり、このディレクトリから読み込まれた csc.rsp ファイルでコンパイルしないようにコンパイラに指示します。  
  
## <a name="syntax"></a>構文  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>コメント  
 csc.rsp ファイルは、.NET Framework に付属するすべてのアセンブリを参照します。 Visual Studio .NET 開発環境に含まれる実際の参照は、プロジェクトの種類によって異なります。  
  
 csc.rsp ファイルを変更し、csc.exe 使ってコマンドラインからすべてのコンパイルに含める必要がある追加のコンパイラ オプションを指定できます (**-noconfig** オプションを除きます)。  
  
 コンパイラは **csc** コマンドに最後に渡されるオプションを処理します。 そのため、コマンドラインで指定した任意のオプションが、csc.rsp ファイル内の同じオプションの設定を上書きします。  
  
 コンパイラで csc.rsp ファイル内の設定を検索して使用しない場合は、**-noconfig** を指定します。  
  
 このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。  
  
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
