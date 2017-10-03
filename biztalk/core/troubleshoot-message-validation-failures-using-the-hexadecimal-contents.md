---
title: "疑難排解訊息驗證失敗，藉由檢視十六進位內容的擱置訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cf14cd9-2d4b-43a3-9738-52bfd879e1e4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f7dc0f24a85f206831e3706bd03f2206aaa2c15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-message-validation-failures-by-viewing-the-hexadecimal-contents-of-suspended-messages"></a>透過檢視十六進位內容的擱置訊息，對訊息驗證失敗的疑難排解
如果因驗證失敗而擱置訊息，檢視十六進位表示的訊息部分，可能有助於判斷驗證失敗的原因。 本主題列出執行步驟來檢視十六進位表示的擱置訊息部分。  
  
## <a name="use-the-message-details-dialog-box-to-view-message-parts"></a>使用訊息詳細資料對話方塊以檢視訊息部分  
 請依照下列步驟檢視十六進位表示的訊息部分：  
  
1.  使用**查詢**在 BizTalk 管理主控台，來傳回含有一或多個擱置訊息的結果集的索引標籤。 請參閱[如何搜尋訊息](../core/how-to-search-for-messages.md)如需詳細資訊。  
  
2.  按兩下您想要調查並顯示擱置的訊息**訊息詳細資料**訊息對話方塊。  
  
3.  按一下左窗格中的訊息部分**訊息詳細資料**對話方塊來顯示訊息部分。  
  
    > [!NOTE]
    >  訊息可能有 0 個、1 個或多個訊息部分， 但是最常有一個稱為「內文」的訊息部分。  
  
4.  按一下**二進位** 索引標籤的右側窗格中**訊息詳細資料**對話方塊來顯示訊息部分的十六進位表示法。  
  
5.  檢查十六進位表示的訊息部分字元是否有下列項目：  
  
    -   遺漏或無效的位元組順序標記。 如需有關位元組順序標記，請參閱[http://go.microsoft.com/fwlink/?LinkId=196380](http://go.microsoft.com/fwlink/?LinkId=196380)。  
  
    -   Unix 和 Windows 在編碼分行符號方面的差異。 Unix 使用十六進位換行字元 (0A) 表示分行符號，而 Windows 則同時使用十六進位歸位字元 (0D) 和換行字元 (0A) 表示分行符號。  
  
    -   訊息部分中的無效控制字元。 未出現在純文字中的控制字元可能會顯示在二進位檢視中。  
  
    -   訊息部分中間的無效 nul 字元可能會使訊息部分遭截斷。 nul 字元是以十六進位 (00) 表示。  
  
    -   位置一般檔案中的無效字元位移。 顯示十六進位表示的訊息部分，可檢視位置一般檔案中的資料位移。  
  
## <a name="see-also"></a>另請參閱  
 [調查協調流程、 連接埠和訊息失敗](../core/investigating-orchestration-port-and-message-failures.md)