---
title: 範例作業錯誤處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Ops adapters, error handler
- process management solution tutorial, Ops adapters
ms.assetid: e6c55f01-c004-4340-beaa-d77764ae34c1
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93536733c884b4d5db57ba18619ebabdead17561
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279622"
---
# <a name="the-sample-operations-error-handler"></a>範例作業錯誤處理常式
範例作業錯誤處理常式有三個主要組件： **OperationsClient**， **OperationsHandler**，和**OperationsServer**。  
  
 這個解決方案會設定配接器使用**OpsClient**物件存放至**OperationsClient**組件。 如您所預期， **OpsClient**物件會實作**IOpsAIC**介面。  
  
 **OpsClient**物件會使用**IOperationsSystem**介面呼叫**OpsHandler**物件透過[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]遠端功能。 **IOperationsSystem**介面顯示如下：  
  
```  
public interface IOperationsSystem  
{  
    void Initialize(string initData);  
    void Post(string originMachine, byte[] message);  
}  
  
```  
  
 **OperationsServer**，主控台應用程式會接聽要求**OpsHandler**物件，並做為伺服器[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]遠端功能。 呼叫**Execute**方法**OpsClient**物件接著會叫用**Post**方法**OpsHandler**物件。  
  
 **OpsHandler**方法的回應方式寫出其引數字串時，使用**追蹤**物件。 這會將錯誤公佈到主控台。 如需有關**追蹤**物件，請參閱中的 「 追蹤類別 」[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]類別庫。  
  
> [!NOTE]
>  這裡的模式是在相同**OrderHandler**所在介面會指定用戶端與遠端物件之間的方法呼叫。 不過，會產生額外一層之間的間接這裡**OpsClient**和**OpsHandler**。  
  
## <a name="see-also"></a>另請參閱  
 [Ops 配接器](../core/the-ops-adapter.md)