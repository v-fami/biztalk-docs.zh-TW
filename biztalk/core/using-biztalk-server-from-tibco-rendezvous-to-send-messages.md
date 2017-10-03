---
title: "使用 BizTalk Server 從 TIBCO Rendezvous 傳送訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, sending
- sending messages
- BizTalk Server, using from TIBCO Rendezvous
ms.assetid: 72057d42-32b5-4748-81e4-5ffb89630f5a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4556ce5ca90b3c62f779d2df55e78c4506458d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-server-from-tibco-rendezvous-to-send-messages"></a><span data-ttu-id="5d794-102">從 TIBCO Rendezvous 使用 BizTalk Server 傳送訊息</span><span class="sxs-lookup"><span data-stu-id="5d794-102">Using BizTalk Server from TIBCO Rendezvous to Send Messages</span></span>
<span data-ttu-id="5d794-103">Microsoft BizTalk Adapter for TIBCO Rendezvous 使用非同步 API (Transport.Send)。</span><span class="sxs-lookup"><span data-stu-id="5d794-103">Microsoft BizTalk Adapter for TIBCO Rendezvous uses the asynchronous API (Transport.Send).</span></span> <span data-ttu-id="5d794-104">您可以使用訊息內容屬性指定配接器傳送的訊息種類：</span><span class="sxs-lookup"><span data-stu-id="5d794-104">You can specify what kind of message the adapter sends using a message context property:</span></span>  
  
-   <span data-ttu-id="5d794-105">**結構化**: 配接器會產生 TIBRVMSG_MSG 結構化的訊息時，根據從 BizTalk Server 接收的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="5d794-105">**Structured**: The adapter generates a TIBRVMSG_MSG structured message, based on the XML data received from BizTalk Server.</span></span> <span data-ttu-id="5d794-106">(*)</span><span class="sxs-lookup"><span data-stu-id="5d794-106">(*)</span></span>  
  
 <span data-ttu-id="5d794-107">如果 BizTalk Server 傳送的訊息中有欄位名稱超過 127 個字元，BizTalk Adapter for TIBCO Rendezvous 會將名稱截斷至 TIBCO Rendezvous 的欄位名稱大小上限 (即 127)。</span><span class="sxs-lookup"><span data-stu-id="5d794-107">If BizTalk Server sends a message with fields that have names longer than 127 characters, BizTalk Adapter for TIBCO Rendezvous truncates the names to the maximum field name size for TIBCO Rendezvous, which is 127.</span></span>  
  
 <span data-ttu-id="5d794-108">如果提供 `reply subject name` 屬性，會用來設定 TIBCO Rendezvous 訊息的回覆主旨。</span><span class="sxs-lookup"><span data-stu-id="5d794-108">If a `reply subject name` property is provided, it is used to set the reply subject on the TIBCO Rendezvous message.</span></span> <span data-ttu-id="5d794-109">這是假設接收埠設為接聽回覆並將它轉寄至 BizTalk Server，或一些其他的 TIBCO Rendezvous 程式會處理回覆。</span><span class="sxs-lookup"><span data-stu-id="5d794-109">It is assumed that either a receive port is set to listen for the reply and forward it to BizTalk Server, or some other TIBCO Rendezvous program is taking care of the reply.</span></span>  
  
 <span data-ttu-id="5d794-110">服務、精靈與網路這三者構成傳輸組態。</span><span class="sxs-lookup"><span data-stu-id="5d794-110">The triplet (service, daemon, network) makes up the transport configuration.</span></span> <span data-ttu-id="5d794-111">傳輸組態空白 (預設值) 時，則會透過預設的傳輸物件傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="5d794-111">An empty (default) transport configuration results in a message being sent through the default transport object.</span></span>  
  
 <span data-ttu-id="5d794-112">如果未指定字碼頁，配接器會使用 UTF-8 編碼 (字碼頁 65001)。</span><span class="sxs-lookup"><span data-stu-id="5d794-112">If the code page is left unspecified, the adapter uses UTF-8 encoding (code page 65001).</span></span> <span data-ttu-id="5d794-113">傳輸器端不支援認證訊息。</span><span class="sxs-lookup"><span data-stu-id="5d794-113">Certified Messages are not supported on the transmitter side.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d794-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d794-114">See Also</span></span>  
 <span data-ttu-id="5d794-115">[TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="5d794-115">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="5d794-116">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="5d794-116">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)