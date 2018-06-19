---
title: HTTP 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP adapters, receive adapters
- HTTP adapters, send adapters
- HTTP adapters
- receive adapters, HTTP adapters
- send adapters, HTTP adapters
- HTTP adapters, about HTTP adapters
ms.assetid: a9423052-8392-4006-ab46-79834169c796
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d9be9fac6fdb65c4516c671b6c0e30096e83a27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256046"
---
# <a name="http-adapter"></a><span data-ttu-id="acb48-102">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="acb48-102">HTTP Adapter</span></span>
<span data-ttu-id="acb48-103">您使用 HTTP 配接器在 Microsoft BizTalk Server 與使用 HTTP 通訊協定的應用程式之間交換資訊。</span><span class="sxs-lookup"><span data-stu-id="acb48-103">You use the HTTP adapter to exchange information between Microsoft BizTalk Server and an application by means of the HTTP protocol.</span></span> <span data-ttu-id="acb48-104">HTTP 是內部商務訊息交換的主要通訊協定。</span><span class="sxs-lookup"><span data-stu-id="acb48-104">HTTP is the primary protocol for interbusiness message exchange.</span></span> <span data-ttu-id="acb48-105">應用程式可以藉由傳送 HTTP POST 或 HTTP GET 要求到指定的 HTTP URL 來傳送訊息到伺服器。</span><span class="sxs-lookup"><span data-stu-id="acb48-105">Applications can send messages to a server by sending HTTP POST or HTTP GET requests to a specified HTTP URL.</span></span> <span data-ttu-id="acb48-106">HTTP 配接器接收 HTTP 要求，然後提交到 BizTalk Server 進行處理。</span><span class="sxs-lookup"><span data-stu-id="acb48-106">The HTTP adapter receives the HTTP requests and submits them to BizTalk Server for processing.</span></span> <span data-ttu-id="acb48-107">同樣地，BizTalk Server 可以藉由傳送 HTTP POST 要求到指定的 HTTP URL 來傳輸訊息到遠端應用程式。</span><span class="sxs-lookup"><span data-stu-id="acb48-107">Similarly, BizTalk Server can transmit messages to remote applications by sending HTTP POST requests to a specified HTTP URL.</span></span>  
  
 <span data-ttu-id="acb48-108">HTTP 配接器是由兩個配接器所組成—接收配接器和傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="acb48-108">The HTTP adapter consists of two adapters—a receive adapter and a send adapter.</span></span> <span data-ttu-id="acb48-109">HTTP 接收配接器是 IIS 程序裝載的 Microsoft Internet Information Services (IIS) Internet Server Application Programming Interface (ISAPI) 延伸模組，控制使用 HTTP 配接器的接收位置。</span><span class="sxs-lookup"><span data-stu-id="acb48-109">The HTTP receive adapter is a Microsoft Internet Information Services (IIS) Internet Server Application Programming Interface (ISAPI) extension that the IIS process hosts, and controls the receive locations that use the HTTP adapter.</span></span> <span data-ttu-id="acb48-110">HTTP 傳送配接器控制使用 HTTP 配接器的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="acb48-110">The HTTP send adapter controls the send ports that use the HTTP adapter.</span></span>  
  
 <span data-ttu-id="acb48-111">本節討論 HTTP 接收配接器與 HTTP 傳送配接器兩者的工作流程與批次支援。</span><span class="sxs-lookup"><span data-stu-id="acb48-111">This section discusses the workflow and batching support for both the HTTP receive adapter and the HTTP send adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="acb48-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="acb48-112">In This Section</span></span>  
  
-   [<span data-ttu-id="acb48-113">HTTP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="acb48-113">HTTP Receive Adapter</span></span>](../core/http-receive-adapter.md)  
  
-   [<span data-ttu-id="acb48-114">HTTP 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="acb48-114">HTTP Send Adapter</span></span>](../core/http-send-adapter.md)  
  
-   [<span data-ttu-id="acb48-115">設定 HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="acb48-115">Configuring the HTTP Adapter</span></span>](../core/configuring-the-http-adapter.md)  
  
-   [<span data-ttu-id="acb48-116">HTTP 配接器安全性建議</span><span class="sxs-lookup"><span data-stu-id="acb48-116">HTTP Adapter Security Recommendations</span></span>](../core/http-adapter-security-recommendations.md)