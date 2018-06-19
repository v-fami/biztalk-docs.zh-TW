---
title: 背景資訊的範例案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security examples [TMA], background information
- DFD
- TMA, examples
ms.assetid: f9518fe7-9892-44f5-8e05-fe48bdb5161a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13dbb247e42116d5b308170d5ef365ed9f20d793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231734"
---
# <a name="background-information-for-sample-scenarios"></a><span data-ttu-id="25b42-102">範例實例的背景資訊</span><span class="sxs-lookup"><span data-stu-id="25b42-102">Background Information for Sample Scenarios</span></span>
<span data-ttu-id="25b42-103">本主題包含本節中實例的背景資訊。</span><span class="sxs-lookup"><span data-stu-id="25b42-103">This topic contains background information for the scenarios in this section.</span></span>  
  
## <a name="background-for-all-scenarios"></a><span data-ttu-id="25b42-104">所有實例的背景</span><span class="sxs-lookup"><span data-stu-id="25b42-104">Background for all scenarios</span></span>  
 <span data-ttu-id="25b42-105">在召開主要威脅模型會議之前，我們先收集下列背景資訊。</span><span class="sxs-lookup"><span data-stu-id="25b42-105">Before the main threat model meeting, we collected the following background information.</span></span> <span data-ttu-id="25b42-106">此資訊適用於我們為範例架構識別的所有使用實例：</span><span class="sxs-lookup"><span data-stu-id="25b42-106">This information applies to all the usage scenarios we identified for the sample architecture:</span></span>  
  
-   <span data-ttu-id="25b42-107">架構的界限與範圍</span><span class="sxs-lookup"><span data-stu-id="25b42-107">Boundaries and scope of the architecture</span></span>  
  
-   <span data-ttu-id="25b42-108">信任與不信任元件之間的界限</span><span class="sxs-lookup"><span data-stu-id="25b42-108">Boundaries between trusted and untrusted components</span></span>  
  
-   <span data-ttu-id="25b42-109">每個元件的組態與管理模型</span><span class="sxs-lookup"><span data-stu-id="25b42-109">Configuration and administration model for each component</span></span>  
  
-   <span data-ttu-id="25b42-110">其他元件與應用程式的相關假設</span><span class="sxs-lookup"><span data-stu-id="25b42-110">Assumptions about other components and applications</span></span>  
  
### <a name="boundaries-and-scope-of-the-architecture"></a><span data-ttu-id="25b42-111">架構的界限與範圍</span><span class="sxs-lookup"><span data-stu-id="25b42-111">Boundaries and scope of the architecture</span></span>  
  
-   <span data-ttu-id="25b42-112">防火牆 2 協助從環境中的周邊網路與任何其他網域 (例如公司網域或其他應用程式的網域)，來保護電子商務網域中的伺服器與應用程式。</span><span class="sxs-lookup"><span data-stu-id="25b42-112">Firewall 2 helps protect the servers and applications in the E-Business domain both from the perimeter network and from any other domains in your environment (for example, a corporate domain or domains for other applications).</span></span>  
  
-   <span data-ttu-id="25b42-113">防火牆 2 路由所有輸入與輸出流量至電子商務網域。</span><span class="sxs-lookup"><span data-stu-id="25b42-113">Firewall 2 routes all incoming and outgoing traffic to the E-Business domain.</span></span>  
  
-   <span data-ttu-id="25b42-114">存取 BizTalk Server 環境的所有使用者群組與帳戶都必須是電子商務網域中的全域群組。</span><span class="sxs-lookup"><span data-stu-id="25b42-114">All user groups and accounts that access the BizTalk Server environment must be global groups in the E-Business domain.</span></span>  
  
-   <span data-ttu-id="25b42-115">限制主控件執行個體服務帳戶的存取；僅限放置訊息在檔案、SQL 或訊息佇列接收伺服器的任何應用程式；以及 BizTalk Server、企業單一登入 (SSO) 與 Windows 的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="25b42-115">Access is limited to the service account for the host instance; any applications that drop messages in the receive server for File, SQL, or Message Queuing; and administrators for BizTalk Server, Enterprise Single Sign-On (SSO), and Windows.</span></span>  
  
### <a name="boundaries-between-trusted-and-untrusted-companies"></a><span data-ttu-id="25b42-116">信任與不信任公司之間的界限</span><span class="sxs-lookup"><span data-stu-id="25b42-116">Boundaries between trusted and untrusted companies</span></span>  
  
-   <span data-ttu-id="25b42-117">防火牆 2 路由所有輸入與輸出流量至電子商務網域。</span><span class="sxs-lookup"><span data-stu-id="25b42-117">Firewall 2 routes all incoming and outgoing traffic to the E-Business domain.</span></span>  
  
-   <span data-ttu-id="25b42-118">使用不同的 BizTalk 主控件做為 BizTalk Server 中應用程式之間的安全性界限。</span><span class="sxs-lookup"><span data-stu-id="25b42-118">Use different BizTalk Hosts as a security boundary between applications within BizTalk Server.</span></span>  
  
-   <span data-ttu-id="25b42-119">只有當您信任應用程式中的程式碼時才使用信任的主控件 (例如，不要在信任的主控件中執行協力廠商元件)。</span><span class="sxs-lookup"><span data-stu-id="25b42-119">Use trusted hosts only when you trust the code within the application (for example, do not run third-party components in a trusted host).</span></span>  
  
### <a name="configuration-and-administration-model-for-each-component"></a><span data-ttu-id="25b42-120">每個元件的組態與管理模型</span><span class="sxs-lookup"><span data-stu-id="25b42-120">Configuration and administration model for each component</span></span>  
 <span data-ttu-id="25b42-121">**組態模型：**</span><span class="sxs-lookup"><span data-stu-id="25b42-121">**Configuration model:**</span></span>  
  
-   <span data-ttu-id="25b42-122">BizTalk Server 執行階段元件只安裝在 BizTalk Server 上。</span><span class="sxs-lookup"><span data-stu-id="25b42-122">BizTalk Server runtime components are installed only on the BizTalk Servers.</span></span>  
  
-   <span data-ttu-id="25b42-123">主要密碼伺服器沒有其他元件。</span><span class="sxs-lookup"><span data-stu-id="25b42-123">Master secret server has no additional components.</span></span>  
  
-   <span data-ttu-id="25b42-124">SQL Server 包含所有 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="25b42-124">SQL Server contains all BizTalk Server databases.</span></span>  
  
-   <span data-ttu-id="25b42-125">周邊網路中的伺服器沒有任何 BizTalk Server 元件。</span><span class="sxs-lookup"><span data-stu-id="25b42-125">Servers in the perimeter networks do not have any BizTalk Server components.</span></span>  
  
-   <span data-ttu-id="25b42-126">管理用戶端是用來管理電子商務網域中的所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="25b42-126">Administration client is used to administer all servers in the E-Business domain.</span></span>  
  
 <span data-ttu-id="25b42-127">**系統管理模型：**</span><span class="sxs-lookup"><span data-stu-id="25b42-127">**Administration model:**</span></span>  
  
-   <span data-ttu-id="25b42-128">系統管理員從桌上型 (或膝上型) 電腦連接到擁有管理工具的電腦 (使用「終端服務」或「遠端桌面」連線)。</span><span class="sxs-lookup"><span data-stu-id="25b42-128">From a desktop (or laptop), an administrator connects to the computer that has the administration tools (using either Terminal Services or Remote Desktop connection).</span></span> <span data-ttu-id="25b42-129">系統管理員連接到擁有管理工具的電腦之後，系統管理員便可使用 BizTalk 管理工具，來管理網域中所有的伺服器與應用程式。</span><span class="sxs-lookup"><span data-stu-id="25b42-129">After the administrator connects to the computer that has the administration tools, the administrator can use the BizTalk Administration tools to manage all servers and applications within the domain.</span></span>  
  
### <a name="assumptions-about-other-components-and-applications"></a><span data-ttu-id="25b42-130">其他元件與應用程式的相關假設</span><span class="sxs-lookup"><span data-stu-id="25b42-130">Assumptions about other components and applications</span></span>  
 <span data-ttu-id="25b42-131">與 BizTalk Server 環境互動的所有其他應用程式與元件在電子商務網域以外的網域中 (例如在周邊網路)。</span><span class="sxs-lookup"><span data-stu-id="25b42-131">All other applications and components that interact with the BizTalk Server environment are in a domain other than the E-Business domain (for example, in a perimeter network).</span></span> <span data-ttu-id="25b42-132">從那些應用程式與元件往返 BizTalk Server 環境的流量都會通過防火牆 2。</span><span class="sxs-lookup"><span data-stu-id="25b42-132">The traffic from those applications and components to and from the BizTalk Server environment goes through Firewall 2.</span></span>  
  
 <span data-ttu-id="25b42-133">BizTalk Server 的任何協力廠商應用程式都來自信任的廠商。</span><span class="sxs-lookup"><span data-stu-id="25b42-133">Any third-party applications for BizTalk Server come from a trusted vendor.</span></span>  
  
### <a name="data-flow-diagrams"></a><span data-ttu-id="25b42-134">資料流程圖</span><span class="sxs-lookup"><span data-stu-id="25b42-134">Data flow diagrams</span></span>  
 <span data-ttu-id="25b42-135">每個使用實例的背景資訊的最終項目是資料流程圖 (DFD)。</span><span class="sxs-lookup"><span data-stu-id="25b42-135">The final element of background information for each usage scenario is a data flow diagram (DFD).</span></span> <span data-ttu-id="25b42-136">DFD 說明資料如何通過此架構。</span><span class="sxs-lookup"><span data-stu-id="25b42-136">A DFD illustrates how data flows through the architecture.</span></span> <span data-ttu-id="25b42-137">每個實例都有不同的 DFD。</span><span class="sxs-lookup"><span data-stu-id="25b42-137">Each scenario has a different DFD.</span></span> <span data-ttu-id="25b42-138">在此文件中，資料流程圖包含下圖所示的項目。</span><span class="sxs-lookup"><span data-stu-id="25b42-138">In this document, the data flow diagrams contain the elements shown in the following figure.</span></span>  
  
 <span data-ttu-id="25b42-139">**圖 1 DFD 的項目**</span><span class="sxs-lookup"><span data-stu-id="25b42-139">**Figure 1 Elements of the DFD**</span></span>  
  
 <span data-ttu-id="25b42-140">![DFD 的項目](../core/media/tdi-sec-dfd-legend.gif "TDI_Sec_DFD_Legend")</span><span class="sxs-lookup"><span data-stu-id="25b42-140">![Elements of the DFD](../core/media/tdi-sec-dfd-legend.gif "TDI_Sec_DFD_Legend")</span></span>  
  
## <a name="background-for-adapter-scenarios"></a><span data-ttu-id="25b42-141">配接器實例的背景</span><span class="sxs-lookup"><span data-stu-id="25b42-141">Background for adapter scenarios</span></span>  
 <span data-ttu-id="25b42-142">在範例架構中，我們根據您可用的一些配接器來識別下列使用實例：</span><span class="sxs-lookup"><span data-stu-id="25b42-142">In our sample architecture, we identified the following usage scenarios based on some of the adapters you can use out-of-the-box:</span></span>  
  
-   <span data-ttu-id="25b42-143">HTTP 與 SOAP (Web 服務) 配接器實例</span><span class="sxs-lookup"><span data-stu-id="25b42-143">HTTP and SOAP (Web services) adapters scenario</span></span>  
  
-   <span data-ttu-id="25b42-144">BizTalk 訊息佇列配接器實例</span><span class="sxs-lookup"><span data-stu-id="25b42-144">BizTalk Message Queuing adapter scenario</span></span>  
  
-   <span data-ttu-id="25b42-145">FILE 配接器實例</span><span class="sxs-lookup"><span data-stu-id="25b42-145">File adapter scenario</span></span>  
  
-   <span data-ttu-id="25b42-146">FTP 配接器實例</span><span class="sxs-lookup"><span data-stu-id="25b42-146">FTP adapter scenario</span></span>  
  
 <span data-ttu-id="25b42-147">對於每個實例，我們遵循下列步驟來完成威脅模型分析：</span><span class="sxs-lookup"><span data-stu-id="25b42-147">For each scenario, we followed these steps to complete the threat model analysis:</span></span>  
  
-   <span data-ttu-id="25b42-148">收集背景資訊</span><span class="sxs-lookup"><span data-stu-id="25b42-148">Collect background information</span></span>  
  
-   <span data-ttu-id="25b42-149">建立和分析威脅模型</span><span class="sxs-lookup"><span data-stu-id="25b42-149">Create and analyze the threat model</span></span>  
  
-   <span data-ttu-id="25b42-150">檢視威脅</span><span class="sxs-lookup"><span data-stu-id="25b42-150">Review threats</span></span>  
  
-   <span data-ttu-id="25b42-151">識別防護技巧與技術</span><span class="sxs-lookup"><span data-stu-id="25b42-151">Identify mitigation techniques and technologies</span></span>  
  
 <span data-ttu-id="25b42-152">對於每個實例，我們已經嘗試開發各種攻擊可能代表的一般威脅層級的評比等級。</span><span class="sxs-lookup"><span data-stu-id="25b42-152">For each scenario, we have tried to develop generic ratings of the level of threat that the various attacks might represent.</span></span> <span data-ttu-id="25b42-153">不過，您所在的環境或經驗可能讓您覺得特定的威脅應該不同於我們所提供的評比等級。</span><span class="sxs-lookup"><span data-stu-id="25b42-153">However, your environment or experience might suggest that a particular threat deserves a different rating than we have given it.</span></span> <span data-ttu-id="25b42-154">至於所有的安全性實例，您自己所擁有的資料對於決定威脅層級是最可信的，所以建議您使用我們的分析與結果做為指南，進行自己的分析。</span><span class="sxs-lookup"><span data-stu-id="25b42-154">As with all security scenarios, your own data is the most robust to determine threat levels, and we recommend that you conduct your own analysis, using our analysis and results as a guide.</span></span>  
  
 <span data-ttu-id="25b42-155">背景資訊，除了資料流程圖 (DFD) 之外，也適用於所有使用實例。</span><span class="sxs-lookup"><span data-stu-id="25b42-155">The background information—except for the data flow diagram (DFD)—is the same for all our usage scenarios.</span></span> <span data-ttu-id="25b42-156">下一節將顯示每個實例的 DFD。</span><span class="sxs-lookup"><span data-stu-id="25b42-156">In the next sections we show the DFD for each scenario.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b42-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25b42-157">See Also</span></span>  
 <span data-ttu-id="25b42-158">[威脅模型分析](../core/threat-model-analysis.md) </span><span class="sxs-lookup"><span data-stu-id="25b42-158">[Threat Model Analysis](../core/threat-model-analysis.md) </span></span>  
 <span data-ttu-id="25b42-159">[威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md) </span><span class="sxs-lookup"><span data-stu-id="25b42-159">[Sample Scenarios for Threat Model Analysis](../core/sample-scenarios-for-threat-model-analysis.md) </span></span>  
 <span data-ttu-id="25b42-160">[安全性規劃](../core/planning-for-security.md) </span><span class="sxs-lookup"><span data-stu-id="25b42-160">[Planning for Security](../core/planning-for-security.md) </span></span>  
 [<span data-ttu-id="25b42-161">小型與中型公司的範例架構</span><span class="sxs-lookup"><span data-stu-id="25b42-161">Sample Architectures for Small & Medium-Sized Companies</span></span>](../core/sample-architectures-for-small-medium-sized-companies.md)