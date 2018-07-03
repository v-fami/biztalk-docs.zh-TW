---
title: 處理壓縮的 AS2 訊息時，解壓縮失敗。 | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5246ee97-cc60-4878-9447-de870c0f4c34
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c77bead00b97bf6fa072223485f2d1cc422053b7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001887"
---
# <a name="decompression-failed-while-processing-a-compressed-as2-message"></a><span data-ttu-id="65e14-103">處理壓縮的 AS2 訊息時，解壓縮失敗。</span><span class="sxs-lookup"><span data-stu-id="65e14-103">Decompression failed while processing a compressed AS2 message.</span></span>
## <a name="details"></a><span data-ttu-id="65e14-104">詳細資料</span><span class="sxs-lookup"><span data-stu-id="65e14-104">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="65e14-105">產品名稱</span><span class="sxs-lookup"><span data-stu-id="65e14-105">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="65e14-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="65e14-106">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="65e14-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="65e14-107">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="65e14-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="65e14-108">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="65e14-109"> EDI</span><span class="sxs-lookup"><span data-stu-id="65e14-109"> EDI</span></span> |
|    <span data-ttu-id="65e14-110">元件</span><span class="sxs-lookup"><span data-stu-id="65e14-110">Component</span></span>    |                                       <span data-ttu-id="65e14-111">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="65e14-111">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="65e14-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="65e14-112">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="65e14-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="65e14-113">Message Text</span></span>   |       <span data-ttu-id="65e14-114">處理壓縮的 AS2 訊息時，解壓縮失敗。</span><span class="sxs-lookup"><span data-stu-id="65e14-114">Decompression failed while processing a compressed AS2 message.</span></span> <span data-ttu-id="65e14-115">錯誤： {0}</span><span class="sxs-lookup"><span data-stu-id="65e14-115">Error: {0}</span></span>       |
  
## <a name="explanation"></a><span data-ttu-id="65e14-116">說明</span><span class="sxs-lookup"><span data-stu-id="65e14-116">Explanation</span></span>  
 <span data-ttu-id="65e14-117">這個錯誤/警告/資訊事件表示，接收管線的 AS2 解碼器元件無法解壓縮 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="65e14-117">This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not decompress the AS2 message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="65e14-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="65e14-118">User Action</span></span>  
 <span data-ttu-id="65e14-119">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="65e14-119">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="65e14-120">確認 AS2 訊息中的壓縮包裝函式有效。</span><span class="sxs-lookup"><span data-stu-id="65e14-120">Verify that the compression wrapper in the AS2 message is valid.</span></span>  
  
-   <span data-ttu-id="65e14-121">確認解壓縮已啟用 BizTalk server，藉由驗證，「 訊息應該壓縮 會檢查屬性對象當做 AS2 訊息傳送者頁面的 AS2 屬性 對話方塊中 （是否覆寫輸入訊息屬性會檢查屬性）.</span><span class="sxs-lookup"><span data-stu-id="65e14-121">Verify that decompression is enabled for BizTalk Server by verifying that the "Message should be compressed" property is checked on the Party as AS2 Message Sender page of the AS2 Properties dialog box (if the Override inbound message properties property is checked).</span></span>  
  
-   <span data-ttu-id="65e14-122">您可以使用提供錯誤訊息文字中的錯誤描述來識別特定的問題。</span><span class="sxs-lookup"><span data-stu-id="65e14-122">Use the error description provided in the error message text to identify the specific issue.</span></span>