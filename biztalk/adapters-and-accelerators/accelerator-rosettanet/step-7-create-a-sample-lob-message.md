---
title: "步驟 7： 建立範例 LOB 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, LOB
- loopback tutorial, creating LOB message
- creating, LOB messages
- LOBs, creating messages
ms.assetid: 3023bbc0-5bc4-4e5a-a345-c3253874f0d3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1246f56615381d2627db3058dc821ba85bf8b74d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-7-create-a-sample-lob-message"></a><span data-ttu-id="51a97-102">步驟 7： 建立範例 LOB 訊息</span><span class="sxs-lookup"><span data-stu-id="51a97-102">Step 7: Create a Sample LOB Message</span></span>
<span data-ttu-id="51a97-103">在此步驟中，您將使用 LOB 應用程式公用程式建立範例商務營運系統 (LOB) 訊息。</span><span class="sxs-lookup"><span data-stu-id="51a97-103">In this step, you use the LOB Application utility to create a sample line-of-business (LOB) message.</span></span>  
  
### <a name="to-create-a-sample-message-using-the-lob-application-utility"></a><span data-ttu-id="51a97-104">若要使用 LOB 應用程式公用程式建立範例訊息</span><span class="sxs-lookup"><span data-stu-id="51a97-104">To create a sample message using the LOB Application utility</span></span>  
  
1.  <span data-ttu-id="51a97-105">在[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管] 中，移至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK 資料夾，然後按兩下 [ **LOBApplication.exe**。</span><span class="sxs-lookup"><span data-stu-id="51a97-105">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK folder, and then double-click **LOBApplication.exe**.</span></span>  
  
2.  <span data-ttu-id="51a97-106">在**LOB 應用程式**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="51a97-106">In the **LOB Application** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="51a97-107">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="51a97-107">**Use this**</span></span>|<span data-ttu-id="51a97-108">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="51a97-108">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="51a97-109">**主要設定檔名稱**</span><span class="sxs-lookup"><span data-stu-id="51a97-109">**Home Profile Name**</span></span>|<span data-ttu-id="51a97-110">型別**首頁**。</span><span class="sxs-lookup"><span data-stu-id="51a97-110">Type **HOME**.</span></span>|  
    |<span data-ttu-id="51a97-111">**交易夥伴名稱**</span><span class="sxs-lookup"><span data-stu-id="51a97-111">**Trading Partner Name**</span></span>|<span data-ttu-id="51a97-112">型別**夥伴**。</span><span class="sxs-lookup"><span data-stu-id="51a97-112">Type **PARTNER**.</span></span>|  
    |<span data-ttu-id="51a97-113">**PIP 名稱**</span><span class="sxs-lookup"><span data-stu-id="51a97-113">**PIP Name**</span></span>|<span data-ttu-id="51a97-114">型別**0c1**。</span><span class="sxs-lookup"><span data-stu-id="51a97-114">Type **0C1**.</span></span>|  
    |<span data-ttu-id="51a97-115">**PIP 版本**</span><span class="sxs-lookup"><span data-stu-id="51a97-115">**PIP Version**</span></span>|<span data-ttu-id="51a97-116">型別**R01.02**。</span><span class="sxs-lookup"><span data-stu-id="51a97-116">Type **R01.02**.</span></span>|  
    |<span data-ttu-id="51a97-117">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="51a97-117">**File Name**</span></span>|<span data-ttu-id="51a97-118">按一下省略符號按鈕 (**...**)，並移至\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances。</span><span class="sxs-lookup"><span data-stu-id="51a97-118">Click the ellipsis button (**...**), and move to \<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances.</span></span> <span data-ttu-id="51a97-119">選取**0C1_Request.xml**從清單中的檔案，然後再按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="51a97-119">Select **0C1_Request.xml** from the list of files, and then click **Open**.</span></span>|  
    |<span data-ttu-id="51a97-120">**訊息類別**</span><span class="sxs-lookup"><span data-stu-id="51a97-120">**Message Category**</span></span>|<span data-ttu-id="51a97-121">選取**動作**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="51a97-121">Select **Action** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="51a97-122">在**LOB 應用程式**對話方塊中，按一下 **提交訊息**。</span><span class="sxs-lookup"><span data-stu-id="51a97-122">In the **LOB Application** dialog box, click **Submit Message**.</span></span>  
  
 <span data-ttu-id="51a97-123">LOB 應用程式會針對 Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 產生訊息，以模擬 LOB 應用程式所產生的原始訊息。</span><span class="sxs-lookup"><span data-stu-id="51a97-123">The LOB application generates a message for Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] simulating an original message generated by an LOB application.</span></span> <span data-ttu-id="51a97-124">您可以在 [狀態] 視窗中檢視訊息的狀態。</span><span class="sxs-lookup"><span data-stu-id="51a97-124">You can view the status of the message in the Status window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51a97-125">範例訊息假設「組織」和「交易夥伴」的「全球商務識別碼」(Global Business Identifier，GBI) 分別是 123456789 和 987654321。</span><span class="sxs-lookup"><span data-stu-id="51a97-125">The sample messages assume that the Global Business Identifiers (GBI) for "HOME" and "PARTNER" are 123456789 and 987654321, respectively.</span></span> <span data-ttu-id="51a97-126">若要使用不同的 GBI，您必須修改這些檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="51a97-126">To use a different GBI, you must modify the content of these files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51a97-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="51a97-127">See Also</span></span>  
 [<span data-ttu-id="51a97-128">步驟 8：檢視 BTARN 資料庫中的訊息</span><span class="sxs-lookup"><span data-stu-id="51a97-128">Step 8: View Messages in the BTARN Databases</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-8-view-messages-in-the-btarn-databases.md)