---
title: 何謂 POP3 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- POP3 adapters, availability
- authenticating, POP3 adapters
- POP3 adapters, data duplication
- data duplication
- POP3 adapters, receive adapters
- high availability, POP3 adapters
- POP3 adapters, supported platforms
- POP3 adapters, authenticating
- POP3 adapters, algorithims
- receive adapters, POP3 adapters
ms.assetid: 05e9598b-cdfe-4216-b6bf-1b84f8ddfeae
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa0f4679cb898f9ce2c4008505bd1ec4a2540dab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974327"
---
# <a name="what-is-the-pop3-adapter"></a>何謂 POP3 配接器？
本節說明 POP3 接收配接器。  
  
## <a name="pop3-receive-adapter"></a>POP3 接收配接器  
 POP3 接收配接器可讓您將資料從啟用 POP3 的信箱移到 BizTalk Server。  
  
 POP3 接收配接器的主要功能包括：  
  
-   依需要從 POP3 伺服器信箱提取檔案。  
  
-   根據可設定的排程執行輪詢。  
  
-   輪詢 POP3 伺服器信箱並直接將資料傳送到 BizTalk Server。  
  
-   將 POP3 伺服器信箱指定為 IP 位址或主控件名稱、連接埠、使用者名稱和密碼。  
  
-   能夠從需要「安全通訊端層」(SSL) 連線的郵件伺服器下載電子郵件。  
  
-   保證傳送檔案。  
  
-   隱含的 MIME 處理。 您不需要使用 POP3 配接器時，接收管線中使用 MIME 解碼器。  
  
## <a name="pop3-adapter-supported-platforms"></a>POP3 配接器支援的平台  
 POP3 配接器的設計是要使用符合以下 RFC 的任何 POP3 伺服器：  
  
- **RFC 1939。** 郵局通訊協定第 3 版 (請參閱[ http://go.microsoft.com/fwlink/?LinkId=58808 ](http://go.microsoft.com/fwlink/?LinkId=58808))  
  
- **RFC 1734。** POP3 驗證命令 (請參閱[ http://go.microsoft.com/fwlink/?LinkId=58809 ](http://go.microsoft.com/fwlink/?LinkId=58809))  
  
- **RFC 2045。** 多用途網際網路郵件延伸標準 (MIME) 第一段： 格式的網際網路訊息內文 (請參閱[ http://go.microsoft.com/fwlink/?LinkId=58810 ](http://go.microsoft.com/fwlink/?LinkId=58810))  
  
- **RFC 2046。** 多用途網際網路郵件延伸標準 (MIME) 第二部分： 媒體類型 (請參閱[ http://go.microsoft.com/fwlink/?LinkId=58811 ](http://go.microsoft.com/fwlink/?LinkId=58811))  
  
- **RFC 2047。** MIME （多用途網際網路郵件延伸標準） 第三部分： 非 ASCII 文字的訊息標頭延伸模組 (請參閱[ http://go.microsoft.com/fwlink/?LinkId=58812 ](http://go.microsoft.com/fwlink/?LinkId=58812))  
  
  POP3 配接器已在 Microsoft Exchange Server 2003 上進行過大規模的測試。  
  
## <a name="considerations-for-preventing-data-duplication-when-using-the-pop3-adapter"></a>使用 POP3 配接器避免資料重複的考量  
 POP3 配接器不是交易式配接器，因此容易處理相同訊息的多個複本，而可能造成資料重複。 在下列實例中，POP3 配接器有可能將傳送訊息的重複複本：  
  
-   在電子郵件成功提交到 BizTalk Server 進行處理後，POP3 配接器一定會從設定為要監控的信箱中刪除電子郵件。 假使 POP3 配接器從信箱擷取電子郵件，提交電子郵件到 BizTalk Server 進行處理，但無法從信箱刪除該電子郵件時，那麼 POP3 配接器下次輪詢信箱時，就會重新提交此電子郵件到 BizTalk Server。  
  
-   若個別 BizTalk 主控件執行個體中的 POP3 配接器之多個執行個體同時監控相同的信箱，且 POP3 伺服器允許多個並行連線到其信箱時，那麼配接器就可能傳送重複的訊息複本。  
  
## <a name="high-availability-for-the-pop3-adapter"></a>POP3 配接器的高可用性  
 有些 POP3 伺服器允許特定信箱可以有多個並行連線。 若設定多個 POP3 配接器執行個體從這類 POP3 伺服器上的信箱擷取郵件，就會發生資料重複的情形。 所以，您應該僅設定一個 POP3 配接器執行個體，以便從允許多個並行連線的信箱擷取郵件。  
  
 若要為此實例中的 POP3 配接器提供容錯功能，應該只設定一個 POP3 配接器接收處理常式在叢集 BizTalk 主控件中執行。 如需詳細資訊，請參閱[在叢集主控件執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。  
  
## <a name="authentication-warnings-when-multiple-instances-of-the-pop3-adapter-connect-to-the-same-mailbox"></a>多個 POP3 配接器執行個體連接到相同信箱時的驗證警告  
 BizTalk Server 可以設定成讓多個 POP3 配接器執行個體從相同信箱擷取郵件。 若是這種情形，BizTalk Server 應用程式記錄中可能會產生驗證警告，因為有些 POP3 伺服器會使用鎖定機制。 在此情形中，這些警告對 POP3 配接器的功能並不會產生影響，因此可以放心略過。  
  
## <a name="encrypted-messages-received-by-the-pop3-adapter-that-are-sent-to-the-suspended-queue-may-be-viewable-in-clear-text"></a>傳送至訊息擱置佇列且由 POP3 配接器接收的加密訊息可以純文字檢視  
 您可以設定 POP3 配接器來解密數位加密的電子郵件。 這是藉由設定**套用 MIME 解碼**屬性設 **，則為 True**的接收位置使用 POP3 配接器。 如果 POP3 配接器收到數位加密的電子郵件並**套用 MIME 解碼**接收位置的屬性設定為 **，則為 True**則 POP3 配接器會嘗試解密電子郵件，如下所示：  
  
- POP3 配接器會搜尋與用來加密電子郵件之公用憑證相符的私用憑證。 私用憑證必須位在伺服器的個人憑證存放區，且此伺服器正在執行 POP3 接收處理常式繫結到的主控件執行個體。  
  
- 如果 POP3 配接器找到對應的私用憑證，便會使用此私用憑證來解密電子郵件訊息。  
  
- 電子郵件會解密並保存到 BizTalk MessageBox。  
  
  如果將訊息解密並保存到 BizTalk MessageBox 後訊息被擱置，將可在 BizTalk 訊息擱置佇列中以純文字檢視訊息的內容。  
  
  如果您必須阻止訊息擱置佇列中的安全訊息文字顯示，請依照下列步驟執行：  
  
- 設定**套用 MIME 解碼**屬性設**False**使用 POP3 配接器接收位置以及具有 SMIME 管線元件的管線中解密訊息。  
  
  > [!NOTE]
  >  此方法將會讓您無法將電子郵件特定的屬性升級為訊息內容。  
  
- 如果您需要將電子郵件特定的屬性升級為訊息內容，並確保當加密的訊息路由至訊息擱置佇列時仍保持加密，請依照下列步驟執行：  
  
  -   核取選項**啟用的路由失敗訊息**包含使用 POP3 配接器的接收位置的接收埠上。  
  
  -   建立協調流程來訂閱無法傳遞到接收埠的訊息，此接收埠包含使用 POP3 配接器的接收位置。  
  
  -   以在管線中使用 SMIME 管線元件加密訊息的傳送埠來設定協調流程。  
  
  -   以擱置圖形設定協調流程，來擱置協調流程執行個體和訊息。  
  
  -   建立和部署協調流程，將部署的協調流程繫結到適當的接收埠。  
  
## <a name="maximum-message-size-supported-by-the-pop3-adapter"></a>POP3 配接器支援的最大訊息大小  
 POP3 配接器經過測試，且可支援接收最高達 50 MB 的訊息容量。  
  
## <a name="see-also"></a>另請參閱  
 [POP3 配接器](../core/pop3-adapter.md)