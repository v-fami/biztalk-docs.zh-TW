---
title: 以程式設計方式取得中繼資料，從 Oracle 資料庫 |Microsoft Docs
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
ms.openlocfilehash: 2380e58605cf401e7ed1138b078d19d5279144f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972871"
---
# <a name="get-metadata-programmatically-from-the-oracle-database"></a>從 Oracle 資料庫，以程式設計方式取得中繼資料
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是自訂的 WCF 繫結會公開為 WCF 服務的 Oracle 資料庫。 配接器會將 Oracle 資料庫公開為自我描述的服務;也就是一項服務，能夠支援之作業相關的中繼資料發行。 中繼資料描述的 WCF 服務; 的邏輯介面也就是服務合約、 訊息和訊息結構描述，必須用來與服務互動。  
  
 此中繼資料工具會使用這類：  
  
- [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 managed 程式碼表示法的服務合約，以及  
  
- [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來產生訊息結構描述。  
  
  不過，您也可以擷取中繼資料以程式設計方式從配接器。 比方說，您可能會想這麼做可以建立自訂的中繼資料擷取工具，將現有的應用程式中使用。  
  
  配接器會發行透過兩個端點的中繼資料：  
  
- WS 中繼資料交換 (MEX) 端點。 WCF 會自動提供所有的 WCF 繫結 MEX 端點。 您可以使用中繼資料交換來擷取中繼資料為基礎的 Oracle 資料庫配接器所支援的作業。  
  
- **IMetadataRetrievalContract**端點。 **IMetadataRetrievalContract**介面由實作[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。 它將多個邏輯層級的 Oracle 資料庫成品的分類，並將它們呈現為樹狀結構的中繼資料節點。 您可以使用所公開的方法**IMetadataRetrievalContract**介面瀏覽和搜尋此樹狀結構的節點，並傳回您感興趣的作業的中繼資料。  
  
  在本節中的主題描述如何使用 MEX 並**IMetadataRetrievalContract**從配接器，以程式設計方式擷取中繼資料端點。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [Oracle 資料庫中使用 Ws-metadata 交換取得中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-using-ws-metadata-exchange-in-oracle-database.md)  
  
-   [在 Oracle 資料庫中使用 IMetadataRetrievalContract 取得中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-in-oracle-database-using-imetadataretrievalcontract.md)  
  
## <a name="see-also"></a>另請參閱  
[開發您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)