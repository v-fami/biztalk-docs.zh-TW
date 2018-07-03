---
title: 空白的 AS2 訊息已收到並擱置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 349f7134-d039-44ab-b2b3-d378d38dfd38
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48701d24b405f46ad66a76c0ac473fb7343317f2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994127"
---
# <a name="an-empty-as2-message-was-received-and-suspended"></a><span data-ttu-id="c9a4e-102">空白的 AS2 訊息已收到並擱置</span><span class="sxs-lookup"><span data-stu-id="c9a4e-102">An empty AS2 message was received and suspended</span></span>
## <a name="details"></a><span data-ttu-id="c9a4e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c9a4e-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="c9a4e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c9a4e-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="c9a4e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c9a4e-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="c9a4e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c9a4e-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="c9a4e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c9a4e-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c9a4e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c9a4e-108"> EDI</span></span> |
|    <span data-ttu-id="c9a4e-109">元件</span><span class="sxs-lookup"><span data-stu-id="c9a4e-109">Component</span></span>    |                                       <span data-ttu-id="c9a4e-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="c9a4e-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="c9a4e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c9a4e-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="c9a4e-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c9a4e-112">Message Text</span></span>   |           <span data-ttu-id="c9a4e-113">收到空白的 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="c9a4e-113">An empty AS2 message was received.</span></span>  <span data-ttu-id="c9a4e-114">將擱置此訊息。</span><span class="sxs-lookup"><span data-stu-id="c9a4e-114">The message will be suspended.</span></span>           |
  
## <a name="explanation"></a><span data-ttu-id="c9a4e-115">說明</span><span class="sxs-lookup"><span data-stu-id="c9a4e-115">Explanation</span></span>  
 <span data-ttu-id="c9a4e-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法處理內送 AS2 訊息，因為訊息不包含主體。</span><span class="sxs-lookup"><span data-stu-id="c9a4e-116">This Error/Warning/Information event indicates BizTalk Server could not process the incoming AS2 message because the message does not contain a body.</span></span> <span data-ttu-id="c9a4e-117">主體必須隔開兩個歸位字元 return/line 摘要的標頭。</span><span class="sxs-lookup"><span data-stu-id="c9a4e-117">The body must be separated from the headers by two carriage return/line feeds.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c9a4e-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c9a4e-118">User Action</span></span>  
 <span data-ttu-id="c9a4e-119">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c9a4e-119">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="c9a4e-120">請確定傳送合作對象將 AS2 訊息內文 （分隔標頭兩個歸位字元 return/line 摘要），再將它傳送。</span><span class="sxs-lookup"><span data-stu-id="c9a4e-120">Ensure the sending party adds a body (separated from the headers by two carriage return/line feeds) to the AS2 message before sending it.</span></span>