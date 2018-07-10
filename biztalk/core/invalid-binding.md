---
title: 無效的繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e851f7f-ffc8-4f55-b06e-501a7f41b32a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 589d55d4ffccadf277f586104f8d5b9b1bf36b00
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996223"
---
# <a name="invalid-binding"></a><span data-ttu-id="7be0f-102">無效的繫結</span><span class="sxs-lookup"><span data-stu-id="7be0f-102">Invalid binding</span></span>
## <a name="details"></a><span data-ttu-id="7be0f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7be0f-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="7be0f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7be0f-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="7be0f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7be0f-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="7be0f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7be0f-106">Event ID</span></span>     |                                         <span data-ttu-id="7be0f-107">0</span><span class="sxs-lookup"><span data-stu-id="7be0f-107">0</span></span>                                          |
|  <span data-ttu-id="7be0f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7be0f-108">Event Source</span></span>   |                                         <span data-ttu-id="7be0f-109">0</span><span class="sxs-lookup"><span data-stu-id="7be0f-109">0</span></span>                                          |
|    <span data-ttu-id="7be0f-110">元件</span><span class="sxs-lookup"><span data-stu-id="7be0f-110">Component</span></span>    |                                         <span data-ttu-id="7be0f-111">0</span><span class="sxs-lookup"><span data-stu-id="7be0f-111">0</span></span>                                          |
|  <span data-ttu-id="7be0f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7be0f-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="7be0f-113">0</span><span class="sxs-lookup"><span data-stu-id="7be0f-113">0</span></span>                                          |
|  <span data-ttu-id="7be0f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7be0f-114">Message Text</span></span>   |                                  <span data-ttu-id="7be0f-115">無效的繫結</span><span class="sxs-lookup"><span data-stu-id="7be0f-115">Invalid binding</span></span>                                   |

## <a name="explanation"></a><span data-ttu-id="7be0f-116">說明</span><span class="sxs-lookup"><span data-stu-id="7be0f-116">Explanation</span></span>  
 <span data-ttu-id="7be0f-117">此錯誤表示配接器無法建立接收位置的繫結組態中指定的繫結，或傳送埠。</span><span class="sxs-lookup"><span data-stu-id="7be0f-117">This error indicates the adapter cannot create the binding specified in the binding configuration of the receive location or send port.</span></span>  

## <a name="user-action"></a><span data-ttu-id="7be0f-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7be0f-118">User Action</span></span>  
 <span data-ttu-id="7be0f-119">您可以使用下列程序來確認繫結項目。</span><span class="sxs-lookup"><span data-stu-id="7be0f-119">Use the following procedure to verify binding elements.</span></span>  

#### <a name="to-verify-binding-elements"></a><span data-ttu-id="7be0f-120">若要確認繫結項目</span><span class="sxs-lookup"><span data-stu-id="7be0f-120">To verify binding elements</span></span>  

1. <span data-ttu-id="7be0f-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="7be0f-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="7be0f-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7be0f-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="7be0f-123">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="7be0f-123">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="7be0f-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="7be0f-124">Right-click the transport name.</span></span>  

5. <span data-ttu-id="7be0f-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="7be0f-125">Click **Properties**.</span></span>  

6. <span data-ttu-id="7be0f-126">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="7be0f-126">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="7be0f-127">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="7be0f-127">Click **Configure**.</span></span>  

8. <span data-ttu-id="7be0f-128">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7be0f-128">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.</span></span>  

9. <span data-ttu-id="7be0f-129">請確定組態中指定的繫結項目都有效。</span><span class="sxs-lookup"><span data-stu-id="7be0f-129">Ensure the binding elements specified in the configuration are valid.</span></span>
