---
title: "測試解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing solutions
- private process tutorial, testing solutions
ms.assetid: 90faf959-bac6-4695-8cb7-ecabe52baf1a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4692035aed17f8432eb2bb515fa75df61be8047f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="testing-the-solution"></a>測試方案
在本節中，您將測試完整的解決方案。 您將使用在 Fabrikam 解決方案中建立的 LOBWebApplication 工具，提交 3A2 PIP 要求至 Contoso LOB 應用程式。 然後，您所建立的 Contoso 私用協調流程會使用 [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] SQL 配接器，將 Contoso 的 3A2 價格與可用性要求提交至 ERP 系統。 接收到來自 ERP 系統的回應時，協調流程便會呼叫商務規則引擎，以強制套用您所建立的緊急需求商務原則。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 Fabrikam 範例建立價格與可用性要求](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-price-and-availability-request-with-the-fabrikam-sample.md)