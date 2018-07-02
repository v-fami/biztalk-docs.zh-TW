---
title: 開發 biztalk 應用程式 Oracle E-business Suite |Microsoft Docs
description: 建立 Oracle EBS 應用程式使用 WCF，或在 BizTalk Server 與 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7b1ebff-b3f8-4e07-a089-d1d5bfb78d56
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bc00f1b22777829b314ccd1171cbc7fb6b4e5ff
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972815"
---
# <a name="develop-your-oracle-e-business-suite-applications"></a>開發您的 Oracle E-business Suite 應用程式

## <a name="overview"></a>概觀
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]繫結。 用戶端應用程式可以取用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]叫用 Oracle E-business Suite 成品的作業。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可取用：  
  
- 中的實體連接埠繫結透過[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 藉由叫用用戶端 proxy 的執行個體上的方法。  
  
- 透過通道中的執行個體使用的 WCF 通道模型的程式碼中傳送 SOAP 訊息。  

## <a name="biztalk-vs-wcf-service-vs-wcf-channel"></a>BizTalk 與 WCF 服務與 WCF 通道 
  
 下表中：  
  
- 列出可對 Oracle E-business Suite 的不同作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
- 提供的連結，其中包含執行工作使用所選的方法的相關資訊的主題 ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型或 WCF 通道模型)。  
  
|作業|BizTalk Server|WCF 服務模型|WCF 通道模型|  
|---|---|---|---|  
|在介面資料表和檢視表上執行作業 | [插入、 更新、 刪除或選取在介面資料表和介面檢視使用 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-or-select-on-interface-tables-and-views-with-oracle-ebs.md) |[插入、 更新、 刪除或選取在介面資料表和檢視使用 WCF 服務模型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)|[執行插入作業在介面資料表上使用 WCF 通道模型的 Oracle E-business Suite 中](../../adapters-and-accelerators/adapter-oracle-ebs/insert-on-an-interface-table-in-oracle-ebs-using-the-wcf-channel-model.md)|  
|執行資料表和檢視表上含有大型資料類型的作業 | [完成使用 WCF 服務模型的 Oracle E-business Suite 中的大型資料類型的資料表作業](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md) |[完成使用 WCF 服務模型的 Oracle E-business Suite 中的大型資料類型的資料表作業](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md)||  
|執行 Oracle 資料庫上的複合作業 | [在 Oracle E-business Suite 完成複合作業](../../adapters-and-accelerators/adapter-oracle-ebs/complete-composite-operations-on-oracle-e-business-suite.md)|||  
|Oracle E-business Suite 中叫用同時執行的程式 | [叫用 Oracle E-business Suite 中的並行程式](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-concurrent-programs-in-oracle-e-business-suite.md) | [叫用 Oracle E-business Suite 使用 WCF 服務模型中的並行程式](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md)||  
|設定 Oracle E-business Suite 中的叫用要求 | [叫用 Oracle E-business Suite 中的要求集](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-request-sets-in-oracle-e-business-suite.md) | [叫用 Oracle E-business Suite 使用 WCF 服務模型中的要求集](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-request-sets-in-oracle-e-business-suite-using-the-wcf-service-model.md)||  
|執行 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業| [Oracle E-business Suite 中的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-oracle-ebs/executereader-executescalar-or-executenonquery-in-oracle-e-business-suite.md) |[使用 WCF 服務模型的 Oracle E-business Suite 中的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-oracle-ebs/executereader-executescalar-executenonquery-in-oracle-ebs-with-a-wcf-service.md)||  
|輪詢 Oracle 資料庫使用 BizTalk Server|[使用 BizTalk Server 輪詢 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)|[使用 WCF 服務模型輪詢 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)||  
|從 Oracle E-business Suite 接收資料庫變更通知|[接收使用 BizTalk Server 的 Oracle 資料庫變更通知](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)|[Oracle E-business Suite 使用接收資料庫變更通知 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-the-wcf-service-model.md)|[使用 WCF 通道模型中的 SELECT 陳述式的輪詢 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model.md)|  

## <a name="next-steps"></a>後續的步驟  
 在本節中的主題提供資訊、 程序和範例，以協助您開發應用程式，使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和.NET 程式設計解決方案。 
  
-   [建立 Oracle EBS 的連接](create-a-connection-to-oracle-e-business-suite.md)
-   [取得 Visual Studio 中的 Oracle EBS 作業中繼資料](get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)
-   [使用繫結屬性](read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)
-   [接收以輪詢為基礎的資料變更訊息](receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md)
-   [使用 MSDTC 啟用交易](enable-ms-dtc-to-allow-transactions-for-oracle-e-business-suite-adapter.md)
-   [使用 Oracle EBS 配接器開發 BizTalk 應用程式](develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)
-   [使用 WCF 服務模型開發應用程式](develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
-   [使用 WCF 通道模型開發應用程式](develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)
-   [搭配使用 SharePoint 與 Oracle EBS 配接器](use-the-oracle-e-business-suite-adapter-with-sharepoint.md)
-   [範例](samples-for-the-oracle-ebs-adapter.md)
-   [設定交易屬性和應用程式內容](configure-transaction-properties-and-application-context-in-oracle-ebs-adapter.md)
  
