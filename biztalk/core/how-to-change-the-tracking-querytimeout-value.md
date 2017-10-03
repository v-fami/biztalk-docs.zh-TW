---
title: "如何變更追蹤 QueryTimeout 值 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [HAT], time-out limits
- HAT, time-out limits
ms.assetid: abc26f37-6537-42fa-81ff-bc8b758b4e10
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca9f61466323e0b154bdeb0499cc5cee6e4ef10c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-tracking-querytimeout-value"></a><span data-ttu-id="74ba7-102">如何變更追蹤 QueryTimeout 值</span><span class="sxs-lookup"><span data-stu-id="74ba7-102">How to Change the Tracking QueryTimeout Value</span></span>
<span data-ttu-id="74ba7-103">根據預設，訊息和服務執行個體追蹤會逾時查詢的執行時間超過 60 秒。</span><span class="sxs-lookup"><span data-stu-id="74ba7-103">By default, message and service instance tracking will time out if a query runs longer than 60 seconds.</span></span> <span data-ttu-id="74ba7-104">您可以在登錄中變更此逾時值，讓查詢的執行時間可以超過 60 秒。</span><span class="sxs-lookup"><span data-stu-id="74ba7-104">You can change the timeout value in the registry to enable queries to run longer than 60 seconds.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="74ba7-105">不當編輯登錄可能會造成系統嚴重受損。</span><span class="sxs-lookup"><span data-stu-id="74ba7-105">Incorrectly editing the registry may severely damage your system.</span></span> <span data-ttu-id="74ba7-106">在變更登錄之前，應備份電腦上的所有重要資料。</span><span class="sxs-lookup"><span data-stu-id="74ba7-106">Before making changes to the registry, you should back up any valued data on the computer.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="74ba7-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="74ba7-107">Prerequisites</span></span>  
 <span data-ttu-id="74ba7-108">您必須以「系統管理員」群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="74ba7-108">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
### <a name="to-change-the-query-timeout-value"></a><span data-ttu-id="74ba7-109">若要變更查詢逾時值</span><span class="sxs-lookup"><span data-stu-id="74ba7-109">To change the query timeout value</span></span>  
  
1.  <span data-ttu-id="74ba7-110">按一下**啟動**，按一下 **執行**，型別**regedit**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="74ba7-110">Click **Start**, click **Run**, type **regedit**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="74ba7-111">在登錄編輯程式中，找出下列子機碼然後按一下它：</span><span class="sxs-lookup"><span data-stu-id="74ba7-111">In Registry Editor, locate and then click the following subkey:</span></span>  
  
     <span data-ttu-id="74ba7-112">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk server\3.0**</span><span class="sxs-lookup"><span data-stu-id="74ba7-112">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0**</span></span>  
  
3.  <span data-ttu-id="74ba7-113">如果有 Tracking 子機碼，請跳到步驟 6。</span><span class="sxs-lookup"><span data-stu-id="74ba7-113">If there is a Tracking subkey, go to step 6.</span></span>  
  
4.  <span data-ttu-id="74ba7-114">若要建立 Tracking 子機碼，在**編輯**功能表上，指向**新增**，然後按一下 **金鑰**。</span><span class="sxs-lookup"><span data-stu-id="74ba7-114">To create a Tracking subkey, on the **Edit** menu, point to **New**, and then click **Key**.</span></span>  
  
5.  <span data-ttu-id="74ba7-115">型別**追蹤**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="74ba7-115">Type **Tracking**, and then press ENTER.</span></span>  
  
6.  <span data-ttu-id="74ba7-116">找出下列子機碼，然後按一下它：</span><span class="sxs-lookup"><span data-stu-id="74ba7-116">Locate and then click the following subkey:</span></span>  
  
     <span data-ttu-id="74ba7-117">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Tracking**</span><span class="sxs-lookup"><span data-stu-id="74ba7-117">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Tracking**</span></span>  
  
7.  <span data-ttu-id="74ba7-118">在**編輯**功能表上，指向**新增**，然後按一下  **DWORD 值**。</span><span class="sxs-lookup"><span data-stu-id="74ba7-118">On the **Edit** menu, point to **New**, and then click **DWORD Value**.</span></span>  
  
8.  <span data-ttu-id="74ba7-119">型別**ConnectionTimeout**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="74ba7-119">Type **ConnectionTimeout**, and then press ENTER.</span></span>  
  
9. <span data-ttu-id="74ba7-120">以滑鼠右鍵按一下**ConnectionTimeout**，然後按一下 **修改**。</span><span class="sxs-lookup"><span data-stu-id="74ba7-120">Right-click **ConnectionTimeout**, and then click **Modify**.</span></span>  
  
10. <span data-ttu-id="74ba7-121">在**編輯 DWORD 值**對話方塊中，按一下 **十進位**。</span><span class="sxs-lookup"><span data-stu-id="74ba7-121">In the **Edit DWORD Value** dialog box, click **Decimal**.</span></span>  
  
11. <span data-ttu-id="74ba7-122">在**數值資料**方塊中，輸入值以秒為單位，您想要設定查詢逾時值，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="74ba7-122">In the **Value data** box, type the value in seconds that you want to set for the query timeout value, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="74ba7-123">在 **[檔案]** 功能表上按一下 **[結束]**。</span><span class="sxs-lookup"><span data-stu-id="74ba7-123">On the **File** menu, click **Exit**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="74ba7-124">您可能需要先關閉再重新開啟 BizTalk Server 管理主控台中新的逾時值的訂單才會生效。</span><span class="sxs-lookup"><span data-stu-id="74ba7-124">You may need to close and then reopen the BizTalk Server Administration Console in order for the new timeout value to take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ba7-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74ba7-125">See Also</span></span>  
 [<span data-ttu-id="74ba7-126">檢視歷程記錄和追蹤資料</span><span class="sxs-lookup"><span data-stu-id="74ba7-126">Viewing Historical and Tracked Data</span></span>](../core/viewing-historical-and-tracked-data.md)