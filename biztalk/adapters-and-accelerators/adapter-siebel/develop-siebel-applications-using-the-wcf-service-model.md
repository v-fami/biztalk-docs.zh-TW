---
title: 開發 Siebel 應用程式使用 WCF 服務模型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, developing applications by using
- WCF service model, performing operations
- proxy programming, performing operations
- WCF service model, advantages of using
ms.assetid: df5627b9-c80d-4a75-a20a-a0be119735a2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c14560fb92eb2cca1e55d32e556dec23725a0de6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222526"
---
# <a name="develop-siebel-applications-using-the-wcf-service-model"></a>開發 Siebel 應用程式使用 WCF 服務模型
[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供程式設計模型呼叫 WCF 服務模型的一部分，可協助解決某些其他的程式設計模型限制 — WCF 通道模型。  
  
 最低層級，[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]呈現在其中用戶端叫用作業服務藉由在用戶端與服務端點之間建立的通道上交換 SOAP 訊息的 WCF 通道模型。 WCF 通道模型公開資料型別和方法，可讓您直接在 WCF 通道架構上運作。 WCF 通道模型會將您提供直接控制您所建立之 SOAP 訊息的內容以及方式這兩個應用程式和[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]取用。 不過，建立格式正確透過通道傳送的 SOAP 訊息並驗證傳回回覆訊息可以是詳細的精確的工作。  
  
 WCF 服務模型，不過，牽涉到使用目標服務上叫用作業，或從用戶端接收作業的 proxy 類別。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] Siebel 系統公開為 WCF 服務，您可以在其叫用作業。  
  
-   用來叫用作業的目標服務上的 proxy 類別會呼叫 WCF 用戶端類別。 這個類別會建立具有強型別參數的.NET 方法為服務所公開的作業。 藉由使用 WCF 服務模型，您可以叫用所公開的作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]為 WCF 用戶端上的.NET 方法。 如需 WCF 用戶端的詳細資訊，請參閱[WCF 用戶端概觀](https://msdn.microsoft.com/library/ms735103.aspx)。   
  
 您使用工具來產生 WCF 用戶端類別，以及相關聯的協助程式程式碼取自服務中繼資料，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開。 您可以使用下列工具之一：  
  
-   ServiceModel Metadata Utility Tool (svcutil.exe)，隨附 WCF  
  
-   [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，隨附[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計經驗，以及顯示標準的 Microsoft Windows 介面提供強大瀏覽和搜尋功能，對配接器所公開的作業。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約為 Siebel 方案成品](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)  
  
## <a name="why-choose-the-wcf-service-model-or-the-wcf-channel-model"></a>為何選擇 WCF 服務模型或 WCF 通道模型？  
 它會呈現的模型與.NET 程式設計人員，並透過通道隱藏基礎 SOAP 訊息交換的複雜性，因為 WCF 服務模型通常是最佳選擇程式設計為開發解決方案[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 不過，有一些的案例中的 WCF 通道模型可能是較好的選擇。 例如，序列化和還原序列化物件中的 SOAP 訊息的 XML 表示法之間用來代表它們 WCF 服務模型中的.NET 類型牽涉到讀入記憶體中的整個訊息。  
  
 WCF 通道模型的 XML 節點層級資料流處理的所有作業提供支援。 在節點層級資料流中，僅將 XML 訊息的每個節點會保留在記憶體中一次。 某些作業，例如，如果您正在執行查詢，傳回大型結果集 WCF 通道模型可能比較好的選擇，您的應用程式。 如需有關如何使用 WCF 通道模型的詳細資訊，請參閱[開發 Siebel 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md)。  
  
 本節中的主題包含資訊、 程序和範例，以協助您建立及使用 WCF 服務模型來開發應用程式使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [Siebel 配接器之 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-siebel/overview-of-the-wcf-service-model-with-the-siebel-adapter.md)  
  
-   [中繼資料和 Siebel 與 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/metadata-and-the-wcf-service-model-with-siebel.md)  
  
-   [產生 WCF 用戶端或 WCF 服務合約為 Siebel 方案成品](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)  
  
-   [設定 Siebel 系統的 WCF 用戶端](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)  
  
-   [使用 Siebel 配接器使用 WCF 服務模型執行商務元件上的作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)  
  
-   [使用 Siebel 配接器使用 WCF 服務模型執行 MVG 欄位的商務元件上的作業](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)  
  
-   [Siebel 配接器使用 WCF 服務模型以叫用商務服務方法](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)