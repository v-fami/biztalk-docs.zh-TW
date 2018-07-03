---
title: 開發使用 WCF 服務模型的 SAP 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, developing applications
ms.assetid: 5387d063-31d3-49b3-9771-354802542f8f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e47e652f01f29c33952187f165c428df63a45c9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998647"
---
# <a name="develop-sap-applications-using-the-wcf-service-model"></a>開發使用 WCF 服務模型的 SAP 應用程式
在最低層級，[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]呈現所在的用戶端來叫用服務上的作業在用戶端與服務端點之間建立的通道上交換的 SOAP 訊息的程式設計模型。 此模型中，稱為 WCF 通道模型中，會公開資料型別和方法，讓您直接在 WCF 通道架構上運作。 WCF 通道模型會將您提供了兩個應用程式和您所建立的 SOAP 訊息的內容上的直接控制和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]取用這些; 不過，建立格式正確的 SOAP 訊息，透過通道傳送和驗證傳回回覆訊息可以是詳細的確切的工作。  
  
 基於這個理由，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供另一個呼叫 WCF 服務模型的程式設計模型。 WCF 服務模型牽涉到使用 proxy 類別叫用目標服務上的作業，或從用戶端接收作業。  
  
- 用來叫用作業的目標服務上的 proxy 類別呼叫的 WCF 用戶端類別。 此類別的模型做為強型別參數使用的.NET 方法的服務所公開的作業。 藉由使用 WCF 服務模型，您可以叫用所公開之作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為 WCF 用戶端上的.NET 方法。 如需有關 WCF 用戶端的詳細資訊，請參閱 < [WCF Client Overview](https://msdn.microsoft.com/library/ms735103.aspx)。
  
- 用來從用戶端接收作業的 proxy 類別呼叫的 WCF 服務合約的類別。 這個類別會建立您的程式碼公開為強型別參數的回呼方法的作業。 然後，您就可以裝載在此類別的執行個體**System.ServiceModel.ServiceHost**来讓用戶端來叫用您的程式碼的作業。 使用 WCF 服務模型和以 POLLINGSTMT 作業為目標的 WCF 服務合約類別，您可以接收來自的輪詢查詢的結果[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
  您使用工具來產生 WCF 用戶端類別或 WCF 服務合約和相關聯協助程式程式碼，從服務中繼資料，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開 （expose)。 您可以使用下列工具：  
  
- ServiceModel Metadata Utility Tool (svcutil.exe)，隨附於 WCF  
  
- [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，隨附 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]  
  
  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計體驗並提供標準的 Microsoft Windows 介面，提供功能強大的瀏覽和搜尋功能，對配接器所公開的作業。 如需如何產生 WCF 用戶端或 WCF 服務合約類別的詳細資訊，請參閱[產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
  由於它會呈現的模型.NET 程式設計人員所熟悉且可透過通道會隱藏基礎 SOAP 訊息交換的複雜性，WCF 服務模型通常是最佳的選擇，以開發適用於程式設計解決方案[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 不過，有些的情況中的 WCF 通道模型可能是較好的選擇;特別是在哪一個資料流中的案例很重要。 這是因為序列化和還原序列化 SOAP 訊息中的物件的 XML 表示法與用來表示服務模型中的.NET 類型之間需要讀取整個訊息載入記憶體。 如需使用 WCF 通道模型的詳細資訊，請參閱[開發的 SAP 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)。
  
  在本節中的主題包含的資訊、 程序和範例，以協助您建立及使用 WCF 服務模型開發應用程式，使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SAP 配接器使用 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-service-model-with-the-sap-adapter.md)  
  
-   [中繼資料和 WCF 服務模型，使用 SAP](../../adapters-and-accelerators/adapter-sap/metadata-and-the-wcf-service-model-with-sap.md)  
  
-   [產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)  
  
-   [設定 SAP 系統的用戶端繫結](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)  
  
-   [使用 WCF 服務模型叫用 sap Rfc](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型，在 SAP 接收輸入的 RFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型叫用 Trfc](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型，在 SAP 接收輸入的 tRFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型叫用在 SAP 中的 Bapi](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)  
  
-   [傳送 Idoc 至 SAP 使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md)