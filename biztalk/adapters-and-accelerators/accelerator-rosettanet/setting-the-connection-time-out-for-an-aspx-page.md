---
title: "設定 ASPX 頁面的連線逾時 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASPX pages, connection time-out
- connections, time-out
ms.assetid: 61d9c996-caf4-48bd-bda7-52f2797a941b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83e083b9f2f0262095e58b4ed9842627888773dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-connection-time-out-for-an-aspx-page"></a>設定 ASPX 頁面的連線逾時
當您使用 ASPX 頁面來處理同步訊息時，必須要增加 ASPX 頁面的連線逾時，如此它才有足夠時間等待預期的訊息。  
  
 增加 ASPX 頁面的連線逾時可能會發生非預期的結果。 首先，遭到拒絕服務攻擊的風險會增加，而且耗盡執行緒集區的威脅也會增加。 再來就是，如果這個 ASPX 頁面上有太多的同步連線，系統便會鎖死這些連線。 所以，當您必須要增加連線逾時的時候，請注意不要增加太多。  
  
 將連線逾時設定為 RosettaNet 組織允許的最小值。 如需 RosettaNet PIP 規格的「交易夥伴介面程序 (PIP)」中，有關時序參數的詳細資訊，請參閱表 4-3：訊息交換控制項。  
  
### <a name="to-set-the-connection-time-out-for-the-aspx-page"></a>設定 ASPX 頁面的連線逾時  
  
1.  按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.  
  
2.  在 [IIS 管理員] 中，展開本機電腦的節點，然後展開**網站**。  
  
3.  以滑鼠右鍵按一下 **[預設網站]**，然後按一下 **[屬性]**。  
  
4.  在 [預設的網站內容] 對話方塊上**網站**索引標籤的**連接逾時**方塊中輸入適當的值，然後再按一下**[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [程式設計指南](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)