---
title: "無法匯出服務端點組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 795145fa-0ce4-498f-a82e-eb752a5f4764
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3b36fa47d9302f3f88f65575bfa8f74c6469e9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-export-service-endpoint-configuration"></a><span data-ttu-id="a210d-102">無法匯出服務端點組態</span><span class="sxs-lookup"><span data-stu-id="a210d-102">Unable to export service endpoint configuration</span></span>
## <a name="details"></a><span data-ttu-id="a210d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a210d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a210d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a210d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a210d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a210d-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="a210d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a210d-106">Event ID</span></span>|<span data-ttu-id="a210d-107">0</span><span class="sxs-lookup"><span data-stu-id="a210d-107">0</span></span>|  
|<span data-ttu-id="a210d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="a210d-108">Event Source</span></span>|<span data-ttu-id="a210d-109">0</span><span class="sxs-lookup"><span data-stu-id="a210d-109">0</span></span>|  
|<span data-ttu-id="a210d-110">元件</span><span class="sxs-lookup"><span data-stu-id="a210d-110">Component</span></span>|<span data-ttu-id="a210d-111">0</span><span class="sxs-lookup"><span data-stu-id="a210d-111">0</span></span>|  
|<span data-ttu-id="a210d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a210d-112">Symbolic Name</span></span>|<span data-ttu-id="a210d-113">0</span><span class="sxs-lookup"><span data-stu-id="a210d-113">0</span></span>|  
|<span data-ttu-id="a210d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a210d-114">Message Text</span></span>|<span data-ttu-id="a210d-115">無法匯出服務端點組態，以"{0}"</span><span class="sxs-lookup"><span data-stu-id="a210d-115">Unable to export service endpoint configuration to "{0}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a210d-116">說明</span><span class="sxs-lookup"><span data-stu-id="a210d-116">Explanation</span></span>  
 <span data-ttu-id="a210d-117">此錯誤表示使用者可能沒有寫入目的地的權限。</span><span class="sxs-lookup"><span data-stu-id="a210d-117">This error indicates the user may not have permission to write to the destination.</span></span> <span data-ttu-id="a210d-118">或某些必要的屬性未正確指定，例如位址 (URI) 和繫結類型。</span><span class="sxs-lookup"><span data-stu-id="a210d-118">Or some of the required properties were not correctly specified, such as Address (URI), and Binding Type.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a210d-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a210d-119">User Action</span></span>  
 <span data-ttu-id="a210d-120">您可以使用下列程序來設定的端點身分識別。</span><span class="sxs-lookup"><span data-stu-id="a210d-120">Use the following procedure to configure the endpoint identity.</span></span>  
  
#### <a name="to-configure-the-endpoint-identity"></a><span data-ttu-id="a210d-121">若要設定的端點身分識別</span><span class="sxs-lookup"><span data-stu-id="a210d-121">To configure the endpoint identity</span></span>  
  
1.  <span data-ttu-id="a210d-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a210d-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a210d-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="a210d-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="a210d-124">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="a210d-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="a210d-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="a210d-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="a210d-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="a210d-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="a210d-127">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="a210d-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="a210d-128">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="a210d-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="a210d-129">在 WCF **[***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a210d-129">In the WCF **[***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="a210d-130">請確定目的地資料夾的寫入允許的。</span><span class="sxs-lookup"><span data-stu-id="a210d-130">Ensure that writing to the destination folder is permitted.</span></span>  
  
10. <span data-ttu-id="a210d-131">請檢查**行為** 索引標籤和**端點身分識別**中的設定**一般**索引標籤，確定其皆有效。</span><span class="sxs-lookup"><span data-stu-id="a210d-131">Check the **Behavior** tab and the **Endpoint Identity** settings in the **General** tab to ensure they are valid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a210d-132">您必須具有目的地資料夾寫入權限。</span><span class="sxs-lookup"><span data-stu-id="a210d-132">You must have write permissions to the destination folder.</span></span> <span data-ttu-id="a210d-133">請連絡機器的系統管理員，以取得這些權限。</span><span class="sxs-lookup"><span data-stu-id="a210d-133">Contact the administrator of the machine to get these permissions.</span></span>