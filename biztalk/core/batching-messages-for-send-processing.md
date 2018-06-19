---
title: 批次處理的訊息傳送處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d9115ec-13bc-41a8-8928-57b168c95af4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e87600bec54679688fae5084af3b4a1bde9ca807
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232454"
---
# <a name="batching-messages-for-send-processing"></a>批次處理傳送訊息
## <a name="send-adapter-batch-management"></a>傳送配接器批次管理  
 在傳送端使用交易時，由 BizTalk Server 建立用來傳送至目標系統的相同交易，會在成功傳送時用於刪除對應的訊息。 如果發生失敗，則會結束交易 (在此情況下會中止刪除訊息)，並且資料是保留在 BizTalk Server 而非目標系統。 這可防止訊息重複的情形。 只有非同步傳送配接器才支援交易， 您不應搭配同步傳送配接器使用交易。  
  
 配接器不僅要結束交易，也必須正確處理所接收訊息的狀態。 具體來說，配接器應該呼叫方法**重新提交**， **MoveToNextTransport**，和**MoveToSuspendQ**根據重試計數以及是否使用備份傳輸。  
  
 請務必將**刪除**和**SubmitResponse**一起放在使用相同交易的批次作業。 失敗的處理方式是結束交易 (確定只提交一次資料給外部系統)。 但您仍然想要重新提交或呼叫**MoveToNextTransport**回 BizTalk Server 上的訊息。 若要執行此動作，請針對這些類型的作業使用個別的一般 (非交易式) 批次。  
  
 下圖顯示針對回應訊息使用個別批次。  
  
 ![回應訊息使用個別的批次](../core/media/eawp-seperatebatch.gif "EAWP_SeperateBatch")  
  
## <a name="sorting-the-send-side-transactional-batches-by-endpoint"></a>依端點來排序傳送端交易批次  
 由 BizTalk Server 傳送至配接器的訊息批次可以跨越多個傳送埠 (或端點)。 配接器通常會想要的單一端點進行交易，因為配接器必須排序依據傳送埠的訊息 (**SPName**或**OutboundTransportLocation**)。 透過這個方式，配接器可以建立只跨越一個特定傳送埠的交易。  
  
 例如，當 FTP 傳送配接器從 BizTalk Server 接收一批訊息時，它取得的是一批混合訊息，其中包含目前所有作用中 FTP 傳送埠的訊息。 這是因為 API 是以單一項目為單位，這表示只會載入一個 FTP 配接器，而不是每個傳送埠各載入一個 FTP 配接器。  
  
 配接器必須先將 BizTalk Server 提供的該批訊息排序為個別批次，每個端點一個批次。 接著輪流處理每個端點，而且可能針對每個端點建構刪除批次。 SDK 範例程式碼中的 BaseAdapter 可重複使用泛型類別就是以相同方式運作。  
  
## <a name="sorting-for-dynamic-send"></a>動態傳送的排序  
 只要訊息標頭和 URL 本身提供充分的組態詳細資料，BizTalk Server 協調流程就會將訊息傳送至未設定的連接埠。 BizTalk Server 必須識別 URL 的通訊協定。  
  
 排序訊息時，您應謹慎建立端點的定義。 尤其在動態傳送時，更是如此。 如果只有 URI 定義端點，情況便很簡單。 但在 FTP 工作階段中，FTP 伺服器可能會使用使用者名稱登入詳細資料，來定義真正的端點。 在此情況下，如果配接器登入為不同帳戶，便可能會連接到不同目錄。  
  
 在某些情況下，真正的端點不知道您的企業單一登入 (SSO) 命令執行之前**ValidateAndRedeemTicket**。  
  
 在 MQSeries 的情況中，判斷是否要使用交易是可設定的。 有鑑於架構和遠端 COM+ 物件的使用，最好將交易式端點和非交易式端點視為不同。  
  
 總而言之，有時將訊息排序為單一端點的批次是項重要工作，而且可能牽涉到額外的步驟，例如考慮內容值，甚至還要考慮 SSO 呼叫後的結果。  
  
## <a name="sorting-for-static-send"></a>靜態傳送的排序  
 如果是靜態設定的端點，訊息內容有唯一的 GUID，稱為靜態連接埠識別碼 (SPID)。 此值可用於排序端點。 下列程式碼可用來擷取它：  
  
```  
string spid = (string)message.Context.Read("SPID", "http://schemas.microsoft.com/BizTalk/2003/system-properties");  
```  
  
 當您正視以「XML 結構描述定義」(XSD) 為基礎的組態架構引入的問題時，這將有所幫助。 在這個架構中，屬性可能是埋在單一內容屬性之 XML 中端點索引鍵的一部分。 如果您的內容有 SPID，可用它來排序批次。 否則，您執行的就是動態傳送，並且必須建構替代索引鍵，用它來排序批次。  
  
 下圖顯示依端點的訊息排序。  
  
 ![端點所排序的訊息](../core/media/eawp-sortbatch.gif "EAWP_SortBatch")  
  
 請記住，訊息的重試計數不知道批次是成功還是失敗。 在傳送端，訊息批次可能因為批次中的少數訊息失敗而造成失敗。 配接器必須判斷它所接收每個訊息的狀態。 在失敗批次的案例中，您可能假設每個訊息都要重新提交。 不過，如果重新提交失敗批次中的所有訊息，因為成功訊息和失敗訊息在相同批次中，即使針對成功訊息，重試計數 (由 BizTalk Server 引擎維護) 都會不正確地遞增。 在此情況下，配接器可能會重新形成輸出批次，並且對外部系統重試成功訊息。