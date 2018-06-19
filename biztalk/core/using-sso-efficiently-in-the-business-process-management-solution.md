---
title: 商務程序管理解決方案中有效使用 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, process management solutions
- SSO, configuration values
- caching, configuration values [SSO]
- SSO, caching
- process management solution tutorial, SSO
ms.assetid: 39fbc42d-caa4-4003-a13b-5cde578eb5e1
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99575e54b887124bfa4c33fc5257cd057ea818fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288518"
---
# <a name="using-sso-efficiently-in-the-business-process-management-solution"></a>商務程序管理解決方案中有效使用 SSO
如同服務導向解決方案，商務程序管理解決方案也使用「企業單一登入」(SSO) 來儲存組態值，例如，訂單處理階段數目。 此解決方案使用密碼存放區，因為只要安裝 BizTalk，密碼存放區就會存在，SSO 會快取組態資訊，讓組態值隨時可供使用，而且它也可以保護如資料庫連接字串和密碼等資訊。 基於這些理由，即使未使用「單一登入」來管理與後端應用程式的連線，密碼存放區仍是保存組態資訊的理想位置。  
  
 為減少延遲，此解決方案將使用本機快取做為組態值。 此解決方案每五分鐘會重新整理一次快取。  
  
 本主題描述解決方案使用的快取機制。 本解決方案與服務導向解決方案的 SSO 快取方式稍有不同。 描述如何在服務導向解決方案會快取 SSO 值，請參閱[使用 SSO 有效率地在服務導向解決方案](../core/using-sso-efficiently-in-the-service-oriented-solution.md)。  
  
## <a name="caching-configuration-values-locally"></a>在本機快取組態值  
 商務程序管理解決方案使用單一物件中的屬性，以供存取 SSO 值。  
  
> [!NOTE]
>  請您回想，單一物件是只能有一個執行個體的物件。 如需單一物件和在 C# 中建立它們的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=58806](http://go.microsoft.com/fwlink/?LinkId=58806)。  
  
 在解決方案中，協調流程首先會擷取單一物件，然後透過該物件的屬性來參考值。 以下為程式碼**OrderManager**協調流程：  
  
```  
configData = Microsoft.Samples.BizTalk.SouthridgeVideo.Utilities  
                .SsoConfigHelper.Singleton;  
numStages = configData.TotalStages;  
```  
  
 協調流程會呼叫**單一**方法**SsoConfigHelper**一份物件存取的物件。 協調流程將會與該物件，擷取處理階段數目**TotalStages**。  
  
 方案會遵循一般的方法，來建立單一： 讓建構函式成為 private，讓物件建立本身的執行個體並指派給私用變數，並透過方法或屬性，讓您存取變數的值。 **SsoConfigHelper**物件使用的屬性，**單一**，以存取本身的單一複本。  
  
> [!NOTE]
>  **SsoConfigHelper**物件使用的靜態建構函式，從 SSO 快取取得初始值並設定重新整理機制。 由於無法呼叫靜態建構函式，所以它會保留單一設計。 如需靜態建構函式的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=59142](http://go.microsoft.com/fwlink/?LinkId=59142)。  
  
 協調流程直接或間接參考的所有物件都必須可序列化。 如需詳細資訊，請參閱 < 序列化 >[持續性和協調流程引擎](../core/persistence-and-the-orchestration-engine.md)。 雖然**SsoConfigHelper**物件必須為可序列化，若引擎凍結協調流程中，當協調流程解除凍結，仍會使用單一的目前物件的執行個體。 如需序列化與 BizTalk Server 變數的詳細資訊，請參閱[協調流程變數的型別](../core/orchestration-variable-types.md)。  
  
> [!NOTE]
>  在服務導向解決方案中，物件上的所有公用方法都是靜態的。 因此協調流程不需指派執行個體給變數，類別也不需要序列化。  
  
 **SsoConfigHelper**物件會使用相同的機制來擷取和重新整理組態值，如同服務導向解決方案。 並且也使用相同的鎖定模式。 如需有關這些機制的詳細資訊，請參閱[使用 SSO 有效率地在服務導向解決方案](../core/using-sso-efficiently-in-the-service-oriented-solution.md)及原始程式碼的**SsoConfigHelper**。  
  
 商務程序管理解決方案的單一登入快取服務導向解決方案中執行，例如實作**IPropertyBag**介面從**ipropertybag**命名空間來儲存值。 商務程序管理解決方案使用**HybridDictionary**物件而非**NameValueCollection**物件。  
  
 和服務導向解決方案不同的是，商務程序管理解決方案會公開具有對應至組態資料的屬性之物件。 如此，協調流程就不需處理訊息類型的差異。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md)