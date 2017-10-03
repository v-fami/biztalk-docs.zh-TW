---
title: "在 Siebel 商務服務的相關作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations, on business services
- business services, operations on
ms.assetid: 29a1a88c-8c7b-46f1-8faf-49ddd32ba2f0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1ffd133d76b1f8cae3f1732e48f817fe4fb26b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-business-services-in-siebel"></a>在 Siebel 商務服務的相關作業
Siebel 商務服務是可以在 Siebel 中直接叫用的商務方法的集合。 商務元件和商務物件都已關聯到特定的資料和 Siebel 中的資料表，而商務服務叫用來執行特定工作的物件。  
  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]呈現的商務服務方法，作業名稱，並支援 IN、 OUT 和 INOUT 參數。 例如，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]介面**ATPRunCheck**做為作業的方法。 這個方法屬於**ATP**商務服務。  
  
 某些條件[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會加諸使用 Siebel 商務服務時：  
  
-   Siebel 商務服務方法會接受並沒有指定的資料類型的引數，如果配接器會公開引數為文字。  
  
-   Siebel 商務服務方法引數可以是下列類型：  
  
    -   字串 （公開為 xsd: string）  
  
    -   數字 (公開為 xsd： 十進位)  
  
    -   日期 （公開為 xsd:DateTime、 使用模式 facet，指出時間部分必須設定為 00:00:00）  
  
    -   階層 （公開為 xsd: string）  
  
    -   整合物件 （公開為 xsd: string）  
  
     此外，商務服務方法會驗證引數傳遞的值是否符合對應型別。 因此，如果商務服務方法會接受或傳回不符合對應的引數類型的值，配接器可能會擲回例外狀況。 如果配接器無法順利叫用商務服務方法，結構描述驗證可能會失敗。  
  
 如需詳細資訊：  
  
-   執行的作業上使用 BizTalk Server 的商務服務，請參閱[叫用商務服務方法使用 BizTalk Server 和 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)。  
  
-   訊息結構和商務服務上執行作業，請參閱的 SOAP 動作[商務服務作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md))。  
  
## <a name="see-also"></a>另請參閱  
 [連接至 SAP 系統使用配接器](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)