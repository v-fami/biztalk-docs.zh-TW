---
title: 瀏覽、 搜尋及取得 SAP 中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata
- adapters, surfacing metadata
- TRFC
- RFC
- metadata, browsing, searching, retrieving
- adapters, operations
- BAPI
- IDOC
ms.assetid: 5f0d7c1f-d6e1-4c56-8d8e-1f5d537aa3ce
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa942786cda8c5e1070b3fa1c66e3300ffd16d4f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984055"
---
# <a name="browse-search-and-get-sap-metadata"></a>瀏覽、 搜尋及取得 SAP 中繼資料
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面從 SAP 系統的中繼資料。 此中繼資料描述使用配接器的 SAP 系統與通訊的訊息結構。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援兩個介面，來擷取中繼資料。  
  
- **MetadataExchange**所提供[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。 WCF 提供的中繼資料交換端點的所有 WCF 繫結，可讓用戶端取得中繼資料從 SAP 系統。  
  
- **IMetadataRetrievalContract**所提供[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，其支援的中繼資料瀏覽和搜尋功能的介面卡。  
  
  其中一個目標[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]是公開為 WCF 服務的 SAP 系統。 配接器會呈現 SAP 成品 （Rfc、 Bapi 和 Idoc） 做為配接器用戶端可以叫用的作業。 配接器也會呈現一些可用來傳送，或從 SAP 系統接收 Idoc 的特定作業。 這些作業會在本主題稍後列出。  
  
  您可瀏覽、 搜尋，並使用 WCF 服務模型中，使用 WCF 通道模型，以擷取中繼資料或藉由建立 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
  使用 WCF 服務模型時，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 proxy 類別來執行 SAP 系統上的作業。 BizTalk 專案時，您必須使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來產生您想要在 SAP 系統上執行作業的中繼資料。  
  
  如需有關瀏覽、 搜尋和擷取中繼資料使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或是[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請參閱[取得 Visual Studio 中的 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)。  
  
## <a name="browsing-metadata"></a>瀏覽中繼資料  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可讓配接器來瀏覽 Rfc、 Trfc、 Bapi 和 Idoc SAP 系統所公開的用戶端。 中繼資料瀏覽作業的一部分，配接器會呈現 Rfc 和 Bapi 作業。 Idoc，配接器會呈現來傳送和接收 Idoc 的作業。 這些作業都是從[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 SAP 中繼資料被分類之下的下列節點：  
  
- **RFC**。 這個節點包含由 SAP 系統的 Rfc，而代表 SAP 中的函式模組。 配接器會將 Rfc 分類成多個邏輯層級，並公開 （expose） 給配接器用戶端的階層式檢視。 RFC 位於此階層的最低層級，而且會公開為可供外部應用程式叫用作業。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 RFC SDK 產生的 Rfc 的中繼資料。 配接器可以叫用只在它可以產生中繼資料的 Rfc。  
  
   不呈現為作業的 Rfc，配接器也會提供諸如某些特定的作業這類**RfcGetAttributes**。 如需有關這些作業的詳細資訊，請參閱 <<c0> [ 對 sap Rfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。  
  
- **TRFC**。 這個節點包含 SAP 系統所公開的 Trfc。 Trfc 不是傳統的成品在 SAP 系統，但而不是叫用 Rfc 的機制。 Trfc 分為不同的節點下，因為它們的中繼資料特性會不同於 Rfc。 具體來說，Rfc 也會包含匯出的參數。 配接器將 Trfc 分類成多個邏輯層級，並公開 （expose） 給配接器用戶端的階層式檢視。 TRFC 位於此階層的最低層級，而且會公開為可供外部應用程式叫用作業。  
  
   不呈現為作業 Trfc，配接器也會提供諸如某些特定的作業這類**RfcConfirmTransID**。 如需有關這些作業的詳細資訊，請參閱 <<c0> [ 對 sap 的 Trfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。  
  
- **BAPI**。 這個節點包含 SAP 系統所公開的 Bapi。 配接器將 Bapi 分類成多個邏輯層級，並公開 （expose） 給配接器用戶端的階層式檢視。 BAPI 位於此階層的最低層級，而且會公開為可供外部應用程式叫用作業。  
  
- **IDOC**。 這個節點包含 SAP 系統所公開的 Idoc。 配接器來分類成多個邏輯層級的 Idoc，並公開 （expose） 給配接器用戶端的階層式檢視。 配接器會公開 Idoc 的作業為：  
  
  - **傳送**並**接收**。 配接器用戶端可以使用這些作業來傳送和接收 Idoc，從 SAP 系統，請使用強型別結構描述。  
  
  - **SendIdoc**並**ReceiveIdoc**。 配接器用戶端可以使用這些作業來傳送和接收 Idoc，從 SAP 系統使用弱型別結構描述。  
  
    如需有關這些作業的詳細資訊，請參閱 <<c0> [ 對 sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。  
  
  如需有關如何分類中繼資料的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  
  
## <a name="searching-metadata"></a>搜尋中繼資料  
 在  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，配接器用戶端可以使用相依於基礎 Rfc 的搜尋運算式中的 SAP 系統中搜尋中繼資料，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用。 下表列出將 SAP 成品和配接器用戶端可以用來搜尋的中繼資料階層。  
  
|成品|在 GUI 中的節點下的搜尋|  
|--------------|------------------------------------|  
|RFC|-/RFC<br />-   /RFC/[Application Group]|  
|tRFC|-/TRFC<br />-   /TRFC/[Application Group]|  
|BAPI|-   /BAPI|  
|IDOC|-   /IDOC|  
  
 下表列出可用來搜尋和其解譯的特殊字元[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|+ (加號)|比對一個字元。<br /><br /> 例如，A + 比對 AB、 AC、 AD|  
|* (星號)|比對零或多個字元。<br /><br /> 例如，A * 會比對的 AB，ABC。|  
  
## <a name="retrieving-metadata"></a>擷取中繼資料  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可讓配接器來擷取 SAP 系統，包括詳細的中繼資料特性的中繼資料的用戶端：  
  
- 如 RFC、[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]擷取 RFC 的名稱，以及匯入、 匯出、 變更和資料表參數。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也會擷取參數，參數、 欄位長度的資料型別除了必要和選用參數。  
  
- TRFC 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會擷取類似於 RFC，除了匯出參數的詳細資料。 TRFC 呼叫是非同步的因為會不擷取任何輸出參數。  
  
- BAPI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]擷取商務物件名稱、 商務物件方法名稱，以及其他類似於 Rfc 的特定資訊。  
  
- Idoc，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]擷取 IDOC 類型、 版本號碼、 版本、 IDOC 控制記錄、 IDOC 資料記錄，以及其他 IDOC 的區段資訊。  
  
  > [!NOTE]
  >  如果 IDOC 的中繼資料包含下限和上限值 （範圍） 資料類型，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開，做為字串。 中繼資料只包含低值，如果[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，公開為列舉。  
  
> [!NOTE]
>  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開 SAP 函式參數，以依字母順序排列的順序，無論 SAP 函式定義中參數的排序方式。 這是由於下列原因：  
> 
> - 不同版本的 SAP RFC SDK 會以不同的順序傳回 SAP 函式參數。 因此，為了提供一致的體驗給配接器的使用者，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開 （expose) 的參數，以依字母順序排列的順序。  
>   - 在不同的 SAP 伺服器上的相同 Rfc 可能會有不同的公開函式參數的順序。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]讓這項差異透明使用者藉由公開一致的字母順序中的參數。  
> 
> [!NOTE]
>  從 SAP 系統使用擷取資料時發生[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不會還原序列化訊息具有超過 65536 的節點。 請確定回應訊息含有節點小於或等於為 65536。 您可以修改您的應用程式的 app.config 檔，以解決這項限制。 如需相關指示，請參閱 <<c0> [ 疑難排解操作問題](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md)。  
  
 如需有關如何瀏覽的詳細資訊，請搜尋和擷取中繼資料，請參閱[取得 Visual Studio 中的 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk adapter for mySAP Business Suite 的架構概觀](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)