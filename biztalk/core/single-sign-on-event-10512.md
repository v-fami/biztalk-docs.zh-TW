---
title: "單一登入： 事件 10512 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4edf0512-112d-40b8-9e29-7dd67f999b6d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a586af2b280e9d968b87a7cb3e7680a17457ca0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10512"></a>單一登入： 事件 10512
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10512|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_ERROR_LOADLIBRARY|  
|訊息文字|無法載入 %1%r<br /><br /> 錯誤碼: %2。|  
  
## <a name="explanation"></a>說明  
 這個錯誤事件表示指定的動態連結程式庫 (DLL) 無法載入至 SSO 伺服器處理程序。 如果 DLL 遺失在 SSO 安裝目錄中，通常是 C:\Program Files\Common Files\Enterprise Single Sign-on，它可能未正確地完成安裝程式，或安裝後已刪除的 DLL 完成。 如果 DLL 存在，則解析 DLL 正確路徑的 SSO 服務可能有問題。 此外，DLL 本身可能已損毀。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列一個或多個動作：  
  
-   如果懷疑有更多設定失敗，可能需要解除安裝然後重新安裝產品。  
  
-   如果單一 DLL 遺失或損毀，嘗試取代它，然後重新啟動服務。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)