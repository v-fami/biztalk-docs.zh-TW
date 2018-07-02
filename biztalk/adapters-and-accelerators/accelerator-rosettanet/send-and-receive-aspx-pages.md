---
title: 傳送和接收 ASPX 頁面 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BTARN, ASPX pages
- ASPX pages, initiator
- HTTP adapters
- connections, HTTP adapters
- connections, single-action
- ASPX pages, responder
- single-action connections
- RNIFSend.aspx
- connections, asynchronous
- ASPX pages, about ASPX pages
- double-action connections
- connections, synchronous
- connections, double-action
- ASPX pages
- HTTP adapters, connections
- asynchronous connections
- RNIFReceive.aspx
- synchronous connections
ms.assetid: 21e52390-35d8-44b1-a5cd-1cd60cfe6e61
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e688686e8bd787e22d7e5a246e0cce62f469649c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982047"
---
# <a name="send-and-receive-aspx-pages"></a>傳送和接收 ASPX 頁面
Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] ASPX 頁面是之間的直接介面[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]和網際網路。 ASPX 頁面有兩種，分別是接收頁面 (RNIFReceive.aspx) 和傳送頁面 (RNIFSend.aspx)。 每個 ASPX 頁面都是對應的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管線的延伸。 管線需要 ASPX 頁面才能處理 RosettaNet 實作架構 (RNIF) 標頭。 管線執行大多數的 HTTP 處理，然而，每個 ASPX 頁面執行 RNIF 標頭的 HTTP 處理。 頁面能夠擴大 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] HTTP 配接器的功能。  
  
 每個 ASPX 頁面都是 ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web 應用程式，但不具有使用者介面。 這些頁面使用 ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web 安全性以確保與外部合作對象建立安全連線。 您可以在所提供的階層中實作容錯、延展性以及高可用性的服務。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 安裝程式會在每個 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 部署中安裝 RNIFSend.aspx 頁面和 RNIFReceive.aspx 頁面。 當啟動者或是回應者與交易夥伴交換訊息時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會使用 ASPX 頁面傳送或接收來自交易夥伴 URL 的訊息。 如果啟動者和回應者都使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，則啟動者的兩個 ASPX 頁面就會與回應者的兩個 ASPX 頁面交換訊息。 如需詳細資訊，請參閱下列的＜啟動者端和回應者端 ASPX 頁面的互動方式＞一節。  
  
## <a name="send-aspx-page"></a>ASPX 傳送頁面  
 RNIFSend.aspx 頁面會接收來自 BizTalk HTTP 配接器的訊息， 建立 RNIF 標頭並新增至訊息中，然後透過網際網路傳送訊息給交易夥伴。 HTTP 配接器使用下列命令呼叫 RNIFSend.aspx：  
  
```  
http://localhost:<port number>/RNIFSend.aspx?<query string>  
```  
  
 查詢字串包括了傳送頁面將訊息傳送給交易夥伴時所需的下列資料，以及交易夥伴處理訊息時所需具備的資料：  
  
- 交易夥伴 URL: http://www.\<*地址*\>.com/RNIFReceive.aspx  
  
- 回應類型： sync 或 async  
  
- RNIF 版本： 1.1 或 2.0。  
  
  BizTalk HTTP 配接器會將 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送管線所產生的 MIME 訊息傳送至啟動者的 RNIFSend.aspx 頁面。 RNIFSend.aspx 會依照下列方式處理訊息：  
  
1.  傳送頁面執行訊息的驗證。  
  
2.  傳送頁面根據內容類型、長度、識別碼以及 MIME 版本，建立多用途網際網路郵件延伸標準 (MIME) 標頭。 它會將 MIME 標頭及 MIME 上下界限新增至訊息中。  
  
3.  對於 RNIF 2.01，傳送頁面會依照下列方式設定 HTTP 標頭的屬性：  
  
    1.  將 X-RN-Version 屬性設為在程序組態設定的 Version 屬性中輸入的版本。  
  
    2.  將 X-RN-ResponseType 屬性設為 sync (同步) 或 async (非同步)，視程序組態設定中 IsSynchronous 屬性的設定而定。  
  
    3.  將 Content-Length 屬性設為完整訊息的大小。  
  
4.  傳送頁面根據交易夥伴協議中的「動作 URL」或「信號 URL」設定，使用 HTTP Post 傳送訊息到交易夥伴的目的地 URL。  
  
5.  傳送頁面等候 HTTP 回應。 一旦收到回應，便將回應傳送至 HTTP 配接器。  
  
6.  如果連線是非同步，傳送頁面會關閉連線，並且它的處理隨即完成。  
  
7.  如果連線是同步，傳送頁面會保持連線開啟以取得回傳訊息。 在收到訊息之後，傳送頁面會如同 RNIFReceive.aspx 頁面處理所接收訊息的方式處理訊息，並傳送接收的訊息至 HTTP 配接器，然後關閉連線。  
  
## <a name="receive-aspx-page"></a>ASPX 接收頁面  
 RNIFReceive.aspx 頁面透過網際網路接收來自交易夥伴的 HTTP 訊息。 它會處理、驗證然後移除 RNIF 標頭，再將訊息提交至 HTTP 配接器。 接收頁面所接收的訊息必須符合 RNIF HTTP 傳輸格式。 接收頁面會依照下列方式處理訊息：  
  
1.  回應者的 RNIFReceive.aspx 頁面接收來自啟動者的訊息。 訊息包含 MIME 標頭以及上下界限。  
  
2.  接收頁面驗證 MIME 標頭。  
  
3.  接收頁面從訊息中移除 MIME 標頭及界限。  
  
4.  接收頁面使用 HTTP 接收位置張貼訊息至 HTTP 配接器。 接收頁面接收 HTTP 回應，然後回傳 HTTP 回應至啟動者的傳送頁面。  
  
5.  如果連線是非同步的，接收頁面會關閉連線。  
  
6.  如果連線是同步的，接收頁面會保持連線開啟，等待回傳的訊息。  
  
7.  在收到 HTTP 配接器回傳的訊息之後，接收頁面處理訊息的方式將如同 RNIFSend.aspx 頁面，並傳送回傳的訊息至啟動者的傳送頁面。 一旦收到 HTTP 回應之後，隨即關閉連線。  
  
## <a name="how-initiator-and-responder-aspx-pages-interact"></a>啟動者端和回應者端 ASPX 頁面的互動方式  
 如果啟動者和回應者都使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，啟動者端和回應者端的四個 ASPX 頁面會根據連線是同步或非同步、訊息是單向動作或雙向動作而採用不同的方式進行互動。 下列各節詳細描述完整的互動方式。  
  
 **雙向動作非同步**  
  
 此實例牽涉四個不同的 HTTP 連線，每個步驟說明一個連線：  
  
1. 啟動者傳送頁面傳送動作要求訊息給回應者接收頁面。  
  
   > [!NOTE]
   >  下列的步驟 2 和 3 可能需要以相反的順序執行，視系統的負載程度而定。  
  
2. 回應者傳送頁面傳送要求信號訊息給啟動者接收頁面。  
  
3. 回應者傳送頁面傳送動作回應訊息給啟動者接收頁面。  
  
4. 啟動者傳送頁面傳送回應信號訊息給回應者接收頁面。  
  
   **單向動作非同步**  
  
   此實例牽涉兩個不同的 HTTP 連線，每個步驟說明一個連線。 請注意，此實例是由雙向動作非同步實例的步驟 1 和 2 組成。  
  
5. 啟動者傳送頁面傳送動作要求訊息給回應者接收頁面。  
  
6. 回應者傳送頁面傳送要求信號訊息給啟動者接收頁面。  
  
   **雙向動作同步**  
  
   此實例牽涉一個 HTTP 連線：  
  
7. 啟動者傳送頁面傳送動作要求訊息給回應者接收頁面。  
  
8. 回應者接收頁面透過步驟 1 所使用的相同連線傳送動作回應訊息 (如果有問題的話，會傳送例外狀況) 至啟動者傳送頁面。  
  
   **單向動作同步**  
  
   此實例牽涉一個 HTTP 連線：  
  
9. 啟動者傳送頁面傳送動作要求訊息給回應者接收頁面。  
  
10. 回應者接收頁面透過相同連線傳送要求信號訊息 (如果有問題的話，會傳送例外狀況) 至啟動者傳送頁面。  
  
## <a name="see-also"></a>另請參閱  
 [BTARN 中的訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)   
 [BTARN 接收管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)   
 [BTARN 傳送管線](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)