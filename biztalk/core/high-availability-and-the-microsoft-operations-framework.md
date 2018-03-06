---
title: "高可用性和 Microsoft Operations Framework |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d8bae3-b241-4371-b8fc-a9cbdca6b495
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a06bdadb026617dc55ed40d03e0344584111a0c
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="high-availability-and-the-microsoft-operations-framework"></a><span data-ttu-id="44daf-102">高可用性與 Microsoft Operations Framework</span><span class="sxs-lookup"><span data-stu-id="44daf-102">High Availability and the Microsoft Operations Framework</span></span>
<span data-ttu-id="44daf-103">Microsoft Operations Framework (MOF) 處理序模型套用之規劃與實作高可用性的 Microsoft BizTalk Server 解決方案可以幫助您確定在發行生命週期的不同階段具有適當的程序。</span><span class="sxs-lookup"><span data-stu-id="44daf-103">Applying the Microsoft Operations Framework (MOF) process model to the planning and implementation of a highly available Microsoft BizTalk Server solution can help you make sure that you have appropriate processes at the different stages of the release life cycle.</span></span> <span data-ttu-id="44daf-104">藉由觀察所有出現高可用性的生命週期階段，您可以讓環境中的安裝、維護和疑難排解可用性問題更為容易。</span><span class="sxs-lookup"><span data-stu-id="44daf-104">By looking ahead at all the life cycle stages where high availability surfaces, you can make the installation, maintenance, and troubleshooting of availability issues in your environment easier.</span></span>  
  
 <span data-ttu-id="44daf-105">本節包含您必須考慮高可用性工作的 MOF 程序資訊。</span><span class="sxs-lookup"><span data-stu-id="44daf-105">This section contains information about the MOF processes where you have to consider high-availability tasks.</span></span>  
  
## <a name="microsoft-operations-framework-process-model"></a><span data-ttu-id="44daf-106">Microsoft Operations Framework 程序模型</span><span class="sxs-lookup"><span data-stu-id="44daf-106">Microsoft Operations Framework Process Model</span></span>  
 <span data-ttu-id="44daf-107">[Microsoft Operations Framework (MOF)](https://technet.microsoft.com/solutionaccelerators/dd320379.aspx)提供指引，讓組織達成關鍵任務系統可靠性、 可用性、 可支援性和管理性的 Microsoft 產品和技術.</span><span class="sxs-lookup"><span data-stu-id="44daf-107">The [Microsoft Operations Framework (MOF)](https://technet.microsoft.com/solutionaccelerators/dd320379.aspx) provides guidance that enables organizations to achieve mission-critical system reliability, availability, supportability, and manageability of Microsoft products and technologies.</span></span> <span data-ttu-id="44daf-108">MOF 以下列方式提供操作指導：白皮書、作業指南、評估工具、最佳作法、案例研究、範本、支援工具以及服務。</span><span class="sxs-lookup"><span data-stu-id="44daf-108">MOF provides operational guidance in the form of white papers, operations guides, assessment tools, best practices, case studies, templates, support tools, and services.</span></span> <span data-ttu-id="44daf-109">此指導將討論與複雜、分散式和異質 IT 環境相關的人員、程序、技術和管理問題。</span><span class="sxs-lookup"><span data-stu-id="44daf-109">This guidance addresses the people, process, technology, and management issues pertaining to complex, distributed, and heterogeneous IT environments.</span></span> 
  
 <span data-ttu-id="44daf-110">MOF 程序模型可讓公司：</span><span class="sxs-lookup"><span data-stu-id="44daf-110">The MOF process model enables companies to:</span></span>  
  
-   <span data-ttu-id="44daf-111">促進整個服務方案一致的 IT 服務管理。</span><span class="sxs-lookup"><span data-stu-id="44daf-111">Facilitate consistent IT service management across service solutions.</span></span>  
  
-   <span data-ttu-id="44daf-112">建立 IT 功能、處理程序，以及程序的結構。</span><span class="sxs-lookup"><span data-stu-id="44daf-112">Establish a structure for IT functions, processes, and procedures.</span></span>  
  
-   <span data-ttu-id="44daf-113">代表生命週期的方法。</span><span class="sxs-lookup"><span data-stu-id="44daf-113">Represent a life-cycle approach.</span></span>  
  
 <span data-ttu-id="44daf-114">MOF 程序模型的中央分為四個象限的操作處理和程序，稱為服務管理功能 (SMF)。</span><span class="sxs-lookup"><span data-stu-id="44daf-114">Central to the MOF process model is its division into four quadrants of operational processes and procedures, named service management functions (SMFs).</span></span> <span data-ttu-id="44daf-115">SMF 是操作和維護 IT 環境的基礎層級最佳作法和指示引導。</span><span class="sxs-lookup"><span data-stu-id="44daf-115">The SMFs are the foundation-level best practices and prescriptive guidance for operating and maintaining an IT environment.</span></span>  
  
 <span data-ttu-id="44daf-116">下圖顯示您必須考慮高可用性的 MOF 程序。</span><span class="sxs-lookup"><span data-stu-id="44daf-116">The following figure shows the MOF processes where you have to consider high availability.</span></span>  
  
 <span data-ttu-id="44daf-117">![MOF 程序](../core/media/tdi-highava-mof.gif "TDI_HighAva_MOF")</span><span class="sxs-lookup"><span data-stu-id="44daf-117">![MOF Processes](../core/media/tdi-highava-mof.gif "TDI_HighAva_MOF")</span></span>  
  
## <a name="changing-quadrant"></a><span data-ttu-id="44daf-118">變動象限</span><span class="sxs-lookup"><span data-stu-id="44daf-118">Changing Quadrant</span></span>  
 <span data-ttu-id="44daf-119">變動象限包括服務管理功能 (SMF)，此功能用以識別、檢視、核准變更，並將變更併入受管理的 IT 環境中。</span><span class="sxs-lookup"><span data-stu-id="44daf-119">The changing quadrant includes the service management functions (SMFs) required to identify, review, approve, and incorporate change into a managed IT environment.</span></span> <span data-ttu-id="44daf-120">這包括軟體、硬體、文件、角色和責任的變更，也包括特定的程序變更。</span><span class="sxs-lookup"><span data-stu-id="44daf-120">This includes changes in software, hardware, documentation, roles and responsibilities, and also specific process and procedural changes.</span></span>  
  
### <a name="change-management"></a><span data-ttu-id="44daf-121">變更管理</span><span class="sxs-lookup"><span data-stu-id="44daf-121">Change Management</span></span>  
 <span data-ttu-id="44daf-122">變更管理負責技術、系統、應用程式、硬體、工具、文件和程序的變更，也負責角色和責任的變更。</span><span class="sxs-lookup"><span data-stu-id="44daf-122">Change management is responsible for changes in technology, systems, applications, hardware, tools, documentation, and processes, and also changes in roles and responsibilities.</span></span>  
  
 <span data-ttu-id="44daf-123">在變更管理程序以做為設計 BizTalk Server 實作部分期間，您可以執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="44daf-123">During the change management process, as part of designing your BizTalk Server implementation, you can do the following:</span></span>  
  
-   <span data-ttu-id="44daf-124">決定夥伴或客戶的服務等級協議，是否需要某個層級的可用性、執行時間以及載入處理能力。</span><span class="sxs-lookup"><span data-stu-id="44daf-124">Determine whether the service level agreement with your partners or customers requires a certain level of availability, uptime, and load-processing capabilities.</span></span>  
  
-   <span data-ttu-id="44daf-125">為您的企業需求決定 BizTalk Server 資料庫的最佳叢集組態。</span><span class="sxs-lookup"><span data-stu-id="44daf-125">Determine the best cluster configuration for the BizTalk Server databases for your business needs.</span></span> <span data-ttu-id="44daf-126">執行階段程序會寫入 BizTalk 管理資料庫、MessageBox 資料庫、追蹤 Analysis Services 資料庫、BAM 分析資料庫、BAM 星狀結構描述資料庫、BAM 主要匯入資料庫以及 BAM 封存資料庫。</span><span class="sxs-lookup"><span data-stu-id="44daf-126">The run-time processes write to the BizTalk Management database, MessageBox databases, Tracking Analysis Services database, BAM Analysis database, BAM Star Schema database, BAM Primary Import database, and BAM Archive database.</span></span> <span data-ttu-id="44daf-127">因此，若發生嚴重損毀，這些資料庫就顯得特別重要，而且在決定要叢集哪些資料庫時必須有較高的優先順序。</span><span class="sxs-lookup"><span data-stu-id="44daf-127">Therefore, these databases are especially important if a disaster occurs, and must have greater priority when determining what databases to cluster.</span></span> <span data-ttu-id="44daf-128">只有使用者或工具會寫入其他資料庫。</span><span class="sxs-lookup"><span data-stu-id="44daf-128">Only users or tools write to the other databases.</span></span> <span data-ttu-id="44daf-129">就 MessageBox 資料庫而言，您可以考慮主動/主動/主動/被動的四個伺服器叢集以便將所需的硬體減到最少。</span><span class="sxs-lookup"><span data-stu-id="44daf-129">For the MessageBox databases, you can consider an active/active/active/passive four-server cluster to minimize the hardware needed.</span></span>  
  
-   <span data-ttu-id="44daf-130">決定是否叢集主要密碼伺服器，或是，若在另一個「企業單一登入」伺服器上手動還原主要密碼伺服器是否符合您的實例。</span><span class="sxs-lookup"><span data-stu-id="44daf-130">Determine whether to cluster the master secret server, or if manually restoring the master secret on another Enterprise Single Sign-On server is satisfactory for your scenario.</span></span> <span data-ttu-id="44daf-131">此方案為可用，但不是高度可用。</span><span class="sxs-lookup"><span data-stu-id="44daf-131">This solution is available, but not highly available.</span></span>  
  
-   <span data-ttu-id="44daf-132">決定您在處理預期的訊息負載並提供高可用性時，需要多少的主控件和主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="44daf-132">Determine the number of hosts and host instances that you will need to process your expected message load and to provide high availability.</span></span>  
  
-   <span data-ttu-id="44daf-133">建立變更管理程序中所需人員的清單。</span><span class="sxs-lookup"><span data-stu-id="44daf-133">Create a list of the people that will be involved in the change-management process.</span></span> <span data-ttu-id="44daf-134">此清單將包括但不限於網域管理員、資料庫管理員、基礎結構管理員、BizTalk Server 系統管理員以及 IT 作業人員。</span><span class="sxs-lookup"><span data-stu-id="44daf-134">This list will include, but is not limited to, the domain administrator, database administrator, infrastructure administrator, BizTalk Server administrator, and IT operations staff.</span></span>  
  
### <a name="configuration-management"></a><span data-ttu-id="44daf-135">組態管理</span><span class="sxs-lookup"><span data-stu-id="44daf-135">Configuration Management</span></span>  
 <span data-ttu-id="44daf-136">組態管理負責在變更管理的控制下識別、控制和追蹤所有版本的軟體、硬體、文件、處理程序、程序以及 IT 環境中所有其他元件。</span><span class="sxs-lookup"><span data-stu-id="44daf-136">Configuration management is responsible for identifying, controlling, and tracking all versions of software, hardware, documentation, processes, procedures, and all other components of the IT environment under the control of change management.</span></span>  
  
 <span data-ttu-id="44daf-137">組態管理程序期間，您必須建立要如何為 BizTalk Server 實作高可用性方案的詳細計劃。</span><span class="sxs-lookup"><span data-stu-id="44daf-137">During the configuration management process, you must create a detailed plan for how you are going to implement your highly available solution for BizTalk Server.</span></span> <span data-ttu-id="44daf-138">您也必須記錄用以建立解決方案的步驟。</span><span class="sxs-lookup"><span data-stu-id="44daf-138">You must also document the steps that you took to create your solution.</span></span> <span data-ttu-id="44daf-139">簡要說明這些步驟：</span><span class="sxs-lookup"><span data-stu-id="44daf-139">At a high level, the steps are:</span></span>  
  
-   <span data-ttu-id="44daf-140">網域控制站建立將用於 BizTalk Server 環境的網域群組和帳戶。</span><span class="sxs-lookup"><span data-stu-id="44daf-140">The domain controller creates the domain groups and accounts that you will use in your BizTalk Server environment.</span></span>  
  
-   <span data-ttu-id="44daf-141">基礎結構管理員為 BizTalk Server 資料庫建立 Windows 叢集，並為主要密碼伺服器建立 Windows 叢集。</span><span class="sxs-lookup"><span data-stu-id="44daf-141">The infrastructure administrator creates the Windows cluster for the BizTalk Server databases and the Windows cluster for the master secret server.</span></span>  
  
-   <span data-ttu-id="44daf-142">資料庫系統管理員為 BizTalk Server 資料庫在 Windows 叢集上安裝和設定 Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="44daf-142">The database administrator installs and configures Microsoft SQL Server on the Windows cluster for the BizTalk Server databases.</span></span>  
  
-   <span data-ttu-id="44daf-143">BizTalk Server 系統管理員設定主要密碼伺服器叢集。</span><span class="sxs-lookup"><span data-stu-id="44daf-143">The BizTalk Server administrator configures the master secret server cluster.</span></span>  
  
-   <span data-ttu-id="44daf-144">BizTalk Server 系統管理員上安裝和設定 BizTalk Server 在處理、 接收和傳送伺服器。</span><span class="sxs-lookup"><span data-stu-id="44daf-144">The BizTalk Server administrator installs and configures BizTalk Server on the processing, receiving, and sending servers.</span></span>  
  
-   <span data-ttu-id="44daf-145">BizTalk Server 系統管理員建立主控件並在適當的伺服器上安裝主控件執行個體，以提供高可用性、增加容量，或兩者。</span><span class="sxs-lookup"><span data-stu-id="44daf-145">The BizTalk Server administrator creates the hosts and installs the host instances on the appropriate servers to provide high availability or to increase capacity, or both.</span></span>  
  
## <a name="operating-quadrant"></a><span data-ttu-id="44daf-146">操作象限</span><span class="sxs-lookup"><span data-stu-id="44daf-146">Operating Quadrant</span></span>  
 <span data-ttu-id="44daf-147">操作象限包括每日監控、控制和管理服務方案所需的 SMF，以達成和維護預先決定參數中的服務層級。</span><span class="sxs-lookup"><span data-stu-id="44daf-147">The operating quadrant includes the SMFs required to monitor, control, manage, and administer service solutions daily to achieve and maintain service levels within predetermined parameters.</span></span>  
  
### <a name="job-scheduling"></a><span data-ttu-id="44daf-148">工作排程</span><span class="sxs-lookup"><span data-stu-id="44daf-148">Job Scheduling</span></span>  
 <span data-ttu-id="44daf-149">工作排程包含以最有效率的順序持續地組織工作和程序，以最大化系統輸送量和使用率以符合服務等級協定的需求。</span><span class="sxs-lookup"><span data-stu-id="44daf-149">Job scheduling involves the continuous organization of jobs and processes in the most efficient sequence, maximizing system throughput and use to meet service level agreement requirements.</span></span>  
  
 <span data-ttu-id="44daf-150">請確定您排程計劃的停機，例如，將更新排程在訊息負載很低時 (例如，深夜)，以便將對企業可能的影響降到最低。</span><span class="sxs-lookup"><span data-stu-id="44daf-150">Make sure that you schedule planned downtime, such as scheduled updates, at times when the message load is low (for example, late at night) to minimize the potential effect on your business.</span></span>  
  
## <a name="supporting-quadrant"></a><span data-ttu-id="44daf-151">支援象限</span><span class="sxs-lookup"><span data-stu-id="44daf-151">Supporting Quadrant</span></span>  
 <span data-ttu-id="44daf-152">支援象限包括識別、指派、診斷、追蹤和解決包含在服務等級協定中已核准的需求內之事件、問題和要求所需的 SMF。</span><span class="sxs-lookup"><span data-stu-id="44daf-152">The supporting quadrant includes the SMFs required to identify, assign, diagnose, track, and resolve incidents, problems, and requests within the approved requirements that are contained in the service level agreements.</span></span>  
  
## <a name="optimizing-quadrant"></a><span data-ttu-id="44daf-153">最佳化象限</span><span class="sxs-lookup"><span data-stu-id="44daf-153">Optimizing Quadrant</span></span>  
 <span data-ttu-id="44daf-154">最佳化象限包括可維護企業和 IT合作的 SMF，它的重點在於維護或改善服務層級時能降低 IT 成本。</span><span class="sxs-lookup"><span data-stu-id="44daf-154">The optimizing quadrant includes the SMFs that contribute to maintaining business and IT alignment by focusing on decreasing IT costs while maintaining or improving service levels.</span></span> <span data-ttu-id="44daf-155">這包括中斷和事件的檢視、成本結構檢驗、員工評估、可用性和效能分析，以及容量預測。</span><span class="sxs-lookup"><span data-stu-id="44daf-155">This includes review of outages and incidents, examination of cost structures, staff assessments, availability and performance analysis, and capacity forecasting.</span></span>  
  
### <a name="service-level-management"></a><span data-ttu-id="44daf-156">服務層級管理</span><span class="sxs-lookup"><span data-stu-id="44daf-156">Service Level Management</span></span>  
 <span data-ttu-id="44daf-157">服務層級管理的目標是透過協調和監控服務層級需求的持續循環，以維護和持續改善 IT 服務的品質。</span><span class="sxs-lookup"><span data-stu-id="44daf-157">The goal of service level management is to maintain and continuously improve the quality of IT service, through a constant cycle of negotiating and monitoring service level requirements.</span></span> <span data-ttu-id="44daf-158">成功的服務層級管理功能將可改善服務品質，提升客戶產能，而且最好能降低提供服務的總成本。</span><span class="sxs-lookup"><span data-stu-id="44daf-158">The successful service level management function causes an improvement in quality of service, greater levels of customer productivity, and ideally, a reduction in the overall cost of services provided.</span></span>  
  
 <span data-ttu-id="44daf-159">在服務層級管理程序期間，您可以執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="44daf-159">During the service level management process, you can do the following:</span></span>  
  
-   <span data-ttu-id="44daf-160">評估目前的環境是否符合您的服務等級協定需求。</span><span class="sxs-lookup"><span data-stu-id="44daf-160">Evaluate how the current environment satisfies your service level agreement requirements.</span></span>  
  
-   <span data-ttu-id="44daf-161">建議新增用於處理、接收或傳送訊息的伺服器以符合需求。</span><span class="sxs-lookup"><span data-stu-id="44daf-161">Recommend the addition of new servers for processing, receiving, or sending messages to meet the requirements.</span></span>  
  
-   <span data-ttu-id="44daf-162">若有必要，建議為原本未減輕的失敗點建立高度可用的方案，以符合服務等級協定的可用性需求。</span><span class="sxs-lookup"><span data-stu-id="44daf-162">If necessary, recommend creating highly available solutions for points of failure that were not originally mitigated to meet the availability requirements in the service level agreement.</span></span>  
  
### <a name="availability-management"></a><span data-ttu-id="44daf-163">可用性管理</span><span class="sxs-lookup"><span data-stu-id="44daf-163">Availability Management</span></span>  
 <span data-ttu-id="44daf-164">可用性管理只有一個目標，就是確定客戶可以在需要時使用特定的 IT 服務。</span><span class="sxs-lookup"><span data-stu-id="44daf-164">The single goal of availability management is to make sure that your customers can use a particular IT service whenever they want.</span></span>  
  
 <span data-ttu-id="44daf-165">在可用性管理程序中，您可以建立發生硬體失敗時通知 IT 人員的機制，以便他們儘快修復或替換硬體，還可以建立伺服器負載大於特定閾值時通知 IT 人員的機制。</span><span class="sxs-lookup"><span data-stu-id="44daf-165">For the availability management process, you can establish mechanisms for notifying IT personnel when a hardware failure occurs so that they can fix or replace the hardware as quickly as possible, and mechanisms for notifying IT personnel when the server load is larger than a particular threshold.</span></span>  
  
### <a name="service-continuity-management"></a><span data-ttu-id="44daf-166">服務延續性管理</span><span class="sxs-lookup"><span data-stu-id="44daf-166">Service Continuity Management</span></span>  
 <span data-ttu-id="44daf-167">服務延續性管理功能的目標是確保一般可用性方案失敗時，指定的 IT 服務可提供價值給客戶。</span><span class="sxs-lookup"><span data-stu-id="44daf-167">The objective of the service continuity management function is to make sure that a specified IT service provides value to the customer if regular-availability solutions fail.</span></span>  
  
 <span data-ttu-id="44daf-168">在服務延續性功能期間，您必須檢查要實作的高可用性組態，以確保發生計劃或非計劃的停機時，您可以繼續提供客戶所需的服務。</span><span class="sxs-lookup"><span data-stu-id="44daf-168">During the service continuity function you must examine what high-availability configuration to implement to make sure that you continue providing your customers with the services they expect even when a planned or unplanned downtime occurs.</span></span> <span data-ttu-id="44daf-169">非計劃的停機像是硬體失敗或自然行為。</span><span class="sxs-lookup"><span data-stu-id="44daf-169">Examples of unplanned downtime are hardware failures or acts of nature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44daf-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44daf-170">See Also</span></span>  
 [<span data-ttu-id="44daf-171">BizTalk Server 高可用性案例範例</span><span class="sxs-lookup"><span data-stu-id="44daf-171">Sample BizTalk Server High Availability Scenarios</span></span>](../core/sample-biztalk-server-high-availability-scenarios.md)