---
title: 無法匯出服務端點設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 795145fa-0ce4-498f-a82e-eb752a5f4764
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2418517b7695aedd5c80a950a9b74faf5d380346
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973351"
---
# <a name="unable-to-export-service-endpoint-configuration"></a><span data-ttu-id="85290-102">無法匯出服務端點組態</span><span class="sxs-lookup"><span data-stu-id="85290-102">Unable to export service endpoint configuration</span></span>
## <a name="details"></a><span data-ttu-id="85290-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="85290-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="85290-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="85290-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="85290-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="85290-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="85290-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="85290-106">Event ID</span></span>     |                                         <span data-ttu-id="85290-107">0</span><span class="sxs-lookup"><span data-stu-id="85290-107">0</span></span>                                          |
|  <span data-ttu-id="85290-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="85290-108">Event Source</span></span>   |                                         <span data-ttu-id="85290-109">0</span><span class="sxs-lookup"><span data-stu-id="85290-109">0</span></span>                                          |
|    <span data-ttu-id="85290-110">元件</span><span class="sxs-lookup"><span data-stu-id="85290-110">Component</span></span>    |                                         <span data-ttu-id="85290-111">0</span><span class="sxs-lookup"><span data-stu-id="85290-111">0</span></span>                                          |
|  <span data-ttu-id="85290-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="85290-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="85290-113">0</span><span class="sxs-lookup"><span data-stu-id="85290-113">0</span></span>                                          |
|  <span data-ttu-id="85290-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="85290-114">Message Text</span></span>   |              <span data-ttu-id="85290-115">無法將服務端點組態匯出到"{0}」</span><span class="sxs-lookup"><span data-stu-id="85290-115">Unable to export service endpoint configuration to "{0}"</span></span>              |
  
## <a name="explanation"></a><span data-ttu-id="85290-116">說明</span><span class="sxs-lookup"><span data-stu-id="85290-116">Explanation</span></span>  
 <span data-ttu-id="85290-117">此錯誤表示使用者可能沒有寫入目的地的權限。</span><span class="sxs-lookup"><span data-stu-id="85290-117">This error indicates the user may not have permission to write to the destination.</span></span> <span data-ttu-id="85290-118">或某些必要的屬性未正確指定，例如位址 (URI) 和繫結類型。</span><span class="sxs-lookup"><span data-stu-id="85290-118">Or some of the required properties were not correctly specified, such as Address (URI), and Binding Type.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="85290-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="85290-119">User Action</span></span>  
 <span data-ttu-id="85290-120">您可以使用下列程序來設定的端點身分識別。</span><span class="sxs-lookup"><span data-stu-id="85290-120">Use the following procedure to configure the endpoint identity.</span></span>  
  
#### <a name="to-configure-the-endpoint-identity"></a><span data-ttu-id="85290-121">若要設定的端點身分識別</span><span class="sxs-lookup"><span data-stu-id="85290-121">To configure the endpoint identity</span></span>  
  
1. <span data-ttu-id="85290-122">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="85290-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="85290-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="85290-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="85290-124">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="85290-124">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="85290-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="85290-125">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="85290-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="85290-126">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="85290-127">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="85290-127">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="85290-128">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="85290-128">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="85290-129">在 WCF **[**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="85290-129">In the WCF **[**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="85290-130">請確定允許的目的地資料夾的寫入。</span><span class="sxs-lookup"><span data-stu-id="85290-130">Ensure that writing to the destination folder is permitted.</span></span>  
  
10. <span data-ttu-id="85290-131">請檢查**行為** 索引標籤和**端點身分識別**中的設定**一般**索引標籤，確定其皆有效。</span><span class="sxs-lookup"><span data-stu-id="85290-131">Check the **Behavior** tab and the **Endpoint Identity** settings in the **General** tab to ensure they are valid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85290-132">您必須在目的地資料夾中具有寫入權限。</span><span class="sxs-lookup"><span data-stu-id="85290-132">You must have write permissions to the destination folder.</span></span> <span data-ttu-id="85290-133">請連絡機器的系統管理員，以取得這些權限。</span><span class="sxs-lookup"><span data-stu-id="85290-133">Contact the administrator of the machine to get these permissions.</span></span>