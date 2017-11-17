---
title: "重要功能，在 SAP 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, deprecated features
- features, technology-related
- adapters, new features
- features, deprecated
- features, metadata-related
- librfc32u.dll
- tRFC server
- features, new
- adapters, new and deprecated features
- queued tRFC client calls
- features, operations-related
- RFC server
ms.assetid: 30e3140c-447f-42ba-a3b0-13ae66e78b0c
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b34a695e34f617f6444b728e92cb544f91448c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="key-features-in-the-sap-adapter"></a><span data-ttu-id="6ca83-102">SAP 配接器中的主要功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-102">Key features in the SAP Adapter</span></span>
<span data-ttu-id="6ca83-103">此區段會列出中的新和已被取代功能[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ca83-103">This section lists the new and deprecated features in [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ca83-104">本主題已經使用舊版的[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="6ca83-104">This topic has been used from the previous version of [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] Help.</span></span>  
  
## <a name="features-in-the-sap-adapter"></a><span data-ttu-id="6ca83-105">SAP 配接器中的功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-105">Features in the SAP Adapter</span></span>  
 <span data-ttu-id="6ca83-106">以下是前一版中引進的功能[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ca83-106">The following are the features introduced in the previous releases of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
### <a name="technology-related-features"></a><span data-ttu-id="6ca83-107">技術相關功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-107">Technology-Related Features</span></span>  
  
|<span data-ttu-id="6ca83-108">功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-108">Feature</span></span>|<span data-ttu-id="6ca83-109">註解</span><span class="sxs-lookup"><span data-stu-id="6ca83-109">Comment</span></span>|  
|-------------|-------------|  
|<span data-ttu-id="6ca83-110">使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]與 SQL Server Reporting Services (SSRS)。</span><span class="sxs-lookup"><span data-stu-id="6ca83-110">Using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] with SQL Server Reporting Services (SSRS).</span></span>|<span data-ttu-id="6ca83-111">現在可以使用用戶端程式[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]從 SAP 後端的資料匯入至 SSRS 專案，產生超出資料的報表。</span><span class="sxs-lookup"><span data-stu-id="6ca83-111">Client programs can now use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] to import data from an SAP backend into an SSRS project and generate reports out of the data.</span></span> <span data-ttu-id="6ca83-112">如需有關如何使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]ssrs，請參閱[資料提供者用於 SAP ssrs](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6ca83-112">For more information on how to use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] with SSRS, see [Use the Data Provider for SAP with SSRS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssrs.md).</span></span> <span data-ttu-id="6ca83-113">如需 SSRS 的詳細資訊，請參閱[SQL Server Reporting Services](https://msdn.microsoft.com/library/ms159106.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6ca83-113">For more information about SSRS, see [SQL Server Reporting Services](https://msdn.microsoft.com/library/ms159106.aspx).</span></span>|  
|<span data-ttu-id="6ca83-114">叫用 SAP 系統中定義查詢的支援</span><span class="sxs-lookup"><span data-stu-id="6ca83-114">Support for invoking queries defined in an SAP system</span></span>|<span data-ttu-id="6ca83-115">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]公開的作業，EXECQUERY，可以用來執行 SAP 系統中定義的查詢。</span><span class="sxs-lookup"><span data-stu-id="6ca83-115">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] exposes an operation, EXECQUERY, that can be used to execute queries defined in an SAP system.</span></span> <span data-ttu-id="6ca83-116">如需有關如何使用 EXECQUERY 功能的詳細資訊，請參閱 < 執行 SAP 查詢的 [支援</span><span class="sxs-lookup"><span data-stu-id="6ca83-116">For more information on how to use the EXECQUERY feature, see [Support for Executing SAP Queries</span></span>

<span data-ttu-id="6ca83-117">] (https://msdn.microsoft.com/library/dd788118.aspx)。 |</span><span class="sxs-lookup"><span data-stu-id="6ca83-117">](https://msdn.microsoft.com/library/dd788118.aspx).|</span></span>  
<span data-ttu-id="6ca83-118">|支援使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 Microsoft Office SharePoint Server (MOSS) |您可以使用配接器呈現到 MOSS 入口網站上的 SAP 系統的資料。</span><span class="sxs-lookup"><span data-stu-id="6ca83-118">|Support for using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Microsoft Office SharePoint Server (MOSS)|You can use the adapters to present data from the SAP system onto a MOSS portal.</span></span> <span data-ttu-id="6ca83-119">如需詳細資訊，請參閱[搭配 SharePoint 使用 SAP 配接器](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md)。 |</span><span class="sxs-lookup"><span data-stu-id="6ca83-119">For more information, see [Use the SAP Adapter with SharePoint](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md).|</span></span>  
  
### <a name="metadata-related-features"></a><span data-ttu-id="6ca83-120">中繼資料相關功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-120">Metadata-Related Features</span></span>  
  
|<span data-ttu-id="6ca83-121">功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-121">Feature</span></span>|<span data-ttu-id="6ca83-122">註解</span><span class="sxs-lookup"><span data-stu-id="6ca83-122">Comment</span></span>|  
|-------------|-------------|  
|<span data-ttu-id="6ca83-123">**DataTypesBehavior**繫結屬性</span><span class="sxs-lookup"><span data-stu-id="6ca83-123">**DataTypesBehavior** binding property</span></span>|<span data-ttu-id="6ca83-124">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]提供複雜繫結屬性， **DataTypesBehavior**，可讓配接器用戶端時遇到 SAP 系統中的特殊的值，控制配接器行為。</span><span class="sxs-lookup"><span data-stu-id="6ca83-124">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] provides a complex binding property, **DataTypesBehavior**, that enables adapter clients to control the adapter behavior when special values are encountered in the SAP system.</span></span> <span data-ttu-id="6ca83-125">如需此繫結屬性的詳細討論，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6ca83-125">For a detailed discussion about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>|  
  
### <a name="operations-related-features"></a><span data-ttu-id="6ca83-126">與作業相關的功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-126">Operations-Related Features</span></span>  
  
|<span data-ttu-id="6ca83-127">功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-127">Feature</span></span>|<span data-ttu-id="6ca83-128">註解</span><span class="sxs-lookup"><span data-stu-id="6ca83-128">Comment</span></span>|  
|-------------|-------------|  
|<span data-ttu-id="6ca83-129">支援叫用外部程式所需的 RFC</span><span class="sxs-lookup"><span data-stu-id="6ca83-129">Support for invoking external programs required by an RFC</span></span>|<span data-ttu-id="6ca83-130">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]提供的繫結屬性， **RfcAllowStartProgram** ，可以設定以啟用 RFC 用戶端程式庫，來叫用外部的程式，如果任何，需要特定的 RFC。</span><span class="sxs-lookup"><span data-stu-id="6ca83-130">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] provides a binding property, **RfcAllowStartProgram** that can be set to enable the RFC client library to invoke external programs, if any, required by a particular RFC.</span></span> <span data-ttu-id="6ca83-131">如需此繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6ca83-131">For more information about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>|  
|<span data-ttu-id="6ca83-132">支援的單一呼叫中傳送多個 Idoc</span><span class="sxs-lookup"><span data-stu-id="6ca83-132">Support for sending multiple IDOCs in a single call</span></span>|<span data-ttu-id="6ca83-133">SAP 配接器現在支援傳送配接器的單一呼叫中的相同類型的多個 Idoc。</span><span class="sxs-lookup"><span data-stu-id="6ca83-133">The SAP adapter now supports sending multiple IDOCs of the same type in a single adapter call.</span></span>|  
  
### <a name="other-features"></a><span data-ttu-id="6ca83-134">其他功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-134">Other Features</span></span>  
  
|<span data-ttu-id="6ca83-135">功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-135">Feature</span></span>|<span data-ttu-id="6ca83-136">註解</span><span class="sxs-lookup"><span data-stu-id="6ca83-136">Comment</span></span>|  
|-------------|-------------|  
|<span data-ttu-id="6ca83-137">使用中的配接器的新方法[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ca83-137">New way of using the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span></span>|<span data-ttu-id="6ca83-138">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可用於 BizTalk 作為 WCF 自訂連接埠或 WCF SAP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="6ca83-138">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can be used in BizTalk either as a WCF-Custom port or a WCF-SAP port.</span></span> <span data-ttu-id="6ca83-139">如果您想要使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過 WCF 自訂連接埠，您不需要新增 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]預設的管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6ca83-139">If you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default.</span></span> <span data-ttu-id="6ca83-140">不過，如果您想要使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過 WCF SAP 連接埠，您必須先新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6ca83-140">However, if you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] through a WCF-SAP port, you must first add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="6ca83-141">如需詳細資訊，請參閱[將 SAP 配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="6ca83-141">For more information, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>|  
  
## <a name="deprecated-features-in-the-sap-adapter"></a><span data-ttu-id="6ca83-142">SAP 配接器中已被取代的功能</span><span class="sxs-lookup"><span data-stu-id="6ca83-142">Deprecated Features in the SAP Adapter</span></span>  
 <span data-ttu-id="6ca83-143">下列各節列出的功能，並支援舊版的配接器，但其目前的版本中不支援[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ca83-143">The following sections lists the features that were supported in the previous version of the adapter, but which are not supported in the current version of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
### <a name="enablebusinessobjects-binding-property-deprecated"></a><span data-ttu-id="6ca83-144">已被取代的 EnableBusinessObjects 繫結屬性</span><span class="sxs-lookup"><span data-stu-id="6ca83-144">EnableBusinessObjects binding property deprecated</span></span>  
 <span data-ttu-id="6ca83-145">中的這個繫結屬性已被取代[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ca83-145">This binding property was deprecated in [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="6ca83-146">這個繫結屬性用來判定是否產生時使用的中繼資料時顯示 BAPI 節點[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ca83-146">This binding property was used to determine whether the BAPI node is displayed while generating metadata while using [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca83-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ca83-147">See Also</span></span>  
 [<span data-ttu-id="6ca83-148">瞭解 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="6ca83-148">Understand BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)