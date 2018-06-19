---
title: 交換 XML 訊息的序列化期間遇到的錯誤結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 97939bfd-d1ee-455a-9952-4f25db020e7c
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44b56cce9fdd3704f7e6ddc2ba5b5bebb62d36e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278590"
---
# <a name="structural-error-encountered-during-serialization-of-an-interchange-xml-message"></a><span data-ttu-id="f287d-102">結構化交換 XML 訊息的序列化期間遇到的錯誤</span><span class="sxs-lookup"><span data-stu-id="f287d-102">Structural error encountered during serialization of an interchange XML message</span></span>
## <a name="details"></a><span data-ttu-id="f287d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f287d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f287d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f287d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f287d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f287d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f287d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f287d-106">Event ID</span></span>|-|  
|<span data-ttu-id="f287d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f287d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f287d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="f287d-108"> EDI</span></span>|  
|<span data-ttu-id="f287d-109">元件</span><span class="sxs-lookup"><span data-stu-id="f287d-109">Component</span></span>|<span data-ttu-id="f287d-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="f287d-110">EDI Engine</span></span>|  
|<span data-ttu-id="f287d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f287d-111">Symbolic Name</span></span>|<span data-ttu-id="f287d-112">InvalidXmlNodeFound</span><span class="sxs-lookup"><span data-stu-id="f287d-112">InvalidXmlNodeFound</span></span>|  
|<span data-ttu-id="f287d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f287d-113">Message Text</span></span>|<span data-ttu-id="f287d-114">結構化交換 Xml 訊息的序列化期間遇到的錯誤</span><span class="sxs-lookup"><span data-stu-id="f287d-114">Structural error encountered during serialization of an Interchange Xml message</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f287d-115">說明</span><span class="sxs-lookup"><span data-stu-id="f287d-115">Explanation</span></span>  
 <span data-ttu-id="f287d-116">此錯誤表示交換 XML 訊息的序列化期間遇到到結構的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f287d-116">This error indicates that a structural error was encountered during serialization of an interchange XML message.</span></span> <span data-ttu-id="f287d-117">BTS 找出 XML StartElement 或 EndElement，但改為遇到不同的 XML 節點類型。</span><span class="sxs-lookup"><span data-stu-id="f287d-117">BTS was looking for an XML StartElement or EndElement but instead a different XML node type was encountered.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f287d-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f287d-118">User Action</span></span>  
 <span data-ttu-id="f287d-119">若要解決這個錯誤，請確定訊息結構正確，並再試一次：</span><span class="sxs-lookup"><span data-stu-id="f287d-119">To resolve this error, make sure the message structure is correct, and try again:</span></span>  
  
1.  <span data-ttu-id="f287d-120">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="f287d-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="f287d-121">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後按一下**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="f287d-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and click **BizTalk Group**.</span></span>  
  
3.  <span data-ttu-id="f287d-122">在右窗格中，按一下 [**群組中樞**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f287d-122">In the right pane, click the **Group Hub** tab.</span></span>  
  
4.  <span data-ttu-id="f287d-123">按一下**擱置服務執行個體**。</span><span class="sxs-lookup"><span data-stu-id="f287d-123">Click **Suspended Service instances**.</span></span>  
  
5.  <span data-ttu-id="f287d-124">按兩下的訊息。</span><span class="sxs-lookup"><span data-stu-id="f287d-124">Double-click the message.</span></span>  
  
6.  <span data-ttu-id="f287d-125">在**服務詳細資料**視窗中，按一下 [**訊息**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f287d-125">In the **Service Details** window, click the **Messages** tab.</span></span>  
  
7.  <span data-ttu-id="f287d-126">按兩下訊息一次。</span><span class="sxs-lookup"><span data-stu-id="f287d-126">Double-click the message again.</span></span>  
  
8.  <span data-ttu-id="f287d-127">在左窗格中，按一下 **訊息部分 / b**。</span><span class="sxs-lookup"><span data-stu-id="f287d-127">In the left pane, click **Message Parts / Body**.</span></span>  
  
9. <span data-ttu-id="f287d-128">判斷訊息結構是否正確。</span><span class="sxs-lookup"><span data-stu-id="f287d-128">Determine if the message structure is correct.</span></span>