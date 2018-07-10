---
title: 無法匯入設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2887da50-4f74-4259-a7d6-c87bc9b9fc58
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5be14cff11021ac1a50116ee2e7784223724f675
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023780"
---
# <a name="unable-to-import-configuration"></a><span data-ttu-id="10618-102">無法匯入設定</span><span class="sxs-lookup"><span data-stu-id="10618-102">Unable to import configuration</span></span>
## <a name="details"></a><span data-ttu-id="10618-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="10618-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="10618-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="10618-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="10618-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="10618-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="10618-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="10618-106">Event ID</span></span>     |                                         <span data-ttu-id="10618-107">0</span><span class="sxs-lookup"><span data-stu-id="10618-107">0</span></span>                                          |
|  <span data-ttu-id="10618-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="10618-108">Event Source</span></span>   |                                         <span data-ttu-id="10618-109">0</span><span class="sxs-lookup"><span data-stu-id="10618-109">0</span></span>                                          |
|    <span data-ttu-id="10618-110">元件</span><span class="sxs-lookup"><span data-stu-id="10618-110">Component</span></span>    |                                         <span data-ttu-id="10618-111">0</span><span class="sxs-lookup"><span data-stu-id="10618-111">0</span></span>                                          |
|  <span data-ttu-id="10618-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="10618-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="10618-113">0</span><span class="sxs-lookup"><span data-stu-id="10618-113">0</span></span>                                          |
|  <span data-ttu-id="10618-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="10618-114">Message Text</span></span>   |                   <span data-ttu-id="10618-115">無法從檔案匯入組態 」{0}"</span><span class="sxs-lookup"><span data-stu-id="10618-115">Unable to import configuration from file "{0}"</span></span>                   |
  
## <a name="explanation"></a><span data-ttu-id="10618-116">說明</span><span class="sxs-lookup"><span data-stu-id="10618-116">Explanation</span></span>  
 <span data-ttu-id="10618-117">可能有多個原因導致此錯誤：</span><span class="sxs-lookup"><span data-stu-id="10618-117">There could be multiple reasons for this error:</span></span>  
  
-   <span data-ttu-id="10618-118">組態檔可能包含無效的字元，以指定的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="10618-118">The configuration file may contain invalid character in the given encoding.</span></span>  
  
-   <span data-ttu-id="10618-119">根項目可能已遺失。</span><span class="sxs-lookup"><span data-stu-id="10618-119">The root element may be missing.</span></span>  
  
-   <span data-ttu-id="10618-120">根層級的資料可能不正確。</span><span class="sxs-lookup"><span data-stu-id="10618-120">The data at the root level may be invalid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10618-121">這種情況，以及使用者的動作，僅適用於 Wcf-custom 和 WCF CustomIsolate 配接器。</span><span class="sxs-lookup"><span data-stu-id="10618-121">This situation, and the user action, applies only to WCF-Custom and WCF-CustomIsolate adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="10618-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="10618-122">User Action</span></span>  
 <span data-ttu-id="10618-123">您可以使用下列程序，匯入有效的組態檔。</span><span class="sxs-lookup"><span data-stu-id="10618-123">Use the following procedure to import a valid configuration file.</span></span>  
  
#### <a name="to-import-a-valid-configuration-file"></a><span data-ttu-id="10618-124">若要匯入有效的組態檔</span><span class="sxs-lookup"><span data-stu-id="10618-124">To import a valid configuration file</span></span>  
  
1. <span data-ttu-id="10618-125">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="10618-125">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="10618-126">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="10618-126">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="10618-127">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="10618-127">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="10618-128">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="10618-128">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="10618-129">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="10618-129">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="10618-130">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="10618-130">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="10618-131">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="10618-131">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="10618-132">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**匯入/匯出**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="10618-132">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Import/Export** tab.</span></span>  
  
9. <span data-ttu-id="10618-133">按一下 **[匯入]**。</span><span class="sxs-lookup"><span data-stu-id="10618-133">Click **Import**.</span></span> <span data-ttu-id="10618-134">匯入有效且完整的組態檔。</span><span class="sxs-lookup"><span data-stu-id="10618-134">Import a valid and complete configuration file.</span></span>  
  
   <span data-ttu-id="10618-135">您也可以藉由使用服務組態編輯器中將它開啟來確認組態檔的有效性 **(開始 > 所有程式 > Windows SDK)** （此步驟假設您已安裝的 Windows SDK）。開啟**svcConfigEditor.exe**並確認組態檔的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="10618-135">You can also verify the validity of the configuration file by opening it with the Service Configuration Editor **(Start > All Programs > Windows SDK)** (this step assumes you have the Windows SDK installed.) Open **svcConfigEditor.exe** and verify each property of the configuration file.</span></span>