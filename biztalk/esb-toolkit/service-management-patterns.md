---
title: 服務管理模式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fea915c-0074-472e-909b-fbbd88d7359c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a48639fb2a540b5b2597b34ad95ee390b4382c34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294622"
---
# <a name="service-management-patterns"></a>服務管理模式
## <a name="repair-and-resubmit"></a>修復後再重新提交  
 修復和重新提交的模式會定義服務無法處理訊息並需要依正常程序外部化失敗訊息的表單中其狀態、 啟用訊息內容，才能用於修復並再將其重新提交至服務方案若要繼續處理訊息。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含的機制哪些 Microsoft biztalk 傳訊與協調流程的例外狀況可以是正規化，而且公開額外的動作。 設計 ESB 解決方案時，務必將如何處理例外狀況的帳戶。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含示範可以如何檢視及管理例外狀況的範例 ESB 管理入口網站應用程式。 如需修復和重新提交 ESB 管理入口網站範例應用程式中的例外狀況的詳細資訊，請參閱[修復和重新提交訊息](../esb-toolkit/repairing-and-resubmitting-messages.md)。