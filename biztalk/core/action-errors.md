---
title: 動作錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87cf0a5b-d1dd-4807-9660-e8a8b7012b40
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3cb63e90f85c830c30524b3adc1e3b0d86ab8b7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997271"
---
# <a name="action-errors"></a><span data-ttu-id="47ecf-102">動作錯誤</span><span class="sxs-lookup"><span data-stu-id="47ecf-102">Action Errors</span></span>
<span data-ttu-id="47ecf-103">本節包含診斷及解決 WCF 動作錯誤的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="47ecf-103">This section contains detailed information for diagnosing and resolving WCF Action errors.</span></span>  
  
## <a name="details"></a><span data-ttu-id="47ecf-104">詳細資料</span><span class="sxs-lookup"><span data-stu-id="47ecf-104">Details</span></span>  
  
|                 |                                                                                                                                                     |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="47ecf-105">產品名稱</span><span class="sxs-lookup"><span data-stu-id="47ecf-105">Product Name</span></span>   |                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                  |
| <span data-ttu-id="47ecf-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="47ecf-106">Product Version</span></span> |                                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                              |
|    <span data-ttu-id="47ecf-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="47ecf-107">Event ID</span></span>     |                                                                          <span data-ttu-id="47ecf-108">0</span><span class="sxs-lookup"><span data-stu-id="47ecf-108">0</span></span>                                                                          |
|  <span data-ttu-id="47ecf-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="47ecf-109">Event Source</span></span>   |                                                                          <span data-ttu-id="47ecf-110">0</span><span class="sxs-lookup"><span data-stu-id="47ecf-110">0</span></span>                                                                          |
|    <span data-ttu-id="47ecf-111">元件</span><span class="sxs-lookup"><span data-stu-id="47ecf-111">Component</span></span>    |                                                                          <span data-ttu-id="47ecf-112">0</span><span class="sxs-lookup"><span data-stu-id="47ecf-112">0</span></span>                                                                          |
|  <span data-ttu-id="47ecf-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="47ecf-113">Symbolic Name</span></span>  |                                                                          <span data-ttu-id="47ecf-114">0</span><span class="sxs-lookup"><span data-stu-id="47ecf-114">0</span></span>                                                                          |
|  <span data-ttu-id="47ecf-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="47ecf-115">Message Text</span></span>   | <span data-ttu-id="47ecf-116">以單一動作不能包含新行字元。</span><span class="sxs-lookup"><span data-stu-id="47ecf-116">A single action cannot contain new line characters.</span></span> <span data-ttu-id="47ecf-117">移除所有的新行字元。</span><span class="sxs-lookup"><span data-stu-id="47ecf-117">Remove all new line characters.</span></span> <span data-ttu-id="47ecf-118">或者，若要指定多個動作，使用動作對應語法。</span><span class="sxs-lookup"><span data-stu-id="47ecf-118">Or, to specify multiple actions, use the action mapping syntax.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="47ecf-119">說明</span><span class="sxs-lookup"><span data-stu-id="47ecf-119">Explanation</span></span>  
 <span data-ttu-id="47ecf-120">此錯誤表示的傳送埠的 [動作] 屬性包含新行字元，這不允許。</span><span class="sxs-lookup"><span data-stu-id="47ecf-120">This error indicates the action property of a send port contains a new line character, which is not allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47ecf-121">這項限制不適用於當動作已定義的對應。</span><span class="sxs-lookup"><span data-stu-id="47ecf-121">This restriction does not apply when the action is defined as a mapping.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="47ecf-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="47ecf-122">User Action</span></span>  
 <span data-ttu-id="47ecf-123">若要修正的 action 屬性中使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="47ecf-123">Use the following procedure to fix the action property.</span></span>  
  
 
1. <span data-ttu-id="47ecf-124">開啟 [BizTalk Server 管理] 。</span><span class="sxs-lookup"><span data-stu-id="47ecf-124">Open **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="47ecf-125">在 [主控台根目錄中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="47ecf-125">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="47ecf-126">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="47ecf-126">Locate your application, and then locate your transport.</span></span>  
  
4. <span data-ttu-id="47ecf-127">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="47ecf-127">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="47ecf-128">選取 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="47ecf-128">Select **Properties**.</span></span>  
  
6. <span data-ttu-id="47ecf-129">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="47ecf-129">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="47ecf-130">選取 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="47ecf-130">Select **Configure**.</span></span>  
  
8. <span data-ttu-id="47ecf-131">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**對話方塊中，選取**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="47ecf-131">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, select the **General** tab.</span></span>  
  
9. <span data-ttu-id="47ecf-132">在  **SOAP 動作標頭**區段中，移除新行字元從**動作**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="47ecf-132">In the **SOAP Action header** section, remove the new line character from the **Action** text box.</span></span>  

## <a name="more-good-info"></a><span data-ttu-id="47ecf-133">良好的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="47ecf-133">More good info</span></span>  
 <span data-ttu-id="47ecf-134">如需其他有關動作的詳細資訊，請參閱[指定 WCF 傳送配接器的 SOAP 動作](../core/specifying-soap-actions-for-wcf-send-adapters.md)</span><span class="sxs-lookup"><span data-stu-id="47ecf-134">For additional information on actions, see [Specifying SOAP Actions for WCF Send Adapters](../core/specifying-soap-actions-for-wcf-send-adapters.md)</span></span>