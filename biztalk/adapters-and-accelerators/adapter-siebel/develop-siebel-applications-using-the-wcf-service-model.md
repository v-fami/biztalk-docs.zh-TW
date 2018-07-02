---
title: 開發使用 WCF 服務模型的 Siebel 應用程式 |Microsoft Docs
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
ms.openlocfilehash: 492d3ca3dc132704913e54045f4c377a32903a67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984063"
---
# <a name="develop-siebel-applications-using-the-wcf-service-model"></a>開發使用 WCF 服務模型的 Siebel 應用程式
[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 提供一個程式設計模型呼叫 WCF 服務模型，這部分，可協助解決的一些其他的程式設計模型限制： WCF 通道模型。  
  
 在最低層級，[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]呈現所在的用戶端來叫用服務上的作業在用戶端與服務端點之間建立的通道上交換的 SOAP 訊息的 WCF 通道模型。 WCF 通道模型會公開資料型別和方法，讓您直接在 WCF 通道架構上運作。 WCF 通道模型會將您提供了兩個應用程式和您所建立的 SOAP 訊息的內容上的直接控制和[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]取用它們。 不過，建立格式正確的 SOAP 訊息，透過通道傳送和驗證傳回回覆訊息可以是詳細的確切的工作。  
  
 WCF 服務模型，不過，牽涉到使用 proxy 類別叫用目標服務上的作業，或從用戶端接收作業。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會 Siebel 系統公開為 WCF 服務，您可以在其叫用作業。  
  
- 用來叫用作業的目標服務上的 proxy 類別呼叫的 WCF 用戶端類別。 此類別的模型做為強型別參數使用的.NET 方法的服務所公開的作業。 藉由使用 WCF 服務模型，您可以叫用所公開之作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]做為 WCF 用戶端上的.NET 方法。 如需有關 WCF 用戶端的詳細資訊，請參閱 < [WCF Client Overview](https://msdn.microsoft.com/library/ms735103.aspx)。   
  
  您使用工具來產生 WCF 用戶端類別和相關聯協助程式程式碼，從服務中繼資料，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開 （expose)。 您可以使用下列工具：  
  
- ServiceModel Metadata Utility Tool (svcutil.exe)，隨附於 WCF  
  
- [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，隨附 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]  
  
  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計體驗並提供標準的 Microsoft Windows 介面，提供功能強大的瀏覽和搜尋功能，對配接器所公開的作業。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 Siebel 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)  
  
## <a name="why-choose-the-wcf-service-model-or-the-wcf-channel-model"></a>為什麼要選擇 WCF 服務模型或 WCF 通道模型？  
 由於它會呈現的模型是以.NET 程式設計人員熟悉並透過通道會隱藏基礎 SOAP 訊息交換的複雜性，WCF 服務模型通常是最佳的選擇，以開發適用於程式設計解決方案[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 不過，有的案例中的 WCF 通道模型可能是較好的選擇。 例如，序列化和還原序列化 SOAP 訊息中的物件的 XML 表示法與使用 WCF 服務模型中表示它們的.NET 型別之間牽涉到讀取整個訊息載入記憶體。  
  
 WCF 通道模型的 XML 節點層級資料流處理的所有作業提供支援。 在串流中節點層級，只有每個節點的 XML 訊息會保留在記憶體，一次。 針對特定作業中，比方說，如果您正在執行的查詢，傳回大型結果集，WCF 通道模型可能是較好的選擇，您的應用程式。 如需使用 WCF 通道模型的詳細資訊，請參閱[開發的 Siebel 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md)。  
  
 在本節中的主題包含的資訊、 程序和範例，以協助您建立及使用 WCF 服務模型開發應用程式，使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 Siebel 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-siebel/overview-of-the-wcf-service-model-with-the-siebel-adapter.md)  
  
-   [中繼資料和 Siebel 與 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/metadata-and-the-wcf-service-model-with-siebel.md)  
  
-   [產生 WCF 用戶端或 Siebel 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)  
  
-   [針對 Siebel 系統設定 WCF 用戶端](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)  
  
-   [Siebel 配接器使用 WCF 服務模型具有的商務元件執行作業](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)  
  
-   [使用 Siebel 配接器使用 WCF 服務模型，對具有 MVG 欄位執行對商務元件作業](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)  
  
-   [Siebel 配接器使用 WCF 服務模型以叫用商務服務方法](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md)  
  
## <a name="see-also"></a>另請參閱  
[開發您的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)