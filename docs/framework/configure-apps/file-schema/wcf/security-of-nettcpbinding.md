---
title: "&lt;netTcpBinding&gt; の &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
caps.latest.revision: 18
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 18
---
# &lt;netTcpBinding&gt; の &lt;security&gt;
バインディングのセキュリティ設定を定義します。  
  
## 構文  
  
```  
  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|モード|省略可能です。  適用するセキュリティの種類を指定します。  有効な値を次に示します。  既定値は `Transport` です。<br /><br /> この属性は <xref:System.ServiceModel.SecurityMode> 型です。|  
  
## mode 属性  
  
|値|説明|  
|-------|--------|  
|なし|セキュリティを無効にします。|  
|Transport|トランスポート セキュリティは、TCP 経由の TLS または SPNaego を使用して提供されます。  サービスは、SSL 証明書を使用して設定する必要があります。  このモードでの保護レベルを制御できます。|  
|メッセージ|セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。  既定では、SOAP 本文は暗号化および署名されます。  このモードは、サービス資格情報をクライアントの帯域外で使用可能にするかどうか、使用するアルゴリズム スイート、メッセージ本文に適用する保護レベルなど、さまざまな機能を提供します。  クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。|  
|TransportWithMessageCredential|トランスポート セキュリティは、メッセージ セキュリティと組み合わせて使用されます。  トランスポート セキュリティは、TCP 経由の TLS または SPNego によって提供され、整合性、機密性、およびサーバー認証が保証されます。  SOAP メッセージ セキュリティは、クライアント認証を提供します。  既定では、クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|トランスポートのセキュリティ設定を定義します。  この要素は <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement> 型です。|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|メッセージのセキュリティ設定を定義します。  この要素は <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|バインド|[\<netTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)のバインディング要素です。|  
  
## 解説  
 標準バインディングにはそれぞれ、転送セキュリティ要件を制御するためのパラメーターが用意されています。  通常、これらのパラメーターには、使用されるセキュリティ レベル \(メッセージ レベルまたはトランスポート レベル\) を指定したセキュリティ モードと、クライアント資格情報の種類が含まれています。  これらのパラメーターが提示するオプションの選択に基づいて、適切なセキュリティが設定されたチャネル スタックが構築されます。  
  
 WCF \(Windows Communication Foundation\) に用意されているシステム標準のバインディグは、最も一般的なシナリオ要件の一部を満たすように設計されたセットです。  これらのバイディングでは、特定のシナリオを対象とするセキュリティ要件を指定できます。  
  
 この構成要素によって、`netTcpBinding` のセキュリティ仕様が提供されます。  これは、コンピューター間通信に適した、安全で信頼できる最適化されたバインディングです。  既定では、このバインディングは、メッセージを配信するための TCP、メッセージの保護と認証を行うための Windows セキュリティ、信頼性を高めるための WS\-ReliableMessaging、およびバイナリ メッセージのエンコーディングをサポートするランタイム通信スタックを生成します。  
  
## 参照  
 <xref:System.ServiceModel.NetTcpSecurity>   
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)