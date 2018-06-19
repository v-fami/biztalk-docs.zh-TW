---
title: BizTalk adapter for Siebel eBusiness 應用程式的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- overview, adapter
- adapter, overview of
- adapter, overview
ms.assetid: 41ab7d42-7096-45ef-9763-a5ccf88eb652
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efcc3a90f7025a5f396cd778676f5f3152bc7657
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222038"
---
# <a name="overview-of-biztalk-adapter-for-siebel-ebusiness-applications"></a>BizTalk Adapter for Siebel eBusiness 應用程式中的概觀
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開為 WCF 服務的 Siebel 系統。 配接器用戶端可以交換 SOAP 訊息的配接器，以執行 Siebel 系統上的作業。 配接器會取用 WCF 訊息，並使適當地呼叫 Siebel 系統執行的作業。 配接器傳回來自 Siebel 系統的回應傳回給用戶端的 SOAP 訊息格式。  
  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]介面描述中繼資料的 Siebel 成品 （商業元件、 商務服務） 結構的 SOAP 訊息的 WSDL 格式。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]讓配接器用戶端擷取作業的中繼資料，並產生可使用的程式設計成品程式設計方案中。  
  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]使用 Siebel COM 資料控制項存取 Siebel 系統。 Siebel COM 資料控制項來自配套 Siebel Web 用戶端。 因此，確定您已安裝在同一部電腦上的 Siebel Web 用戶端[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 您可以使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Siebel 系統通訊，以下列方式：  
  
-   開發 BizTalk 應用程式。 請參閱[開發 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)。
  
-   使用 WCF 服務模型。 請參閱[開發 Siebel 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)。  
  
-   使用 WCF 通道模型。 請參閱開發的 Oracle 資料庫應用程式使用 WCF 通道模型[輸入連結描述](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [配接器如何連接至 Siebel 系統？](https://msdn.microsoft.com/library/cc185212(v=bts.10).aspx)  
  
-   [配接器介面 Siebel 中繼資料的運作方式](https://msdn.microsoft.com/library/cc185267(v=bts.10).aspx)  
  
-   [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)  
  
-   [配接器所支援的其他功能](https://msdn.microsoft.com/library/cc185252(v=bts.10).aspx) 
  
## <a name="see-also"></a>另請參閱  
 [瞭解 BizTalk Adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)