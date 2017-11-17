---
title: "發佈 Web Services2 規劃 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, planning
- virtual directories, updating
- BizTalk Server Web Services Publishing Wizard
ms.assetid: 69107557-48e2-4f15-ba42-9fad476a8294
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d0b9d593a3309f7b4477f2fa735f7e265b614c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-publishing-web-services"></a><span data-ttu-id="2a819-102">規劃發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="2a819-102">Planning for Publishing Web Services</span></span>
<span data-ttu-id="2a819-103">您可以從您的協調流程存取 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="2a819-103">You can access Web services from your orchestrations.</span></span> <span data-ttu-id="2a819-104">您也可以使用「BizTalk Web 服務發佈精靈」來發佈 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="2a819-104">You can also use the BizTalk Web Services Publishing Wizard to publish your Web service.</span></span>  
  
 <span data-ttu-id="2a819-105">下表列出在您規劃 Web 服務時應回答的一些問題。</span><span class="sxs-lookup"><span data-stu-id="2a819-105">The following table lists some of the questions that you need to answer in planning for Web services.</span></span>  
  
|<span data-ttu-id="2a819-106">規劃問題</span><span class="sxs-lookup"><span data-stu-id="2a819-106">Planning question</span></span>|<span data-ttu-id="2a819-107">建議</span><span class="sxs-lookup"><span data-stu-id="2a819-107">Recommendation</span></span>|  
|-----------------------|--------------------|  
|<span data-ttu-id="2a819-108">您是否已經建立自己的 BizTalk Server 專案？</span><span class="sxs-lookup"><span data-stu-id="2a819-108">Have you built your BizTalk Server project?</span></span>|<span data-ttu-id="2a819-109">您必須先建立自己的 BizTalk Server 專案，才可以執行「BizTalk Web 服務發佈精靈」。</span><span class="sxs-lookup"><span data-stu-id="2a819-109">You must build your BizTalk Server project prior to running the BizTalk Web Services Publishing Wizard.</span></span>|  
|<span data-ttu-id="2a819-110">您是否已經將系統啟用成執行 Web 服務？</span><span class="sxs-lookup"><span data-stu-id="2a819-110">Have you enabled your system to run Web services?</span></span>|<span data-ttu-id="2a819-111">您必須先啟用電腦上的 Web 服務，才可以執行「BizTalk Web 服務發佈精靈」。</span><span class="sxs-lookup"><span data-stu-id="2a819-111">You must enable Web services on your computer before running the BizTalk Web Services Publishing Wizard.</span></span> <span data-ttu-id="2a819-112">如需將系統啟用成 Web 服務的詳細資訊，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2a819-112">For more information about enabling your system for Web services, see [Enabling Web Services](../core/enabling-web-services.md).</span></span>|  
|<span data-ttu-id="2a819-113">您是否已確認您的結構描述只包含有效的 XML 字元和項目？</span><span class="sxs-lookup"><span data-stu-id="2a819-113">Have you verified that your schema contains only valid XML characters and elements?</span></span>|<span data-ttu-id="2a819-114">Web 服務不支援中文、日文或韓文 (CJK) Unified Ideograph Extension A 等字元。</span><span class="sxs-lookup"><span data-stu-id="2a819-114">Web services do not support Chinese, Japanese, or Korean (CJK) Unified Ideograph Extension A characters.</span></span> <span data-ttu-id="2a819-115">特定的 XML 結構描述 (XSD) 項目也有所限制。</span><span class="sxs-lookup"><span data-stu-id="2a819-115">There are also restrictions on certain XML Schema (XSD) elements.</span></span> <span data-ttu-id="2a819-116">如需有效的 XML 字元和支援的元素和元素的考量的詳細資訊，請參閱[考量發佈 Web 服務時](../core/considerations-when-publishing-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2a819-116">For more information about valid XML characters and supported elements and considerations for elements, see [Considerations When Publishing Web Services](../core/considerations-when-publishing-web-services.md).</span></span>|  
|<span data-ttu-id="2a819-117">在您的 BizTalk Server 專案中，是否有任何訊息類型會使用使用者定義的 .NET 類別？</span><span class="sxs-lookup"><span data-stu-id="2a819-117">Do any of the message types in your BizTalk Server project use user-defined .NET classes?</span></span>|<span data-ttu-id="2a819-118">您必須安裝其中包含訊息類型在全域組件快取 (GAC) 內參考之使用者定義 .NET 類別的組件。</span><span class="sxs-lookup"><span data-stu-id="2a819-118">You must install assemblies containing user-defined .NET classes that message types reference in the global assembly cache (GAC).</span></span>|  
|<span data-ttu-id="2a819-119">執行您 Web 用戶端會使用提供的認證用於**WindowsUser**內容屬性？</span><span class="sxs-lookup"><span data-stu-id="2a819-119">Do your Web clients use the supplied credentials for the **WindowsUser** context property?</span></span>|<span data-ttu-id="2a819-120">已發行的 Web 服務使用之 Web 用戶端所提供的認證**WindowsUser**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="2a819-120">The credentials supplied by the Web clients consuming a published Web service use the **WindowsUser** context property.</span></span> <span data-ttu-id="2a819-121">「合作對象解析」會使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="2a819-121">Party Resolution uses this property.</span></span> <span data-ttu-id="2a819-122">如果您設定合作對象使用**WindowsUser**內容屬性和 Web 用戶端使用 Web 服務的認證來比對合作對象，BizTalk Server 會識別為來自對應的預先定義合作對象的訊息。</span><span class="sxs-lookup"><span data-stu-id="2a819-122">If you set up a Party using the **WindowsUser** context property and the Web client consumes the Web service with credentials that match the Party, BizTalk Server identifies the message as coming from the corresponding predefined party.</span></span> <span data-ttu-id="2a819-123">如需合作對象解析管線元件的詳細資訊，請參閱[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="2a819-123">For more information about party resolution with pipeline components, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a819-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a819-124">See Also</span></span>  
 [<span data-ttu-id="2a819-125">發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="2a819-125">Publishing Web Services</span></span>](../core/publishing-web-services.md)