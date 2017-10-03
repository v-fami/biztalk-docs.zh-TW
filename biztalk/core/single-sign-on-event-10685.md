---
title: "單一登入： 事件 10685 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 810b37b5-51c4-4201-8d88-0bf7d9e16dae
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47844a979e93789f4baa94fbcbd58fd23762db84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10685"></a>單一登入： 事件 10685
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10685|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_REPLAY_CANNOT_OPEN|  
|訊息文字|無法開啟重新執行或進度 file.%r<br /><br /> 檔案名稱: %1 %r<br /><br /> 錯誤碼： %2|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示 SSO 已重新建立連絡人與 SSO 資料庫，但無法開啟重新執行檔案或進度檔案。 如果 SSO 無法開啟重新執行檔案，它將繼續進行下一個重新執行檔案。  
  
 在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示幅度透過 SSO 時能夠讀取與 SSO 資料庫重新執行檔案中案例的連絡人是遺失一次透過播放背面的重新執行檔的部分方法。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告事件，執行下列作業：  
  
-   您應該檢查相關聯的事件，以判斷為什麼 SSO 無法連絡 SSO 資料庫的系統和應用程式事件記錄檔。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [如何設定密碼同步化](../core/how-to-configure-password-synchronization.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)