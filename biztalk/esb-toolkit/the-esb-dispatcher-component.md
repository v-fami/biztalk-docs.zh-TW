---
title: "ESB 發送器元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85655b5f-4717-42d1-b005-0a5592d5653b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe377221034637eab23b70c50ccf48a8454a23bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-dispatcher-component"></a>ESB 發送器元件
傳訊架構路線服務會在 ESB 發送器元件內執行。 發送器元件可以也會動態地設定輸出訊息的端點位置屬性，並以動態方式將訊息轉換。  
  
## <a name="component-properties"></a>元件屬性  
 發送器元件有六個屬性：  
  
-   **RoutingServiceName**。 此屬性會指定以傳訊為基礎的路由服務為已註冊的名稱。 預設值是**Microsoft.Practices.ESB.Services.Routing**。  
  
-   **TransformServiceName**。 此屬性指定已註冊的服務的名稱以傳訊為基礎的轉換。 預設值是**Microsoft.Practices.ESB.Services.Transform**。  
  
-   **驗證**。 此屬性會指定是否需要驗證訊息。  
  
-   **啟用**。 這個屬性會啟用或停用元件。  
  
-   **端點**。 這個屬性是向 BizTalk ESB Toolkit 格式的解析程式連接字串。  
  
-   **對應名稱**。 這個屬性是完整限定的名稱的對應，或是連接字串格式向[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:  
  
    -   對應名稱的範例如下：  
  
        ```  
        GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN, GlobalBank.ESB.DynamicResolution.Transforms, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c2c8b2b87f54180a  
        ```