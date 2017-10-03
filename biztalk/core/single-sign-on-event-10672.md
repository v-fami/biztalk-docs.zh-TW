---
title: "單一登入： 事件 10672 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2422c7d-51bc-4f12-8830-193d71d2bce9
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03eb6a72be53f928c8c173ac84556f709df0723c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10672"></a>單一登入： 事件 10672
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10672|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_WARN_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED|  
|訊息文字|Windows 密碼變更可能已造成一個以上的帳戶的變更上相同的外部 system.%r<br /><br /> 這不讓因為這個外部系統的配接器已設定為允許對應 conflicts.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> Windows 帳戶: %3 %r<br /><br /> 外部帳戶 1: %4 %r<br /><br /> 外部帳戶 2: %5|  
  
## <a name="explanation"></a>說明  
 這個警告事件表示，Windows 密碼變更可能已造成一個以上的帳戶的變更相同外部系統上。 因為配接器組態不會讓它無法的這項變更。  
  
## <a name="user-action"></a>使用者動作  
  
-   使用 SSO 管理工具來設定**允許對應衝突**密碼同步配接器的屬性。  
  
## <a name="more-info"></a>其他資訊
  
-   **密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [密碼同步處理](../core/password-synchronization2.md)