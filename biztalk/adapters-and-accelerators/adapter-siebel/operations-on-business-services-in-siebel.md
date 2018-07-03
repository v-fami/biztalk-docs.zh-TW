---
title: 在 Siebel 商務服務的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, on business services
- business services, operations on
ms.assetid: 29a1a88c-8c7b-46f1-8faf-49ddd32ba2f0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df24fa8ee0bd51ddf919e5f88a47ceae9d0743fa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001367"
---
# <a name="operations-on-business-services-in-siebel"></a>在 Siebel 商務服務的相關作業
Siebel 商務服務是可直接叫用在 Siebel 商務方法的集合。 商務元件和商務物件是特定資料和 Siebel 中的資料表相關聯，而商務服務叫用來執行特定工作的物件。  
  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]呈現商務服務方法，作業名稱，並支援 IN、 OUT 及 INOUT 參數。 例如，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]表面**ATPRunCheck**做為作業的方法。 這個方法所屬**ATP**商務服務。  
  
 某些條件[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]加諸使用 Siebel 商務服務時：  
  
- Siebel 商務服務方法會接受並沒有指定的資料類型的引數，如果配接器會公開為文字的引數。  
  
- Siebel 商務服務方法引數可以是下列類型：  
  
  - 字串 （公開為 xsd: string）  
  
  - 數字 (公開為 xsd: decimal)  
  
  - 日期 （公開為 xsd:DateTime，使用模式 facet 表示之時間部分必須設定為 00:00:00）  
  
  - 階層 （公開為 xsd: string）  
  
  - 整合物件 （公開為 xsd: string）  
  
    此外，商務服務方法會驗證傳遞的引數的值是否符合對應的型別。 因此，如果商務服務方法會接受或傳回不符合對應的引數類型的值，配接器可能會擲回例外狀況。 如果配接器未成功叫用商務服務方法，結構描述驗證可能會失敗。  
  
  如需詳細資訊：  
  
- 執行使用 BizTalk Server 的商務服務的相關作業，請參閱[叫用商務服務方法使用 BizTalk Server 和 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)。  
  
- 訊息結構和 SOAP 動作的商務服務執行作業，請參閱[商務服務作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md))。  
  
## <a name="see-also"></a>另請參閱  
 [連接到 SAP 系統使用配接器](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)