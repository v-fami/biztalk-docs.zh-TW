---
title: 低權限環境 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: abdc45d0-b63a-4b6c-80c4-1f8e87644cd9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d43f363bd96dd8e3109a8ce21b9565fb43e5f9bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298294"
---
# <a name="low-privilege-environments"></a>低權限環境
所包含的數個工作流程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件需要提高權限來執行特定動作。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件可讓您在低權限環境中執行基本監視功能。 有兩個系統管理角色： BizTalk Server 系統管理員和 BizTalk Server 操作員。 BizTalk Server 系統管理員是具有組態和追蹤資料存取權的高權限角色。 BizTalk Server 系統管理員可以執行所有的主要系統管理工作，這類登錄與啟動成品。 BizTalk Server 操作員則是低權限角色，僅具有用來監控和疑難排解動作的存取權。 如需詳細資訊，請參閱[最低安全性使用者權限](http://technet.microsoft.com/library/aa559845\(BTS.80\).aspx)。  
  
 使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件：  
  
-   BizTalk Server 操作員群組的成員可執行下列動作：  
  
    -   監控 BizTalk Server 的錯誤，暫停 messages\instances，檢視設定的查詢。  
  
    -   監控 BizTalk Server 安裝和成品。  
  
    -   檢視服務狀態及訊息流程。  
  
    -   啟動或停止應用程式和成品，例如協調流程、 傳送埠或傳送埠群組中已登錄狀態。  
  
    -   啟用或停用接收位置。 在下一個 60 秒 (預設值) 的快取重新整理間隔之前，變更不會生效。 快取重新整理間隔視在 BizTalk Server 群組層級設定。  
  
-   BizTalk Server 操作員群組的成員無法執行下列動作：  
  
    -   修改 BizTalk Server 的組態。  
  
    -   檢視分類為個人識別資訊 (PII) 的訊息內容屬性或訊息內文。  
  
    -   修改訊息路由過程，例如移除或新增新的訂閱到執行中的系統，包括將訊息發佈到 BizTalk Server 執行階段。  
  
> [!NOTE]  
>  若要執行所有管理組件，例如，重新啟動 BTSNTSvc.exe 服務所提供的監視工作，您必須是 BizTalk 伺服器上本機 Administrators 群組的成員。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [監視](../technical-guides/monitoring.md)  
  
-   [探索](../technical-guides/discoveries.md)