---
title: 記錄程序的相關 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- logging, about logging
- auditing, about auditing
- logging
- auditing
ms.assetid: 859ee1f5-aae4-4a47-ab39-8d2b4168a429
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07dba617358d6ad451c53eeb75dbe5d1986f9066
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204718"
---
# <a name="about-the-logging-process"></a><span data-ttu-id="5fb77-102">關於記錄處理程序</span><span class="sxs-lookup"><span data-stu-id="5fb77-102">About the Logging Process</span></span>
<span data-ttu-id="5fb77-103">您的應用程式處理重要，因為時間敏感資料和貨幣資料，稽核會變成應用程式很重要的一部分。</span><span class="sxs-lookup"><span data-stu-id="5fb77-103">Since your applications handle critical, time sensitive and monetary data, auditing becomes a critical part of the application.</span></span> <span data-ttu-id="5fb77-104">若要啟用企業層級的管理性和可用性， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]依賴下列共用的執行的階段和管理元件：</span><span class="sxs-lookup"><span data-stu-id="5fb77-104">To enable enterprise level manageability and availability, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] relies on the following shared run time and administrative components:</span></span>  
  
-   <span data-ttu-id="5fb77-105">**記錄**： 來收集和傳送的所有記錄事件中指定之資料庫的 managed 方法</span><span class="sxs-lookup"><span data-stu-id="5fb77-105">**Logging**: to collect and route all log events in a managed way to a designated database</span></span>  
  
-   <span data-ttu-id="5fb77-106">**事件監視及服務偵錯**： 若要設定記錄行為，以及調查/管理系統管理員和其他 IT 專業人員所收集的資訊</span><span class="sxs-lookup"><span data-stu-id="5fb77-106">**Event Monitoring and Service Debugging**: to configure logging behavior and to investigate/manage collected information for system administrators and other IT professionals</span></span>  
  
 <span data-ttu-id="5fb77-107">使用增強稽核功能[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]，您可以最佳化您的營運效率、 安全性和效能，以確保相容性與 HL7 法規。</span><span class="sxs-lookup"><span data-stu-id="5fb77-107">With the enhanced auditing features in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], you can optimize your operational efficiency, security, and performance to ensure compliance with HL7 regulations.</span></span>  
  
## <a name="types-of-data"></a><span data-ttu-id="5fb77-108">資料類型</span><span class="sxs-lookup"><span data-stu-id="5fb77-108">Types of Data</span></span>  
 <span data-ttu-id="5fb77-109">本主題說明不同類型的使用記錄功能，以及這項資料的儲存位置的記錄資料：</span><span class="sxs-lookup"><span data-stu-id="5fb77-109">This topic describes different types of logging data used by the logging feature and where this data is stored:</span></span>  
  
-   <span data-ttu-id="5fb77-110">設定資料： 記錄組態資料會儲存在組態資料庫 （也稱為 「 BizTalk 管理資料庫），並包含稽核資訊和稽核資料的 SQL ([!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)]事件檢視器，集中式資料庫 WMI) 的位置。</span><span class="sxs-lookup"><span data-stu-id="5fb77-110">Configuration data: Logging configuration data is stored in the Configuration database (also known as the BizTalk Management database) and includes SQL auditing information and audit data ([!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] Event viewer, centralized database WMI) location.</span></span>  
  
-   <span data-ttu-id="5fb77-111">封存資料： SQL 記錄檔中的事件記錄檔資料表會儲存 '記錄' 的資料。</span><span class="sxs-lookup"><span data-stu-id="5fb77-111">Archival data: The EventLog table in the SQL log stores the 'Logging' data.</span></span>  
  
## <a name="how-logging-works"></a><span data-ttu-id="5fb77-112">記錄的運作方式</span><span class="sxs-lookup"><span data-stu-id="5fb77-112">How Logging Works</span></span>  
 <span data-ttu-id="5fb77-113">本主題說明三種事件軟體記錄檔，以及三個位置，您可以在其中儲存記錄的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5fb77-113">This topic describes the three types of events the software logs, as well as the three locations where you can store the logged data.</span></span>  
  
|<span data-ttu-id="5fb77-114">元件</span><span class="sxs-lookup"><span data-stu-id="5fb77-114">Component</span></span>|<span data-ttu-id="5fb77-115">目的</span><span class="sxs-lookup"><span data-stu-id="5fb77-115">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="5fb77-116">組態編輯器</span><span class="sxs-lookup"><span data-stu-id="5fb77-116">Configuration Editor</span></span>|<span data-ttu-id="5fb77-117">若要指定儲存記錄資料的位置。</span><span class="sxs-lookup"><span data-stu-id="5fb77-117">To specify where to save the log data.</span></span> <span data-ttu-id="5fb77-118">BTAHL7 支援記錄功能，下列的任何組合： 事件檢視器、 WMI 和 SQL Server 記錄。</span><span class="sxs-lookup"><span data-stu-id="5fb77-118">BTAHL7 supports logging to any combination of the following: Event Viewer, WMI, and SQL Server logging.</span></span>|  
|<span data-ttu-id="5fb77-119">事件 Broker</span><span class="sxs-lookup"><span data-stu-id="5fb77-119">Event Broker</span></span>|<span data-ttu-id="5fb77-120">要接收記錄事件的其他元件所引發並將其根據記錄組態資料記錄。</span><span class="sxs-lookup"><span data-stu-id="5fb77-120">To receive log events raised by other components and log them based on logging configuration data.</span></span>|  
|<span data-ttu-id="5fb77-121">記錄應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="5fb77-121">Logging API</span></span>|<span data-ttu-id="5fb77-122">記錄所有 BTAHL7 組件所呼叫介面。</span><span class="sxs-lookup"><span data-stu-id="5fb77-122">Logging interface called by all BTAHL7 assemblies.</span></span>|  
  
### <a name="types-of-logging"></a><span data-ttu-id="5fb77-123">類型的記錄</span><span class="sxs-lookup"><span data-stu-id="5fb77-123">Types of Logging</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="5fb77-124">記錄錯誤的三種：</span><span class="sxs-lookup"><span data-stu-id="5fb77-124"> logs three types of errors:</span></span>  
  
-   <span data-ttu-id="5fb77-125">參考事件、 服務啟動或停止或事件失敗。</span><span class="sxs-lookup"><span data-stu-id="5fb77-125">Informational events, such a service started or stopped or an event failed.</span></span>  
  
-   <span data-ttu-id="5fb77-126">警告事件，例如非重大錯誤和警告中的[!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)]事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5fb77-126">Warning events such as non-critical errors and warnings in [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] Event logs.</span></span> <span data-ttu-id="5fb77-127">例如，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]擱置訊息，因為資料驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="5fb77-127">For example, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] suspends a message because data validation failed.</span></span>  
  
-   <span data-ttu-id="5fb77-128">在元件中的嚴重失敗的錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="5fb77-128">Error events for critical failures in a component.</span></span> <span data-ttu-id="5fb77-129">例如，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]擱置訊息，因為剖析器發生失敗。</span><span class="sxs-lookup"><span data-stu-id="5fb77-129">For example, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] suspends a message because of parser failures.</span></span>  
  
 <span data-ttu-id="5fb77-130">系統可以記錄[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]事件加入下列可設定的位置：</span><span class="sxs-lookup"><span data-stu-id="5fb77-130">The system can log [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] events into following configurable locations:</span></span>  
  
-   [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)]<span data-ttu-id="5fb77-131">事件檢視器</span><span class="sxs-lookup"><span data-stu-id="5fb77-131"> Event viewer</span></span>  
  
-   <span data-ttu-id="5fb77-132">WMI 事件</span><span class="sxs-lookup"><span data-stu-id="5fb77-132">WMI events</span></span>  
  
-   <span data-ttu-id="5fb77-133">集中式的資料庫 （SQL 記錄資料庫）</span><span class="sxs-lookup"><span data-stu-id="5fb77-133">Centralized database (SQL logging database)</span></span>  
  
 <span data-ttu-id="5fb77-134">事件 broker 接收所有[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]記錄的事件，根據組態資訊、 將它們傳送到適當的位置。</span><span class="sxs-lookup"><span data-stu-id="5fb77-134">An event broker receives all [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logging events and, based on the configuration information, sends them to the appropriate location.</span></span>  
  
### <a name="overview-of-features"></a><span data-ttu-id="5fb77-135">功能概觀</span><span class="sxs-lookup"><span data-stu-id="5fb77-135">Overview of Features</span></span>  
 <span data-ttu-id="5fb77-136">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]提供記錄功能：</span><span class="sxs-lookup"><span data-stu-id="5fb77-136">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logging feature provides:</span></span>  
  
-   <span data-ttu-id="5fb77-137">統一的方式，記錄所有錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="5fb77-137">A unified way of logging all the error messages</span></span>  
  
-   <span data-ttu-id="5fb77-138">集中式的儲存機制來儲存所有的事件詳細資料</span><span class="sxs-lookup"><span data-stu-id="5fb77-138">A centralized repository for storing all event details</span></span>  
  
-   <span data-ttu-id="5fb77-139">記錄訊息在離散的特定業務應用程式一致的物件模型</span><span class="sxs-lookup"><span data-stu-id="5fb77-139">A consistent object model for logging messages flowing to discrete line-of-business applications</span></span>  
  
-   <span data-ttu-id="5fb77-140">組合的記錄和追蹤，以協助的系統管理員將相互關聯的文件已記錄錯誤</span><span class="sxs-lookup"><span data-stu-id="5fb77-140">A combination of logging and tracing to help system administrators correlate logged errors with documents</span></span>  
  
## <a name="event-log-data"></a><span data-ttu-id="5fb77-141">事件記錄檔資料</span><span class="sxs-lookup"><span data-stu-id="5fb77-141">Event Log Data</span></span>  
 <span data-ttu-id="5fb77-142">本主題描述的格式和內容的事件記錄檔資料。</span><span class="sxs-lookup"><span data-stu-id="5fb77-142">This topic describes the format and content of the event log data.</span></span>  
  
 <span data-ttu-id="5fb77-143">下表顯示為夥伴的一般記錄的資料。</span><span class="sxs-lookup"><span data-stu-id="5fb77-143">The following table shows typical logged data for partners.</span></span>  
  
|<span data-ttu-id="5fb77-144">data</span><span class="sxs-lookup"><span data-stu-id="5fb77-144">Data</span></span>|<span data-ttu-id="5fb77-145">Description</span><span class="sxs-lookup"><span data-stu-id="5fb77-145">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="5fb77-146">LogData</span><span class="sxs-lookup"><span data-stu-id="5fb77-146">LogData</span></span>|<span data-ttu-id="5fb77-147">資料記錄</span><span class="sxs-lookup"><span data-stu-id="5fb77-147">Data log</span></span>|  
|<span data-ttu-id="5fb77-148">CategoryNumber</span><span class="sxs-lookup"><span data-stu-id="5fb77-148">CategoryNumber</span></span>|<span data-ttu-id="5fb77-149">類別目錄數目</span><span class="sxs-lookup"><span data-stu-id="5fb77-149">Category number</span></span>|  
|<span data-ttu-id="5fb77-150">EntryType</span><span class="sxs-lookup"><span data-stu-id="5fb77-150">EntryType</span></span>|<span data-ttu-id="5fb77-151">事件的類型</span><span class="sxs-lookup"><span data-stu-id="5fb77-151">Type of the event</span></span>|  
|<span data-ttu-id="5fb77-152">EventId</span><span class="sxs-lookup"><span data-stu-id="5fb77-152">EventId</span></span>|<span data-ttu-id="5fb77-153">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5fb77-153">Event ID</span></span>|  
|<span data-ttu-id="5fb77-154">MachineName</span><span class="sxs-lookup"><span data-stu-id="5fb77-154">MachineName</span></span>|<span data-ttu-id="5fb77-155">電腦名稱</span><span class="sxs-lookup"><span data-stu-id="5fb77-155">Computer name</span></span>|  
|<span data-ttu-id="5fb77-156">訊息</span><span class="sxs-lookup"><span data-stu-id="5fb77-156">Message</span></span>|<span data-ttu-id="5fb77-157">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="5fb77-157">Message detail</span></span>|  
|<span data-ttu-id="5fb77-158">Source</span><span class="sxs-lookup"><span data-stu-id="5fb77-158">Source</span></span>|<span data-ttu-id="5fb77-159">建立、 更新、 讀取、 刪除、 部署，或將資料封存</span><span class="sxs-lookup"><span data-stu-id="5fb77-159">Creating, updating, reading, deleting, deploying, or archiving data</span></span>|  
|<span data-ttu-id="5fb77-160">TimeGenerated</span><span class="sxs-lookup"><span data-stu-id="5fb77-160">TimeGenerated</span></span>|<span data-ttu-id="5fb77-161">成功或失敗</span><span class="sxs-lookup"><span data-stu-id="5fb77-161">Success or Failure</span></span>|  
|<span data-ttu-id="5fb77-162">UserName</span><span class="sxs-lookup"><span data-stu-id="5fb77-162">UserName</span></span>|<span data-ttu-id="5fb77-163">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="5fb77-163">User name</span></span>|  
|<span data-ttu-id="5fb77-164">MsgGuid</span><span class="sxs-lookup"><span data-stu-id="5fb77-164">MsgGuid</span></span>|<span data-ttu-id="5fb77-165">訊息的 GUID</span><span class="sxs-lookup"><span data-stu-id="5fb77-165">Message GUID</span></span>|  
|<span data-ttu-id="5fb77-166">SvcGuid</span><span class="sxs-lookup"><span data-stu-id="5fb77-166">SvcGuid</span></span>|<span data-ttu-id="5fb77-167">服務 GUID</span><span class="sxs-lookup"><span data-stu-id="5fb77-167">Service GUID</span></span>|  
|<span data-ttu-id="5fb77-168">作業</span><span class="sxs-lookup"><span data-stu-id="5fb77-168">Operation</span></span>|<span data-ttu-id="5fb77-169">作業詳細資料</span><span class="sxs-lookup"><span data-stu-id="5fb77-169">Operation detail</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fb77-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fb77-170">See Also</span></span>  
 [<span data-ttu-id="5fb77-171">設定記錄</span><span class="sxs-lookup"><span data-stu-id="5fb77-171">Configuring Logging</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)