---
title: 不明或非預期的繫結項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56021ff3-5abf-46ab-90bb-4531ccc9abd0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bfe15cf5aeab233c4ecef56f7b278e0646de5ad
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015639"
---
# <a name="unknown-or-unexpected-binding-element"></a><span data-ttu-id="d8814-102">不明或非預期的繫結項目</span><span class="sxs-lookup"><span data-stu-id="d8814-102">Unknown or unexpected binding element</span></span>
## <a name="details"></a><span data-ttu-id="d8814-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d8814-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="d8814-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d8814-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="d8814-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d8814-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="d8814-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d8814-106">Event ID</span></span>     |                                         <span data-ttu-id="d8814-107">0</span><span class="sxs-lookup"><span data-stu-id="d8814-107">0</span></span>                                          |
|  <span data-ttu-id="d8814-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d8814-108">Event Source</span></span>   |                                         <span data-ttu-id="d8814-109">0</span><span class="sxs-lookup"><span data-stu-id="d8814-109">0</span></span>                                          |
|    <span data-ttu-id="d8814-110">元件</span><span class="sxs-lookup"><span data-stu-id="d8814-110">Component</span></span>    |                                         <span data-ttu-id="d8814-111">0</span><span class="sxs-lookup"><span data-stu-id="d8814-111">0</span></span>                                          |
|  <span data-ttu-id="d8814-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d8814-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="d8814-113">0</span><span class="sxs-lookup"><span data-stu-id="d8814-113">0</span></span>                                          |
|  <span data-ttu-id="d8814-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d8814-114">Message Text</span></span>   |                       <span data-ttu-id="d8814-115">不明或非預期的繫結項目</span><span class="sxs-lookup"><span data-stu-id="d8814-115">Unknown or unexpected binding element</span></span>                        |

## <a name="explanation"></a><span data-ttu-id="d8814-116">說明</span><span class="sxs-lookup"><span data-stu-id="d8814-116">Explanation</span></span>  
 <span data-ttu-id="d8814-117">此錯誤表示配接器找不到繫結中指定的使用者定義繫結項目。</span><span class="sxs-lookup"><span data-stu-id="d8814-117">This error indicates the adapter cannot find the user defined binding element specified in the binding.</span></span> <span data-ttu-id="d8814-118">主要使用 Wcf-custom 和 Wcf-customisolated 配接器，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="d8814-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  

## <a name="user-action"></a><span data-ttu-id="d8814-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d8814-119">User Action</span></span>  
 <span data-ttu-id="d8814-120">您可以使用下列程序來驗證繫結項目有效。</span><span class="sxs-lookup"><span data-stu-id="d8814-120">Use the following procedure to verify binding elements are valid.</span></span>  

#### <a name="to-verify-binding-elements-are-valid"></a><span data-ttu-id="d8814-121">若要驗證繫結項目有效</span><span class="sxs-lookup"><span data-stu-id="d8814-121">To verify binding elements are valid</span></span>  

1. <span data-ttu-id="d8814-122">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="d8814-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="d8814-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d8814-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="d8814-124">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="d8814-124">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="d8814-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="d8814-125">Right-click the transport name.</span></span>  

5. <span data-ttu-id="d8814-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="d8814-126">Click **Properties**.</span></span>  

6. <span data-ttu-id="d8814-127">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d8814-127">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="d8814-128">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="d8814-128">Click **Configure**.</span></span>  

8. <span data-ttu-id="d8814-129">在 WCF **[**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d8814-129">In the WCF **[**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.</span></span>  

9. <span data-ttu-id="d8814-130">請確定組態中指定的繫結項目有效。</span><span class="sxs-lookup"><span data-stu-id="d8814-130">Ensure that the binding elements specified in the configuration are valid.</span></span>
