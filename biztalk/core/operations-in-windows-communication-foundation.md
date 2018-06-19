---
title: Windows Communication Foundation 中的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1728d2f-ac74-446e-a36f-4b645a6e042a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c6b5344b8fb2c5a5ba7a68b112adb50133198c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263766"
---
# <a name="operations-in-windows-communication-foundation"></a>Windows Communication Foundation 內的作業
本章節包含 BAM WCF 攔截器所支援的自訂作業。  
  
 請注意，如果作業名稱項目含有 Action 屬性：  
  
1.  針對用戶端和伺服器，作業名稱是以名稱屬性識別，  
  
2.  針對回覆路徑 (回呼回覆)、用戶端回覆和服務回覆而言，作業名稱是以名稱屬性辨識。  
  
> [!NOTE]
>  回覆訊息會擁有一個節點，其名稱是在名稱屬性所指定之名稱附加 "Result" 字樣。 您必須確保 XPaths 反應此命名慣例。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [AutoGenerateCorrelationToken](../core/autogeneratecorrelationtoken.md)  
  
-   [GetContextProperty](../core/getcontextproperty1.md)  
  
-   [GetEndpointName](../core/getendpointname.md)  
  
-   [使用 GetOperationName](../core/getoperationname.md)  
  
-   [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md)  
  
-   [XPath](../core/xpath.md)