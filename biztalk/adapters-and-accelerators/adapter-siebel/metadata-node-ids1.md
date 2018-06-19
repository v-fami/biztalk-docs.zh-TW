---
title: Siebel 配接器在 BizTalk Adapter Pack 中的中繼資料節點識別碼 |Microsoft 文件
description: 中繼資料、 搜尋、 擷取節點型別和 Siebel 配接器-BizTalk 配接器組件 (BAP) 中公開的 Siebel 元件中使用的識別碼
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bdffc8d1-0a0a-48d7-b134-5d16acf2c523
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5aecf8995b30f5cd545e4202da0c468d730e277
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223382"
---
# <a name="node-types-and-ids-for-the-siebel-adapter"></a>節點型別和 Siebel 配接器的識別碼

## <a name="metadata-node-types-and-ids"></a>中繼資料節點類型和 Id 
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]以階層方式呈現 Siebel 系統成品。 下表描述的節點型別和 Siebel 成品所顯示的節點識別碼[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
|成品|節點類型|節點識別碼|範例|Description|  
|--------------|---------------|-------------|-------------|-----------------|  
|商務物件 （所有商務物件）|類別目錄|[版本] / BusinessObjects|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects|傳回所有的商務物件。|  
|商務物件 (BO)|類別目錄|[版本] /BusinessObjects/ [BO]|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account|傳回與指定的商務物件相關聯的所有商務元件。|  
|商務元件 (BC)|類別目錄|[版本] /BusinessObjects/ [BO] / [BC]|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account|傳回與指定的商務元件相關聯的所有作業。|  
|Insert|OPERATION|[版本] /BusinessObjects/ [BO] / [BC] / 插入|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert|傳回指定的商務元件的插入作業。|  
|查詢|OPERATION|[版本] /BusinessObjects/ [BO] / [BC] / 查詢|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Query|傳回指定的商務元件的查詢作業。|  
|Update|OPERATION|[版本] /BusinessObjects/ [BO] / [BC] / 更新|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Update|傳回指定的商務元件的更新作業。|  
|DELETE|OPERATION|[版本] /BusinessObjects/ [BO] / [BC] / 刪除|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Delete|傳回指定的商務元件上的刪除作業。|  
|關聯|OPERATION|[版本] /BusinessObjects/ [BO] / [BC] / 關聯|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Associate|傳回指定的商務元件關聯的作業。|  
|中斷關聯|OPERATION|[版本] /BusinessObjects/ [BO] / [BC] / 中斷關聯|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Dissociate|傳回指定的商務元件中斷的作業。|  
|Query_ [MVG 下層業務元件]|OPERATION|[版本] /BusinessObjects/ [BO] / [BC] / Query_ [MVG 下層業務元件]|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Query_Contact|傳回的下層業務元件的查詢作業|  
|商務服務|類別目錄|[版本] / BusinessServices|http://Microsoft.LobServices.Siebel/2007/03/BusinessServices|傳回所有商務服務。|  
|商務服務|類別目錄|[版本] /BusinessServices/ [商務服務]|http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/ATP|傳回指定的商務服務的所有商務方法。|  
|商務服務方法|OPERATION|[版本] /BusinessServices/ [商務服務] / [商務服務方法]|http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/ATP/ATPRunCheck|傳回指定的商務服務方法。|  
  
 [版本] = 版本字串。例如 http://Microsoft.LobServices.Siebel/2007/03。  
  
 [BO] = Siebel 商務物件。例如，帳戶。  
  
 [BC] = 商務元件。例如，帳戶。  
  
 [商務服務] = Siebel 商務服務;例如，ATP。  
  
 [商務服務方法] = 的商務服務; 方法例如，DismissAlarm。  
  
 [MVG 下層業務元件] = 多重值群組子商務元件。例如，請連絡。  
  
## <a name="metadata-search-and-node-ids"></a>中繼資料的搜尋和節點識別碼  
 中繼資料搜尋是功能強大功能[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]介面的一部分其**MetadataRetrievalContract**介面。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會利用此功能以支援搜尋下列 Siebel 成品。  
  
|成品|節點識別碼|Description|  
|--------------|-------------|-----------------|  
|商務物件|[版本] / BusinessObjects|傳回符合搜尋運算式的商務物件。|  
|商務元件|[版本] /BusinessObjects/ [BO]|傳回符合搜尋運算式的商務元件。|  
|商務服務|[版本] / BusinessServices|傳回符合搜尋運算式的商務服務。|  
|商務服務方法|[版本] /BusinessServices/ [商務服務]|傳回符合搜尋運算式的商務服務方法。|  
  
 [版本] = 版本字串。例如 http://Microsoft.LobServices.Siebel/2007/03。  
  
 [BO] = Siebel 商務物件。例如，帳戶。  
  
 [商務服務] = Siebel 商務服務;例如，ATP。  
  
 如需有效的搜尋運算式中，請參閱 Siebel 文件。  
  
> [!NOTE]
>  [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]只支援在目前所選節點下的層級的搜尋。  例如，選取 BusinessObjects 時，A * 為支援搜尋，但 A\*/A\*不是。  
  
## <a name="metadata-retrieval-and-node-ids"></a>擷取中繼資料和節點識別碼  
 Siebel 配接器會擷取每種類型的成品的下列特性。  
  
|成品|中繼資料的特性|  
|--------------|------------------------------|  
|商務元件|<ul><li>商務元件名稱</li><li>商務元件欄位名稱</li><li>對應至 WSDL/複雜簡單類型的商務元件欄位資料類型</li><li>對應至 facet maxLength 的商務元件欄位長度</li><li>商務元件必要的欄位對應到 facet minOccurs = 1</li><li>商務元件選擇性欄位對應到 facet minOccurs = 0</li><li>商務元件挑選清單欄位對應至 WSDL 中的挑選清單複雜類型</li><li>商務元件靜態繫結包含值的列舉的清單的挑選清單</li><li>商務元件欄位 NULL 條件約束對應至 facet isNillable = true</li><li>商務元件操作<br /><br /> <ul><li>INSERT</li><li>QUERY</li><li>UPDATE</li><li>DELETE</li><li>建立關聯</li><li>中斷關聯</li><li>針對每個商務元件具有 m:n 關聯性的下層業務元件 QUERY_ [MVG 子商務 Comp]</li></ul></li></ul>|  
|商務服務方法|商務服務名稱<br />方法名稱<br />方法是作業<br />方法參數名稱<br />方法參數的資料類型對應至 WSDL 類型<br />對應至 WSDL 參數方向的方法參數方向<br />對應至項目順序的方法參數順序|  
  
 中繼資料的格式的詳細資訊，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]公開特定成品和作業在 Siebel 系統上，請參閱[訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).  
  