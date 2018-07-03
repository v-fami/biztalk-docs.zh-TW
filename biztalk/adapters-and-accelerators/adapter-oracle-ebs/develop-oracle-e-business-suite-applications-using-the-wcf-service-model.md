---
title: 開發 Oracle E-business Suite 應用程式使用 WCF 服務模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cf3430d-12e9-437c-b398-d978faa4da2b
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b290ef99349d970179b07ecfce45c72499d88c5c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996015"
---
# <a name="develop-oracle-e-business-suite-applications-using-the-wcf-service-model"></a>開發 Oracle E-business Suite 應用程式使用 WCF 服務模型
[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] 提供程式設計模型呼叫 WCF 服務模型，來連接到[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。 服務模型已新增至 WCF，若要解決，部分的一些 WCF 通道的程式設計模型的限制。  
  
 WCF 服務模型會使用熟悉的.NET 架構來隱藏在通道上交換的 SOAP 訊息複雜性。 服務模型會完成這個簡化的讀入記憶體中的整個 SOAP 訊息，再將資訊複製到.NET 資料結構。 載入記憶體中的長訊息可能不適合某些應用程式。 在這些情況下，開發人員應該使用的 WCF 通道模型。 如需使用 WCF 通道模型的詳細資訊，請參閱[開發 Oracle E-business Suite 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)。  
  
 在最低層級，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]呈現所在的用戶端來叫用服務上的作業在用戶端與服務端點之間建立的通道上交換的 SOAP 訊息的 WCF 通道模型。 WCF 通道模型會公開資料型別和方法，讓您直接在 WCF 通道架構上運作。 WCF 通道模型會將您提供了兩個應用程式和您所建立的 SOAP 訊息的內容上的直接控制和[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]取用它們。 不過，建立格式正確的 SOAP 訊息，透過通道傳送和驗證傳回回覆訊息可以是詳細的確切的工作。  
  
 WCF 服務模型會使用 proxy 類別，來叫用目標服務上的作業，或從用戶端接收作業。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開為 WCF 服務，您可以在其叫用作業的 Oracle E-business Suite。  
  
- 用來叫用作業的目標服務上的 proxy 類別呼叫的 WCF 用戶端類別。 此類別的模型做為強型別參數使用的.NET 方法的服務所公開的作業。 藉由使用 WCF 服務模型，您可以叫用所公開之作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]做為 WCF 用戶端上的.NET 方法。 如需有關 WCF 用戶端的詳細資訊，請參閱 < [WCF Client Overview](https://msdn.microsoft.com/library/ms735103.aspx)。
  
  您可以使用下列工具來產生 WCF 用戶端類別和相關聯協助程式程式碼，從服務中繼資料，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開 （expose):  
  
- **ServiceModel Metadata Utility Tool (svcutil.exe)**，隨附 WCF。  
  
- **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** ，其中隨附[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，並與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計經驗。 此工具會提供標準的 Microsoft Windows 介面，提供功能強大的瀏覽和搜尋功能，對配接器所公開的作業。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[Oracle E-business Suite 解決方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
## <a name="in-this-section"></a>本節內容  
 下列主題提供有關如何開發使用 WCF 服務模型的應用程式的資訊：  
  
-   [Oracle E-business Suite 配接器使用 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)  
  
-   [中繼資料和 WCF 服務模型與 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/metadata-and-the-wcf-service-model-with-oracle-e-business-suite.md)  
  
-   [Oracle E-business Suite 解決方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)  
  
-   [設定用戶端繫結 for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)  
  
-   [執行 Insert、 Update、 Delete 或 Select 作業介面資料表和檢視表使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)  
  
-   [完成使用 WCF 服務模型的 Oracle E-business Suite 中的大型資料類型的資料表上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md)  
  
-   [叫用 Oracle E-business Suite 使用 WCF 服務模型中的並行程式](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [叫用 Oracle E-business Suite 使用 WCF 服務模型中的要求集](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-request-sets-in-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [執行 Oracle E-business Suite 使用 WCF 服務模型中的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-oracle-ebs/executereader-executescalar-executenonquery-in-oracle-ebs-with-a-wcf-service.md)  
  
-   [使用 WCF 服務模型輪詢 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [Oracle E-business Suite 使用接收資料庫變更通知 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-the-wcf-service-model.md)  
  
## <a name="see-also"></a>另請參閱  
[開發您的 Oracle E-business Suite 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)