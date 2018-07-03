---
title: 如何檢視 BAM 彙總 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], viewing aggregations
- viewing, aggregations [BAM]
ms.assetid: aa697f16-ac47-46f9-98a5-a951961d0413
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c30ef9b9cb5604936f5cd71bcecdc7068c54744
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006439"
---
# <a name="how-to-view-bam-aggregations"></a><span data-ttu-id="98fbc-102">如何檢視 BAM 彙總</span><span class="sxs-lookup"><span data-stu-id="98fbc-102">How to View BAM Aggregations</span></span>
<span data-ttu-id="98fbc-103">BAM 彙總是由商務分析師在 Excel 中使用 Excel 增益集所定義。</span><span class="sxs-lookup"><span data-stu-id="98fbc-103">BAM aggregations are defined by the business analyst in Excel using the Excel add-in.</span></span>  
  
### <a name="to-view-your-bam-aggregations"></a><span data-ttu-id="98fbc-104">檢視 BAM 彙總</span><span class="sxs-lookup"><span data-stu-id="98fbc-104">To view your BAM aggregations</span></span>  
  
1. <span data-ttu-id="98fbc-105">在執行電腦上[!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]; 按一下**開始**，指向**所有程式**，以滑鼠右鍵按一下**Internet Explorer**，然後按一下 **身分執行系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="98fbc-105">On Computers running [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]; click **Start**, point to **All Programs**, right-click **Internet Explorer**, and then click **Run as administrator**.</span></span> <span data-ttu-id="98fbc-106">在 [**使用者帳戶控制**] 對話方塊中，按一下**繼續**。</span><span class="sxs-lookup"><span data-stu-id="98fbc-106">In the **User Account Control** dialog box, click **Continue**.</span></span> <span data-ttu-id="98fbc-107">在 Internet Explorer 網址列中，輸入`http://<server>/BAM/`，其中 *\<server >* 是正在執行 BAM 入口網站之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="98fbc-107">In the Internet Explorer address bar, type `http://<server>/BAM/`, where *\<server>* is the name of the computer that is running the BAM portal.</span></span>  
  
    <span data-ttu-id="98fbc-108">-或-</span><span class="sxs-lookup"><span data-stu-id="98fbc-108">-- or --</span></span>  
  
    <span data-ttu-id="98fbc-109">按一下 **開始**，按一下**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BAM 入口網站**。</span><span class="sxs-lookup"><span data-stu-id="98fbc-109">Click **Start**, click **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BAM Portal Web Site**.</span></span>  
  
2. <span data-ttu-id="98fbc-110">從**我的檢視**瀏覽窗格中，按一下檢視，即可展開檢視來顯示工作清單。</span><span class="sxs-lookup"><span data-stu-id="98fbc-110">From the **MyViews** navigation pane, click a view to expand the view to show the task list.</span></span>  
  
3. <span data-ttu-id="98fbc-111">按一下 **彙總**工作以展開的清單定義彙總。</span><span class="sxs-lookup"><span data-stu-id="98fbc-111">Click the **Aggregations** task to expand the list of defined aggregations.</span></span>  
  
4. <span data-ttu-id="98fbc-112">按一下列出的彙總，將該項彙總載入至 BAM 入口網站的內容框架中。</span><span class="sxs-lookup"><span data-stu-id="98fbc-112">Click an aggregation listed to load the aggregation in the content frame of the BAM portal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98fbc-113">如果沒有顯示任何檢視，原因可能是因為尚未建立檢視 (通常是商務分析師的工作)，或尚未授與該使用者權限 (通常是系統管理員的工作)。</span><span class="sxs-lookup"><span data-stu-id="98fbc-113">If there are no views shown, then either views have not been created, a task typically performed by a business analyst, or permissions have not been granted to the user, a task typically performed by an administrator.</span></span>  
  
 <span data-ttu-id="98fbc-114">如需您可以執行與即時資料活頁簿的詳細資訊，請參閱[檢視即時 BAM 資料](../core/viewing-live-bam-data.md)。</span><span class="sxs-lookup"><span data-stu-id="98fbc-114">For more information about what you can do with the live data workbooks, see [Viewing Live BAM Data](../core/viewing-live-bam-data.md).</span></span>  
  
 <span data-ttu-id="98fbc-115">下圖顯示預先計算的 BAM 彙總。</span><span class="sxs-lookup"><span data-stu-id="98fbc-115">The following figure shows pre-calculated BAM aggregations.</span></span>  
  
 <span data-ttu-id="98fbc-116">![](../core/media/bam-olap-cube.gif "bam_olap_cube")</span><span class="sxs-lookup"><span data-stu-id="98fbc-116">![](../core/media/bam-olap-cube.gif "bam_olap_cube")</span></span>  
<span data-ttu-id="98fbc-117">預先計算的 BAM 彙總</span><span class="sxs-lookup"><span data-stu-id="98fbc-117">Pre-calculated BAM aggregations</span></span>