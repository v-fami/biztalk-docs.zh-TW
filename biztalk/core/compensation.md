---
title: 補償 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- compensations, errors
- compensations
- errors, compensations
- compensations, about compensations
- compensations, atomic transactions
- atomic transactions, compensations
- transactions, compensations
ms.assetid: 0a80dd16-fd35-4f45-95b7-52bb9df80cbb
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c572638ea6212c3fb79e6b239aa8ffbe713c3c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231598"
---
# <a name="compensation"></a>補償
如果發生錯誤，而您必須復原或回復已成功認可之交易的結果，則可以將補償程式碼加入協調流程中，以達到此目的。  
  
 您可以在交易順利完成其動作後叫用補償。 此時，協調流程的狀態是已知的，補償中的程式碼能夠取得狀態資訊；這表示您可以撰寫程式碼，在交易認可時，根據協調流程的狀態執行適當的動作。  
  
 在不可部分完成的交易上也可以提供補償， 但只有在不可部分完成的交易認可之後，才能呼叫這些補償。 您需要撰寫程式碼，在補償中復原或回復正常執行的路徑。  
  
 補償區塊相當有彈性，可以容納任何其他圖形，甚至包括另一個交易範圍。  
  
> [!NOTE]
>  您只能在指定範圍中進行補償一次。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何設定補償圖形](../core/how-to-configure-the-compensate-shape.md)  
  
-   [如何新增自訂補償至協調流程](../core/how-to-add-custom-compensation-to-an-orchestration.md)  
  
-   [如何新增補償區塊](../core/how-to-add-a-compensation-block.md)