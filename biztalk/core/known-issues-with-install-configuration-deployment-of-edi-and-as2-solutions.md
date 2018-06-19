---
title: 安裝、 設定及部署 EDI 和 AS2 解決方案的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2dee03f0-2447-4cc2-90f4-e9b73caa0f39
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 406e69cafd4822a0f8f436b471d53c4e815dce32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262798"
---
# <a name="known-issues-with-installation-configuration-and-deployment-of-edi-and-as2-solutions"></a><span data-ttu-id="67886-102">安裝、組態及部署 EDI 和 AS2 解決方案的已知問題</span><span class="sxs-lookup"><span data-stu-id="67886-102">Known Issues with Installation, Configuration, and Deployment of EDI and AS2 Solutions</span></span>
<span data-ttu-id="67886-103">本主題描述部署和管理方面的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 和 AS2 解決方案。</span><span class="sxs-lookup"><span data-stu-id="67886-103">This topic describes known issues with deployment and management of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 solutions.</span></span>  
  
## <a name="blank-strings-were-imported-for-party-properties"></a><span data-ttu-id="67886-104">針對合作對象屬性匯入空白字串</span><span class="sxs-lookup"><span data-stu-id="67886-104">Blank Strings Were Imported for Party Properties</span></span>  
 <span data-ttu-id="67886-105">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="67886-105">**Symptom**</span></span>  
  
 <span data-ttu-id="67886-106">當您從繫結檔將 EDI/AS2 繫結匯入至 BizTalk 應用程式時，並不會匯入機密的合作對象屬性，例如密碼或安全性/驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="67886-106">When you imported EDI/AS2 bindings from a binding file into a BizTalk application, sensitive party properties, such as passwords or security/authentication information, were not imported.</span></span> <span data-ttu-id="67886-107">這些屬性會設為空白字串。</span><span class="sxs-lookup"><span data-stu-id="67886-107">Those properties were set to blank strings.</span></span>  
  
 <span data-ttu-id="67886-108">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="67886-108">**Possible Cause**</span></span>  
  
 <span data-ttu-id="67886-109">BizTalk Server 不會匯入這些機密欄位的設定。</span><span class="sxs-lookup"><span data-stu-id="67886-109">BizTalk Server will not import the settings of sensitive fields.</span></span> <span data-ttu-id="67886-110">匯入這些設定可能製造安全性問題。</span><span class="sxs-lookup"><span data-stu-id="67886-110">Importing those settings could create a security issue.</span></span>  
  
 <span data-ttu-id="67886-111">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="67886-111">**Resolution**</span></span>  
  
 <span data-ttu-id="67886-112">您必須在將繫結匯入至另一部電腦之後，手動設定 EDI 機密欄位的值。</span><span class="sxs-lookup"><span data-stu-id="67886-112">You must manually set the values for EDI sensitive fields after importing the bindings onto another computer.</span></span>  
  
## <a name="ftp-adapter-is-not-supported-natively-in-64-bit-mode"></a><span data-ttu-id="67886-113">64 位元模式本身不支援 FTP 配接器</span><span class="sxs-lookup"><span data-stu-id="67886-113">FTP Adapter Is Not Supported Natively in 64-bit Mode</span></span>  
 <span data-ttu-id="67886-114">FTP 配接器無法以原生 64 位元模式執行。</span><span class="sxs-lookup"><span data-stu-id="67886-114">The FTP adapter cannot run in native 64-bit mode.</span></span> <span data-ttu-id="67886-115">如果您使用 FTP 配接器中的 EDI 解決方案中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須在 64 位元 Windows 上 WOW64 上執行它。</span><span class="sxs-lookup"><span data-stu-id="67886-115">If you use an FTP adapter in your EDI solution in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you will have to run it on WOW64 on 64-bit Windows.</span></span>  
  
## <a name="some-edias2-artifacts-are-still-active-after-unconfiguring"></a><span data-ttu-id="67886-116">一些 EDI/AS2 成品在取消設定後依然在作用中</span><span class="sxs-lookup"><span data-stu-id="67886-116">Some EDI/AS2 Artifacts Are Still Active After Unconfiguring</span></span>  
 <span data-ttu-id="67886-117">您取消設定 Microsoft EDI/AS2 功能之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，某些與 EDI 和 AS2 處理相關的 BizTalk Server 成品仍會在 BizTalk 群組組態的內容中使用。</span><span class="sxs-lookup"><span data-stu-id="67886-117">After you unconfigure the Microsoft EDI/AS2 feature of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], some BizTalk Server artifacts related to EDI and AS2 processing will still be active in the context of the BizTalk group configuration.</span></span> <span data-ttu-id="67886-118">這些成品將會包括 EDI 和 AS2 管線，以及批次協調流程。</span><span class="sxs-lookup"><span data-stu-id="67886-118">These artifacts will include EDI and AS2 pipelines and the batching orchestration.</span></span> <span data-ttu-id="67886-119">因此，即使在取消設定 Microsoft EDI/AS2 功能後，您依然能夠執行基本的 EDI 和 AS2 處理。</span><span class="sxs-lookup"><span data-stu-id="67886-119">As a result, you will still be able to perform basic EDI and AS2 processing even after unconfiguring the Microsoft EDI/AS2 feature.</span></span> <span data-ttu-id="67886-120">若要停用此功能，您應停用、停止或刪除與 EDI 和 AS2 處理相關的連接埠。</span><span class="sxs-lookup"><span data-stu-id="67886-120">To disable this functionality, you should disable, stop, or delete the ports associated with EDI and AS2 processing.</span></span>  
  
## <a name="you-receive-the-error-failed-to-configure-edias2-status-reporting-functionalities"></a><span data-ttu-id="67886-121">您會收到 「 無法設定 EDI/AS2 狀態報告功能 」 錯誤</span><span class="sxs-lookup"><span data-stu-id="67886-121">You Receive the Error "Failed to Configure EDI/AS2 Status Reporting Functionalities"</span></span>  
 <span data-ttu-id="67886-122">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="67886-122">**Symptom**</span></span>  
  
 <span data-ttu-id="67886-123">設定「EDI/AS2 Runtime 狀態報告」時，您收到「無法設定 EDI/AS2 狀態報告功能」錯誤。</span><span class="sxs-lookup"><span data-stu-id="67886-123">When configuring EDI/AS2 Runtime Status Reporting, you receive error "Failed to Configure EDI/AS2 Status Reporting Functionalities".</span></span>  
  
 <span data-ttu-id="67886-124">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="67886-124">**Possible Cause**</span></span>  
  
 <span data-ttu-id="67886-125">如果您之前設定了 [BAM 工具] 然後解除設定，就可能會收到此錯誤。</span><span class="sxs-lookup"><span data-stu-id="67886-125">You can receive this error if BAM Tools was previously configured and then unconfigured.</span></span>  
  
 <span data-ttu-id="67886-126">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="67886-126">**Resolution**</span></span>  
  
 <span data-ttu-id="67886-127">請在設定 EDI 和 (或) AS2 狀態報告之前，先設定 [BAM 工具]。</span><span class="sxs-lookup"><span data-stu-id="67886-127">Configure BAM Tools prior to configuring EDI and/or AS2 status reporting.</span></span>  
  
## <a name="recovering-a-deleted-artifact-from-the-biztalk-edi-application-requires-you-to-reconfigure-the-edias2-runtime"></a><span data-ttu-id="67886-128">復原刪除的成品從 「 BizTalk EDI 應用程式會要求您重新設定 EDI/AS2 執行階段</span><span class="sxs-lookup"><span data-stu-id="67886-128">Recovering a Deleted Artifact From the BizTalk EDI Application Requires You to Reconfigure the EDI/AS2 Runtime</span></span>  
 <span data-ttu-id="67886-129">您應避免針對自己的成品使用 BizTalk EDI 應用程式。</span><span class="sxs-lookup"><span data-stu-id="67886-129">You should avoid using the BizTalk EDI Application for your own artifacts.</span></span> <span data-ttu-id="67886-130">此應用程式包含 EDI/AS2 設定期間部署的 EDI/AS2 成品。</span><span class="sxs-lookup"><span data-stu-id="67886-130">This application contains the EDI/AS2 artifacts that are deployed during EDI/AS2 configuration.</span></span> <span data-ttu-id="67886-131">建議的方法是建立另一個應用程式，並且新增 BizTalk EDI 應用程式的參考至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="67886-131">The recommended approach is to create a separate application and add a reference to BizTalk EDI Application to your application.</span></span> <span data-ttu-id="67886-132">不過，如果您從 BizTalk EDI 應用程式刪除任何 EDI/AS2 成品，可透過在群組中的每部執行階段電腦上取消設定 BizTalk EDI/AS2 執行階段 (或是透過從群組取消設定 EDI/AS2 執行階段，以及在每一部可存取的執行階段電腦上取消設定 EDI/AS2 執行階段) 的方式從該狀態復原。</span><span class="sxs-lookup"><span data-stu-id="67886-132">However, if you delete any EDI/AS2 artifact from BizTalk EDI Application, you can recover from that state by unconfiguring the BizTalk EDI/AS2 runtime from each runtime computer in the group (or by unconfiguring the EDI/AS2 runtime from the group and unconfiguring the EDI/AS2 runtime on each of the reachable runtime computers).</span></span> <span data-ttu-id="67886-133">建議您不要刪除資料庫或 EDI/AS2 BAM 活動，以避免資料遺失。</span><span class="sxs-lookup"><span data-stu-id="67886-133">It is recommended that you do not delete your databases or the EDI/AS2 BAM activities to prevent data loss.</span></span> <span data-ttu-id="67886-134">然後，您可以在群組中的所有執行階段電腦上重新設定 EDI/AS2 執行階段，以復原刪除的 EDI/AS2 成品。</span><span class="sxs-lookup"><span data-stu-id="67886-134">You can then reconfigure the EDI/AS2 runtime on all the runtime computers in the group to recover the deleted EDI/AS2 artifacts.</span></span>  
  
## <a name="numeric-transaction-set-group-control-and-interchange-control-values-may-be-truncated"></a><span data-ttu-id="67886-135">數字的交易集、 群組控制項和交換控制項的值可能被截斷</span><span class="sxs-lookup"><span data-stu-id="67886-135">Numeric Transaction Set, Group Control and Interchange Control Values May be Truncated</span></span>  
 <span data-ttu-id="67886-136">交易集參考編號的交換控制編號值範圍欄位，以及群組控制編號可讓您輸入超過最大允許值的值。</span><span class="sxs-lookup"><span data-stu-id="67886-136">The value range fields for interchange control numbers, transaction set reference numbers, and group control numbers allow you to enter values that exceed the maximum allowed value.</span></span> <span data-ttu-id="67886-137">當您儲存設定時，這些值會被截斷的最大值。</span><span class="sxs-lookup"><span data-stu-id="67886-137">When you save the configuration, these values will be truncated to the maximum value.</span></span>  
  
 <span data-ttu-id="67886-138">X12 的最大值屬性欄位是 999999999。</span><span class="sxs-lookup"><span data-stu-id="67886-138">The maximum value for X12 property fields is 999999999.</span></span>  
  
 <span data-ttu-id="67886-139">EDIFACT 屬性欄位的最大值是 99999999999999。</span><span class="sxs-lookup"><span data-stu-id="67886-139">The maximum value for EDIFACT property fields is 99999999999999.</span></span>  
  
## <a name="control-numbers-are-reset-to-1-after-upgrade"></a><span data-ttu-id="67886-140">控制編號重設為 1 之後升級</span><span class="sxs-lookup"><span data-stu-id="67886-140">Control Numbers are Reset to 1 After Upgrade</span></span>  
 <span data-ttu-id="67886-141">在升級之後，您可能會注意到所有顯示的合作對象的 EDI 內容中的控制編號重設的預設最小值為 1，並顯示 999999999 (X12) 或 99999999999999 (EDIFACT) 的預設最大值。</span><span class="sxs-lookup"><span data-stu-id="67886-141">After upgrading, you may notice that all control numbers displayed in the EDI Properties of a party have been reset to the default minimum value of 1 and display a default maximum value of 999999999 (X12) or 99999999999999 (EDIFACT).</span></span> <span data-ttu-id="67886-142">任何前置詞或後置詞的值會在升級之後維持相同。</span><span class="sxs-lookup"><span data-stu-id="67886-142">Any prefix or suffix values will remain the same after upgrade.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="67886-143">顯示用於控制編號的最小和最大值。</span><span class="sxs-lookup"><span data-stu-id="67886-143"> shows the minimum and maximum values to be used for the control number.</span></span> <span data-ttu-id="67886-144">升級; 期間，將保留目前的控制編號不過它不會顯示合作對象的 EDI 屬性中。</span><span class="sxs-lookup"><span data-stu-id="67886-144">The current control number will be preserved during upgrade; however it is not displayed in the EDI Properties of the party.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67886-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67886-145">See Also</span></span>  
 <span data-ttu-id="67886-146">[疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="67886-146">[Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md) </span></span>  
 <span data-ttu-id="67886-147">[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span><span class="sxs-lookup"><span data-stu-id="67886-147">[Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span></span>  
 <span data-ttu-id="67886-148">[BizTalk Server 2013 和 2013 R2 設定概觀](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72) </span><span class="sxs-lookup"><span data-stu-id="67886-148">[Configuration Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72) </span></span>  
 [<span data-ttu-id="67886-149">環境最佳化的後續設定步驟</span><span class="sxs-lookup"><span data-stu-id="67886-149">Post-configuration steps to optimize your environment</span></span>](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)