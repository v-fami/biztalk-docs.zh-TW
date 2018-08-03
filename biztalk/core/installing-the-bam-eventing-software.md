---
title: 安裝 Bam-eventing 軟體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3638d34-f5a8-4ffd-99eb-d38aed4c0732
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca5d13e058799113d7847fe6377ce82c7e0a7ea5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000287"
---
# <a name="installing-the-bam-eventing-software"></a><span data-ttu-id="38fa7-102">安裝 BAM-Eventing 軟體</span><span class="sxs-lookup"><span data-stu-id="38fa7-102">Installing the BAM-Eventing Software</span></span>
<span data-ttu-id="38fa7-103">若要使用 BAM-Eventing API 來實作 BAM 方案，或是設定您的 Windows Workflow Foundation 或 Windows Communication Foundation 應用程式來使用 Windows Workflow Foundation 適用的 BAM 攔截器，您必須使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式來安裝 BAM-Eventing 軟體。</span><span class="sxs-lookup"><span data-stu-id="38fa7-103">To implement BAM solutions using the BAM eventing APIs or configure your Windows Workflow Foundation or Windows Communication Foundation application to use the BAM interceptor for Windows Workflow Foundation, you must install the BAM-Eventing software by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Setup program.</span></span> <span data-ttu-id="38fa7-104">這個軟體可以安裝為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段的一部分，或是在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝應用程式中選取 [其他軟體] 底下的 [BAM Eventing Support] 來個別安裝。</span><span class="sxs-lookup"><span data-stu-id="38fa7-104">This software can be installed as part of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime or separately by selecting BAM Eventing Support under Additional Software in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup application.</span></span>  
  
### <a name="to-install-the-bam-eventing-software"></a><span data-ttu-id="38fa7-105">若要安裝 BAM-Eventing 軟體</span><span class="sxs-lookup"><span data-stu-id="38fa7-105">To install the BAM-Eventing software</span></span>  
  
1. <span data-ttu-id="38fa7-106">使用具有系統管理員權限的帳戶登入將裝載 WF 應用程式的電腦。</span><span class="sxs-lookup"><span data-stu-id="38fa7-106">Log on to the computer that will host the WF application using an account that has Administrator privileges.</span></span>  
  
2. <span data-ttu-id="38fa7-107">執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝光碟上的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="38fa7-107">Run the Setup program on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Installation CD.</span></span>  
  
3. <span data-ttu-id="38fa7-108">清除所有選取的選項。</span><span class="sxs-lookup"><span data-stu-id="38fa7-108">Clear all selected options.</span></span> <span data-ttu-id="38fa7-109">如果您不執行這個步驟，您可能會安裝您不需要的軟體。</span><span class="sxs-lookup"><span data-stu-id="38fa7-109">If you do not perform this step, you may install software you do not need.</span></span>  
  
4. <span data-ttu-id="38fa7-110">依序展開**額外的軟體**，然後選取**Bam-eventing**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="38fa7-110">Expand **Additional Software**, and then select the **BAM-Eventing** check box.</span></span>  
  
5. <span data-ttu-id="38fa7-111">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="38fa7-111">Click **Next**.</span></span>  
  
6. <span data-ttu-id="38fa7-112">按一下 **[安裝]**。</span><span class="sxs-lookup"><span data-stu-id="38fa7-112">Click **Install**.</span></span>  
  
7. <span data-ttu-id="38fa7-113">完成安裝程序時，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="38fa7-113">When the installation procedure is complete, click **OK**.</span></span>  
  
    <span data-ttu-id="38fa7-114">BAM-Eventing 軟體現在已經安裝好了。</span><span class="sxs-lookup"><span data-stu-id="38fa7-114">The BAM-Eventing software is now installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38fa7-115">使用這個方法安裝 BAM 攔截器程式庫不需要購買額外的授權。</span><span class="sxs-lookup"><span data-stu-id="38fa7-115">Installing the BAM interceptor library using this method does not require the purchase of additional licenses.</span></span>  
  
 <span data-ttu-id="38fa7-116">如果您對於監控 BAM 攔截器的效能計數器資料感興趣，您必須先使用 InstallUtil.exe 進行註冊。</span><span class="sxs-lookup"><span data-stu-id="38fa7-116">If you are interested in monitoring performance counter data for the BAM interceptors, you must first register them by using InstallUtil.exe.</span></span>  
  
### <a name="to-register-bam-interceptor-performance-counters-by-using-installutilexe"></a><span data-ttu-id="38fa7-117">若要使用 InstallUtil.exe 註冊 BAM 攔截器效能計數器</span><span class="sxs-lookup"><span data-stu-id="38fa7-117">To register BAM interceptor performance counters by using InstallUtil.exe</span></span>  
  
1. <span data-ttu-id="38fa7-118">開始**[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元**身為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="38fa7-118">Start **[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt** as an administrator.</span></span>  
  
2. <span data-ttu-id="38fa7-119">在命令提示字元中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="38fa7-119">At the command prompt, enter the following command:</span></span>  
  
    <span data-ttu-id="38fa7-120">InstallUtil [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\Microsoft.BizTalk.Bam.Interceptors.dll</span><span class="sxs-lookup"><span data-stu-id="38fa7-120">InstallUtil [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\Microsoft.BizTalk.Bam.Interceptors.dll</span></span>  
  
3. <span data-ttu-id="38fa7-121">型別**結束**，然後按 ENTER 關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="38fa7-121">Type **Exit**, and then press ENTER to close the command prompt.</span></span>  
  
    <span data-ttu-id="38fa7-122">現在就可以使用 BAM 攔截器效能計數器。</span><span class="sxs-lookup"><span data-stu-id="38fa7-122">The BAM interceptor performance counters are now available.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38fa7-123">根據預設，只有系統管理員和某些系統帳戶才有記錄效能資料的權限。</span><span class="sxs-lookup"><span data-stu-id="38fa7-123">By default, only Administrators and some system accounts have permission to log performance data.</span></span> <span data-ttu-id="38fa7-124">若要在 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上啟用存取，請將用來執行工作流程應用程式的帳戶加入到 Performance Log Users 群組。</span><span class="sxs-lookup"><span data-stu-id="38fa7-124">To enable access on [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], add the account used for running workflow applications to the Performance Log Users group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38fa7-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38fa7-125">See Also</span></span>  
 <span data-ttu-id="38fa7-126">[實作 BAM 解決方案](../core/implementing-bam-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="38fa7-126">[Implementing BAM Solutions](../core/implementing-bam-solutions.md) </span></span>  
 [<span data-ttu-id="38fa7-127">BizTalk Server 2013 和 2013 R2 的安裝概觀</span><span class="sxs-lookup"><span data-stu-id="38fa7-127">Installation Overview for BizTalk Server 2013 and 2013 R2</span></span>](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)