---
title: Ops 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, Ops adapters
- Ops adapters, about Ops adapters
- Ops adapters
- process management solution tutorial, Ops adapters
- process management solution tutorial, errors
ms.assetid: 7f747a5f-14af-4e4c-bc29-f083f8f00bd0
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67463adf4e1e960ab6608e67595a679804aa223e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279374"
---
# <a name="the-ops-adapter"></a>Ops 配接器
解決方案的設計是儘可能將有問題的訊息和錯誤傳送到決策作業系統，以決定要修正錯誤或終止訂單。 結合新錯誤報告功能的 Ops 配接器可處理許多這類情況。  
  
 解決方案可在設定為使用新錯誤報告功能的連接埠上使用配接器。 當它收到錯誤時，配接器會呼叫兩個方法：**初始化**和**Execute**，在指定的組件中的類別。 在解決方案中，這些方法會將錯誤傳送到正確的作業群組。  
  
 解決方案包括一個範例處理常式，但您可以輕鬆的撰寫自己的處理常式，並使用其他解決方案中的配接器。 如需新的錯誤報告功能的一般資訊，請參閱[使用失敗訊息路由](../core/using-failed-message-routing.md)。  
  
> [!NOTE]
>  Ops 配接器是使用「配接器架構」建置。 建置配接器架構的相關資訊，請參閱[開發自訂配接器](../core/developing-custom-adapters.md)。  
  
 本節描述配接器的運作方式和設定方式，同時提供有關錯誤處理常式組件的詳細資訊。 此節以非常有用的實作詳細資料做為結束，協助使用者修改配接器或在其他應用程式中使用配接器。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 Ops 配接器](../core/using-the-ops-adapter.md)  
  
-   [範例作業錯誤處理常式](../core/the-sample-operations-error-handler.md)  
  
-   [Ops 配接器實作詳細資料](../core/ops-adapter-implementation-details.md)