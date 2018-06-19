---
title: 單一登入： 事件 10706 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d73db77e-5bb6-431c-a8ca-5682d7ab3d6a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5703c81d87376349561f644da558b8594cd51b79
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22271558"
---
# <a name="single-sign-on-event-10706"></a>單一登入： 事件 10706
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|제품 이름|Enterprise Single Sign-On|  
|제품 버전|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10706|  
|事件來源|ENTSSO|  
|구성 요소|해당 없음|  
|符號名稱|SSO_WARN_PS_NO_GLOBAL_SYNC|  
|訊息文字|群組配接器需要全域旗標所允許的密碼同步處理。 檢查全域旗標。%r<br /><br /> 介面卡: %1|  
  
## <a name="explanation"></a>說明  
 此警告事件表示外部密碼同步配接器已要求密碼同步，且兩者全域旗標設定。 有兩個旗標，一個允許傳送到外部系統的密碼︰ SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL，另一個可接收外部系統 SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB 的密碼。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列作業︰  
  
-   使用 SSO 管理 MMC 嵌入式管理單元、 (系統 & #124;屬性與 #124。選項） 或命令列工具  `ssomanage –enable winsync/extsync` 啟用全域旗標。  
  
## <a name="more-info"></a>其他資訊
  
-   **企業單一登入旗標** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [如何管理密碼同步處理](../core/how-to-administer-password-synchronization.md)