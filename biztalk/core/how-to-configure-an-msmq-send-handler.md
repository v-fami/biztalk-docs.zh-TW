---
title: 如何設定 MSMQ 傳送處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, send handlers
- configuring [MSMQ adapters], send handlers
- send handlers, MSMQ adapters
ms.assetid: 21917596-f27a-473b-859e-186ab5f4cd94
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: feacaec9d2794cf8806fa5156fe64b7290699faa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248262"
---
# <a name="how-to-configure-an-msmq-send-handler"></a>如何設定 MSMQ 傳送處理常式
您可以使用下列程序來變更 MSMQ 傳送處理常式的全域變數。  
  
> [!NOTE]
>  每個主控件只可和一個傳送處理常式建立關聯。  
  
### <a name="to-change-global-variables-for-an-msmq-send-handler-by-using-the-biztalk-server-administration-console"></a>使用 [BizTalk Server 管理] 主控台變更 MSMQ 傳送處理常式的全域變數  
  
1.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **配接器**。  
  
2.  在展開的配接器清單中，按一下  **MSMQ**，在右窗格，以滑鼠右鍵按一下您想要設定的傳送處理常式，然後按一下**屬性**。  
  
3.  在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取主控件與傳送處理常式將會產生關聯，然後按一下**屬性**。  
  
4.  在**MSMQ 傳輸屬性**對話方塊方塊中，輸入一個值**批次大小**。  
  
     MSMQ 傳送處理常式會將訊息傳送至使用指定的目的地佇列**批次大小**參數。 預設值**批次大小**值為 5。  
  
5.  按一下**確定**按一下**確定** 以關閉 **配接器處理常式屬性** 對話方塊。