---
title: 使用 BizTalk ESB Toolkit 公用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2dc05ac-831a-44e1-bd44-e41398552ab1
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db4a8ef2def05e0b77d272463d7a79f937623b1a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976684"
---
# <a name="using-the-biztalk-esb-toolkit-utilities"></a><span data-ttu-id="6f448-102">使用 BizTalk ESB Toolkit 公用程式</span><span class="sxs-lookup"><span data-stu-id="6f448-102">Using the BizTalk ESB Toolkit Utilities</span></span>
<span data-ttu-id="6f448-103">本章節描述各種公用程式的一部分加入[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6f448-103">This section describes various utilities included as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="6f448-104">**ESB 路線匯入公用程式**</span><span class="sxs-lookup"><span data-stu-id="6f448-104">**ESB Itinerary Import Utility**</span></span>  
  
 <span data-ttu-id="6f448-105">此公用程式位於 \bin 目錄之[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]稱為 EsbImportUtil.exe。</span><span class="sxs-lookup"><span data-stu-id="6f448-105">This utility is located under the \bin directory of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and is named EsbImportUtil.exe.</span></span> <span data-ttu-id="6f448-106">此公用程式可用來發行或部署到 ESBItineraryDB 資料庫 XML 路線。</span><span class="sxs-lookup"><span data-stu-id="6f448-106">This utility can be used to publish or deploy the itinerary XML into the ESBItineraryDB database.</span></span>  
  
 <span data-ttu-id="6f448-107">此公用程式的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f448-107">The syntax for the utility is as follows:</span></span>  
  
```  
>EsbImportUtil <Parameter1> <Value> <parameter2> <Value>...  
```  
  
 <span data-ttu-id="6f448-108">它可以接受各種參數如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f448-108">The various parameters it can accept are the following:</span></span>  
  
 <span data-ttu-id="6f448-109">/？:\<顯示說明的參數\></span><span class="sxs-lookup"><span data-stu-id="6f448-109">/?: \<Show the parameters help\></span></span>  
  
 <span data-ttu-id="6f448-110">/f:\<路線 xml 檔案路徑\></span><span class="sxs-lookup"><span data-stu-id="6f448-110">/f: \<Itinerary xml file path\></span></span>  
  
 <span data-ttu-id="6f448-111">包裝\<發行 &#124; 部署\></span><span class="sxs-lookup"><span data-stu-id="6f448-111">/c: \<published &#124; deployed\></span></span>  
  
 <span data-ttu-id="6f448-112">/n:\<預設行程名稱\></span><span class="sxs-lookup"><span data-stu-id="6f448-112">/n: \<Default Itinerary name\></span></span>  
  
 <span data-ttu-id="6f448-113">/v\<預設路線版本 （格式為 'major.minor'）\></span><span class="sxs-lookup"><span data-stu-id="6f448-113">/v: \<Default Itinerary version (format 'major.minor')\></span></span>  
  
 <span data-ttu-id="6f448-114">/o\<無訊息的覆寫\></span><span class="sxs-lookup"><span data-stu-id="6f448-114">/o: \<Silent overwrite\></span></span>  
  
 <span data-ttu-id="6f448-115">以下是如何使用此公用程式的範例。</span><span class="sxs-lookup"><span data-stu-id="6f448-115">The following are examples of how to use this utility.</span></span>  
  
 <span data-ttu-id="6f448-116">若要發行到路線資料庫：</span><span class="sxs-lookup"><span data-stu-id="6f448-116">To publish to the Itinerary database:</span></span>  
  
```  
>EsbImportUtil /f:myitinerary.xml /c:published  
```  
  
 <span data-ttu-id="6f448-117">將部署至路線資料庫：</span><span class="sxs-lookup"><span data-stu-id="6f448-117">To deploy to the Itinerary database:</span></span>  
  
```  
>EsbImportUtil  /f:myitinerary.xml /c:deployed  
```  
  
 <span data-ttu-id="6f448-118">**SSO 組態保存公用程式**</span><span class="sxs-lookup"><span data-stu-id="6f448-118">**SSO Configuration Persist Utility**</span></span>  
  
 <span data-ttu-id="6f448-119">此公用程式位於 \bin 目錄之[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]稱為 Microsoft.Practices.ESB.PersistConfigurationTool.exe。</span><span class="sxs-lookup"><span data-stu-id="6f448-119">This utility is located under the \bin directory of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and is named Microsoft.Practices.ESB.PersistConfigurationTool.exe.</span></span> <span data-ttu-id="6f448-120">此公用程式可以用來保存到 BizTalk SSO 資料庫的 ESB 組態資訊。</span><span class="sxs-lookup"><span data-stu-id="6f448-120">This utility can be used to persist the ESB configuration information into the BizTalk SSO database.</span></span> <span data-ttu-id="6f448-121">這也可用來檢視組態資訊，以及從 SSO 資料庫中移除組態資訊。</span><span class="sxs-lookup"><span data-stu-id="6f448-121">This can also be used to view configuration information and remove the configuration information from the SSO database.</span></span>  
  
 <span data-ttu-id="6f448-122">此公用程式的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f448-122">The syntax for the utility is as follows:</span></span>  
  
 <span data-ttu-id="6f448-123">**若要新增的組態區段：**</span><span class="sxs-lookup"><span data-stu-id="6f448-123">**To add a configuration section:**</span></span>  
  
```  
>Microsoft.Practices.ESB.PersistConfigurationTool  /P /F:app.config /S:SectionName /A:ApplicationName  
```  
  
> [!NOTE]
>  <span data-ttu-id="6f448-124">如果未提供 /S，就會加入下列各節： connectionStrings esb、 esb.resolver 和 cachingConfiguration。</span><span class="sxs-lookup"><span data-stu-id="6f448-124">If /S is not provided, the following sections will be added: connectionStrings, esb, esb.resolver and cachingConfiguration.</span></span>  
  
 <span data-ttu-id="6f448-125">**若要移除的區段：**</span><span class="sxs-lookup"><span data-stu-id="6f448-125">**To remove a section:**</span></span>  
  
```  
>Microsoft.Practices.ESB.PersistConfigurationTool  /R /S:SectionName  
```  
  
 <span data-ttu-id="6f448-126">若要檢視現有的區段，請與 /V 交換器搭配的應用程式和區段的參數。</span><span class="sxs-lookup"><span data-stu-id="6f448-126">To view an existing section, use the application and section switches with the /V switch.</span></span>  
  
 <span data-ttu-id="6f448-127">若要設定系統管理員群組名稱，請使用 AG:AdminGroupName 交換器。</span><span class="sxs-lookup"><span data-stu-id="6f448-127">To set the administrator group name, use the AG:AdminGroupName switch.</span></span>  
  
 <span data-ttu-id="6f448-128">若要設定使用者群組名稱，請使用 UG:UserGroupName 交換器。</span><span class="sxs-lookup"><span data-stu-id="6f448-128">To set the user group name, use the UG:UserGroupName switch.</span></span>