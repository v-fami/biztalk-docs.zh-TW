---
title: 無法匯出用戶端端點組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d93fe5e-fdb2-49c5-86de-d428b1ecda7f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 752546eb85f8285e18c0a38d0877637e3627b6a2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999423"
---
# <a name="unable-to-export-client-endpoint-configuration"></a><span data-ttu-id="79020-102">無法匯出用戶端結束點組態</span><span class="sxs-lookup"><span data-stu-id="79020-102">Unable to export client endpoint configuration</span></span>
## <a name="details"></a><span data-ttu-id="79020-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="79020-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="79020-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="79020-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="79020-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="79020-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="79020-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="79020-106">Event ID</span></span>     |                                         <span data-ttu-id="79020-107">0</span><span class="sxs-lookup"><span data-stu-id="79020-107">0</span></span>                                          |
|  <span data-ttu-id="79020-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="79020-108">Event Source</span></span>   |                                         <span data-ttu-id="79020-109">0</span><span class="sxs-lookup"><span data-stu-id="79020-109">0</span></span>                                          |
|    <span data-ttu-id="79020-110">元件</span><span class="sxs-lookup"><span data-stu-id="79020-110">Component</span></span>    |                                         <span data-ttu-id="79020-111">0</span><span class="sxs-lookup"><span data-stu-id="79020-111">0</span></span>                                          |
|  <span data-ttu-id="79020-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="79020-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="79020-113">0</span><span class="sxs-lookup"><span data-stu-id="79020-113">0</span></span>                                          |
|  <span data-ttu-id="79020-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="79020-114">Message Text</span></span>   |              <span data-ttu-id="79020-115">無法匯出用戶端端點組態，以 「{0}"</span><span class="sxs-lookup"><span data-stu-id="79020-115">Unable to export client endpoint configuration to "{0}"</span></span>               |
  
## <a name="explanation"></a><span data-ttu-id="79020-116">說明</span><span class="sxs-lookup"><span data-stu-id="79020-116">Explanation</span></span>  
 <span data-ttu-id="79020-117">此錯誤表示下列其中一個狀況：</span><span class="sxs-lookup"><span data-stu-id="79020-117">This error indicates one of the following:</span></span>  
  
-   <span data-ttu-id="79020-118">使用者沒有寫入目的地的權限。</span><span class="sxs-lookup"><span data-stu-id="79020-118">The user may not have permission to write to the destination.</span></span>  
  
     <span data-ttu-id="79020-119">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="79020-119">\- OR -</span></span>  
  
-   <span data-ttu-id="79020-120">某些必要的屬性未正確指定，這類**位址 (URI)** 並**繫結的型別**。</span><span class="sxs-lookup"><span data-stu-id="79020-120">Some of the required properties were not correctly specified, such as **Address (URI)** and **Binding Type**.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="79020-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="79020-121">User Action</span></span>  
 <span data-ttu-id="79020-122">使用下列程序，以確認使用者權限，並確認**位址 (URI)** 並**繫結的型別**設定是否有效。</span><span class="sxs-lookup"><span data-stu-id="79020-122">Use the following procedure to verify user permissions and confirm **Address (URI)** and **Binding Type** settings are valid.</span></span>  
  
#### <a name="to-verify-user-permissions-and-confirm-settings"></a><span data-ttu-id="79020-123">確認使用者權限，並確認設定</span><span class="sxs-lookup"><span data-stu-id="79020-123">To verify user permissions and confirm settings</span></span>  
  
1. <span data-ttu-id="79020-124">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="79020-124">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="79020-125">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="79020-125">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="79020-126">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="79020-126">Locate your application, and then locate your transport.</span></span>  
  
4. <span data-ttu-id="79020-127">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="79020-127">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="79020-128">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="79020-128">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="79020-129">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="79020-129">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="79020-130">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="79020-130">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="79020-131">在 WCF **[**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="79020-131">In the WCF **[**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="79020-132">請確定允許寫入至目的地資料夾。</span><span class="sxs-lookup"><span data-stu-id="79020-132">Ensure writing to the destination folder is permitted.</span></span>  
  
10. <span data-ttu-id="79020-133">請檢查**行為** 索引標籤和**端點身分識別**中的設定**一般**索引標籤，確定其皆有效。</span><span class="sxs-lookup"><span data-stu-id="79020-133">Check the **Behavior** tab and the **Endpoint Identity** settings in **General** tab to ensure they are valid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79020-134">您必須在目的地資料夾中具有寫入權限。</span><span class="sxs-lookup"><span data-stu-id="79020-134">You must have write permissions to the destination folder.</span></span> <span data-ttu-id="79020-135">請連絡機器的系統管理員，以取得這些權限。</span><span class="sxs-lookup"><span data-stu-id="79020-135">Contact the administrator of the machine to get these permissions.</span></span>