---
title: '方法 : IIS で WCF サービスをホストする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: a1759434d259cdffe1dac6b19a6582bfb83784bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492485"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>方法 : IIS で WCF サービスをホストする
このトピックでは、インターネット インフォメーション サービス (IIS) でホストされている Windows Communication Foundation (WCF) サービスを作成するために必要な基本的な手順について説明します。 このトピックは、IIS に関する知識があり、IIS 管理ツールを使用して IIS アプリケーションを作成および管理する方法を理解していることを前提としています。 IIS の詳細については、次を参照してください。[インターネット インフォメーション サービス](http://go.microsoft.com/fwlink/?LinkId=132449)です。 IIS 環境で実行されますが、プロセスのリサイクルなどの IIS 機能を最大限に活用する WCF サービスのアイドル シャット ダウン、処理状況の監視、およびメッセージに基づくアクティベーション。 このホスト オプションでは、IIS が正しく構成されている必要がありますが、アプリケーションの一部としてホスト コードを書く必要はありません。 IIS ホストは、HTTP トランスポートでのみ使用できます。  
  
 方法の詳細についての WCF と[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]対話は、「 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)です。 セキュリティの構成の詳細については、次を参照してください。[セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)です。  
  
 この例の元のコピーを次を参照してください。 [IIS ホストを使用してインライン コード](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)です。  
  
### <a name="to-create-a-service-hosted-by-iis"></a>IIS でホストされるサービスを作成するには  
  
1.  コンピューターに IIS がインストールされ、実行されていることを確認します。 インストールして、IIS の構成の詳細については、次を参照してください[のインストールと IIS 7.0 の構成。](http://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  アプリケーション ファイル用に "IISHostedCalcService" という新しいフォルダーを作成し、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] がそのフォルダーの内容にアクセスできることを確認します。次に、IIS 管理ツールを使用して、このアプリケーション ディレクトリに物理的に配置する新しい IIS アプリケーションを作成します。 アプリケーション ディレクトリのエイリアスを作成する場合は、"IISHostedCalc" を使用します。  
  
3.  "service.svc" という新しいファイルをアプリケーション ディレクトリに作成します。 次を追加することでこのファイルを編集@ServiceHost要素。  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  アプリケーション ディレクトリ内に App_Code サブディレクトリを作成します。  
  
5.  App_Code サブディレクトリに Service.cs というコード ファイルを作成します。  
  
6.  Service.cs ファイルの先頭に次の using ステートメントを追加します。  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  using ステートメントの後に、次の名前空間宣言を追加します。  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  次のコードに示すように、名前空間宣言内にサービス コントラクトを定義します。  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. 次のコードに示すように、サービス コントラクト定義の後に、サービス コントラクトを実装します。  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. アプリケーション ディレクトリ内に "Web.config" というファイルを作成し、次の構成コードをファイルに追加します。 実行時に、WCF インフラストラクチャは、クライアント アプリケーションと通信できるエンドポイントを構築するために情報を使用します。  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     この例では、構成ファイルにエンドポイントを明示的に指定します。 エンドポイントをサービスに追加しない場合、ランタイムによって既定のエンドポイントが追加されます。 詳細については、既定のエンドポイント、バインディング、および動作を参照してください[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。  
  
11. サービスが正確にホストされるようにするには、Internet Explorer のインスタンスを開き、サービスの URL: `http://localhost/IISHostedCalc/Service.svc` を参照します。  
  
## <a name="example"></a>例  
 IIS がホストする電卓サービスのコードの完全な一覧を次に示します。  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>関連項目  
 [インターネット インフォメーション サービスでのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)  
 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
