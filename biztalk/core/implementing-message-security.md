---
title: 實作訊息安全性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 971977a0-b74e-4408-8a07-ad327658f2bc
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae25a8e09b6e9aa8f4b5cef7b6dc5365a601e7de
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001183"
---
# <a name="implementing-message-security"></a><span data-ttu-id="702c1-102">實作訊息安全性</span><span class="sxs-lookup"><span data-stu-id="702c1-102">Implementing Message Security</span></span>
<span data-ttu-id="702c1-103">您可以設定 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境來使用憑證，以傳送及接收簽署和加密的訊息。</span><span class="sxs-lookup"><span data-stu-id="702c1-103">You can configure your Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment to use certificates for sending and receiving signed and encrypted messages.</span></span> <span data-ttu-id="702c1-104">藉由在加密和數位簽章中使用憑證，BizTalk Server 便可以：</span><span class="sxs-lookup"><span data-stu-id="702c1-104">By using certificates for encryption and digital signatures, BizTalk Server can:</span></span>  
  
- <span data-ttu-id="702c1-105">傳送及接收可以信任的資料。</span><span class="sxs-lookup"><span data-stu-id="702c1-105">Send and receive data that can be trusted.</span></span>  
  
- <span data-ttu-id="702c1-106">確認它所處理的資料是安全的。</span><span class="sxs-lookup"><span data-stu-id="702c1-106">Make sure that the data it processes is secure.</span></span>  
  
- <span data-ttu-id="702c1-107">確認授權的合作對象可以收到它的訊息。</span><span class="sxs-lookup"><span data-stu-id="702c1-107">Make sure that authorized parties receive its messages.</span></span>  
  
- <span data-ttu-id="702c1-108">確認它可以從授權的合作對象收到訊息。</span><span class="sxs-lookup"><span data-stu-id="702c1-108">Make sure that it receives messages from authorized parties.</span></span>  
  
  <span data-ttu-id="702c1-109">本章節提供的資訊是關於如何設定 BizTalk Server 管線、接收位置、連接埠和 BizTalk Server 環境來實作訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="702c1-109">This section provides information about how to configure BizTalk Server pipelines, receive locations, ports, and the BizTalk Server environment to implement message security.</span></span>  
  
  <span data-ttu-id="702c1-110">如需訊息安全性的詳細資訊，請參閱[規劃訊息安全性](../core/planning-message-security.md)。</span><span class="sxs-lookup"><span data-stu-id="702c1-110">For more information about message security, see [Planning Message Security](../core/planning-message-security.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="702c1-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="702c1-111">In This Section</span></span>  
  
-   [<span data-ttu-id="702c1-112">傳送和接收加密訊息</span><span class="sxs-lookup"><span data-stu-id="702c1-112">Sending and Receiving Encrypted Messages</span></span>](../core/sending-and-receiving-encrypted-messages.md)  
  
-   [<span data-ttu-id="702c1-113">傳送和接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="702c1-113">Sending and Receiving Signed Messages</span></span>](../core/sending-and-receiving-signed-messages.md)  
  
-   [<span data-ttu-id="702c1-114">使用憑證進行合作對象解析</span><span class="sxs-lookup"><span data-stu-id="702c1-114">Using Certificates for Party Resolution</span></span>](../core/using-certificates-for-party-resolution.md)