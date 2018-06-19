---
title: 無法匯入組態 |Microsoft 文件
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
ms.openlocfilehash: 8e565b466e4f9ce8af3745948952b4318a029ff2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286678"
---
# <a name="unable-to-import-configuration"></a><span data-ttu-id="7976a-102">無法匯入組態</span><span class="sxs-lookup"><span data-stu-id="7976a-102">Unable to import configuration</span></span>
## <a name="details"></a><span data-ttu-id="7976a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7976a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7976a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7976a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7976a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7976a-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="7976a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7976a-106">Event ID</span></span>|<span data-ttu-id="7976a-107">0</span><span class="sxs-lookup"><span data-stu-id="7976a-107">0</span></span>|  
|<span data-ttu-id="7976a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7976a-108">Event Source</span></span>|<span data-ttu-id="7976a-109">0</span><span class="sxs-lookup"><span data-stu-id="7976a-109">0</span></span>|  
|<span data-ttu-id="7976a-110">元件</span><span class="sxs-lookup"><span data-stu-id="7976a-110">Component</span></span>|<span data-ttu-id="7976a-111">0</span><span class="sxs-lookup"><span data-stu-id="7976a-111">0</span></span>|  
|<span data-ttu-id="7976a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7976a-112">Symbolic Name</span></span>|<span data-ttu-id="7976a-113">0</span><span class="sxs-lookup"><span data-stu-id="7976a-113">0</span></span>|  
|<span data-ttu-id="7976a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7976a-114">Message Text</span></span>|<span data-ttu-id="7976a-115">無法匯入組態檔"{0}"</span><span class="sxs-lookup"><span data-stu-id="7976a-115">Unable to import configuration from file "{0}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7976a-116">說明</span><span class="sxs-lookup"><span data-stu-id="7976a-116">Explanation</span></span>  
 <span data-ttu-id="7976a-117">可能有這項錯誤的原因很多：</span><span class="sxs-lookup"><span data-stu-id="7976a-117">There could be multiple reasons for this error:</span></span>  
  
-   <span data-ttu-id="7976a-118">組態檔可能包含無效的字元，以指定的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="7976a-118">The configuration file may contain invalid character in the given encoding.</span></span>  
  
-   <span data-ttu-id="7976a-119">根項目可能已遺失。</span><span class="sxs-lookup"><span data-stu-id="7976a-119">The root element may be missing.</span></span>  
  
-   <span data-ttu-id="7976a-120">根層級的資料可能不正確。</span><span class="sxs-lookup"><span data-stu-id="7976a-120">The data at the root level may be invalid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7976a-121">這種情況，以及使用者動作，僅適用於 Wcf-custom 和 WCF CustomIsolate 配接器。</span><span class="sxs-lookup"><span data-stu-id="7976a-121">This situation, and the user action, applies only to WCF-Custom and WCF-CustomIsolate adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7976a-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7976a-122">User Action</span></span>  
 <span data-ttu-id="7976a-123">您可以使用下列程序，匯入有效的組態檔。</span><span class="sxs-lookup"><span data-stu-id="7976a-123">Use the following procedure to import a valid configuration file.</span></span>  
  
#### <a name="to-import-a-valid-configuration-file"></a><span data-ttu-id="7976a-124">若要匯入有效的組態檔</span><span class="sxs-lookup"><span data-stu-id="7976a-124">To import a valid configuration file</span></span>  
  
1.  <span data-ttu-id="7976a-125">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="7976a-125">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7976a-126">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7976a-126">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="7976a-127">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="7976a-127">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="7976a-128">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="7976a-128">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="7976a-129">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="7976a-129">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="7976a-130">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="7976a-130">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="7976a-131">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="7976a-131">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="7976a-132">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**匯入/匯出**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7976a-132">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Import/Export** tab.</span></span>  
  
9. <span data-ttu-id="7976a-133">按一下 **[匯入]**。</span><span class="sxs-lookup"><span data-stu-id="7976a-133">Click **Import**.</span></span> <span data-ttu-id="7976a-134">匯入有效的完整組態檔。</span><span class="sxs-lookup"><span data-stu-id="7976a-134">Import a valid and complete configuration file.</span></span>  
  
 <span data-ttu-id="7976a-135">您也可以藉由使用服務組態編輯器中將它開啟來確認組態檔的有效性 **(開始 > 所有程式 > Windows SDK)** （此步驟中假設您已安裝 Windows SDK）。開啟**svcConfigEditor.exe**並確認每一個屬性的組態檔。</span><span class="sxs-lookup"><span data-stu-id="7976a-135">You can also verify the validity of the configuration file by opening it with the Service Configuration Editor **(Start > All Programs > Windows SDK)** (this step assumes you have the Windows SDK installed.) Open **svcConfigEditor.exe** and verify each property of the configuration file.</span></span>