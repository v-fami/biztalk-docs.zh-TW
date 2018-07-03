---
title: 安裝、 結構描述，以及限制 TIBCO Rendezvous 配接器 |Microsoft Docs
description: 安裝、 產生和結構描述，BizTalk adapter for TIBCO Rendezvous 在 BizTalk Server 中的限制
ms.custom: ''
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6404e7e-f671-4c57-a222-0bbe7cbc334f
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f1eafd0c4a5ff96c3083d28b23347a2908aa52c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022100"
---
# <a name="install-schemas-and-limitations-of-the-tibco-rendezvous-adapter"></a><span data-ttu-id="92fcd-103">安裝、 結構描述和 TIBCO Rendezvous 配接器的限制</span><span class="sxs-lookup"><span data-stu-id="92fcd-103">Install, schemas, and limitations of the TIBCO Rendezvous adapter</span></span>

## <a name="install-and-setup"></a><span data-ttu-id="92fcd-104">安裝及設定</span><span class="sxs-lookup"><span data-stu-id="92fcd-104">Install and setup</span></span>

<span data-ttu-id="92fcd-105">[安裝及設定企業應用程式的介面卡](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md)包含的步驟安裝企業配接器，而且也包含 安裝配接器之前和之後安裝配接器所知道的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="92fcd-105">[Install and configure the adapters for enterprise applications](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md) includes the steps to install the enterprise adapters, and also includes key information to know before you install the adapter, and after you install the adapter.</span></span> 

## <a name="generate-schemas"></a><span data-ttu-id="92fcd-106">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="92fcd-106">Generate schemas</span></span>
<span data-ttu-id="92fcd-107">TIBCO Rendezvous 系統不包含訊息類型儲存機制。</span><span class="sxs-lookup"><span data-stu-id="92fcd-107">A TIBCO Rendezvous system does not include a message types repository.</span></span> <span data-ttu-id="92fcd-108">所有訊息建構和剖析都是在嵌入在 Rendezvous 應用程式層級。</span><span class="sxs-lookup"><span data-stu-id="92fcd-108">All the message construction and parsing is buried at the Rendezvous application level.</span></span> <span data-ttu-id="92fcd-109">由於此限制，配接器無法提供結構描述產生功能。</span><span class="sxs-lookup"><span data-stu-id="92fcd-109">Because of this limitation, adapter cannot provide schema-generation capabilities.</span></span>  
  
<span data-ttu-id="92fcd-110">您必須撰寫結構描述，並使用**加入現有項目**在 Visual Studio 中將它匯入協調流程中使用。</span><span class="sxs-lookup"><span data-stu-id="92fcd-110">You must write a schema, and use **Add Existing Item** in Visual Studio to import it for use in orchestrations.</span></span> <span data-ttu-id="92fcd-111">結構描述對於 BizTalk Server 開發工具以及 Visual Studio 中的整合十分重要。</span><span class="sxs-lookup"><span data-stu-id="92fcd-111">Schemas are very important for BizTalk Server development tools and for integration in Visual Studio.</span></span> <span data-ttu-id="92fcd-112">BizTalk Server 開發人員可以選擇提供完整的結構描述、精簡的結構描述，或介於兩者之間的版本。</span><span class="sxs-lookup"><span data-stu-id="92fcd-112">BizTalk Server developers can choose to provide a complete schema, a minimalist schema, or a version somewhere in between.</span></span>  

## <a name="limitations"></a><span data-ttu-id="92fcd-113">限制</span><span class="sxs-lookup"><span data-stu-id="92fcd-113">Limitations</span></span>

- <span data-ttu-id="92fcd-114">不保證欄位名稱的唯一性。</span><span class="sxs-lookup"><span data-stu-id="92fcd-114">Field name uniqueness is not guaranteed.</span></span> <span data-ttu-id="92fcd-115">如果 TIBCO Rendezvous 訊息包含兩個相同的欄位名稱，結果產生的 XML 會無效。</span><span class="sxs-lookup"><span data-stu-id="92fcd-115">If a TIBCO Rendezvous message contains two field names that are the same, the resulting XML is not valid.</span></span>  
  
- <span data-ttu-id="92fcd-116">不會提供欄位排序。</span><span class="sxs-lookup"><span data-stu-id="92fcd-116">Field ordering/sorting is not provided.</span></span>  
  
- <span data-ttu-id="92fcd-117">根據 TIBCO Rendezvous 文件，不可列印的字元不會使用在主體名稱中，但是，仍有使用這類字元的可能。</span><span class="sxs-lookup"><span data-stu-id="92fcd-117">According to TIBCO Rendezvous documentation, non-printable characters are not used in subject names; however, it is still possible that such characters are used.</span></span> <span data-ttu-id="92fcd-118">BizTalk Adapter for TIBCO Rendezvous 不支援含有這些字元的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="92fcd-118">BizTalk Adapter for TIBCO Rendezvous does not support subject names containing those characters.</span></span>  
  
- <span data-ttu-id="92fcd-119">不支援對精靈的安全連線。</span><span class="sxs-lookup"><span data-stu-id="92fcd-119">Secure connection to daemons is not supported.</span></span>  
  
- <span data-ttu-id="92fcd-120">不支援自訂資料型別。</span><span class="sxs-lookup"><span data-stu-id="92fcd-120">Custom data types are not supported.</span></span>  
  
- <span data-ttu-id="92fcd-121">傳輸端不支援「認證傳訊」。</span><span class="sxs-lookup"><span data-stu-id="92fcd-121">Certified Messaging is not supported on the transmit side.</span></span>  
- 
  ## <a name="next-step"></a><span data-ttu-id="92fcd-122">下一步</span><span class="sxs-lookup"><span data-stu-id="92fcd-122">Next step</span></span>

[<span data-ttu-id="92fcd-123">教學課程：使用 Microsoft BizTalk Adapter for TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="92fcd-123">Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous</span></span>](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)  