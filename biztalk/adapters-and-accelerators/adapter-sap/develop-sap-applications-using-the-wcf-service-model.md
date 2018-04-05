---
title: 開發使用 WCF 服務模型的 SAP 應用程式 |Microsoft 文件
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
ms.openlocfilehash: 4933610f8416b2c7fb81861562480e355dd8d373
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-sap-applications-using-the-wcf-service-model"></a>開發使用 WCF 服務模型的 SAP 應用程式
最低層級，[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]提供程式設計的模型中的用戶端叫用作業服務藉由在用戶端與服務端點之間建立的通道上交換 SOAP 訊息。 此模型中，稱為 WCF 通道模型，公開資料型別和方法，可讓您直接在 WCF 通道架構上運作。 WCF 通道模型會將您提供直接控制您所建立之 SOAP 訊息的內容以及方式這兩個應用程式和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]取用這些; 不過，建立格式正確的 SOAP 訊息，透過通道傳送，並驗證傳回回覆訊息可以是詳細的精確的工作。  
  
 基於這個理由，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供其他呼叫 WCF 服務模型的程式設計模型。 WCF 服務模型牽涉到使用目標服務上叫用作業，或從用戶端接收作業的 proxy 類別。  
  
-   用來叫用作業的目標服務上的 proxy 類別會呼叫 WCF 用戶端類別。 這個類別會建立具有強型別參數的.NET 方法為服務所公開的作業。 藉由使用 WCF 服務模型，您可以叫用所公開的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為 WCF 用戶端上的.NET 方法。 如需 WCF 用戶端的詳細資訊，請參閱[WCF 用戶端概觀](https://msdn.microsoft.com/library/ms735103.aspx)。
  
-   用來從用戶端接收作業的 proxy 類別會呼叫 WCF 服務合約類別。 這個類別會建立您的程式碼公開為回呼方法具有強型別參數的作業。 然後，您就可以裝載在此類別的執行個體**system.servicemodel.servicehost 內**啟用用戶端來叫用您的程式碼的作業。 您可以使用 WCF 服務模型和 POLLINGSTMT 作業的目標是 WCF 服務合約類別，接收從輪詢查詢的結果[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
 您使用工具來產生 WCF 用戶端類別或 WCF 服務合約，以及相關聯的協助程式程式碼取自服務中繼資料，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開。 您可以使用下列工具之一：  
  
-   ServiceModel Metadata Utility Tool (svcutil.exe)，隨附 WCF  
  
-   [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，隨附[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計經驗，以及顯示標準的 Microsoft Windows 介面提供強大瀏覽和搜尋功能，對配接器所公開的作業。 如需如何產生 WCF 用戶端或 WCF 服務合約類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約為 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
 它會呈現的模型.NET 程式設計人員熟悉且可透過通道隱藏基礎 SOAP 訊息交換的複雜性，因為 WCF 服務模型通常是最佳選擇程式設計為開發解決方案[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 不過，在的案例中的 WCF 通道模型可能比較好的選擇。特別是在哪一個資料流中的案例很重要。 這是因為序列化和還原序列化之 XML 表示的 SOAP 訊息中的物件與用來代表服務模型中的.NET 類型之間涉及讀入記憶體中的整個訊息。 如需有關如何使用 WCF 通道模型的詳細資訊，請參閱[開發 SAP 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)。
  
 本節中的主題包含資訊、 程序和範例，以協助您建立及使用 WCF 服務模型來開發應用程式使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SAP 配接器之 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-service-model-with-the-sap-adapter.md)  
  
-   [中繼資料和 WCF 服務模型，與 SAP](../../adapters-and-accelerators/adapter-sap/metadata-and-the-wcf-service-model-with-sap.md)  
  
-   [產生 WCF 用戶端或 WCF 服務合約為 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)  
  
-   [設定 SAP 系統的用戶端繫結](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)  
  
-   [使用 WCF 服務模型來叫用 sap Rfc](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型中 SAP 接收輸入的 RFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型來叫用 tRFCs](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型中 SAP 接收輸入的 tRFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型來叫用 SAP 中的 Bapi](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)  
  
-   [傳送 Idoc 至 SAP 使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md)