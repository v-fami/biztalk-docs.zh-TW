---
title: 以程式設計方式取得中繼資料，從 Oracle 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving programmatically from the Oracle database
ms.assetid: 28a55935-6078-41d0-abfa-ac86e9ca8471
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c36fcd6a791f1d960a4dd4dfd78ca199d2e49cb5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-programmatically-from-the-oracle-database"></a>以程式設計方式從 Oracle 資料庫中取得中繼資料
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是自訂的 WCF 繫結會公開為 WCF 服務的 Oracle 資料庫。 配接器公開 Oracle 資料庫為自我描述的服務。也就是能夠發行中繼資料支援的作業有關的服務。 中繼資料描述至 WCF 服務; 的邏輯介面也就是服務合約、 訊息和訊息結構描述必須用來與服務互動。  
  
 此中繼資料工具會使用這類：  
  
-   [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 managed 程式碼表示法的服務合約，以及  
  
-   [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來產生訊息結構描述。  
  
 不過，您也可以擷取中繼資料以程式設計方式從配接器。 比方說，您可能想要執行此作業以建立要在現有的應用程式中使用的自訂中繼資料擷取工具。  
  
 配接器會將發佈到兩個端點的中繼資料：  
  
-   WS 中繼資料交換 (MEX) 端點。 WCF 會自動提供 MEX 端點，所有的 WCF 繫結。 您可以使用中繼資料交換來擷取中繼資料為基礎的 Oracle 資料庫上的介面卡所支援的作業。  
  
-   **IMetadataRetrievalContract**端點。 **IMetadataRetrievalContract**介面由實作[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。 它將分類多個邏輯層級的 Oracle 資料庫成品並呈現為樹狀結構的中繼資料節點。 您可以使用所公開的方法**IMetadataRetrievalContract**瀏覽和搜尋此樹狀結構的節點，並傳回您感興趣的作業的中繼資料的介面。  
  
 本節中的主題描述如何使用 MEX 和**IMetadataRetrievalContract**從配接器，以程式設計方式擷取中繼資料端點。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [取得使用 Ws-metadata Exchange Oracle 資料庫中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-using-ws-metadata-exchange-in-oracle-database.md)  
  
-   [使用 IMetadataRetrievalContract Oracle 資料庫中取得中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-in-oracle-database-using-imetadataretrievalcontract.md)  
  
## <a name="see-also"></a>另請參閱  
[開發應用程式的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)