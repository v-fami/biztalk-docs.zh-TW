---
title: 若要啟用狀態報告，執行 &#39;BizTalk Server 組態 &#39;設定 EDI AS2 狀態報告功能和 |Microsoft 文件
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
ms.openlocfilehash: 334e77ed58d460aea3ca37f73c1165d62da0f10b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268910"
---
# <a name="to-enable-status-reporting-run-39biztalk-server-configuration39-and-configure-edi-as2-status-reporting-feature"></a>若要啟用狀態報告，執行 &#39;BizTalk Server 組態 &#39;設定 EDI AS2 狀態報告功能
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|0|  
|訊息文字|若要啟用狀態報告，請執行 BizTalk Server 組態 並設定 EDI/AS2 狀態報告功能。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，EDI/AS2 狀態報告並未運作，因為尚未設定。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
1.  執行 BizTalk Server 組態精靈。 按一下 [BizTalk EDI/AS2 Runtime] 節點，然後檢查 「 啟用 BizTalk EDI/AS2 Runtime 狀態報告的此 BizTalk 群組 」 屬性。 若要設定 EDI/AS2 狀態報告，您必須設定 BAM。  
  
2.  在 BizTalk Server 管理主控台中，啟用 EDI 狀態報告的合作對象，按一下 [啟動 EDI 報告] 屬性中的 [EDI 屬性] 對話方塊的 [一般] 頁面。 啟用 AS2 狀態報告的合作對象，按一下 [AS2 屬性] 對話方塊的 [一般] 頁面的 [啟動 AS2 報告] 屬性。 您必須在啟用 EDI 或 AS2 狀態報告之後，重新啟動 BizTalk 服務。