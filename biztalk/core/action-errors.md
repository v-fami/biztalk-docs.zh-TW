---
title: "動作錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cf0a5b-d1dd-4807-9660-e8a8b7012b40
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49f25f1f15307077943ef370a335885690bea22c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="action-errors"></a><span data-ttu-id="46aba-102">動作的錯誤</span><span class="sxs-lookup"><span data-stu-id="46aba-102">Action Errors</span></span>
<span data-ttu-id="46aba-103">本節包含診斷及解決 WCF 動作錯誤的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="46aba-103">This section contains detailed information for diagnosing and resolving WCF Action errors.</span></span>  
  
## <a name="details"></a><span data-ttu-id="46aba-104">詳細資料</span><span class="sxs-lookup"><span data-stu-id="46aba-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46aba-105">產品名稱</span><span class="sxs-lookup"><span data-stu-id="46aba-105">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="46aba-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="46aba-106">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="46aba-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="46aba-107">Event ID</span></span>|<span data-ttu-id="46aba-108">0</span><span class="sxs-lookup"><span data-stu-id="46aba-108">0</span></span>|  
|<span data-ttu-id="46aba-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="46aba-109">Event Source</span></span>|<span data-ttu-id="46aba-110">0</span><span class="sxs-lookup"><span data-stu-id="46aba-110">0</span></span>|  
|<span data-ttu-id="46aba-111">元件</span><span class="sxs-lookup"><span data-stu-id="46aba-111">Component</span></span>|<span data-ttu-id="46aba-112">0</span><span class="sxs-lookup"><span data-stu-id="46aba-112">0</span></span>|  
|<span data-ttu-id="46aba-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="46aba-113">Symbolic Name</span></span>|<span data-ttu-id="46aba-114">0</span><span class="sxs-lookup"><span data-stu-id="46aba-114">0</span></span>|  
|<span data-ttu-id="46aba-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="46aba-115">Message Text</span></span>|<span data-ttu-id="46aba-116">單一動作不能包含新行字元。</span><span class="sxs-lookup"><span data-stu-id="46aba-116">A single action cannot contain new line characters.</span></span> <span data-ttu-id="46aba-117">移除所有的新行字元。</span><span class="sxs-lookup"><span data-stu-id="46aba-117">Remove all new line characters.</span></span> <span data-ttu-id="46aba-118">或者，若要指定多個動作，使用動作對應語法。</span><span class="sxs-lookup"><span data-stu-id="46aba-118">Or, to specify multiple actions, use the action mapping syntax.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="46aba-119">說明</span><span class="sxs-lookup"><span data-stu-id="46aba-119">Explanation</span></span>  
 <span data-ttu-id="46aba-120">此錯誤表示傳送埠的 action 屬性中包含不允許新行字元。</span><span class="sxs-lookup"><span data-stu-id="46aba-120">This error indicates the action property of a send port contains a new line character, which is not allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46aba-121">動作已定義的對應時，則不適用這項限制。</span><span class="sxs-lookup"><span data-stu-id="46aba-121">This restriction does not apply when the action is defined as a mapping.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="46aba-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="46aba-122">User Action</span></span>  
 <span data-ttu-id="46aba-123">若要修正的 action 屬性中使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="46aba-123">Use the following procedure to fix the action property.</span></span>  
  
 
1.  <span data-ttu-id="46aba-124">開啟 [BizTalk Server 管理] 。</span><span class="sxs-lookup"><span data-stu-id="46aba-124">Open **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="46aba-125">在 主控台根目錄中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="46aba-125">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="46aba-126">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="46aba-126">Locate your application, and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="46aba-127">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="46aba-127">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="46aba-128">選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="46aba-128">Select **Properties**.</span></span>  
  
6.  <span data-ttu-id="46aba-129">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="46aba-129">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="46aba-130">選取 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="46aba-130">Select **Configure**.</span></span>  
  
8.  <span data-ttu-id="46aba-131">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，選取**一般** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="46aba-131">In the **WCF [***transport type***] Transport Properties** dialog box, select the **General** tab.</span></span>  
  
9. <span data-ttu-id="46aba-132">在**SOAP 動作標頭**區段中，移除新行字元從**動作**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="46aba-132">In the **SOAP Action header** section, remove the new line character from the **Action** text box.</span></span>  

## <a name="more-good-info"></a><span data-ttu-id="46aba-133">良好的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="46aba-133">More good info</span></span>  
 <span data-ttu-id="46aba-134">如需有關動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../core/specifying-soap-actions-for-wcf-send-adapters.md)</span><span class="sxs-lookup"><span data-stu-id="46aba-134">For additional information on actions, see [Specifying SOAP Actions for WCF Send Adapters](../core/specifying-soap-actions-for-wcf-send-adapters.md)</span></span>