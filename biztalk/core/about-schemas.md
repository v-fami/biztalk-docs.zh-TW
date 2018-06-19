---
title: 關於結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ec2b79c-7cfe-4b00-bcff-dfad3944c83b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a452675cb11b13ae83f940ce10b09c72a622dc8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224222"
---
# <a name="about-schemas"></a><span data-ttu-id="4502a-102">關於結構描述</span><span class="sxs-lookup"><span data-stu-id="4502a-102">About Schemas</span></span>
<span data-ttu-id="4502a-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用 XML 結構描述定義 (XSD) 語言定義它所處理的所有訊息之結構，這些訊息結構的定義就稱為結構描述。</span><span class="sxs-lookup"><span data-stu-id="4502a-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the XML Schema definition (XSD) language to define the structure of all messages that it processes, and refers to these definitions of message structure as schemas.</span></span> <span data-ttu-id="4502a-104">在絕大部分的情況下，結構化訊息是所有應用程式的核心。</span><span class="sxs-lookup"><span data-stu-id="4502a-104">With few exceptions, structured messages are the core of any application.</span></span> <span data-ttu-id="4502a-105">這些結構化訊息可以是任何形式、大小，並以一系列大範圍的後端系統和資料存放區為目標。</span><span class="sxs-lookup"><span data-stu-id="4502a-105">These structured messages can take any form, large or small, and target a wide array of back-end systems and data stores.</span></span> <span data-ttu-id="4502a-106">經常建立和消耗結構化訊息的系統使用不同的格式。</span><span class="sxs-lookup"><span data-stu-id="4502a-106">Systems that create and consume the structured messages frequently use different formats.</span></span> <span data-ttu-id="4502a-107">結構化訊息最常使用的兩種格式為 XML 和一般檔案。</span><span class="sxs-lookup"><span data-stu-id="4502a-107">Two of the most common formats for structured messages are XML and flat files.</span></span>  
  
 <span data-ttu-id="4502a-108">「BizTalk 編輯器」的設計目的是簡化定義訊息結構描述和驗證特定訊息是否符合該結構描述的程序。</span><span class="sxs-lookup"><span data-stu-id="4502a-108">BizTalk Editor is designed to simplify the process of defining a message schema and validating whether a particular message conforms to that schema.</span></span> <span data-ttu-id="4502a-109">在定義結構描述和驗證訊息的程序中，您可能會執行部分下列工作：</span><span class="sxs-lookup"><span data-stu-id="4502a-109">In the process of defining schemas and validating messages, you will likely perform some of the following tasks:</span></span>  
  
-   <span data-ttu-id="4502a-110">為結構化 XML 訊息建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="4502a-110">Create schemas for structured XML messages.</span></span>  
  
-   <span data-ttu-id="4502a-111">為一般檔案訊息建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="4502a-111">Create schemas for flat file messages.</span></span>  
  
-   <span data-ttu-id="4502a-112">從格式正確的 XML 執行個體資料產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="4502a-112">Generate schemas from well-formed XML instance data.</span></span>  
  
-   <span data-ttu-id="4502a-113">驗證訊息是否符合特定的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4502a-113">Validate message conformance to a specific schema.</span></span>  
  
-   <span data-ttu-id="4502a-114">執行設計階段的結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="4502a-114">Perform design-time validation of schemas.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4502a-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="4502a-115">In This Section</span></span>  
  
-   [<span data-ttu-id="4502a-116">不同類型的 BizTalk 結構描述</span><span class="sxs-lookup"><span data-stu-id="4502a-116">Different Types of BizTalk Schemas</span></span>](../core/different-types-of-biztalk-schemas.md)  
  
-   [<span data-ttu-id="4502a-117">XSD 的角色</span><span class="sxs-lookup"><span data-stu-id="4502a-117">Role of XSD</span></span>](../core/role-of-xsd.md)  
  
-   [<span data-ttu-id="4502a-118">在網站上的 XSD 資源</span><span class="sxs-lookup"><span data-stu-id="4502a-118">XSD Resources on the Web</span></span>](../core/xsd-resources-on-the-web.md)  
  
-   [<span data-ttu-id="4502a-119">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="4502a-119">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)  
  
-   [<span data-ttu-id="4502a-120">使用其他結構描述的結構描述</span><span class="sxs-lookup"><span data-stu-id="4502a-120">Schemas That Use Other Schemas</span></span>](../core/schemas-that-use-other-schemas.md)  
  
-   [<span data-ttu-id="4502a-121">型別重複使用和衍生類別</span><span class="sxs-lookup"><span data-stu-id="4502a-121">Type Reuse and Derivations</span></span>](../core/type-reuse-and-derivations.md)  
  
-   [<span data-ttu-id="4502a-122">從舊版的 BizTalk Server 移轉結構描述</span><span class="sxs-lookup"><span data-stu-id="4502a-122">Schema Migration from Previous Versions of BizTalk Server</span></span>](../core/schema-migration-from-previous-versions-of-biztalk-server.md)  
  
-   [<span data-ttu-id="4502a-123">使用訊息內容控制訊息處理方式</span><span class="sxs-lookup"><span data-stu-id="4502a-123">Ways to Use Message Content to Control Message Processing</span></span>](../core/ways-to-use-message-content-to-control-message-processing.md)  
  
-   [<span data-ttu-id="4502a-124">Visual Studio 中的結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="4502a-124">Schema Validation in Visual Studio</span></span>](../core/schema-validation-in-visual-studio.md)  
  
-   [<span data-ttu-id="4502a-125">執行個體訊息產生和驗證</span><span class="sxs-lookup"><span data-stu-id="4502a-125">Instance Message Generation and Validation</span></span>](../core/instance-message-generation-and-validation.md)