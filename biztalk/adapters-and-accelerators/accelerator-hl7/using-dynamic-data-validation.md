---
title: 使用動態資料驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic data validation
- validating, dynamic data
ms.assetid: 8dac7f74-92a7-447c-97bf-b1f3ce39b614
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b0ff37ff260ca11e594a208c125f229e2961c01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967159"
---
# <a name="using-dynamic-data-validation"></a><span data-ttu-id="d3e2a-102">使用動態資料驗證</span><span class="sxs-lookup"><span data-stu-id="d3e2a-102">Using Dynamic Data Validation</span></span>
<span data-ttu-id="d3e2a-103">動態資料驗證很重要的一部分就驗證動態資料，其中包含驗證的訊息格式和訊息內容的訊息內容。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-103">An important part of dynamic data validation is validating message content against dynamic data, which includes validating the message format and the message content.</span></span> <span data-ttu-id="d3e2a-104">MicrosoftBizTalk 伺服器實作 XSD 檔案中，文件結構描述定義，並驗證訊息格式。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-104">A document schema, which MicrosoftBizTalk Server implements in an XSD file, defines and validates message formats.</span></span> <span data-ttu-id="d3e2a-105">商務規則定義訊息內容，其中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]透過商務規則引擎原則驗證。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-105">Business rules define message content, which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] validates through Business Rule Engine policies.</span></span> <span data-ttu-id="d3e2a-106">內容驗證可以包含確認訊息執行個體中的資料符合相對頻率可能會變更的資料。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-106">Content validation can include confirmation that data in the message instance matches data that may change with relative frequency.</span></span> <span data-ttu-id="d3e2a-107">Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]動態的方式，實作這種類型的驗證，以便您可以更新此資料在生產環境中，而不必重新編譯程式碼，或關閉服務。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-107">Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] implements this type of validation in a dynamic manner, so that you can update this data in a production environment, without having to recompile code or shut down services.</span></span>  
  
## <a name="validate-and-expose-data"></a><span data-ttu-id="d3e2a-108">驗證，並公開資料</span><span class="sxs-lookup"><span data-stu-id="d3e2a-108">Validate and Expose Data</span></span>  
 <span data-ttu-id="d3e2a-109">在執行動態資料驗證 (DDV) 有兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="d3e2a-109">There are two steps in performing Dynamic Data Validation (DDV):</span></span>  
  
- <span data-ttu-id="d3e2a-110">公開資料。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-110">Expose the data.</span></span>  
  
- <span data-ttu-id="d3e2a-111">適用於使用該資料的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-111">Apply validation rules using that data.</span></span>  
  
  <span data-ttu-id="d3e2a-112">DDV 支援下列用於儲存、 公開，和快取動態資料：</span><span class="sxs-lookup"><span data-stu-id="d3e2a-112">DDV provides the following support for storing, exposing, and caching dynamic data:</span></span>  
  
- <span data-ttu-id="d3e2a-113">Message 類別的商務規則引擎會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-113">The Business Rule Engine or Message Class performs validation.</span></span>  
  
- <span data-ttu-id="d3e2a-114">商務規則引擎會透過資料庫資料表資料行詞彙的資料公開。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-114">The Business Rule Engine exposes data through the Database table column vocabulary.</span></span> <span data-ttu-id="d3e2a-115">商務規則引擎會驗證這個動態的資料，對訊息，藉由實作從管線或協調流程執行的規則集。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-115">The Business Rule Engine validates this dynamic data against messages by implementing a rule set that runs from a pipeline or orchestration.</span></span>  
  
- <span data-ttu-id="d3e2a-116">現有 SQL 介面，例如 SQL Enterprise Manager 和 Query Analyzer 中，公開在設計階段是被動的動態資料。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-116">Existing SQL interfaces, such as SQL Enterprise Manager and Query Analyzer, expose dynamic data that is passive at design time.</span></span>  
  
- <span data-ttu-id="d3e2a-117">商務規則引擎資料庫資料表資料行的詞彙定義在執行階段公開動態資料。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-117">The Business Rule Engine database table column vocabulary definition exposes dynamic data at run time.</span></span>  
  
- <span data-ttu-id="d3e2a-118">商務規則引擎在執行階段公開訊息執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-118">The Business Rule Engine exposes message instance data at run time.</span></span>  
  
- <span data-ttu-id="d3e2a-119">商務規則引擎的 XML 文件的詞彙定義在設計階段公開訊息執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-119">A Business Rules Engine XML document vocabulary definition exposes message instance data at design time.</span></span>  
  
- <span data-ttu-id="d3e2a-120">您可以撰寫規則在設計階段中的商務規則編輯器 」 使用者介面或直接在 商務規則語言 」 (BRL) XML 文字編輯器中。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-120">You can compose rules at design time in the Business Rule Composer user interface or directly in Business Rules Language (BRL) XML in a text editor.</span></span>  
  
  <span data-ttu-id="d3e2a-121">如需有關商務規則和商務規則引擎的詳細資訊，請參閱 「 開發與商務規則 」 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-121">For more information about business rules and the Business Rule Engine, see "Developing with Business Rules" in BizTalk Server Help.</span></span>  
  
## <a name="extending-ddv"></a><span data-ttu-id="d3e2a-122">擴充 DDV</span><span class="sxs-lookup"><span data-stu-id="d3e2a-122">Extending DDV</span></span>  
 <span data-ttu-id="d3e2a-123">如果您變更 HL7 欄位交互驗證或資料類型驗證，您必須注意兩件事：</span><span class="sxs-lookup"><span data-stu-id="d3e2a-123">If you change HL7-based cross-field validation or data type validation, you must note two things:</span></span>  
  
-   <span data-ttu-id="d3e2a-124">如果您修改現有的規則，您不需要重新部署。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-124">If you modify an existing rule, you do not need to redeploy.</span></span>  
  
-   <span data-ttu-id="d3e2a-125">如果您建立或刪除的管線元件會影響新規則，然後您必須重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d3e2a-125">If you create or delete a new rule that a pipeline component affects, then you must recompile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e2a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3e2a-126">See Also</span></span>  
 <span data-ttu-id="d3e2a-127">[程式設計手冊](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span><span class="sxs-lookup"><span data-stu-id="d3e2a-127">[Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span></span>  
 [<span data-ttu-id="d3e2a-128">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="d3e2a-128">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)