---
title: RNIFReceive |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf1253b0-ceca-4e7a-91ed-3837bd904472
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d54b66c42fae286ec748ef560c461a22124165b0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991767"
---
# <a name="rnifreceive"></a><span data-ttu-id="45d73-102">RNIFReceive</span><span class="sxs-lookup"><span data-stu-id="45d73-102">RNIFReceive</span></span>
<span data-ttu-id="45d73-103">此範例提供了有效 Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFReceive.aspx 檔案接收 RNIF 訊息，並準備好進行處理[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]公開程序。</span><span class="sxs-lookup"><span data-stu-id="45d73-103">This sample provides a working Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFReceive.aspx file that receives an RNIF message, and prepares it for processing by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] public process.</span></span> <span data-ttu-id="45d73-104">您可以自訂 ASPX 頁面來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="45d73-104">You can customize the ASPX page to do the following:</span></span>  
  
- <span data-ttu-id="45d73-105">新增或移除效能計數器</span><span class="sxs-lookup"><span data-stu-id="45d73-105">Add or remove performance counters</span></span>  
  
- <span data-ttu-id="45d73-106">新增頁面的功能，例如將資料寫入資料庫或自訂追蹤功能</span><span class="sxs-lookup"><span data-stu-id="45d73-106">Add functionality to the page, such as writing data to a database or customizing tracking functionality</span></span>  
  
- <span data-ttu-id="45d73-107">新增驗證到頁面</span><span class="sxs-lookup"><span data-stu-id="45d73-107">Add validation to the page</span></span>  
  
  <span data-ttu-id="45d73-108">此範例位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>RosettaNet\SDK\WebApplication\RNIFReceiver 的加速器。</span><span class="sxs-lookup"><span data-stu-id="45d73-108">This sample is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\WebApplication\RNIFReceiver.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="45d73-109">示範</span><span class="sxs-lookup"><span data-stu-id="45d73-109">Demonstrates</span></span>  
 <span data-ttu-id="45d73-110">本範例示範如何準備內送訊息以供公開程序使用，包括下列動作：</span><span class="sxs-lookup"><span data-stu-id="45d73-110">This sample demonstrates how to prepare incoming messages for the public process, including the following:</span></span>  
  
-   <span data-ttu-id="45d73-111">從交易夥伴的 RNIFSend.aspx 接收訊息</span><span class="sxs-lookup"><span data-stu-id="45d73-111">Receiving the message from the partner's RNIFSend.aspx</span></span>  
  
-   <span data-ttu-id="45d73-112">驗證 MIME 標題</span><span class="sxs-lookup"><span data-stu-id="45d73-112">Validating the MIME header</span></span>  
  
-   <span data-ttu-id="45d73-113">從訊息中移除 MIME 標題和界限</span><span class="sxs-lookup"><span data-stu-id="45d73-113">Removing the MIME header and boundaries from the message</span></span>  
  
-   <span data-ttu-id="45d73-114">將訊息路由到交易夥伴的 RNIFReceive.aspx</span><span class="sxs-lookup"><span data-stu-id="45d73-114">Routing the message to the partner's RNIFReceive.aspx</span></span>  
  
-   <span data-ttu-id="45d73-115">回傳信號訊息</span><span class="sxs-lookup"><span data-stu-id="45d73-115">Returning a signal message</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d73-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45d73-116">See Also</span></span>  
 <span data-ttu-id="45d73-117">[傳送和接收 ASPX 頁面](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md) </span><span class="sxs-lookup"><span data-stu-id="45d73-117">[Send and Receive ASPX Pages](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md) </span></span>  
 [<span data-ttu-id="45d73-118">Web 應用程式範例</span><span class="sxs-lookup"><span data-stu-id="45d73-118">Web Application Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)