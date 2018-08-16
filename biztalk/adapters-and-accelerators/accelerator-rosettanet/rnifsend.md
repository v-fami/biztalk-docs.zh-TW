---
title: RNIFSend |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 780f7446-56c5-40bf-95e2-25d0cff12f12
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d9aca64afee9ed979b2eee58a5f2bdafb25b461
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011599"
---
# <a name="rnifsend"></a><span data-ttu-id="3ef08-102">RNIFSend</span><span class="sxs-lookup"><span data-stu-id="3ef08-102">RNIFSend</span></span>
<span data-ttu-id="3ef08-103">此範例提供了有效 Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFSend.aspx 檔案，準備一個訊息供 RNIF 處理，並將訊息傳送至回應者的 RNIFReceive.aspx 頁面。</span><span class="sxs-lookup"><span data-stu-id="3ef08-103">This sample provides a working Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFSend.aspx file that prepares a message for RNIF processing, and sends the message to the RNIFReceive.aspx page at the responder.</span></span> <span data-ttu-id="3ef08-104">您可以自訂 ASPX 頁面來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3ef08-104">You can customize the ASPX page to do the following:</span></span>  
  
- <span data-ttu-id="3ef08-105">新增或移除效能計數器</span><span class="sxs-lookup"><span data-stu-id="3ef08-105">Add or remove performance counters</span></span>  
  
- <span data-ttu-id="3ef08-106">新增頁面的功能，例如將資料寫入資料庫或自訂追蹤功能</span><span class="sxs-lookup"><span data-stu-id="3ef08-106">Add functionality to the page, such as writing data to a database or customizing tracking functionality</span></span>  
  
- <span data-ttu-id="3ef08-107">新增驗證到頁面</span><span class="sxs-lookup"><span data-stu-id="3ef08-107">Add validation to the page</span></span>  
  
  <span data-ttu-id="3ef08-108">此範例位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\webapplication\rnifsender。</span><span class="sxs-lookup"><span data-stu-id="3ef08-108">This sample is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\WebApplication\RNIFSender.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3ef08-109">示範</span><span class="sxs-lookup"><span data-stu-id="3ef08-109">Demonstrates</span></span>  
 <span data-ttu-id="3ef08-110">這個範例示範如何製造外寄訊息讓 RNIF 進行處理，其中包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3ef08-110">This sample demonstrates how to prepare outgoing messages for RNIF processing, including the following:</span></span>  
  
-   <span data-ttu-id="3ef08-111">驗證 MIME 標頭資料</span><span class="sxs-lookup"><span data-stu-id="3ef08-111">Validating the data for the MIME header</span></span>  
  
-   <span data-ttu-id="3ef08-112">將 MIME 標頭和 MIME 範圍加入訊息</span><span class="sxs-lookup"><span data-stu-id="3ef08-112">Adding a MIME header and MIME boundaries to the message</span></span>  
  
-   <span data-ttu-id="3ef08-113">將訊息傳送至交易夥伴的 RNIFReceive.aspx 頁面</span><span class="sxs-lookup"><span data-stu-id="3ef08-113">Sending the message to the partner's RNIFReceive.aspx</span></span>  
  
-   <span data-ttu-id="3ef08-114">處理傳回的信號訊息</span><span class="sxs-lookup"><span data-stu-id="3ef08-114">Processing a returned signal message</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef08-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ef08-115">See Also</span></span>  
 <span data-ttu-id="3ef08-116">[傳送和接收 ASPX 頁面](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md) </span><span class="sxs-lookup"><span data-stu-id="3ef08-116">[Send and Receive ASPX Pages](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md) </span></span>  
 [<span data-ttu-id="3ef08-117">Web 應用程式範例</span><span class="sxs-lookup"><span data-stu-id="3ef08-117">Web Application Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)