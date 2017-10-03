---
title: "單一登入： 事件 10697 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4263ecbd-939e-4374-b0b6-aada3b2af900
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5c2c130a3e3473933939d896ab9c4714865bf62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10697"></a>單一登入： 事件 10697
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10697|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_PROGRESS_FILE_MISMATCH|  
|訊息文字|進度 file.%r 中偵測到損毀<br /><br /> 重新執行檔案: %1 %r<br /><br /> 其他資料： %2|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示 SSO 已重新建立與 SSO 資料庫，請連絡，但是無法使用對應的重新執行檔案，因為不相符開啟進度檔案。 如果 SSO 無法開啟進行檔案，就會開始在第一次重新執行檔的開頭記錄。  
  
 在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   檢查關聯事件的系統和應用程式事件記錄檔。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [如何設定密碼同步化](../core/how-to-configure-password-synchronization.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)