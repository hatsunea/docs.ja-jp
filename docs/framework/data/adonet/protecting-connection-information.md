---
title: 接続情報の保護
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 4cf503af6f57eefb0990a8e7e728ea5c1474bfa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363352"
---
# <a name="protecting-connection-information"></a>接続情報の保護
アプリケーションのセキュリティを実現するうえで、データ ソースへのアクセスを保護することは、最も重要な目標の 1 つです。 保護されていない接続文字列は脆弱性を招く原因になります。 接続情報をテキスト形式で保存したり、メモリ内に保持したりすると、システム全体のセキュリティが損なわれる可能性があります。 使用して、ソース コードに埋め込まれた接続文字列を読み取ることができます、 [Ildasm.exe (IL 逆アセンブラー)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md)コンパイルされたアセンブリで Microsoft intermediate language (MSIL) を表示します。  
  
 接続文字列に関係したセキュリティ上の脆弱性は、使用されている認証の種類、メモリやディスクへの接続文字列の保存方法、実行時に接続文字列を作成する際の手法などから発生します。  
  
## <a name="use-windows-authentication"></a>Windows 認証の使用  
 データ ソースへのアクセスを制限するには、ユーザー ID、パスワード、データ ソース名などの接続情報をセキュリティで保護する必要があります。 Windows 認証の使用をお勧めをユーザー情報を公開することを避けるために (とも呼ば*統合セキュリティ*) 可能な限りです。 Windows 認証は、接続文字列に `Integrated Security` キーワードまたは `Trusted_Connection` キーワードを使用することによって指定できます。こうすることで、ユーザー ID とパスワードを使う必要がなくなります。 Windows 認証を使用した場合、ユーザーは Windows によって認証され、サーバー リソースやデータベース リソースへのアクセスは Windows のユーザーおよびグループに付与された権限によって制御されます。  
  
 Windows 認証が使用できない場合、ユーザーの資格情報を接続文字列に含めることになるため、十分な注意が必要です。 ASP.NET アプリケーションでは、Windows アカウントを、データベースやその他のネットワーク リソースに接続する際の固定 ID として構成できます。 Identity 要素での偽装を有効にする、 **web.config**ファイルし、ユーザー名とパスワードを指定します。  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 固定 ID アカウントには、権限の低いアカウント、つまり、データベースに対する必要な権限だけが付与されたアカウントを使用してください。 さらに、ユーザー名とパスワードがクリア テキストで表示されないよう、構成ファイルを暗号化する必要があります。  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>UDL (Universal Data Link) ファイルの使用回避  
 <xref:System.Data.OleDb.OleDbConnection> の接続文字列を UDL (Universal Data Link) ファイルに保存することは避けてください。 UDL はクリア テキストで保存され暗号化できません。 UDL ファイルは、アプリケーションにとって外部ファイルをベースにしたリソースであるため、.NET Framework ではセキュリティ保護も暗号化もされません。  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>接続文字列ビルダーを使用したインジェクション攻撃の防止  
 ユーザー入力から文字列を動的に連結することによって接続文字列を構築している場合、接続文字列のインジェクション攻撃を受ける可能性があります。 ユーザー入力の検証や悪意のある文字のエスケープを怠ると、機密データなど、サーバー上のリソースへのアクセスを攻撃者に許してしまうことも考えられます。 こうした問題を解消するために、ADO.NET 2.0 では、接続文字列の構文を検証し、余分なパラメーターの追加を防ぐ新しい接続文字列ビルダー クラスが導入されました。 詳細については、次を参照してください。[接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)です。  
  
## <a name="use-persist-security-infofalse"></a>Persist Security Info=False の使用  
 `Persist Security Info` の既定値は false です。すべての接続文字列には、この既定値を使用することをお勧めします。 `Persist Security Info` を `true` または `yes` に設定すると、ユーザー ID やパスワードなどのセキュリティ関連情報を、接続を開いた後にその接続から取得できます。 `Persist Security Info` を `false` または `no` に設定した場合、その情報を使って接続を開いた後で、セキュリティ情報が破棄されるため、信頼できないソースによってセキュリティ関連情報がアクセスされることを確実に防ぐことができます。  
  
## <a name="encrypt-configuration-files"></a>構成ファイルの暗号化  
 接続文字列は構成ファイルに保存することもでき、そうすることで、アプリケーションのコードに接続文字列を組み込むことを避けられます。 構成ファイルは、.NET Framework が基本的な要素を定義するために使用する標準的な XML ファイルです。 構成ファイル内の接続文字列内に格納されて通常、  **\<connectionStrings >** 内の要素、 **app.config** Windows アプリケーションの場合、または**web.config** ASP.NET アプリケーションのファイルです。 格納する基本の詳細については、取得して、構成ファイルから接続文字列の暗号化を参照してください[接続文字列と構成ファイル](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [保護された構成を使用して構成情報の暗号化](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)  
 [ネイティブ コードと .NET Framework コードのセキュリティ](http://msdn.microsoft.com/library/bd61be84-c143-409a-a75a-44253724f784)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
