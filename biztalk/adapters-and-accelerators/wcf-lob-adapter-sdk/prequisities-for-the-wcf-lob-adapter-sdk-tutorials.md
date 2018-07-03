---
title: WCF LOB 配接器 SDK 教學課程的 Prequisities |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7d47ac1-1605-4c6d-a331-8583771dca28
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9e0f1959563b0a0f1273de6341e2402f90f8f34
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995447"
---
# <a name="prequisities-for-the-wcf-lob-adapter-sdk-tutorials"></a><span data-ttu-id="54758-102">如需 WCF LOB 配接器 SDK 教學課程的 Prequisities</span><span class="sxs-lookup"><span data-stu-id="54758-102">Prequisities for the WCF LOB Adapter SDK tutorials</span></span>
<span data-ttu-id="54758-103">本章節提供詳細資料的概念，您應該先熟悉以充分利用教學課程中，以及完成所需的軟體。</span><span class="sxs-lookup"><span data-stu-id="54758-103">This section provides details about the concepts you should be familiar with to get the most out of the tutorials, as well as the software required to complete them.</span></span>  
  
## <a name="what-to-install"></a><span data-ttu-id="54758-104">要安裝的項目</span><span class="sxs-lookup"><span data-stu-id="54758-104">What to Install</span></span>  
 <span data-ttu-id="54758-105">若要開始教學課程，您必須在電腦上安裝下列軟體。</span><span class="sxs-lookup"><span data-stu-id="54758-105">To start the tutorials, you must have the following software installed on your computer.</span></span>  
  
- [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]
  
- <span data-ttu-id="54758-106">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="54758-106">Internet Information Services (IIS)</span></span>  
  
- [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)]
  
- [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<span data-ttu-id="54758-107"> （適用於您的 BizTalk Server 安裝檔案，以及具名 ASDK_x64 和 ASDK_x86）</span><span class="sxs-lookup"><span data-stu-id="54758-107"> (available with your BizTalk Server installation files, and named ASDK_x64 and ASDK_x86)</span></span>  
  
  <span data-ttu-id="54758-108">若要完成教學課程 3，您必須在電腦上安裝下列軟體。</span><span class="sxs-lookup"><span data-stu-id="54758-108">To complete Tutorial 3, you must have the following software installed on your computer.</span></span>  
  
- <span data-ttu-id="54758-109">Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="54758-109">Microsoft SharePoint</span></span>  
  
- <span data-ttu-id="54758-110">Microsoft SharePoint SDK</span><span class="sxs-lookup"><span data-stu-id="54758-110">Microsoft SharePoint SDK</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="54758-111">不要在生產環境中執行這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="54758-111">Do not perform these tutorials in your production environment.</span></span>  
  
<span data-ttu-id="54758-112">已完成的 Echo 配接器的 BizTalk 安裝檔案隨附`\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples`或`\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`。</span><span class="sxs-lookup"><span data-stu-id="54758-112">The completed Echo Adapter is included with your BizTalk installation files at `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` or `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="54758-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="54758-113">Prerequisites</span></span>  
 <span data-ttu-id="54758-114">教學課程假設您已熟悉下列：</span><span class="sxs-lookup"><span data-stu-id="54758-114">The tutorials assume that you are familiar with the following:</span></span>  
  
- <span data-ttu-id="54758-115">物件導向的軟體設計與開發</span><span class="sxs-lookup"><span data-stu-id="54758-115">Object-oriented software design and development</span></span>  
  
- <span data-ttu-id="54758-116">Windows Communication Foundation (WCF) 具體來說，通道模型程式設計和服務模型程式設計</span><span class="sxs-lookup"><span data-stu-id="54758-116">Windows Communication Foundation (WCF), specifically, channel model programming and service model programming</span></span>  
  
- <span data-ttu-id="54758-117">XSD、 XML、 WSDL 與 Web 服務描述語言 (WSDL) 與 API 之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="54758-117">XSD, XML, WSDL, and the relationship between Web Services Description Language (WSDL) and an API</span></span>  
  
- <span data-ttu-id="54758-118">C# 程式設計語言</span><span class="sxs-lookup"><span data-stu-id="54758-118">C# programming language</span></span>  
  
- <span data-ttu-id="54758-119">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="54758-119">.NET Framework</span></span>  
  
  <span data-ttu-id="54758-120">開始教學課程之前, 它很有幫助如果您已檢閱概念性主題的此 SDK，並有大致的了解中的頻道[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，包括中的型別**T:Microsoft.ServiceModel.Channels**並**T:Microsoft.ServiceModel.Channels.Common**命名空間。</span><span class="sxs-lookup"><span data-stu-id="54758-120">Before starting the tutorials, it will be helpful if you have reviewed the conceptual topics of this SDK, and have a general understanding of channels in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], including the types within the **T:Microsoft.ServiceModel.Channels** and **T:Microsoft.ServiceModel.Channels.Common** namespaces.</span></span>  <span data-ttu-id="54758-121">如需有關通道的詳細資訊，請參閱[通道模型概觀](https://msdn.microsoft.com/library/ms729840.aspx)。</span><span class="sxs-lookup"><span data-stu-id="54758-121">For more information about channels, see the [Channel Model Overview](https://msdn.microsoft.com/library/ms729840.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54758-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54758-122">See Also</span></span>  
 [<span data-ttu-id="54758-123">若要了解 WCF LOB 配接器 SDK 教學課程</span><span class="sxs-lookup"><span data-stu-id="54758-123">Tutorials to learn the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)