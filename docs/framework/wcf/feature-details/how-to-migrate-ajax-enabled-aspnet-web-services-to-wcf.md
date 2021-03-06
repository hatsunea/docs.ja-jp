---
title: '方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 048408adf8678c243a225a233cb1173c9b7f869f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する
このトピックでは、基本的な ASP.NET AJAX サービスを同等の AJAX 対応の Windows Communication Foundation (WCF) サービスに移行する手順について説明します。 ASP.NET AJAX サービスの同等の WCF バージョンを作成する方法を示します。 サイド バイ サイドで、2 つのサービスは使用して、または WCF サービスは、ASP.NET AJAX サービスを置き換えるを使用することができます。  
  
 既存の ASP.NET AJAX を移行するサービスを WCF AJAX サービスでは、次の利点があります。  
  
-   最小限の追加構成で、AJAX サービスを SOAP サービスとして公開できます。  
  
-   トレースなどの WCF 機能を利用しにできます。  
  
 次の手順では、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] が使用されていることを前提としています。  
  
 手順に続く例で、ここで説明する手順によって作成されるコードを示します。  
  
 AJAX 対応エンドポイントを介して WCF サービスを公開する詳細については、次を参照してください。、[する方法: ASP.NET AJAX エンドポイントを追加する構成を使用する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)トピックです。  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a>ASP.NET Web サービス アプリケーションを作成してテストする  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を開きます。  
  
2.  **ファイル**メニューの **新規**、し**プロジェクト**、し**Web**、し、 **ASP.NET Web サービス アプリケーション**.  
  
3.  プロジェクトに名前を`ASPHello` をクリック**OK**です。  
  
4.  Service1.asmx.cs ファイルで、`System.Web.Script.Services.ScriptService]` が含まれた行のコメントを解除し、このサービスに対して AJAX を有効にします。  
  
5.  **ビルド**メニューの **ソリューションのビルド**です。  
  
6.  **デバッグ**メニューの **デバッグなしで開始**です。  
  
7.  生成された Web ページで、`HelloWorld` 操作を選択します。  
  
8.  クリックして、 **Invoke**のボタンでは、`HelloWorld`テスト ページ。 次の XML 応答を受信します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. この応答は、ASP.NET AJAX サービスが現在機能していること、およびこのサービスが現在 Service1.asmx/HelloWorld でエンドポイントを公開していることを確認するものです。このエンドポイントが HTTP POST 要求に応答し、XML を返します。  
  
     WCF AJAX サービスを使用するには、このサービスに変換する準備が整いました。  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>同等の WCF AJAX サービス アプリケーションを作成するには  
  
1.  右クリックし、 **ASPHello**プロジェクトし、選択**追加**、し**新しい項目の**、し**AJAX 対応 WCF サービス**です。  
  
2.  サービスの名前を付けます`WCFHello` をクリック**追加**です。  
  
3.  WCFHello.svc.cs ファイルを開きます。  
  
4.  Service1.asmx.cs からの次の実装をコピー、`HelloWorld`操作します。  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  コピーの実装に貼り付け、`HelloWorld`次のコードの代わりに、WCFHello.svc.cs ファイルに操作します。  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  指定して、`Namespace`属性<xref:System.ServiceModel.ServiceContractAttribute>として`WCFHello`です。  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  追加、<xref:System.ServiceModel.Web.WebInvokeAttribute>を`HelloWorld`操作とセット、<xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>を返すプロパティ<xref:System.ServiceModel.Web.WebMessageFormat.Xml>です。 この設定を行わない場合、既定の戻り値の型は <xref:System.ServiceModel.Web.WebMessageFormat.Json> です。  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  **ビルド**メニューの **ソリューションのビルド**です。  
  
9. WCFHello.svc ファイルを開くとの間、**デバッグ**メニューの **デバッグなしで開始**です。  
  
10. サービス エンドポイントを公開今すぐ`WCFHello.svc/HelloWorld`、HTTP POST 要求に応答します。 HTTP POST 要求をブラウザーからテストすることはできませんが、エンドポイントは次の XML を返します。  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. `WCFHello.svc/HelloWorld`と`Service1.aspx/HelloWorld`エンドポイントは機能的に等価ようになりました。  
  
## <a name="example"></a>例  
 このトピックで説明した手順によって作成されるコードを次の例に示します。  
  
```  
//This is the ASP.NET code in the Service1.asmx.cs file.  
  
using System;  
using System.Collections;  
using System.ComponentModel;  
using System.Data;  
using System.Linq;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Linq;  
using System.Web.Script.Services;  
  
namespace ASPHello  
{  
    /// <summary>  
    /// Summary description for Service1.  
    /// </summary>  
    [WebService(Namespace = "http://tempuri.org/")]  
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
    [ToolboxItem(false)]  
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.   
    [System.Web.Script.Services.ScriptService]  
    public class Service1 : System.Web.Services.WebService  
    {  
  
        [WebMethod]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
    }  
}   
  
//This is the WCF code in the WCFHello.svc.cs file.  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace ASPHello  
{  
    [ServiceContract(Namespace = "WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class WCFHello  
    {  
        // Add [WebInvoke] attribute to use HTTP GET.  
        [OperationContract]  
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
  
        // Add more operations here and mark them with [OperationContract].  
    }  
}  
```  
  
 <xref:System.Xml.XmlDocument> 型は、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> によってシリアル化できないため、<xref:System.Xml.Serialization.XmlSerializer> ではサポートされていません。 <xref:System.Xml.Linq.XDocument> 型を使用するか、<xref:System.Xml.XmlDocument.DocumentElement%2A> をシリアル化します。  
  
 ASMX Web サービスがアップグレード中は、WCF サービスにサイド バイ サイドを移行する場合は、クライアントで同じ名前に 2 つの型をマッピングしないようにします。 同じ名前が割り当てられていると、<xref:System.Web.Services.WebMethodAttribute> と <xref:System.ServiceModel.ServiceContractAttribute> で同じ型が使用されている場合に、シリアライザーで次のような例外が発生します。  
  
-   WCF サービスを最初に追加すると場合に、例外の原因の ASMX Web サービス メソッドを呼び出して<xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29>のため、WCF スタイルの定義、プロキシでの順序が優先されます。  
  
-   WCF サービスでメソッドを呼び出す場合は、ASMX Web サービスを最初に追加するで例外が発生<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>のため、プロキシでの順序の Web サービス スタイル定義が優先されます。  
  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> と ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> の動作には大きな違いがあります。 たとえば、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> はディクショナリをキーと値のペアの配列として表しますが、ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> はディクショナリを実際の JSON オブジェクトとして表します。 したがって、ASP.NET AJAX では、ディクショナリが次のように表されます。  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 このディクショナリは、JSON オブジェクトでは次のように表されます。  
  
-   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> では [{"Key":"one","Value":1},{"Key":"two","Value":2}] と表され、  
  
-   {"one": 1,"two": 2} ASP.NET ajax <xref:System.Web.Script.Serialization.JavaScriptSerializer>  
  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、キーの種類が文字列ではないディクショナリを処理でき、<xref:System.Web.Script.Serialization.JavaScriptSerializer> はできません。この点で前者はより強力と言えます。 しかし、後者の方が JSON で使いやすいと言えます。  
  
 これらのシリアライザーの主な違いを次の表に示します。  
  
|相違点のカテゴリ|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|  
|-----------------------------|--------------------------------|---------------------------------------|  
|空きバッファー (新しい byte[0]) の <xref:System.Object> (または <xref:System.Uri>、あるいは他の一部のクラス) への逆シリアル化|SerializationException|null|  
|<xref:System.DBNull.Value> のシリアル化|{} (または {"_ _type":"#System"})|Null|  
|[Serializable] 型のプライベート メンバーのシリアル化|シリアル化できます|シリアル化できません|  
|<xref:System.Runtime.Serialization.ISerializable> 型のパブリック プロパティのシリアル化|シリアル化できません|シリアル化できます|  
|JSON の「拡張機能」|オブジェクト メンバー名で引用符を必要とする ({"a":"hello"}) JSON 仕様に準拠しています。|引用符のないオブジェクト メンバー名 ({a:"hello"}) をサポートします。|  
|<xref:System.DateTime> 協定世界時刻 (UTC)|形式をサポートしていません"\\/Date(123456789U)\\/"または"\\日付/\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".|形式"\\/Date(123456789U)\\/"および"\\日付/\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\)\\ \\/)"としての DateTime 値。|  
|ディクショナリの表現|KeyValuePair の配列\<K, V >、文字列以外の種類のキーを処理します。|実際の JSON オブジェクトですが、文字列の種類のキーのみ処理します。|  
|エスケープ文字|必ず、エスケープ文字であるスラッシュ (/) を付けます。"\n" などのエスケープされない無効な JSON 文字は使用できません。|DateTime 値には、エスケープ文字スラッシュ (/) を付けます。|  
  
## <a name="see-also"></a>関連項目  
 [方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
