---
title: "如何設定 MSMQ 接收處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive handlers, MSMQ adapters
- configuring [MSMQ adapters], receive handlers
- MSMQ adapters, receive handlers
ms.assetid: d6d82098-3a73-44e2-80d5-143f77e919cc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f34e1b3f399c93bd92aa9c4e07f6e0082d25204
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-msmq-receive-handler"></a>如何設定 MSMQ 接收處理常式
使用下列程序，變更 MSMQ 接收處理常式關聯的主控件。  
  
> [!NOTE]
>  每個主控件只可和一個接收處理常式建立關聯。  
  
### <a name="to-change-the-host-with-which-the-msmq-receive-handler-is-associated"></a>變更 MSMQ 接收處理常式關聯的主控件  
  
1.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **配接器**。  
  
2.  在展開的配接器清單中，按一下  **MSMQ**，在右窗格，以滑鼠右鍵按一下您想要設定的接收處理常式，然後按一下**屬性**。  
  
3.  在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯的接收處理常式的主機。  
  
4.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [設定 MSMQ 配接器](../core/configuring-the-msmq-adapter.md)