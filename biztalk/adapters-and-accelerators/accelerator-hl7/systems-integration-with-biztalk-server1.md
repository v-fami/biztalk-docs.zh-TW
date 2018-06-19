---
title: HL7 系統整合 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f66a4fc-186c-415f-a7ed-31f620f0495f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c7189802ea981bd26b717f09bb3de0e445c9314
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005031"
---
# <a name="systems-integration-with-biztalk-server"></a><span data-ttu-id="3fa12-102">與 BizTalk Server 進行系統整合</span><span class="sxs-lookup"><span data-stu-id="3fa12-102">Systems Integration with BizTalk Server</span></span>
<span data-ttu-id="3fa12-103">Microsoft BizTalk Server 是專為電子商務應用程式設計所設計的整合伺服器。</span><span class="sxs-lookup"><span data-stu-id="3fa12-103">Microsoft BizTalk Server is an integration server designed for eBusiness applications.</span></span> <span data-ttu-id="3fa12-104">它建置在 Windows Server、 SQL Server 和 SharePoint，並利用 Visual Studio 的功能。</span><span class="sxs-lookup"><span data-stu-id="3fa12-104">It is built on the  Windows Server, SQL Server, and SharePoint, and leverages the functionality of  Visual Studio.</span></span> <span data-ttu-id="3fa12-105">此技術堆疊提供許多功能，可以用來開發、實作、操作和維護您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="3fa12-105">This technology stack provides a range of functionality and features for developing, implementing, operating, and maintaining your solution.</span></span>  
  
 <span data-ttu-id="3fa12-106">BizTalk Server 提供下列整合服務可讓您搭配利用 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="3fa12-106">BizTalk Server provides the following integration services that you can use in conjunction with BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).</span></span>  
  
## <a name="message-integration"></a><span data-ttu-id="3fa12-107">訊息整合</span><span class="sxs-lookup"><span data-stu-id="3fa12-107">Message Integration</span></span>  
 <span data-ttu-id="3fa12-108">BizTalk Server 透過自動化訊息交換，整合不同的實體 （部門、 商務合作夥伴、 廠商、 等等）。</span><span class="sxs-lookup"><span data-stu-id="3fa12-108">BizTalk Server integrates different entities (departments, business partners, vendors, and so on) by automating message exchange.</span></span> <span data-ttu-id="3fa12-109">它會使用可延伸標記語言 (XML) 做為一般的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="3fa12-109">It uses Extensible Markup Language (XML) as a common communication protocol.</span></span> <span data-ttu-id="3fa12-110">並使用 XML 結構描述定義 (XSD) 結構描述來描述和驗證訊息，另外也利用 XSL 轉換 (XSLT) 將資料從一個訊息轉換到另一個。</span><span class="sxs-lookup"><span data-stu-id="3fa12-110">It uses XML Schema Definition (XSD) schemas to describe and validate messages, and XSL Transformations (XSLT) to transform data from one message to another.</span></span>  
  
 <span data-ttu-id="3fa12-111">BizTalk Server 整合引擎會將訊息從一個位置路由至另一個。</span><span class="sxs-lookup"><span data-stu-id="3fa12-111">The BizTalk Server integration engine routes messages from one location to another.</span></span> <span data-ttu-id="3fa12-112">它的特色是發行者/訂閱者模型，可讓一個部門發佈文件，讓另一個部門訂閱該文件。</span><span class="sxs-lookup"><span data-stu-id="3fa12-112">It features a publisher/subscriber model that enables one department to publish a document, and another to subscribe to it.</span></span> <span data-ttu-id="3fa12-113">訂閱的部門可以在發佈的部門不知情的情形下訂閱訊息。</span><span class="sxs-lookup"><span data-stu-id="3fa12-113">The subscribing department can subscribe to the message without the publishing department knowing about it.</span></span> <span data-ttu-id="3fa12-114">如此一來，即可有效地處理交易夥伴組織，透過彈性的中樞-支點安排方式取代點對點通訊。</span><span class="sxs-lookup"><span data-stu-id="3fa12-114">This enables efficient handling of partner organizations, replacing point-to-point communications with a flexible hub-spoke arrangement.</span></span>  
  
## <a name="business-process-automation"></a><span data-ttu-id="3fa12-115">商務程序自動化</span><span class="sxs-lookup"><span data-stu-id="3fa12-115">Business Process Automation</span></span>  
 <span data-ttu-id="3fa12-116">BizTalk Server 會自動執行，並整合商務程序，透過呼叫協調流程的程序對應連結一組獨特、 相關的動作，以單一處理序。</span><span class="sxs-lookup"><span data-stu-id="3fa12-116">BizTalk Server automates and integrates business processes by using a process map called an orchestration to link a set of distinct, related actions in a single process.</span></span> <span data-ttu-id="3fa12-117">透過建立協調流程，可以根據資料交換及分析來連結步驟，諸如訊息接收、訊息傳送、決策、迴圈及其他作業。</span><span class="sxs-lookup"><span data-stu-id="3fa12-117">By creating an orchestration, you can link steps based on data exchange and analysis, such as message receiving, message sending, decisions, loops, and other operations.</span></span> <span data-ttu-id="3fa12-118">協調流程可讓您建立商務程序，將會在事件發生時自動執行。</span><span class="sxs-lookup"><span data-stu-id="3fa12-118">An orchestration enables you to create a business process that will run automatically when an event occurs.</span></span>  
  
 <span data-ttu-id="3fa12-119">使用 BizTalk Server，您可以動態變更商務規則為基礎的處理序。</span><span class="sxs-lookup"><span data-stu-id="3fa12-119">Using BizTalk Server, you can dynamically change a process based on business rules.</span></span> <span data-ttu-id="3fa12-120">這種做法讓您可以依照商務的考量，彈性地變更協調流程程序中採取的措施。</span><span class="sxs-lookup"><span data-stu-id="3fa12-120">This gives you the flexibility to change the actions taken in an orchestrated process according to business considerations.</span></span> <span data-ttu-id="3fa12-121">例如，針對超過特定上限金額的訂單，限制其核准程序。</span><span class="sxs-lookup"><span data-stu-id="3fa12-121">An example is restricting the approval process for billing orders to those orders over a certain threshold.</span></span>  
  
 <span data-ttu-id="3fa12-122">BizTalk Server 也可讓您透過 「 人力工作流程服務自動化的協調流程內納入人為操作。</span><span class="sxs-lookup"><span data-stu-id="3fa12-122">BizTalk Server also enables you to include human actions within automated orchestrations, through Human Workflow Services.</span></span>  
  
## <a name="integration-of-heterogeneous-systems"></a><span data-ttu-id="3fa12-123">異質系統的整合</span><span class="sxs-lookup"><span data-stu-id="3fa12-123">Integration of Heterogeneous Systems</span></span>  
 <span data-ttu-id="3fa12-124">BizTalk Server 可以將在其中系統傳輸資料在不同的通訊協定的異質環境中的 IT 系統整合。</span><span class="sxs-lookup"><span data-stu-id="3fa12-124">BizTalk Server can integrate IT systems in a heterogeneous environment in which systems transmit data in different communications protocols.</span></span> <span data-ttu-id="3fa12-125">執行的方式是使用配接器透過不同的通訊協定連線至系統。</span><span class="sxs-lookup"><span data-stu-id="3fa12-125">It does so by using adapters to connect to systems using different protocols.</span></span> <span data-ttu-id="3fa12-126">它支援檔案、 FTP、 HTTP、 SMTP、 SOAP 和 SQL 配接器的使用。</span><span class="sxs-lookup"><span data-stu-id="3fa12-126">It supports the use of File, FTP, HTTP, SMTP, SOAP, and SQL adapters.</span></span> <span data-ttu-id="3fa12-127">您可以透過「BizTalk 配接器架構」(BizTalk Adapter Framework) 建立自訂的配接器。</span><span class="sxs-lookup"><span data-stu-id="3fa12-127">You can create custom adapters by using the BizTalk Adapter Framework.</span></span>  
  
## <a name="role-based-tools"></a><span data-ttu-id="3fa12-128">以角色為基礎的工具</span><span class="sxs-lookup"><span data-stu-id="3fa12-128">Role-based Tools</span></span>  
 <span data-ttu-id="3fa12-129">BizTalk Server 為開發和執行環境中開發人員、 IT 專業人員和商務專業人員共同作業以建立、 實作、 操作、 維護及自訂系統。</span><span class="sxs-lookup"><span data-stu-id="3fa12-129">BizTalk Server is a development and execution environment in which developers, IT professionals, and business professionals collaborate to create, implement, operate, maintain, and customize the system.</span></span> <span data-ttu-id="3fa12-130">BizTalk Server 會提供每個角色量身其使用的工具。</span><span class="sxs-lookup"><span data-stu-id="3fa12-130">BizTalk Server provides each of these roles with tools tailored to their use.</span></span>  
  
 <span data-ttu-id="3fa12-131">如需詳細資訊，請參閱[為基礎的角色為基礎的產品](../../adapters-and-accelerators/accelerator-hl7/a-role-based-product1.md)。</span><span class="sxs-lookup"><span data-stu-id="3fa12-131">For more information, see [A Role-based Product](../../adapters-and-accelerators/accelerator-hl7/a-role-based-product1.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3fa12-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="3fa12-132">See Also</span></span>  
 [<span data-ttu-id="3fa12-133">BizTalk Accelerator for HL7 在 BizTalk Server 中新增的項目</span><span class="sxs-lookup"><span data-stu-id="3fa12-133">What BizTalk Accelerator for HL7 Adds to BizTalk Server</span></span>](../../adapters-and-accelerators/accelerator-hl7/what-biztalk-accelerator-for-hl7-adds-to-biztalk-server.md)