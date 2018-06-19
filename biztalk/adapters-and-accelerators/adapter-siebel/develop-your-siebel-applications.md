---
title: 開發 BizTalk Server 在 Siebel 應用程式 |Microsoft 文件
description: 建立使用 WCF，Siebel 應用程式或 BizTalk Server 與 BizTalk 配接器組件 (BAP) 中
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bc04906-6d64-433c-b357-797ec5883279
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c1535a3aa7861effdad998d4d997fbcdfced02c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222598"
---
# <a name="develop-your-siebel-applications"></a>開發 Siebel 應用程式

## <a name="overview"></a>概觀
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 用戶端應用程式可以取用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]到 Siebel 成品上叫用作業。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可以取用：  
  
-   透過 BizTalk Server 解決方案中的實體連接埠繫結。  
  
-   藉由叫用用戶端 proxy 的執行個體上的方法。  
  
-   為託管的 WCF 服務。  
  
-   傳送 SOAP 訊息中使用 WCF 通道模型的程式碼是通道執行個體。  
  
-   透過 ADO.NET 介面。  
  
## <a name="biztalk-vs-wcf-service-vs-wcf-channel-vs-adonet"></a>BizTalk 與 WCF 服務與 WCF 通道 vs ADO.NET
 下表：  
  
-   列出可對使用 Siebel 系統的不同作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
-   指出哪些方法 ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型、 WCF 通道模型或 ADO.NET 介面) 可以用來執行作業。  
  
-   提供有關執行工作，使用所選的方法的詳細資訊連結。  
  
|工作|BizTalk Server|WCF 服務模型|WCF 通道模型|ADO.NET 介面|  
|----------|--------------------|-----------------------|-----------------------|-----------------------|  
|商務元件的基本 Insert、 Update、 Delete 和查詢作業|[在商務元件使用 BizTalk Server 和 Siebel 配接器上執行作業](run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)|[使用 Siebel 配接器使用 WCF 服務模型執行商務元件上的作業](run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)|[使用 Siebel 配接器使用 WCF 通道模型執行商務元件上的作業](run-tasks-on-business-components-with-the-siebel-adapter-using-a-wcf-channel.md)|[Siebel 商務元件上執行選取查詢](run-a-select-query-on-business-components-with-siebel.md)**附註：** 您只能執行 SELECT 作業使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。|  
|MVG 欄位的商務元件上的作業|[使用 MVG 欄位使用 BizTalk Server 和 Siebel 配接器執行商務元件上的作業](run-operations-on-business-components-with-mvg-fields-using-the-siebel-adapter.md)|[使用 Siebel 配接器使用 WCF 服務模型執行 MVG 欄位的商務元件上的作業](work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)|||  
|在挑選清單欄位的商務元件上的作業|[使用挑選清單欄位使用 BizTalk Server 和 Siebel 配接器執行商務元件上的作業](run-tasks-on-business-components-with-picklist-fields-using-the-siebel-adapter.md)||||  
|叫用商務服務|[叫用商務服務方法使用 BizTalk Server 和 Siebel 配接器](invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)|||[執行與 Siebel 商務服務上的執行作業](run-an-execute-operation-on-business-services-with-siebel.md)|  
|使用整合物件叫用商務服務|[叫用商務服務方法使用整合物件使用 Siebel 配接器](run-business-service-methods-with-integration-objects-using-the-siebel-adapter.md)||||  

## <a name="next-steps"></a>後續的步驟  
 本節中的主題提供資訊、 程序和範例，以協助您開發應用程式取用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]程式設計方案。 

- [建立連接至 Siebel 系統](create-a-connection-to-the-siebel-system.md)
- [取得 Visual Studio 中的 Siebel 作業的中繼資料](get-metadata-for-siebel-operations-in-visual-studio.md)
- [中繼資料節點識別碼](metadata-node-ids1.md)
- [使用繫結屬性](read-about-biztalk-adapter-for-siebel-binding-properties.md)
- [開發 BizTalk 應用程式使用 Siebel 配接器](develop-biztalk-applications-using-the-siebel-adapter.md)
- [開發應用程式使用 WCF 服務模型](develop-siebel-applications-using-the-wcf-service-model.md)
- [開發應用程式使用 WCF 通道模型](develop-siebel-applications-using-the-wcf-channel-model3.md)
- [使用.NET Framework Data Provider for Siebel eBusiness 應用程式](use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)
- [搭配 SharePoint 使用 Siebel 配接器](use-the-siebel-adapter-with-sharepoint.md)
- [範例](samples-for-the-siebel-adapter.md)
- [使用 BizTalk adapter 的 ServiceModel Metadata Utility Tool for Siebel eBusiness 應用程式](use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md)