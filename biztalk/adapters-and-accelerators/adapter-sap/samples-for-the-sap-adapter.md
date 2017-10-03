---
title: "適用於 SAP 配接器範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- samples, Data Provider for SAP
- samples, migration
- samples, BizTalk
- samples, WCF service model
- samples, WCF channel model
- samples
ms.assetid: 4654c458-83be-417f-ae54-5c3a8f6ab81f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0374aada037282a68e7575136b8671bba5ca181d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="samples-for-the-sap-adapter"></a>適用於 SAP 配接器範例
範例如[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]分類成：  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 範例  
  
-   WCF 服務模型範例  
  
-   WCF 通道模型範例  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] 範例  
  
-   移轉範例  
  
 這些範例位於[http://go.microsoft.com/fwlink/?LinkID=196854](http://go.microsoft.com/fwlink/?LinkID=196854)。  
  
 下列清單包含的名稱和描述的範例如[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="biztalk-server-samples"></a>BizTalk Server 範例  
  
|範例目錄名稱|Description|  
|---------------------------|-----------------|  
|IDOCSend|示範如何傳送 IDOC 至 SAP 系統。|  
|ReceiveIDOC|示範如何從 SAP 系統接收 IDOC。|  
|ReceiveIDOC_SYSREL|示範如何從 SAP 系統接收 IDOC。 正在接收的 IDOC 具有小於 SAP SYSREL 的版本號碼。|  
|RFCServer|示範如何從 SAP 系統接收的 RFC 伺服器呼叫。|  
|SAPTransaction|示範如何執行 SAP 系統使用的交易。|  
|tRFCClient|示範如何在 SAP 系統上進行 tRFC 用戶端呼叫。|  
  
## <a name="wcf-service-model-samples"></a>WCF 服務模型範例  
  
|範例目錄名稱|Description|  
|---------------------------|-----------------|  
|SapIdocStringClientSM|示範如何叫用 SendIdoc 作業傳送 IDOC 到 SAP 系統。|  
|SapRfcServerSM|示範如何從 SAP 系統接收的 RFC 伺服器呼叫。|  
|SapBapiTxClientSM|示範如何在 SAP 系統上的交易內叫用的 Bapi。|  
|SapTrfcClientSM|示範如何叫用對 SAP 系統進行 tRFC 用戶端呼叫。|  
  
## <a name="wcf-channel-model-samples"></a>WCF 通道模型範例  
  
|範例目錄名稱|Description|  
|---------------------------|-----------------|  
|SapIdocReceiveCM|示範如何從 SAP 系統接收 Idoc|  
|SapRfcServerCM|示範如何從 SAP 系統接收的 RFC 伺服器呼叫。|  
  
## <a name="data-provider-for-sap-samples"></a>Data Provider for SAP 範例  
  
|範例目錄名稱|Description|  
|---------------------------|-----------------|  
|sap ado|示範如何使用[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。|  
  
## <a name="migration-samples"></a>移轉範例  
  
|範例目錄名稱|Description|  
|---------------------------|-----------------|  
|SAP_RFC_Migration|示範如何使用 BizTalk 專案使用舊版的 SAP 配接器所建立，並讓它運作以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 BizTalk 專案包含協調流程叫用 SD_RFC_CUSTOMER_GET RFC。|  
|SendIDOC_Migration|示範如何使用 BizTalk 專案使用舊版的 SAP 配接器所建立，並讓它運作以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 BizTalk 專案包含協調流程傳送 IDOC 至 SAP 系統。|  
|ReceiveIDOC_Migration|示範如何使用 BizTalk 專案使用舊版的 SAP 配接器所建立，並讓它運作以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 BizTalk 專案包含協調流程叫用接收 IDOC 從 SAP 系統。|  
  
## <a name="see-also"></a>另請參閱  
[開發您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)