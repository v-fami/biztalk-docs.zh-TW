---
title: ESB 發送器元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85655b5f-4717-42d1-b005-0a5592d5653b
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16281ff49da6470212e9e8396a051270adf1eef7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982127"
---
# <a name="the-esb-dispatcher-component"></a>ESB 發送器元件
以傳訊為基礎的路線服務的 ESB 發送器元件內執行。 發送器元件可以也會動態地設定為輸出訊息的端點位置屬性，並動態地轉換訊息。  
  
## <a name="component-properties"></a>元件屬性  
 發送器元件有六個屬性：  
  
- **RoutingServiceName**。 此屬性會指定以傳訊為基礎的路由服務的已註冊的名稱。 預設值是**Microsoft.Practices.ESB.Services.Routing**。  
  
- **TransformServiceName**。 此屬性會指定訊息為基礎的轉換服務登錄的名稱。 預設值是**Microsoft.Practices.ESB.Services.Transform**。  
  
- **驗證**。 此屬性會指定訊息是否需要驗證。  
  
- **啟用**。 這個屬性會啟用或停用元件。  
  
- **端點**。 這個屬性是解析程式的連接字串，以註冊使用 BizTalk ESB 工具組的格式。  
  
- **將名稱對應**。 這個屬性是對應的完整的名稱或連接字串格式向[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:  
  
  -   對應名稱的範例如下：  
  
      ```  
      GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN, GlobalBank.ESB.DynamicResolution.Transforms, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c2c8b2b87f54180a  
      ```