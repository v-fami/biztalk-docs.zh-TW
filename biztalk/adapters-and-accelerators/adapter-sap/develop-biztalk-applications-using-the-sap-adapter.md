---
title: 開發 BizTalk 應用程式使用 SAP 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk applications, developing
- developing, BizTalk applications
ms.assetid: 4aa10897-a08e-4fc3-9c1f-40485d204273
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75e70a52f12227b1bde3a43f9330c6fe373ac5a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216638"
---
# <a name="develop-biztalk-applications-using-the-sap-adapter"></a>開發 BizTalk 應用程式使用 SAP 配接器
建立 BizTalk 專案中的開發 BizTalk 應用程式牽涉到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生 XML 結構描述。 一旦您已經產生結構描述，您可以使用以內容為基礎的路由 (CBR)，或建立 BizTalk 協調流程傳送和接收符合產生結構描述的訊息。  
  
 CBR 可用在案例中傳送到 SAP 系統的訊息不需要任何大量的處理。 比方說，如果您知道接收埠會接收僅特定類型的訊息，您可以加入篩選條件要比對篩選條件運算式至傳送埠將訊息路由傳送埠。  
  
 在 BizTalk 協調流程，建立傳送和接收埠以傳送和接收訊息的[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，這會將訊息傳送至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 本節提供使用 BizTalk 協調流程對 SAP 系統使用執行作業的相關資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]接著會採用[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]配接器，以互動的 WCF 繫結。  
  
> [!IMPORTANT]
>  若要使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您都必須設定**EnableBizTalkCompatibilityMode**內容繫結至**True**。 如需如何設定繫結屬性的資訊，請參閱[設定 SAP 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [若要建立的 SAP 應用程式的必要條件](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
-   [若要建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)
  
-   [叫用中使用 BizTalk Server 的 SAP Rfc](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)  
  
-   [從 SAP 使用 BizTalk Server 接收輸入 RFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)  
  
-   [叫用中使用 BizTalk Server 的 SAP tRFCs](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)  
  
-   [從 SAP 使用 BizTalk Server 接收輸入的 tRFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md)  
  
-   [執行 SAP 使用 BizTalk Server 中的 BAPI 交易](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)  
  
-   [傳送 Idoc 至 SAP 使用 BizTalk Server](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md)  
  
-   [從 SAP 使用 BizTalk Server 接收 Idoc](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)  
  
-   [從交易內容，使用 BizTalk Server 中的 SAP 接收 Idoc](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md)  
  
## <a name="see-also"></a>另請參閱  
[開發您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)