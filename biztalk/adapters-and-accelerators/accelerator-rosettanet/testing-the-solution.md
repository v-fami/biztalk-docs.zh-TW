---
title: 測試解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing solutions
- private process tutorial, testing solutions
ms.assetid: 90faf959-bac6-4695-8cb7-ecabe52baf1a
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7af2cab529344f499ff006a6cd99401ae63c4668
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005535"
---
# <a name="testing-the-solution"></a>測試方案
在本節中，您將測試完整的解決方案。 您將使用在 Fabrikam 解決方案中建立的 LOBWebApplication 工具，提交 3A2 PIP 要求至 Contoso LOB 應用程式。 然後您建立的 Contoso 私用協調流程提交 Contoso 3A2 價格與可用性要求至 ERP 系統，以便讓 BizTalk Server 使用 SQL 配接器。 接收到來自 ERP 系統的回應時，協調流程便會呼叫商務規則引擎，以強制套用您所建立的緊急需求商務原則。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 Fabrikam 範例建立價格與可用性要求](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-price-and-availability-request-with-the-fabrikam-sample.md)