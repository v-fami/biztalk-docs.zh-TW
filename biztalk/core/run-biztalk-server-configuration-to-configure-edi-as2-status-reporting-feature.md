---
title: 若要啟用狀態報告，請執行&#39;BizTalk Server 組態&#39;並設定 EDI-AS2 狀態報告功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf125919-80ab-4cb8-b1f5-0f2616cc6f5c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89d7fcf5e473485d0b61edcd6d5f287198021d3f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992711"
---
# <a name="to-enable-status-reporting-run-39biztalk-server-configuration39-and-configure-edi-as2-status-reporting-feature"></a>若要啟用狀態報告，請執行&#39;BizTalk Server 組態&#39;並設定 EDI-AS2 狀態報告功能
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------|
|  產品名稱   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| 產品版本 |                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                           |
|    事件識別碼     |                                                       -                                                        |
|  事件來源   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI             |
|    元件    |                                                   將 EDI 引擎                                                   |
|  符號名稱  |                                                       0                                                        |
|  訊息文字   | 若要啟用狀態報告，請執行 [BizTalk Server 組態] 並設定 EDI/AS2 狀態報告功能。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，EDI/AS2 狀態報告並未運作，因為尚未設定。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
1.  執行 BizTalk Server 組態精靈。 按一下 [BizTalk EDI/AS2 Runtime] 節點中，並檢查 「 啟用 BizTalk EDI/AS2 執行階段狀態報告為此 BizTalk 群組 」 屬性。 若要設定 EDI/AS2 狀態報告，您必須設定 BAM。  
  
2.  在 BizTalk Server 管理主控台中，啟用 EDI 狀態報告的合作對象，按一下 [啟動 EDI 報告] 屬性中的 [EDI 屬性] 對話方塊中的 [一般] 頁面。 啟用 AS2 狀態報告的合作對象，按一下 [啟動 AS2 報告] 屬性中的 [AS2 屬性] 對話方塊中的 [一般] 頁面。 您必須在啟用 EDI 或 AS2 狀態報告之後，重新啟動 BizTalk 服務。