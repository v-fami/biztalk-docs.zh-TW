---
title: "解析程式管理員 (ResolverMgr) 類別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89fa551d-0aca-4777-adbc-2bc46ab8664a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6621ad0c6b9edb5bf93950f9b9d05a7655f0e36d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolver-manager-resolvermgr-class"></a>解析程式管理員 (ResolverMgr) 類別
轉換和路由訊息處理服務會使用**ResolverMgr**執行解析的類別。 在 ESB 動態轉換和動態傳遞代理程式也使用**ResolverManager**類別來執行在 just-in-time (JIT) 解析。  
  
 ESB 核心安裝程式安裝並註冊**Microsoft.Practices.ESB.Resolver.dll**具有組件**ResolverMgr**在全域組件快取中的類別。  
  
 您可以使用這個類別，在您自己的程式碼中您要執行的結束點或地圖的動態解析。 您也可以擴充這個類別，以使用自訂解決方法。 不過，請記住，類別已經支援解析機制，可以使用任何自訂解決器組件，必須符合任何您可能需要的另一種解決方案演算法。  
  
 下列程式碼範例示範如何使用**ResolverMgr**類別解析端點。  
  
```csharp  
// Move to retrieve the first resolver.  
resolvers = itineraryStep.ResolverCollection;  
resolver = resolvers.Current;  
  
// Pass the resolver configuration to the Resolver Manager for resolution.  
resolverDictionary = Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage, resolver);  
  
// Set transport properties.  
transportLocation = resolverDictionary.Item("Resolver.TransportLocation");  
transportType = resolverDictionary.Item("Resolver.TransportType");  
```  
  
 通常，您解析程式的連接字串指定至少一個解決方法，例如規則原則、 自訂組件，XPath 陳述式或通用描述、 探索與整合 (UDDI) 的標籤和伺服器名稱的屬性值。 最後，它會傳回一個字典物件，可以輕鬆地填入從具象的解析程式的自訂事實的解析程式事實的集合。  
  
 如需 ESB 解決機制的運作方式的詳細資訊，請參閱[使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)。