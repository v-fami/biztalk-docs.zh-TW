---
title: "How to Configure 之間瀏覽分散式活動 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f8faf0a-eb06-4383-932d-4106306d6cf3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ab210f5ab728134b406b5c4bdaf25a1ec6db1c2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-navigation-between-distributed-activities"></a><span data-ttu-id="7407c-102">如何設定分散式活動之間的導覽</span><span class="sxs-lookup"><span data-stu-id="7407c-102">How to Configure Navigation Between Distributed Activities</span></span>
<span data-ttu-id="7407c-103">分散式導覽讓使用者得以檢視現存於遠端 BAM 部署中的活動。</span><span class="sxs-lookup"><span data-stu-id="7407c-103">Distributed navigation allows users to view activities that exist in remote BAM deployments.</span></span> <span data-ttu-id="7407c-104">啟用分散式導覽後，任一部電腦上 BAM 入口網站的使用者都可以檢視其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署中 BAM 入口網站上的活動。</span><span class="sxs-lookup"><span data-stu-id="7407c-104">When you enable distributed navigation, users of the BAM portal on one computer will be able to view activities in the BAM portal on another deployment of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7407c-105">本主題中的程序舉下列實例說明如何啟用分散式導覽：</span><span class="sxs-lookup"><span data-stu-id="7407c-105">The procedure in this topic describes how to enable distributed navigation in the following scenario:</span></span>  
  
-   <span data-ttu-id="7407c-106">業務部門由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署在電腦 1。</span><span class="sxs-lookup"><span data-stu-id="7407c-106">A sales department with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployed on computer 1.</span></span>  
  
-   <span data-ttu-id="7407c-107">貨運部門由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署在電腦 2。</span><span class="sxs-lookup"><span data-stu-id="7407c-107">A shipping department with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployed on computer 2.</span></span>  
  
-   <span data-ttu-id="7407c-108">myBusinessView 檢視連同稱為「銷售資料」的活動部署在電腦 1。</span><span class="sxs-lookup"><span data-stu-id="7407c-108">A view called myBusinessView with an activity called Sales Data deployed on computer 1.</span></span>  
  
-   <span data-ttu-id="7407c-109">myBusinessView 檢視連同稱為「送貨資料」的活動安裝在電腦 2。</span><span class="sxs-lookup"><span data-stu-id="7407c-109">A view called myBusinessView with an activity called Shipping Data installed on computer 2.</span></span>  
  
-   <span data-ttu-id="7407c-110">業務部門的商務使用者基於商務需求而同時查看兩部電腦上的活動。</span><span class="sxs-lookup"><span data-stu-id="7407c-110">A business user in the sales department with a business need to see the activities on both computers.</span></span>  
  
### <a name="how-to-set-up-distributed-navigation-for-remote-activities"></a><span data-ttu-id="7407c-111">如何為遠端活動設定分散式導覽</span><span class="sxs-lookup"><span data-stu-id="7407c-111">How to set up distributed navigation for remote activities</span></span>  
  
1.  <span data-ttu-id="7407c-112">電腦 1 的系統管理員授與商務使用者存取電腦 1 上的 myBusinessView 檢視。</span><span class="sxs-lookup"><span data-stu-id="7407c-112">The administrator of computer 1 grants the business user access to the myBusinessView view on computer 1.</span></span> <span data-ttu-id="7407c-113">使用 bm.exe 命令，如下：**新增帳戶-AccountName:\<帳戶名稱\>-檢視：** myBusinessView</span><span class="sxs-lookup"><span data-stu-id="7407c-113">You use the bm.exe command, as follows: **add-account -AccountName:\<account name\> -View:** myBusinessView</span></span>  
  
2.  <span data-ttu-id="7407c-114">電腦 1 上的系統管理員，如下所示執行啟用參考命令，來啟用分散式的導覽： **bm.exe 啟用參考 TargetServer:** computer2 **-TargetDatabase:\<目標資料庫\>**</span><span class="sxs-lookup"><span data-stu-id="7407c-114">The administrator on computer 1 enables distributed navigation by running the enable reference command, as follows: **bm.exe enable-reference -TargetServer:** computer2 **-TargetDatabase:\<target database\>**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7407c-115">一般來說，跨部門從不同的電腦存取 BAM Web 服務時所用的帳戶會各有不同。</span><span class="sxs-lookup"><span data-stu-id="7407c-115">Typically the account used between departments for BAM Web services access will be different on different computers.</span></span> <span data-ttu-id="7407c-116">因此，在此案例中電腦 1 的系統管理員必須加入 Web 服務模擬帳戶，電腦 1 的電腦 2 的 BAM 主要匯入資料庫的 BAM_ManagementWS 角色。</span><span class="sxs-lookup"><span data-stu-id="7407c-116">Therefore, in this scenario the administrator of computer 1 must add the Web services Impersonation account of computer 1 to the BAM_ManagementWS role of the BAM Primary Import database for computer 2.</span></span> <span data-ttu-id="7407c-117">詳細資訊，請參閱 「 檢視和修改角色成員資格 >，網址[http://go.microsoft.com/fwlink/?LinkId=66990](http://go.microsoft.com/fwlink/?LinkId=66990)。</span><span class="sxs-lookup"><span data-stu-id="7407c-117">For more information, see "Viewing and Modifying Role Memberships" at [http://go.microsoft.com/fwlink/?LinkId=66990](http://go.microsoft.com/fwlink/?LinkId=66990).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7407c-118">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="7407c-118">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
3.  <span data-ttu-id="7407c-119">電腦 2 的系統管理員使用步驟 1 提到的 BM.exe 命令，授與商務使用者存取電腦 2 上的 myBusinessView 檢視。</span><span class="sxs-lookup"><span data-stu-id="7407c-119">The administrator of computer 2 grants the business user access to the myBusinessView view on computer 2 using the BM.exe command as noted in step 1.</span></span>  
  
## <a name="results-of-setting-up-distributed-navigation"></a><span data-ttu-id="7407c-120">設定分散式導覽的結果</span><span class="sxs-lookup"><span data-stu-id="7407c-120">Results of Setting Up Distributed Navigation</span></span>  
 <span data-ttu-id="7407c-121">啟用分散式導覽後，已獲授權存取這兩部電腦上指定檢視的使用者將可在其主要入口網站的 [我的檢視] 窗格中，看到部署在這些電腦上之指定檢視的相關活動。</span><span class="sxs-lookup"><span data-stu-id="7407c-121">When distributed navigation is enabled the users added to the views on both computers will see the activities for the views deployed on both computers in the My Views pane of their home portal.</span></span> <span data-ttu-id="7407c-122">當這些使用者會按一下裝載於遠端部署的活動時，會順暢地導向至入口網站上的活動裝載，並能夠檢視的活動，就好像在其預設入口網站上。</span><span class="sxs-lookup"><span data-stu-id="7407c-122">When these users click an activity that is hosted on a remote deployment, they are seamlessly directed to the portal on which that activity is hosted and they are able to view the activity as if it were on their default portal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7407c-123">您可以雙向啟用分散式導覽。</span><span class="sxs-lookup"><span data-stu-id="7407c-123">Distributed navigation can be enabled in both directions.</span></span> <span data-ttu-id="7407c-124">若同時在共用遠端活動的兩部電腦上執行上述程序，則任一電腦之入口網站的商務使用者皆可使用分散式導覽。</span><span class="sxs-lookup"><span data-stu-id="7407c-124">Following the procedure above on both computers that are sharing remote activities enables business users of the portals on either computer to use distributed navigation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7407c-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="7407c-125">See Also</span></span>  
 <span data-ttu-id="7407c-126">[管理遠端活動的分散式的導覽](../core/managing-distributed-navigation-of-remote-activities.md) </span><span class="sxs-lookup"><span data-stu-id="7407c-126">[Managing Distributed Navigation of Remote Activities](../core/managing-distributed-navigation-of-remote-activities.md) </span></span>  
 [<span data-ttu-id="7407c-127">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="7407c-127">BAM Portal</span></span>](../core/bam-portal.md)