---
title: 開發 Oracle E-business Suite 應用程式使用 WCF 服務模型 |Microsoft 文件
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
ms.openlocfilehash: 103a5f8c84b57693dd8f19d47d2b94d5e26256d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217318"
---
# <a name="develop-oracle-e-business-suite-applications-using-the-wcf-service-model"></a>開發 Oracle E-business Suite 應用程式使用 WCF 服務模型
[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]提供呼叫連線到 WCF 服務模型程式設計模型[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。 服務模型已加入至 WCF 部分，解決部份的 WCF 通道的程式設計模型限制。  
  
 WCF 服務模型會使用熟悉的.NET 開發架構來隱藏在通道上交換的 SOAP 訊息複雜性。 服務模型可完成此簡化作業由讀入記憶體中的整個 SOAP 訊息，然後再將資訊複製到.NET 資料結構。 載入記憶體中的長訊息可能不適合某些應用程式。 在這些情況下，開發人員應該使用 WCF 通道模型。 如需有關如何使用 WCF 通道模型的詳細資訊，請參閱[開發 Oracle E-business Suite 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)。  
  
 最低層級，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]呈現在其中用戶端叫用作業服務藉由在用戶端與服務端點之間建立的通道上交換 SOAP 訊息的 WCF 通道模型。 WCF 通道模型公開資料型別和方法，可讓您直接在 WCF 通道架構上運作。 WCF 通道模型會將您提供直接控制您所建立之 SOAP 訊息的內容以及方式這兩個應用程式和[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]取用。 不過，建立格式正確透過通道傳送的 SOAP 訊息並驗證傳回回覆訊息可以是詳細的精確的工作。  
  
 WCF 服務模型會使用 proxy 類別，來叫用目標服務上的作業，或從用戶端接收作業。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] Oracle E-business Suite 公開為 WCF 服務，您可以在其叫用作業。  
  
-   用來叫用作業的目標服務上的 proxy 類別會呼叫 WCF 用戶端類別。 這個類別會建立具有強型別參數的.NET 方法為服務所公開的作業。 藉由使用 WCF 服務模型，您可以叫用所公開的作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]為 WCF 用戶端上的.NET 方法。 如需 WCF 用戶端的詳細資訊，請參閱[WCF 用戶端概觀](https://msdn.microsoft.com/library/ms735103.aspx)。
  
 您可以使用下列工具來產生 WCF 用戶端類別，以及相關聯的協助程式程式碼取自服務中繼資料，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開：  
  
-   **ServiceModel Metadata Utility Tool (svcutil.exe)**，隨附 WCF。  
  
-   **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** ，隨附[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]以及與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計經驗。 此工具會顯示標準 Microsoft Windows 介面提供強大瀏覽和搜尋功能，對配接器會公開的作業。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
## <a name="in-this-section"></a>本節內容  
 下列主題提供有關如何開發使用 WCF 服務模型的應用程式資訊：  
  
-   [Oracle E-business Suite 配接器之 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)  
  
-   [中繼資料和 Oracle E-business Suite 之 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/metadata-and-the-wcf-service-model-with-oracle-e-business-suite.md)  
  
-   [Oracle E-business Suite 方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)  
  
-   [設定用戶端繫結 for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)  
  
-   [執行 Insert、 Update、 Delete 或 Select 作業介面資料表和檢視表使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)  
  
-   [完成 Oracle E-business Suite 使用 WCF 服務模型中的大型資料類型的資料表上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md)  
  
-   [叫用 Oracle E-business Suite 使用 WCF 服務模型中的並行程式](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [叫用要求集 Oracle E-business Suite 使用 WCF 服務模型中](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-request-sets-in-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [執行 Oracle E-business Suite 使用 WCF 服務模型中的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-oracle-ebs/executereader-executescalar-executenonquery-in-oracle-ebs-with-a-wcf-service.md)  
  
-   [使用 WCF 服務模型輪詢 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [接收 Oracle E-business Suite 資料庫變更通知使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-the-wcf-service-model.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 Oracle E-business Suite 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)