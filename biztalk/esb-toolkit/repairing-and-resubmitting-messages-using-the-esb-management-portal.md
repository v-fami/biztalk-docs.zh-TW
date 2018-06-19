---
title: 修復和重新提交訊息使用 ESB 管理入口網站 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43091cbd-77d1-4cbd-9190-2d423ce7d4df
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61602fb41a2c6754fe6d77d249e2ec8c2f40cd39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295254"
---
# <a name="repairing-and-resubmitting-messages-using-the-esb-management-portal"></a>修復和重新提交訊息使用 ESB 管理入口網站
在此使用情況下，預先設定傳送埠會使用 ESB 錯誤處理器傳送管線，接收協調流程或 Microsoft BizTalk 的失敗訊息路由機制所產生的錯誤訊息中的例外狀況處理常式所產生的 ESB 錯誤訊息伺服器。 ESB 錯誤處理器正規化，加速功能，並將其路由至 ESB 管理入口網站資料庫。 入口網站監視傳入的錯誤訊息的資料庫，並產生警示的通知訂閱的處理失敗的使用者。 使用者可以開啟入口網站錯誤檢視器中的錯誤訊息、 編輯訊息內容，並再重新送出訊息以進行處理，如圖 1 所示。  
  
 ![修復訊息](../esb-toolkit/media/ch3-repairingmessages.gif "Ch3 RepairingMessages")  
  
 **圖 1**  
  
 **修復和重新提交訊息使用 ESB 管理入口網站**  
  
 ESB 管理入口網站中包含的範例，具有[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。 它提供完整的圖形化環境編輯和重新提交訊息。它也支援警示、 通知和訊息重新提交稽核。  
  
 如需詳細資訊，請參閱[使用例外狀況和錯誤訊息](../esb-toolkit/working-with-exceptions-and-fault-messages.md)。