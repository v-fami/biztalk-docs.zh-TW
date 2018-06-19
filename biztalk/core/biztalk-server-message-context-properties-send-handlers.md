---
title: BizTalk Server 訊息內容屬性 （傳送處理常式） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a065ba89-9fdb-47dc-9021-fb95cf347cdc
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0504e13115229f1325938e8ca48acc17fa5bc1d
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013837"
---
# <a name="biztalk-server-message-context-properties-send-handlers"></a>BizTalk Server 訊息內容屬性 （傳送處理常式）
在執行階段，必須可從 BizTalk Server 協調流程存取的，除了有訊息內容以外，還有訊息包含的補充資訊。  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a>已升級為訊息內容屬性的 TIBCO RV 訊息資訊  
  
|資料識別|型別|可路由傳送|傳送位置|  
|-------------------------|----------|--------------|-------------------|  
|傳送主體|string|是|協調流程會 指定 TIBCO Rendezvous 傳送主體 。 預設值是空值。 除非連接埠組態中已指定預設主體，否則為強制性。|  
|回覆主體|string|是|協調流程會 提供用於回覆訊息的相關主體 。 預設值是空值。|  
  
## <a name="getting-a-tibco-reply"></a>取得 TIBCO 回覆  
 **問題：** 如何執行 BizTalk Adapter for TIBCO Rendezvous 讀取及操作的協調流程內的回覆主旨，以便讓使用的傳送主體做為回應？ 配接器如何找到來自 Rendezvous 之內送訊息的訊息內容？  
  
 **回答：** 內送訊息的內容中填入回覆主體及協調流程可以讀取它。 如果協調流程最終會產生回覆，即可使用該值來設定回覆訊息的傳送主體。  
  
1.  在 BizTalk Server 專案中，新增 <install_directory>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll 的參考。  
  
2.  在協調流程中的接收圖形 (內送 Rendezvous 訊息傳入之處) 與傳送圖形 (傳送回覆之處) 之間的某處，新增訊息建構/指派圖形 (或運算式圖形)，以對您所建構的回覆執行如下列範例的作業：  
  
    ```  
    OutgoingMsg(Rendezvous.SendSubject) = IncomingMsg  
    (Rendezvous.ReplySubject);  
    ```  
## <a name="management-assembly"></a>管理組件
TIBCO Rendezvous 未提供中繼資料儲存機制，而 Microsoft BizTalk Adapter for TIBCO Rendezvous 管理組件未提供瀏覽功能或結構描述產生功能。 因此，您必須提供描述結構給 BizTalk Server。 如需詳細資訊，請參閱[安裝、 結構描述，與限制](../core/installing-biztalk-adapter-for-tibco-rendezvous.md)。
  
 BizTalk Adapter for TIBCO Rendezvous 含有一個具有預先定義類型的結構描述。 針對部分特定資料類型 (陣列) 產生訊息時，配接器會使用這些類型。

  
## <a name="see-also"></a>另請參閱  
 [TIBCO Rendezvous 中的傳送處理常式的資料類型對應](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md)   
 [建立 TIBCO Rendezvous 傳送處理常式](../core/creating-tibco-rendezvous-send-handlers.md)