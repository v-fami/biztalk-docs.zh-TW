---
title: 開發 BizTalk Server 中的 Siebel 應用程式 |Microsoft Docs
description: 建立 Siebel 應用程式使用 WCF，或在 BizTalk Server 與 BizTalk 配接器組件 (BAP)
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
ms.openlocfilehash: 6d65dd25f3b2bbcc90acda9fcdc5cb0eb3b2f5c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002423"
---
# <a name="develop-your-siebel-applications"></a>開發您的 Siebel 應用程式

## <a name="overview"></a>概觀
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 用戶端應用程式可以取用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]到 Siebel 成品上叫用作業。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可取用：  
  
-   透過 BizTalk Server 解決方案中的實體連接埠繫結。  
  
-   藉由叫用用戶端 proxy 的執行個體上的方法。  
  
-   為託管的 WCF 服務。  
  
-   透過通道中的執行個體使用的 WCF 通道模型的程式碼中傳送 SOAP 訊息。  
  
-   透過 ADO.NET 介面。  
  
## <a name="biztalk-vs-wcf-service-vs-wcf-channel-vs-adonet"></a>BizTalk 與 WCF 服務與 WCF 通道與 ADO.NET
 下表中：  
  
- 列出可對使用 Siebel 系統的不同作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
- 指示何種方法 ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型、 WCF 通道模型或 ADO.NET 介面) 可用來執行作業。  
  
- 提供執行工作使用所選的方法的詳細資訊的連結。  
  
|                                   工作                                    |                                                                                       BizTalk Server                                                                                        |                                                                                    WCF 服務模型                                                                                    |                                                                              WCF 通道模型                                                                               |                                                                                                                        ADO.NET 介面                                                                                                                        |
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 對商務元件的基本插入、 更新、 刪除和查詢作業 |              [對商務元件使用 BizTalk Server 和 Siebel 配接器執行作業](run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)              |     [Siebel 配接器使用 WCF 服務模型具有的商務元件執行作業](run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)     | [Siebel 配接器使用 WCF 通道模型具有的商務元件執行作業](run-tasks-on-business-components-with-the-siebel-adapter-using-a-wcf-channel.md) | [使用 Siebel 商務元件上執行選取查詢](run-a-select-query-on-business-components-with-siebel.md)**附註：** 您可以只執行選取作業，使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。 |
|             對具有 MVG 欄位的商務元件作業             |   [具有 MVG 欄位使用 BizTalk Server 和 Siebel 配接器的商務元件執行作業](run-operations-on-business-components-with-mvg-fields-using-the-siebel-adapter.md)    | [使用 Siebel 配接器使用 WCF 服務模型，對具有 MVG 欄位執行對商務元件作業](work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md) |                                                                                                                                                                              |                                                                                                                                                                                                                                                                 |
|          在挑選清單欄位的商務元件上的作業           | [挑選清單欄位使用 BizTalk Server 和 Siebel 配接器具有的商務元件執行作業](run-tasks-on-business-components-with-picklist-fields-using-the-siebel-adapter.md) |                                                                                                                                                                                         |                                                                                                                                                                              |                                                                                                                                                                                                                                                                 |
|                        叫用商務服務                         |                [叫用商務服務方法使用 BizTalk Server 和 Siebel 配接器](invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)                |                                                                                                                                                                                         |                                                                                                                                                                              |                                                                    [使用 Siebel 執行 EXECUTE 作業對商務服務](run-an-execute-operation-on-business-services-with-siebel.md)                                                                    |
|            使用整合物件叫用商務服務            |           [叫用商務服務方法，使用整合物件使用 Siebel 配接器](run-business-service-methods-with-integration-objects-using-the-siebel-adapter.md)            |                                                                                                                                                                                         |                                                                                                                                                                              |                                                                                                                                                                                                                                                                 |

## <a name="next-steps"></a>後續的步驟  
 在本節中的主題提供資訊、 程序和範例，以協助您開發應用程式，使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在這兩[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]程式設計解決方案。 

- [建立與 Siebel 系統的連線](create-a-connection-to-the-siebel-system.md)
- [在 Visual Studio 中取得 Siebel 作業的中繼資料](get-metadata-for-siebel-operations-in-visual-studio.md)
- [中繼資料節點識別碼](metadata-node-ids1.md)
- [使用繫結屬性](read-about-biztalk-adapter-for-siebel-binding-properties.md)
- [使用 Siebel 配接器開發 BizTalk 應用程式](develop-biztalk-applications-using-the-siebel-adapter.md)
- [使用 WCF 服務模型開發應用程式](develop-siebel-applications-using-the-wcf-service-model.md)
- [使用 WCF 通道模型開發應用程式](develop-siebel-applications-using-the-wcf-channel-model3.md)
- [使用 .NET Framework Data Provider for Siebel eBusiness 應用程式](use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)
- [搭配使用 SharePoint 與 Siebel 配接器](use-the-siebel-adapter-with-sharepoint.md)
- [範例](samples-for-the-siebel-adapter.md)
- [搭配使用 ServiceModel Metadata Utility Tool 與 BizTalk Adapter for Siebel eBusiness Applications](use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md)