---
title: "安裝 「 JMS MQRFH2 元件 」 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a5bd855-512f-40a4-8038-ae9b847b1097
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b522d986524c77a53cf5a847f749a9ce41e2c50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-jms-mqrfh2-component-sample"></a><span data-ttu-id="1a769-102">安裝 JMS MQRFH2 元件範例</span><span class="sxs-lookup"><span data-stu-id="1a769-102">Installing the JMS MQRFH2 Component Sample</span></span>
<span data-ttu-id="1a769-103">若要使用這個範例使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，您也必須安裝下列：</span><span class="sxs-lookup"><span data-stu-id="1a769-103">To use this sample with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], you must also install the following:</span></span>  
  
-   <span data-ttu-id="1a769-104">IBM WebSphere MQ 5.3 （具有 CSD12) WebSphere MQ 6.x 或 WebSphere MQ 7.0</span><span class="sxs-lookup"><span data-stu-id="1a769-104">IBM WebSphere MQ 5.3 (with CSD12), WebSphere MQ 6.x or WebSphere MQ 7.0</span></span>  
  
-   <span data-ttu-id="1a769-105">IBM"RfhUtil"JMS 測試佇列和擷取訊息的公用程式</span><span class="sxs-lookup"><span data-stu-id="1a769-105">The IBM "RfhUtil" JMS test utility for queuing and retrieving messages</span></span>  
  
 <span data-ttu-id="1a769-106">JMS MQRFH2 元件範例需要 JMS MQRFH2 元件放在您的 Microsoft BizTalk Server 安裝資料夾，以及要在全域組件快取中的對應結構描述的 PipelineComponents 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1a769-106">The JMS MQRFH2 Component sample requires the JMS MQRFH2 component to reside in the PipelineComponents folder of your Microsoft BizTalk Server installation folder and the corresponding schemas to reside in the global assembly cache.</span></span> <span data-ttu-id="1a769-107">安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心自動複製和組件安裝到正確的位置。</span><span class="sxs-lookup"><span data-stu-id="1a769-107">Installing the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core automatically copies and installs the assemblies to the correct locations.</span></span> <span data-ttu-id="1a769-108">不過，如果需要，您可以手動執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="1a769-108">However, if required, you can manually perform these tasks.</span></span>  
  
 <span data-ttu-id="1a769-109">**若要手動安裝的 JMS MQRFH2 元件和結構描述**</span><span class="sxs-lookup"><span data-stu-id="1a769-109">**To manually install the JMS MQRFH2 component and schemas**</span></span>  
  
1.  <span data-ttu-id="1a769-110">將組件 Microsoft.Practices.ESB.JMS.PipelineComponents.dll 複製到 PipelineComponents 資料夾，您的 BizTalk Server 安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="1a769-110">Copy the assembly Microsoft.Practices.ESB.JMS.PipelineComponents.dll to the PipelineComponents folder of your BizTalk Server installation folder.</span></span>  
  
2.  <span data-ttu-id="1a769-111">加入至全域組件快取使用.NET Framework 組態工具 Microsoft.Practices.ESB.JMS.Schemas.Property.dll 找到系統管理工具 部分中的結構描述組件**啟動**功能表。</span><span class="sxs-lookup"><span data-stu-id="1a769-111">Add the schema assembly Microsoft.Practices.ESB.JMS.Schemas.Property.dll to the global assembly cache using the .NET Framework Configuration Tool located in the Administrative Tools section of the **Start** menu.</span></span>  
  
 <span data-ttu-id="1a769-112">本章節描述 JMS MQRFH2 範例安裝到 GlobalBank.JMS BizTalk 應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="1a769-112">This section describes the process for installing the JMS MQRFH2 sample into the GlobalBank.JMS BizTalk application.</span></span> <span data-ttu-id="1a769-113">中所述安裝此範例之前，您必須安裝 ESB Toolkit 核心[安裝 BizTalk ESB Toolkit 核心](http://go.microsoft.com/fwlink/?LinkId=187612)([http://go.microsoft.com/fwlink/?LinkId=187612](http://go.microsoft.com/fwlink/?LinkId=187612))。</span><span class="sxs-lookup"><span data-stu-id="1a769-113">Before you install this sample, you must install the ESB Toolkit Core as described in [Installing the BizTalk ESB Toolkit Core](http://go.microsoft.com/fwlink/?LinkId=187612) ([http://go.microsoft.com/fwlink/?LinkId=187612](http://go.microsoft.com/fwlink/?LinkId=187612)).</span></span>  
  
 <span data-ttu-id="1a769-114">您可以從方案專案中安裝 「 JMS MQRFH2 元件 」 範例，或使用隨附的 Windows Installer 檔案[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1a769-114">You can install the JMS MQRFH2 Component sample from the solution project or use the Windows Installer file included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="1a769-115">本節包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="1a769-115">This section contains the following topics:</span></span>  
  
-   [<span data-ttu-id="1a769-116">安裝 JMS MQRFH2 範例使用安裝指令碼</span><span class="sxs-lookup"><span data-stu-id="1a769-116">Install the JMS MQRFH2 Sample Using the Install Scripts</span></span>](../esb-toolkit/install-the-jms-mqrfh2-sample-using-the-install-scripts.md)  
  
-   [<span data-ttu-id="1a769-117">組件和成品安裝 JMS MQRFH2 元件範例</span><span class="sxs-lookup"><span data-stu-id="1a769-117">Assemblies and Artifacts Installed by the JMS MQRFH2 Component Sample</span></span>](../esb-toolkit/assemblies-and-artifacts-installed-by-the-jms-mqrfh2-component-sample.md)  
  
-   [<span data-ttu-id="1a769-118">測試 JMS MQRFH2 範例的安裝</span><span class="sxs-lookup"><span data-stu-id="1a769-118">Test the JMS MQRFH2 Sample Installation</span></span>](../esb-toolkit/test-the-jms-mqrfh2-sample-installation.md)