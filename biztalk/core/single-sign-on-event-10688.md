---
title: 單一登入： 事件 10688 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63fe4ac5-dc1d-4d5a-8ce3-40ed4556afcf
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96e93263c8be58fd7fd2cecb40d3daee16baae09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271214"
---
# <a name="single-sign-on-event-10688"></a>單一登入： 事件 10688
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10688|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_REPLAY_FILE_UNEXPECTED_DATA|  
|訊息文字|在重新執行檔案中偵測到損毀。%r<br /><br /> 重新執行檔案： %1|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示 SSO 已重新建立連絡人與 SSO 資料庫中，但無法讀取的重新執行檔案，因為已損毀。 如果 SSO 無法開啟重新執行檔案，它將繼續進行下一個重新執行檔案 （如果有的話）。  
  
 在 ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。 進行檔案表示幅度透過 SSO 無法讀取與 SSO 資料庫重新執行檔案中案例的連絡人一次會遺失。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   檢查關聯事件的系統和應用程式事件記錄檔。  
  
-   刪除重新執行檔案。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [如何設定密碼同步化](../core/how-to-configure-password-synchronization.md)  
  
-   [密碼同步處理](../core/password-synchronization2.md)