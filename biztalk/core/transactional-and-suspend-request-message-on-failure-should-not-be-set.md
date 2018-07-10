---
title: 交易選項&quot;Transactional&quot;和 錯誤處理選項&quot;失敗時擱置要求訊息&quot;應該不能兩者都設定為 false |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc6c66cc-6713-4396-b0d4-ac6a0e72164f
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3818ddba18b89aedd1185f5ad87f3682dd5686a7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971415"
---
# <a name="transactions-option-quottransactionalquot-and-the-error-handling-option-quotsuspend-request-message-on-failurequot-should-not-both-be-set-to-false"></a><span data-ttu-id="aab5a-102">交易選項&quot;Transactional&quot;和 錯誤處理選項&quot;失敗時擱置要求訊息&quot;應該不能兩者都設定為 false</span><span class="sxs-lookup"><span data-stu-id="aab5a-102">Transactions option &quot;Transactional&quot; and the error handling option &quot;Suspend request message on failure&quot; should not both be set to false</span></span>
## <a name="details"></a><span data-ttu-id="aab5a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aab5a-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="aab5a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aab5a-104">Product Name</span></span>   |                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                |
| <span data-ttu-id="aab5a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="aab5a-105">Product Version</span></span> |                                                                            [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                            |
|    <span data-ttu-id="aab5a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aab5a-106">Event ID</span></span>     |                                                                                                        <span data-ttu-id="aab5a-107">0</span><span class="sxs-lookup"><span data-stu-id="aab5a-107">0</span></span>                                                                                                         |
|  <span data-ttu-id="aab5a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="aab5a-108">Event Source</span></span>   |                                                                                                        <span data-ttu-id="aab5a-109">0</span><span class="sxs-lookup"><span data-stu-id="aab5a-109">0</span></span>                                                                                                         |
|    <span data-ttu-id="aab5a-110">元件</span><span class="sxs-lookup"><span data-stu-id="aab5a-110">Component</span></span>    |                                                                                                        <span data-ttu-id="aab5a-111">0</span><span class="sxs-lookup"><span data-stu-id="aab5a-111">0</span></span>                                                                                                         |
|  <span data-ttu-id="aab5a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aab5a-112">Symbolic Name</span></span>  |                                                                                                        <span data-ttu-id="aab5a-113">0</span><span class="sxs-lookup"><span data-stu-id="aab5a-113">0</span></span>                                                                                                         |
|  <span data-ttu-id="aab5a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aab5a-114">Message Text</span></span>   | <span data-ttu-id="aab5a-115">交易選項 「 交易式 」 和錯誤處理選項 「 失敗時擱置要求訊息 」 應該不能兩者都設定為 false 因為可能會造成訊息遺失。</span><span class="sxs-lookup"><span data-stu-id="aab5a-115">The transactions option "Transactional" and the error handling option "Suspend request message on failure" should not both be set to false since message loss may occur.</span></span> <span data-ttu-id="aab5a-116">請設定一個或兩個選項為 true。</span><span class="sxs-lookup"><span data-stu-id="aab5a-116">Please set one or both options to true.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="aab5a-117">說明</span><span class="sxs-lookup"><span data-stu-id="aab5a-117">Explanation</span></span>  
 <span data-ttu-id="aab5a-118">Wcf-netmsmq 配接器的選項中**Transactional**並**失敗時擱置要求訊息**應該不能兩者都設定為 false （未核取）。</span><span class="sxs-lookup"><span data-stu-id="aab5a-118">In the WCF-NetMsmq adapter, the options **Transactional** and **Suspend request message on failure** should not both be set to false (unchecked).</span></span> <span data-ttu-id="aab5a-119">如果失敗的訊息提交不會回復為交易，雖然訊息不會暫停，而不是儲存在訊息方塊中，可能會造成訊息遺失。</span><span class="sxs-lookup"><span data-stu-id="aab5a-119">Message loss may occur if the failed message submission does not roll back as a transaction, while the message is not suspended and stored in the Message Box.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aab5a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aab5a-120">User Action</span></span>  
 <span data-ttu-id="aab5a-121">您可以使用下列程序來確認介面卡設定。</span><span class="sxs-lookup"><span data-stu-id="aab5a-121">Use the following procedure to verify adapter settings.</span></span>  
  
#### <a name="to-verify-adapter-settings"></a><span data-ttu-id="aab5a-122">若要確認介面卡設定</span><span class="sxs-lookup"><span data-stu-id="aab5a-122">To verify adapter settings</span></span>  
  
1. <span data-ttu-id="aab5a-123">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="aab5a-123">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="aab5a-124">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="aab5a-124">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="aab5a-125">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="aab5a-125">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="aab5a-126">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="aab5a-126">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="aab5a-127">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="aab5a-127">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="aab5a-128">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="aab5a-128">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="aab5a-129">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="aab5a-129">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="aab5a-130">在  **Wcf-netmsmq 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="aab5a-130">In the **WCF-NetMsmq Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="aab5a-131">在 **交易**區段中，判斷**交易式**已核取。</span><span class="sxs-lookup"><span data-stu-id="aab5a-131">In the **Transactions** section, determine if **Transactional** is checked.</span></span>  
  
10. <span data-ttu-id="aab5a-132">按一下 [**訊息**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="aab5a-132">Click the **Messages** tab.</span></span>  
  
11. <span data-ttu-id="aab5a-133">判斷是否**失敗時擱置要求訊息**已核取。</span><span class="sxs-lookup"><span data-stu-id="aab5a-133">Determine if **Suspend request message on failure** is checked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aab5a-134">這些步驟僅適用於對接收位置。</span><span class="sxs-lookup"><span data-stu-id="aab5a-134">These steps only apply to receive locations.</span></span>