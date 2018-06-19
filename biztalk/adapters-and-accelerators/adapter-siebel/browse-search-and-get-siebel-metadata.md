---
title: 瀏覽、 搜尋及取得 Siebel 中繼資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving
- metadata, surfacing
- retrieving, metadata
- metadata, browsing
- browsing, metadata
- metadata, searching
- searching, metadata
ms.assetid: 48fc3bb1-b949-4b8d-ab62-a41cd8c2f0a0
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef1ed7d74b4e69f56c53beda8273533bb6891a55
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22222566"
---
# <a name="browse-search-and-get-siebel-metadata"></a>瀏覽、 搜尋及取得 Siebel 中繼資料
[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]表面來自 Siebel 系統的說明與使用配接器的 Siebel 系統通訊的訊息結構的中繼資料。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援兩個介面來擷取中繼資料。  
  
-   所提供的中繼資料交換[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。 WCF 提供的中繼資料交換端點的所有 WCF 繫結，讓來自 Siebel 系統中取得中繼資料的用戶端。  
  
-   所提供的 IMetadataRetrievalContract [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，可支援瀏覽和搜尋功能的介面卡的中繼資料。  
  
 目標[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]是公開為 WCF 服務的 Siebel 系統。 配接器會呈現 Siebel 成品 （商務物件和商務服務） 做為配接器用戶端可以叫用的作業。  
  
 配接器用戶端可以瀏覽、 搜尋，並使用 WCF 通道模型，透過 WCF 服務模型擷取中繼資料或藉由建立 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 使用 WCF 服務模型時，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 proxy 類別，用於在 Siebel 系統上執行作業。 當使用 BizTalk 專案時，您必須使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生您想要在 Siebel 系統上執行作業的中繼資料。 如需有關瀏覽、 搜尋和擷取中繼資料使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請參閱[取得 Visual Studio 中的 Siebel 作業的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)。  
  
## <a name="browsing-metadata"></a>瀏覽中繼資料  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可讓配接器即可瀏覽商務物件和 Siebel 系統所公開的商務服務的用戶端。 中繼資料瀏覽作業的一部分，配接器會將成品分類至多個邏輯層級，並公開 （expose） 給配接器用戶端的中繼資料的階層式檢視。 來自 Siebel 系統的中繼資料會分為下列節點：  
  
-   **商務物件**。 這個節點包含商務物件在 Siebel 系統中，這是一種商務元件的邏輯集合。 商務物件會進一步分類為商務元件中。 在階層的最低層級都是您可以叫用商務元件的作業。  
  
-   **商務服務**。 這個節點包含由 Siebel 系統的商務服務。 Siebel 商務服務是商務服務方法或可以在 Siebel 系統中直接叫用的函式的集合。  
  
 如需中繼資料的分類方式的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。  
  
## <a name="searching-metadata"></a>搜尋中繼資料  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可讓配接器用戶端在 Siebel 系統中搜尋中繼資料。 它會使用有效的 Siebel Siebel 與相容的搜尋運算式的 LIKE 運算子用於中繼資料瀏覽 Siebel 儲存機制的商務元件的 [名稱] 欄位上。 下表列出 Siebel 成品和可以用以搜尋中繼資料階層。  
  
|成品|在 GUI 中的節點下搜尋|  
|--------------|----------------------------------------|  
|商務物件|/ 商務物件|  
|商務元件|/ 商務物件/商務物件名稱|  
|商務服務|/ 商務服務|  
  
 下表列出可用於搜尋和由其解譯的特殊字元[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|? （問號）|比對一個字元。<br /><br /> 例如，A？比對 AB、 AC、 AD|  
|* (星號)|比對零個或多個字元。<br /><br /> 例如，A * 比對 A，AB，ABC。|  
  
## <a name="retrieving-metadata"></a>擷取中繼資料  
 擷取中繼資料時[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可以擷取中繼資料，在結構描述，包括所有或商務物件或商務服務的個別作業參數的子集。 它會顯示來自 Siebel 系統的實體當做 XML 中的項目名稱。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可讓配接器用戶端擷取 Siebel 系統中，包括詳細的中繼資料特性的中繼資料：  
  
-   商務元件[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]擷取商務物件名稱、 商務元件名稱、 欄位名稱、 資料型別、 欄位長度、 必要欄位，選擇性欄位，和挑選清單欄位的這類項目。 配接器也會擷取商務元件，例如 INSERT、 UPDATE、 DELETE 和查詢上可能的作業。  
  
-   商務服務方法，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]擷取這類項目，做為商務服務名稱、 方法名稱 （與作業相同）、 方法參數和參數資料類型。  
  
 如需有關擷取的中繼資料的詳細資訊，請參閱[取得 Visual Studio 中的 Siebel 作業的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Siebel eBusiness Applications 概觀](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)