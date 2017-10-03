---
title: "單一登入： 事件 10671 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06c5564f-6412-4e83-9bec-03264e992ebe
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db44ecfd9980db445d3a611e4992f4b3961b3548
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10671"></a>單一登入： 事件 10671
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10671|  
|事件來源|ENTSSO|  
|元件|N\A|  
|符號名稱|SSO_INFO_EXTERNAL_MAPPING_CONFLICT_ALLOWED|  
|訊息文字|Windows 密碼變更會導致在相同的外部 system.%r 上的多個帳戶變更<br /><br /> 這被允許的因為這個外部系統的配接器已設定為允許對應 conflicts.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> Windows 帳戶: %3 %r<br /><br /> 外部帳戶 1: %4 %r<br /><br /> 外部帳戶 2: %5|  
  
## <a name="explanation"></a>說明  
 這個資訊事件表示 Windows 密碼變更將多個帳戶的變更會造成相同外部系統上。  
  
## <a name="user-action"></a>使用者動作  
  
-   使用者不必採取任何動作。  
  
## <a name="more-info"></a>其他資訊
  
-   **密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [密碼同步處理](../core/password-synchronization2.md)