---
title: 開發使用配接器在 BizTalk 中的 SAP 應用程式 |Microsoft Docs
description: 建立 SAP 應用程式使用 WCF、 BizTalk Server 或 ADO.NET 與 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, use adapters
- adapters, working with
- working with adapters
ms.assetid: e8315c0d-923b-433e-9d11-4e8a53e0a1d9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a023f3890eff7b3b8c846f0c2c3e15cda4c1d35
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003157"
---
# <a name="develop-your-sap-applications"></a>開發您的 SAP 應用程式

## <a name="overview"></a>概觀
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 用戶端應用程式可以取用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]至 SAP 成品上叫用作業。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可取用：  
  
- 中的實體連接埠繫結透過[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 藉由叫用用戶端 proxy 的執行個體上的方法。  
  
- 為託管的 WCF 服務。  
  
- 透過通道中的執行個體使用的 WCF 通道模型的程式碼中傳送 SOAP 訊息。  
  
- 透過 ADO.NET 介面。  

## <a name="biztalk-vs-wcf-service-vs-wcf-channel-vs-adonet"></a>BizTalk 與 WCF 服務與 WCF 通道與 ADO.NET
  
 下表中：  
  
- 列出可對 SAP 系統使用的不同作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
- 指示何種方法 ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型、 WCF 通道模型或 ADO.NET 介面) 可用來執行作業。  
  
- 提供執行工作使用所選的方法的詳細資訊的連結。  
  
|工作|BizTalk Server|WCF 服務模型|WCF 通道模型|ADO.NET 介面|  
|----------|--------------------|-----------------------|-----------------------|-----------------------|  
|SAP 系統中叫用 Rfc|[叫用 Rfc，SAP 使用 BizTalk Server 中](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)|[叫用中使用 WCF 服務模型的 SAP Rfc](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)|[使用 WCF 通道模型的 SAP 系統上叫用作業](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)|[叫用 Rfc 和 Bapi SAP 中使用 EXEC 命令](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-and-bapis-using-the-exec-command-in-sap.md)|  
|從 SAP 系統接收輸入的 RFC 呼叫|[從使用 BizTalk Server 的 SAP 接收輸入的 RFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)|[使用 WCF 服務模型的 sap 接收輸入的 RFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)|[從使用 WCF 通道模型的 SAP 系統接收輸入的作業](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  
|SAP 系統中叫用 Trfc|[叫用 Trfc SAP 使用 BizTalk Server 中](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)|[叫用 Trfc SAP 使用 WCF 服務模型中](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)|[使用 WCF 通道模型的 SAP 系統上叫用作業](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|接收來自輸入的 tRFC 呼叫|[從使用 BizTalk Server 的 SAP 接收輸入的 tRFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md)|[使用 WCF 服務模型的 sap 接收輸入的 tRFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md)|[從使用 WCF 通道模型的 SAP 系統接收輸入的作業](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  
|SAP 系統上執行交易|[使用 BizTalk Server 的 sap 執行 BAPI 交易](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)|[叫用 SAP 使用 WCF 服務模型中的 Bapi](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)|[使用 WCF 通道模型的 SAP 系統上叫用作業](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|傳送 IDOC 到 SAP 系統|[傳送 Idoc 至 SAP 使用 BizTalk Server](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md)|[傳送 Idoc 至 SAP 使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md)|[使用 WCF 通道模型的 SAP 系統上叫用作業](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|從 SAP 系統接收 IDOC|[從使用 BizTalk Server 的 SAP 接收 Idoc](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)||[從使用 WCF 通道模型的 SAP 系統接收輸入的作業](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  

## <a name="next-steps"></a>後續的步驟

 下一步 的主題提供資訊的程序和開發應用程式所使用的範例[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在這兩[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，和[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]程式設計解決方案。 

- [建立與 SAP 系統的連線](create-a-connection-to-the-sap-system.md)
- [在 Visual Studio 中取得 SAP 作業的中繼資料](get-metadata-for-sap-operations-in-visual-studio.md)
- [使用繫結屬性](read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)
- [串流和 SAP 配接器](streaming-and-the-sap-adapter.md)
- [使用 SAP 配接器開發 BizTalk 應用程式](develop-biztalk-applications-using-the-sap-adapter.md)
- [使用 WCF 服務模型開發應用程式](develop-sap-applications-using-the-wcf-service-model.md)
- [使用 WCF 通道模型開發應用程式](develop-sap-applications-using-the-wcf-channel-model.md)
- [以程式設計方式取得中繼資料](get-metadata-programmatically-from-sap.md)
- [使用.NET Framework Data Provider for mySAP](use-the-net-framework-data-provider-for-mysap-business-suite.md)
- [搭配使用 SharePoint 與 SAP 配接器](use-the-sap-adapter-with-sharepoint.md)
- [範例](samples-for-the-sap-adapter.md)
- [使用 svcutil.exe](use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md) 
 
  
## <a name="see-also"></a>另請參閱  
 [建立 SAP 系統連線 URI](create-the-sap-system-connection-uri.md)