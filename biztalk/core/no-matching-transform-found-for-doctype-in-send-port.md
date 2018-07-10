---
title: 在 傳送埠 DocType 找不到任何相符的轉換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 23f62ac7-3849-49fe-a765-2be72880a4c9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9668694f5cde2e99775d1392c8722bad0645b251
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966207"
---
# <a name="no-matching-transform-found-for-doctype-in-send-port"></a><span data-ttu-id="52553-102">傳送埠中找到的文件類型不相符的轉換</span><span class="sxs-lookup"><span data-stu-id="52553-102">No matching transform found for DocType in Send Port</span></span>
## <a name="details"></a><span data-ttu-id="52553-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="52553-103">Details</span></span>  
  
|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="52553-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="52553-104">Product Name</span></span>   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| <span data-ttu-id="52553-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="52553-105">Product Version</span></span> |                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    <span data-ttu-id="52553-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="52553-106">Event ID</span></span>     |                                                   -                                                    |
|  <span data-ttu-id="52553-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="52553-107">Event Source</span></span>   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="52553-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="52553-108"> EDI</span></span>         |
|    <span data-ttu-id="52553-109">元件</span><span class="sxs-lookup"><span data-stu-id="52553-109">Component</span></span>    |                                               <span data-ttu-id="52553-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="52553-110">EDI Engine</span></span>                                               |
|  <span data-ttu-id="52553-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="52553-111">Symbolic Name</span></span>  |                             <span data-ttu-id="52553-112">NoMatchingTransformFoundForSendPortAndDocType</span><span class="sxs-lookup"><span data-stu-id="52553-112">NoMatchingTransformFoundForSendPortAndDocType</span></span>                              |
|  <span data-ttu-id="52553-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="52553-113">Message Text</span></span>   | <span data-ttu-id="52553-114">DocType 找不到任何相符的轉換{0}傳送埠中{1}。</span><span class="sxs-lookup"><span data-stu-id="52553-114">No matching transform found for DocType {0} in Send Port {1}.</span></span> <span data-ttu-id="52553-115">與 ExplorerOM 資訊不一致</span><span class="sxs-lookup"><span data-stu-id="52553-115">Inconsistent with ExplorerOM information</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="52553-116">說明</span><span class="sxs-lookup"><span data-stu-id="52553-116">Explanation</span></span>  
 <span data-ttu-id="52553-117">此錯誤表示，相符的轉換找不到指定的文件類型和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="52553-117">This error indicates that a matching transform was not found for a given DocType and SendPort.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="52553-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="52553-118">User Action</span></span>  
 <span data-ttu-id="52553-119">若要解決這個錯誤，請繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="52553-119">To resolve this error, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="52553-120">開啟 BizTalk 管理主控台，找出傳輸，並以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="52553-120">Open the BizTalk Administration console, locate the transport, and right-click the transport name.</span></span>  
  
2.  <span data-ttu-id="52553-121">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="52553-121">Click **Properties**.</span></span>  
  
3.  <span data-ttu-id="52553-122">在 [連接埠類型] 清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="52553-122">In the port Type list, select the correct port.</span></span> <span data-ttu-id="52553-123">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="52553-123">Click **Configure**.</span></span>  
  
4.  <span data-ttu-id="52553-124">在 [連接埠名稱] 傳送埠屬性] 對話方塊中，按一下**輸出對應**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="52553-124">In the [port name] Send Port Properties dialog box, click **Outbound Maps** in the left pane.</span></span>  
  
5.  <span data-ttu-id="52553-125">請確認該對應會列在此處，而且它對應到正確的文件類型。</span><span class="sxs-lookup"><span data-stu-id="52553-125">Verify that the map is listed here and that it corresponds to the correct document type.</span></span>