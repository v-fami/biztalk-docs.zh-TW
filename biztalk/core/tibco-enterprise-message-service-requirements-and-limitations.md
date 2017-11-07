---
title: "TIBCO Enterprise Message Service 的需求和限制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e4c022c-e6a8-4ac5-b998-b0465002a31e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcd386245ba06c2e3b5a5b92df7b7a7f01a1a749
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="tibco-enterprise-message-service-requirements-and-limitations"></a>TIBCO Enterprise Message Service 的需求和限制

## <a name="system-requirements"></a>系統需求  
隨附 TIBCO Enterprise Message Service 包含用戶端 SDK （使用 TIBCO EMS C# API）。 BizTalk Adapter for TIBCO EMS 會使用此 API 來與 TIBCO EMS 進行通訊。  
  
## <a name="add-the-api-to-the-gac"></a>將 API 加入 GAC  
 BizTalk Adapter for TIBCO EMS 需要 TIBCO EMS C# API，TIBCO。EMS.dll，要加入至全域組件快取 (GAC)。 配接器會觸發例外狀況，並記錄適當的訊息，如果未安裝這個組件。  
  
1.  複製至 TIBCO EMS C #API 您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。  
  
2.  將目錄變更為 C# API 檔案，TIBCO 的位置。EMS。DLL。  
  
     在預設安裝中，這個 dll 的路徑會是 c:\tibco\ems\clients\cs\TIBCO。EMS。DLL。  
  
3.  在命令提示字元中，輸入：  
  
     `C:\bin> gacutil /i TIBCO.EMS.dll`  
  
     TIBCO。EMS.dll 現在會顯示 GAC。  
  
     若要檢視 GAC 清單中，控制台] 中，開啟**系統管理工具**，開啟**Microsoft.NET Framework X.XConfiguration**，然後按一下 [**組件快取**。  
  
## <a name="limitations"></a>限制  
 BizTalk Adapter for TIBCO Enterprise Message Service 會使用 TIBCO。EMS.dll 與 TIBCO Enterprise Message Service 進行通訊。 當您使用 TIBCO EMS C# API 時，您應該考慮下列限制：  
  
-   訊息壓縮功能，可讓 TIBCO EMS 用戶端是以壓縮格式的訊息傳送給 EMS，都無法使用 C# API。  
  
-   找不到適用於 C# API 的配接器和伺服器之間的訊息加密。 C# API 不允許使用 OpenSSL 程式庫的 SSL 加密。  
  
-   C# API 不支援適用於 EMS 的系統管理 API。  
  
-   無法傳送或接收使用 BizTalk TIBCO EMS 配接器的訊息大於 50 MB 的大小。 超過此大小，在環境發生 System.OutOfMemoryException 例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [規劃和架構](../core/planning-and-architecture16.md)