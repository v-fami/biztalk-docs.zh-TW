---
title: "單一登入： 事件 10706 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d73db77e-5bb6-431c-a8ca-5682d7ab3d6a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5703c81d87376349561f644da558b8594cd51b79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10706"></a>單一登入： 事件 10706
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10706|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_PS_NO_GLOBAL_SYNC|  
|訊息文字|群組配接器需要全域旗標允許密碼同步處理。 檢查全域旗標。%r<br /><br /> 配接器： %1|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示外部密碼同步配接器已要求密碼同步，而且兩者皆非全域的旗標的設定。 有兩個旗標，可讓傳送密碼至外部系統的其中一個： SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL，另一個，可讓接收的外部系統 SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB 的密碼。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，執行下列作業：  
  
-   使用 SSO 管理 MMC 嵌入式管理單元、 (系統 &#124;屬性 &#124;選項） 或命令列工具`ssomanage –enable winsync/extsync`啟用全域旗標。  
  
## <a name="more-info"></a>其他資訊
  
-   **企業單一登入旗標**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)