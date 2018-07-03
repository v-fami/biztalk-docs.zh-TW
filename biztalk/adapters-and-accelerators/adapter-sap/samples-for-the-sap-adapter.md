---
title: SAP 配接器範例 |Microsoft Docs
description: 可以搭配 BizTalk Server、 WCF 服務模型、 WCF 通道模型和資料提供者適用於 SAP 的 mySAP WCF 配接器範例
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4654c458-83be-417f-ae54-5c3a8f6ab81f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1926c9899d1c1198998c25845d5d6b4189884f0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012063"
---
# <a name="samples-for-the-sap-adapter"></a>適用於 SAP 配接器範例
範例[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]會分類為：  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 範例  

- WCF 服務模型範例  

- WCF 通道模型範例  

- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] 範例  


 這些範例位於[BizTalk Adapter Pack 2010: SAP 配接器範例](https://www.microsoft.com/download/details.aspx?id=1314)。 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]

 下列清單描述的範例。

## <a name="biztalk-server-samples"></a>BizTalk Server 範例  

|範例目錄名稱|描述|  
|---------------------------|-----------------|  
|IDOCSend|示範如何傳送 IDOC 至 SAP 系統。|  
|ReceiveIDOC|示範如何從 SAP 系統接收 IDOC。|  
|ReceiveIDOC_SYSREL|示範如何從 SAP 系統接收 IDOC。 正在接收的 IDOC 具有小於 SAP SYSREL 的版本號碼。|  
|RFCServer|示範如何接收來自 SAP 系統的 RFC 伺服器呼叫。|  
|SAPTransaction|示範如何執行 SAP 系統使用的交易。|  
|tRFCClient|示範如何將 SAP 系統上進行 tRFC 用戶端呼叫。|  

## <a name="wcf-service-model-samples"></a>WCF 服務模型範例   

|範例目錄名稱|描述|  
|---------------------------|-----------------|  
|SapIdocStringClientSM|示範如何傳送 IDOC 至 SAP 系統中，藉由叫用 SendIdoc 作業。|  
|SapRfcServerSM|示範如何從 SAP 系統接收 RFC 伺服器呼叫。|  
|SapBapiTxClientSM|示範如何在 SAP 系統上的交易內叫用 Bapi。|  
|SapTrfcClientSM|示範如何叫用 tRFC 用戶端呼叫，在 SAP 系統上。|  

## <a name="wcf-channel-model-samples"></a>WCF 通道模型範例  

|範例目錄名稱|描述|  
|---------------------------|-----------------|  
|SapIdocReceiveCM|示範如何從 SAP 系統接收 Idoc|  
|SapRfcServerCM|示範如何接收來自 SAP 系統的 RFC 伺服器呼叫。|  

## <a name="data-provider-for-sap-samples"></a>如需 SAP 範例的資料提供者  

| 範例目錄名稱 |                                             描述                                              |
|-----------------------|------------------------------------------------------------------------------------------------------|
|        sap ado        | 示範如何使用[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。 |

## <a name="see-also"></a>另請參閱  
[開發您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)