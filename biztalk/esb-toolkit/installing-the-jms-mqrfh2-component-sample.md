---
title: 安裝 JMS MQRFH2 元件範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a5bd855-512f-40a4-8038-ae9b847b1097
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f04067ef6b2e1a057edc05601059d931b7ba7f28
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018599"
---
# <a name="installing-the-jms-mqrfh2-component-sample"></a><span data-ttu-id="bc827-102">安裝 JMS MQRFH2 元件範例</span><span class="sxs-lookup"><span data-stu-id="bc827-102">Installing the JMS MQRFH2 Component Sample</span></span>
<span data-ttu-id="bc827-103">若要使用此範例，其中含有[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，您也必須安裝下列：</span><span class="sxs-lookup"><span data-stu-id="bc827-103">To use this sample with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], you must also install the following:</span></span>  
  
- <span data-ttu-id="bc827-104">IBM WebSphere MQ 5.3 （含 CSD12) WebSphere MQ 6.x 或 WebSphere MQ 7.0</span><span class="sxs-lookup"><span data-stu-id="bc827-104">IBM WebSphere MQ 5.3 (with CSD12), WebSphere MQ 6.x or WebSphere MQ 7.0</span></span>  
  
- <span data-ttu-id="bc827-105">IBM"RfhUtil"JMS 測試佇列，和擷取訊息的公用程式</span><span class="sxs-lookup"><span data-stu-id="bc827-105">The IBM "RfhUtil" JMS test utility for queuing and retrieving messages</span></span>  
  
  <span data-ttu-id="bc827-106">JMS MQRFH2 元件範例需要 JMS MQRFH2 元件位於您的 Microsoft BizTalk Server 安裝資料夾，以及要在全域組件快取中的對應結構描述的 PipelineComponents 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bc827-106">The JMS MQRFH2 Component sample requires the JMS MQRFH2 component to reside in the PipelineComponents folder of your Microsoft BizTalk Server installation folder and the corresponding schemas to reside in the global assembly cache.</span></span> <span data-ttu-id="bc827-107">安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]core 會自動複製，並會將組件安裝到正確的位置。</span><span class="sxs-lookup"><span data-stu-id="bc827-107">Installing the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core automatically copies and installs the assemblies to the correct locations.</span></span> <span data-ttu-id="bc827-108">不過，如有需要，您可以手動執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="bc827-108">However, if required, you can manually perform these tasks.</span></span>  
  
  <span data-ttu-id="bc827-109">**若要手動安裝 JMS MQRFH2 元件和結構描述**</span><span class="sxs-lookup"><span data-stu-id="bc827-109">**To manually install the JMS MQRFH2 component and schemas**</span></span>  
  
1. <span data-ttu-id="bc827-110">將組件 Microsoft.Practices.ESB.JMS.PipelineComponents.dll 複製到 PipelineComponents 資料夾的 BizTalk Server 安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="bc827-110">Copy the assembly Microsoft.Practices.ESB.JMS.PipelineComponents.dll to the PipelineComponents folder of your BizTalk Server installation folder.</span></span>  
  
2. <span data-ttu-id="bc827-111">新增 Microsoft.Practices.ESB.JMS.Schemas.Property.dll 至全域組件快取使用.NET Framework 組態工具位於系統管理工具 區段的結構描述組件**啟動**功能表。</span><span class="sxs-lookup"><span data-stu-id="bc827-111">Add the schema assembly Microsoft.Practices.ESB.JMS.Schemas.Property.dll to the global assembly cache using the .NET Framework Configuration Tool located in the Administrative Tools section of the **Start** menu.</span></span>  
  
   <span data-ttu-id="bc827-112">本節描述安裝 JMS MQRFH2 範例到 GlobalBank.JMS BizTalk 應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="bc827-112">This section describes the process for installing the JMS MQRFH2 sample into the GlobalBank.JMS BizTalk application.</span></span> <span data-ttu-id="bc827-113">安裝此範例之前，您必須先安裝 ESB Toolkit 核心，如中所述[安裝 BizTalk ESB 工具組核心](http://go.microsoft.com/fwlink/?LinkId=187612)([http://go.microsoft.com/fwlink/?LinkId=187612](http://go.microsoft.com/fwlink/?LinkId=187612))。</span><span class="sxs-lookup"><span data-stu-id="bc827-113">Before you install this sample, you must install the ESB Toolkit Core as described in [Installing the BizTalk ESB Toolkit Core](http://go.microsoft.com/fwlink/?LinkId=187612) ([http://go.microsoft.com/fwlink/?LinkId=187612](http://go.microsoft.com/fwlink/?LinkId=187612)).</span></span>  
  
   <span data-ttu-id="bc827-114">您可以從解決方案專案中安裝 JMS MQRFH2 元件範例，或使用包含的 Windows Installer 檔[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bc827-114">You can install the JMS MQRFH2 Component sample from the solution project or use the Windows Installer file included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="bc827-115">本節包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="bc827-115">This section contains the following topics:</span></span>  
  
-   [<span data-ttu-id="bc827-116">使用安裝指令碼安裝 JMS MQRFH2 範例</span><span class="sxs-lookup"><span data-stu-id="bc827-116">Install the JMS MQRFH2 Sample Using the Install Scripts</span></span>](../esb-toolkit/install-the-jms-mqrfh2-sample-using-the-install-scripts.md)  
  
-   [<span data-ttu-id="bc827-117">JMS MQRFH2 元件範例所安裝的組件和成品</span><span class="sxs-lookup"><span data-stu-id="bc827-117">Assemblies and Artifacts Installed by the JMS MQRFH2 Component Sample</span></span>](../esb-toolkit/assemblies-and-artifacts-installed-by-the-jms-mqrfh2-component-sample.md)  
  
-   [<span data-ttu-id="bc827-118">測試 JMS MQRFH2 範例安裝</span><span class="sxs-lookup"><span data-stu-id="bc827-118">Test the JMS MQRFH2 Sample Installation</span></span>](../esb-toolkit/test-the-jms-mqrfh2-sample-installation.md)