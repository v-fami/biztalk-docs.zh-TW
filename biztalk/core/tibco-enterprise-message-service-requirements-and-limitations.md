---
title: TIBCO Enterprise Message Service 需求和限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4c022c-e6a8-4ac5-b998-b0465002a31e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 453edabdadbd50b320a0bc078a638991ab7a3a5c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995983"
---
# <a name="tibco-enterprise-message-service-requirements-and-limitations"></a>TIBCO Enterprise Message Service 的需求和限制

## <a name="system-requirements"></a>系統需求  
隨附 TIBCO Enterprise Message Service 包含的用戶端 SDK （使用 TIBCO EMS C# API）。 BizTalk Adapter for TIBCO EMS 會使用此 API 來與 TIBCO EMS 進行通訊。  
  
## <a name="add-the-api-to-the-gac"></a>將 API 加入 GAC  
 BizTalk Adapter for TIBCO EMS 需要 TIBCO EMS C# API，TIBCO。EMS.dll，可以加入至全域組件快取 (GAC)。 配接器會觸發例外狀況，並記錄適當的訊息，如果未安裝此組件。  
  
1. 複製至 TIBCO EMS C #API 您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。  
  
2. 將目錄變更至 TIBCO 的 C# API 檔案的位置。EMS。DLL。  
  
    在預設安裝中，此 DLL 的路徑會是 c:\tibco\ems\clients\cs\TIBCO。EMS。DLL。  
  
3. 在命令提示字元中，輸入：  
  
    `C:\bin> gacutil /i TIBCO.EMS.dll`  
  
    TIBCO。EMS.dll 現在會顯示 GAC。  
  
    若要檢視 GAC 清單中，在控制台中，開啟**系統管理工具**，開啟**Microsoft.NET Framework X.XConfiguration**，然後按一下**組件快取**。  
  
## <a name="limitations"></a>限制  
 BizTalk Adapter for TIBCO Enterprise Message Service 會使用 TIBCO。EMS.dll 與 TIBCO Enterprise Message Service 進行通訊。 當您使用 TIBCO EMS C# API 時，您應該考慮下列限制：  
  
-   訊息壓縮功能，可讓 TIBCO EMS 用戶端，以壓縮格式的訊息傳送給 EMS，不適用於 C# API。  
  
-   配接器和伺服器之間的訊息加密不提供使用 C# API。 C# API 不允許進行 SSL 加密，使用 OpenSSL 程式庫。  
  
-   C# API 不支援適用於 EMS 的系統管理 API。  
  
-   無法傳送訊息大於 50 MB 的大小，或使用 BizTalk TIBCO EMS 配接器接收。 超過此大小，環境會體驗 System.OutOfMemoryException 例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [規劃和架構](../core/planning-and-architecture16.md)