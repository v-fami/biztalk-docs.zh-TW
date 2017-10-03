---
title: "使用 ESB 例外狀況管理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de6ce411-2d34-4fd8-9644-6fbc9cec266d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fec20c447b184c2fdadf87f62f37f576f5100d08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-esb-exception-management"></a>使用 ESB 例外管理
範圍的內容，並在數個不同的處理階段，在 ESB 期間可能會發生錯誤和例外狀況。 本節提供處理例外狀況的相關資訊，並說明您如何發行透過 ESB 管理入口網站的詳細資料。  
  
## <a name="overview"></a>概觀  
 有許多方式來處理例外狀況[!INCLUDE[prague](../includes/prague-md.md)]解決方案，包括使用架構，例如企業程式庫。 不過，在 ESB 與 BizTalk Server 開發時，您以訊息為基礎的環境中運作。 BizTalk 解決方案中的所有項目是訊息導向和 BizTalk 開發人員認為訊息導向的方式。 因此，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]實作例外狀況處理的訊息導向方法。  
  
 ESB 例外狀況管理 Framework 會遵循設計模式，提供有彈性的方法例外狀況監視，可讓來自方案之外的錯誤回應，可能是在業務單位層級。  
  
 下列主題將討論 ESB 例外狀況管理架構，在更多詳細資料：  
  
-   [在 ESB 例外狀況管理架構的設計](../esb-toolkit/design-of-the-esb-exception-management-framework.md)  
  
-   [例外狀況管理 Framework 的元件](../esb-toolkit/the-components-of-the-exception-management-framework.md)  
  
-   [使用例外狀況管理架構](../esb-toolkit/using-the-exception-management-framework.md)  
  
-   [建立自訂例外狀況處理常式](../esb-toolkit/creating-custom-exception-handlers.md)