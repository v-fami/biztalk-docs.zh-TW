---
title: 如何擲回錯誤例外狀況，從協調流程發佈為 WCF 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors, WCF services
- WCF services, orchestrations
- WCF services, errors
- orchestrations, WCF services
ms.assetid: 89f57841-d40e-4a5a-90a8-5556a2766c03
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bf64501f619e74991fafa59b2ab1c2a3e62cbca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255734"
---
# <a name="how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services"></a>如何從發佈為 WCF 服務的協調流程擲回錯誤例外狀況
可以從協調流程傳送兩種類型的 SOAP 錯誤： 輸入，而且不具類型的 SOAP 錯誤。 具類型的 SOAP 錯誤是其中作業具有**System.ServiceModel.FaultContractAttribute**指定自訂 SOAP 錯誤類型。 不具類型的 SOAP 錯誤則是作業合約中未指定的錯誤。  
  
 WCF 配接器不支援處理發佈為 WCF 服務之協調流程的具類型錯誤合約例外狀況。 不過，協調流程或管線永遠都可以傳回不具類型的 SOAP 錯誤。 若要傳回不具類型的 SOAP 錯誤，您必須設定**System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults**接收位置，或在組態檔中，以允許 WCF 用戶端取得資訊有關內部服務作業例外狀況。  
  
 下列程式碼示範如何在組態檔中設定屬性：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <serviceBehaviors>  
                <behavior name="ServiceBehaviorConfiguration">  
                    <serviceDebug includeExceptionDetailInFaults="true" />  
                </behavior>  
            </serviceBehaviors>  
        </behaviors>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何處理協調流程中的具型別的的錯誤合約](../core/how-to-handle-typed-fault-contracts-in-orchestrations.md)