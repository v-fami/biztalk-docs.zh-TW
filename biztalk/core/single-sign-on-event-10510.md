---
title: "單一登入： 事件 10510 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4553ad4c-9553-4b8b-b3a3-72aed2a61202
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 053f75541597e3b2e721c53714aaaf8517c3c49f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10510"></a>單一登入： 事件 10510
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10510|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_INFO_DLL_LOAD_FAILED|  
|訊息文字|無法載入 %1。 請檢查此檔案可用。|  
  
## <a name="explanation"></a>說明  
 這個資訊事件表示 SSO 服務已無法載入的 DLL。  
  
## <a name="user-action"></a>使用者動作  
 若要解決此事件，執行下列一或多個項目：  
  
-   請確認 DLL 位於 SSO 安裝目錄中，通常是 C:\Program Files\Common Files\Enterprise Single Sign-on。 您的 SSO 安裝目錄可能會不同。  
  
-   如果單一 DLL 遺失或損毀，嘗試取代它，然後重新啟動服務。  
  
 如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)