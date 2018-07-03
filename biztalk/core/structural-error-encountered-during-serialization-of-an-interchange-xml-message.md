---
title: 結構化的交換 XML 訊息的序列化期間發生的錯誤 |Microsoft Docs
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
ms.openlocfilehash: 7e5ce0694b60afcb743c138d3059a78f63f6fcb5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994295"
---
# <a name="structural-error-encountered-during-serialization-of-an-interchange-xml-message"></a><span data-ttu-id="45292-102">結構化的交換 XML 訊息的序列化期間發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="45292-102">Structural error encountered during serialization of an interchange XML message</span></span>
## <a name="details"></a><span data-ttu-id="45292-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="45292-103">Details</span></span>  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="45292-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="45292-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="45292-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="45292-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="45292-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="45292-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="45292-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="45292-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="45292-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="45292-108"> EDI</span></span> |
|    <span data-ttu-id="45292-109">元件</span><span class="sxs-lookup"><span data-stu-id="45292-109">Component</span></span>    |                                       <span data-ttu-id="45292-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="45292-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="45292-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="45292-111">Symbolic Name</span></span>  |                                  <span data-ttu-id="45292-112">InvalidXmlNodeFound</span><span class="sxs-lookup"><span data-stu-id="45292-112">InvalidXmlNodeFound</span></span>                                   |
|  <span data-ttu-id="45292-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="45292-113">Message Text</span></span>   |    <span data-ttu-id="45292-114">結構化的交換 Xml 訊息的序列化期間發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="45292-114">Structural error encountered during serialization of an Interchange Xml message</span></span>     |

## <a name="explanation"></a><span data-ttu-id="45292-115">說明</span><span class="sxs-lookup"><span data-stu-id="45292-115">Explanation</span></span>  
 <span data-ttu-id="45292-116">此錯誤表示，交換 XML 訊息序列化期間遇到結構錯誤。</span><span class="sxs-lookup"><span data-stu-id="45292-116">This error indicates that a structural error was encountered during serialization of an interchange XML message.</span></span> <span data-ttu-id="45292-117">BTS 尋找 Xmlstartelement 或 EndElement，但改為遇到不同的 XML 節點型別。</span><span class="sxs-lookup"><span data-stu-id="45292-117">BTS was looking for an XML StartElement or EndElement but instead a different XML node type was encountered.</span></span>  

## <a name="user-action"></a><span data-ttu-id="45292-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="45292-118">User Action</span></span>  
 <span data-ttu-id="45292-119">若要解決這個錯誤，請確定訊息結構正確，並再試一次：</span><span class="sxs-lookup"><span data-stu-id="45292-119">To resolve this error, make sure the message structure is correct, and try again:</span></span>  

1. <span data-ttu-id="45292-120">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="45292-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="45292-121">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後按一下**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="45292-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and click **BizTalk Group**.</span></span>  

3. <span data-ttu-id="45292-122">在右窗格中，按一下**群組中樞** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="45292-122">In the right pane, click the **Group Hub** tab.</span></span>  

4. <span data-ttu-id="45292-123">按一下 **擱置服務執行個體**。</span><span class="sxs-lookup"><span data-stu-id="45292-123">Click **Suspended Service instances**.</span></span>  

5. <span data-ttu-id="45292-124">按兩下的訊息。</span><span class="sxs-lookup"><span data-stu-id="45292-124">Double-click the message.</span></span>  

6. <span data-ttu-id="45292-125">在 **服務詳細資料** 視窗中，按一下**訊息** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="45292-125">In the **Service Details** window, click the **Messages** tab.</span></span>  

7. <span data-ttu-id="45292-126">一次按兩下的訊息。</span><span class="sxs-lookup"><span data-stu-id="45292-126">Double-click the message again.</span></span>  

8. <span data-ttu-id="45292-127">在左窗格中，按一下**訊息部分 / b**。</span><span class="sxs-lookup"><span data-stu-id="45292-127">In the left pane, click **Message Parts / Body**.</span></span>  

9. <span data-ttu-id="45292-128">判斷訊息結構是否正確。</span><span class="sxs-lookup"><span data-stu-id="45292-128">Determine if the message structure is correct.</span></span>
