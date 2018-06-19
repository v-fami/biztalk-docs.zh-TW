---
title: AS2 處理的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 941111d8-b394-4648-a675-e4a8f118a84b
caps.latest.revision: 40
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61ce04c572c95a1a4e2433d6b046028468eca805
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009391"
---
# <a name="known-issues-with-as2-processing"></a>AS2 處理的已知問題
本節中的主題描述 BizTalk Server AS2 解決方案的已知的問題。  
  
## <a name="as2-processing-not-supported-on-64-bit-computers"></a>64 位元電腦不支援 AS2 處理  
 BizTalk Server AS2 解決方案不支援在 64 位元電腦上。 AS2 處理只能在 32 位元電腦或 64 位元電腦的 WOW64 模擬器下運作。  
  
## <a name="the-as2-receive-pipelines-require-the-account-that-the-biztalk-isolated-host-instance-process-is-running-under-to-be-part-of-the-biztalk-application-users-group"></a>AS2 接收管線需要執行 BizTalk 外掛式主控件執行個體處理序的帳戶，屬於 BizTalk 應用程式使用者群組的成員  
 使用 AS2EdiReceive 或 AS2Receive 管線時，您必須將用來執行 BizTalk 外掛式主控件執行個體處理序的使用者帳戶，新增至 BizTalk 應用程式使用者群組。 AS2EdiReceive 和 AS2Receive 管線會在 BizTalk 外掛式主控件執行個體處理序中執行。  
  
## <a name="an-empty-receipt-delivery-option-header-will-cause-an-mdn-to-be-sent-synchronously"></a>空的 Receipt-Delivery-Option 標頭會導致以同步方式傳送 MDN  
 若 AS2Receive 管線所收到訊息之 receipt-delivery-option 標頭是空的，且收到非同步 MSN 要求，則管線會略過非同步 MSN 要求。 該管線反而會傳回同步 MDN，並在事件日誌和 AS2 狀態報告 (若已啟用) 公佈錯誤。 若未選取 [覆寫輸入訊息屬性] 屬性，就會發生這個情形。 若已選取該屬性，就會以 [AS2 屬性] 對話方塊之 [做為 AS2 訊息傳送者的合作對象] 頁面中的 Receipt-Delivery-Option 屬性值，覆寫訊息中的 Receipt-Delivery-Option 標頭。  
  
 在這個例子中，由於 receipt-delivery-option 標頭是空的，因此 AS2Receive 管線沒有可以透過非同步連線傳送 MDN 回應的位址。 然而該管線仍具有開啟的同步連線，因此會透過該連線傳回 MDN。 若為單向接收埠，BizTalk Server 傳送 HTTP 200OK 訊息後隨即會關閉連線。  
  
## <a name="use-of-unfolded-and-folded-http-line-headers"></a>使用展開和摺疊的 HTTP 行標頭  
 為求達到最大的互通性，AS2 訊息應該使用展開的 HTTP 行標頭。 資訊服務 (IIS) 7.0 支援只有展開的 HTTP 標頭。 IIS 6.0 支援摺疊與展開的標頭。 然而，並不是所有系統都可以支援每行 80 個字元以上的標頭，針對這類系統，應該使用摺疊的標頭。  
  
 AS2 在 BizTalk Server 中的預設值是展開的 HTTP 行標頭。  
  
## <a name="party-resolution-can-be-affected-by-a-localized-name"></a>合作對象解析可能受當地語系化名稱影響  
 BizTalk Server 在輸出的 AS2 訊息執行合作對象解析時，合作對象解析可能受訊息標頭中之當地語系化值的影響。 若 [AS2 屬性] 對話方塊之 [做為 AS2 訊息接收者的合作對象] 頁面中的 AS2-To 合作對象屬性預設為英文的合作對象名稱，而 AS2 訊息 AS2-To 標頭內的值設定為非英文名稱，則會找不到對應。  
  
## <a name="as2-message-size-limitation"></a>AS2 訊息大小限制  
 加密的 AS2 訊息應該小於 96 MB 才能處理。 這個限制是 AS2 解碼器所給予的，它屬於 AS2Receive 和 AS2EdiReceive 管線的一部分。  
  
 解決此大小限制的一種方法就是使用壓縮，因為 AS2 訊息會先壓縮再加密。  
  
## <a name="biztalk-edi-application-must-not-be-modified"></a>不得修改 BizTalk EDI 應用程式  
 不得修改或刪除 BizTalk EDI 應用程式內的成品。 應用程式一經修改就無法還原，取消設定和重新設定 EDI 與 AS2 的功能也不行。  
  
## <a name="partner-may-reject-multipart-messages"></a>協力廠商可能會拒絕多部分訊息  
 **徵兆**  
  
 將傳送多部分訊息使用 AS2 傳送管線時，您的合作夥伴可以拒絕的訊息，因為遺漏的 Content-type MIME 標頭。  
  
 **可能的原因**  
  
 內容類型是可以針對每個主體組件的多部分訊息中出現的選擇性標頭。 有些合作夥伴要求，此標頭會顯示每個內文部分、 集合，為特定的內容類型。  
  
> [!NOTE]
>  訊息的本文會有設定透過 AS2 傳送管線中，內容類型的屬性，然而任何附件不會將內容類型屬性設定。  
  
 **解決方式**  
  
 如果您的夥伴需要每個內文部分內容類型標頭值，您必須建立自訂管線元件會設定這個屬性，並使用的傳送管線中的元件。  
  
## <a name="when-receiving-multipart-messages-the-first-part-is-considered-the-body"></a>當接收多部分訊息，第一個部分會被視為主體  
 **徵兆**  
  
 當接收多組件的 AS2 訊息、[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能不正確會識別附件的其中一個做為訊息主體。  
  
 **可能的原因**  
  
 訊息 multipart/related 的 MIME 標頭可能包含一個選擇性指出哪些組件的 'start' 參數應視為訊息的本文藉由指定組件的內容識別碼。 如果 start 參數不存在，第一個部分應該視為訊息的本文。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]如果它存在，並且會一律將視為訊息本文的第一個部分，不接受啟動參數。  
  
 **解決方式**  
  
 如果您的夥伴無法做為第一個部分 multipart/related 訊息的傳送主體時，您必須建立的管線元件，以正確識別訊息的本文。  
  
## <a name="see-also"></a>請參閱  
 [疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md)   
 [AS2 方案架構](../core/as2-solution-architecture.md)   
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)