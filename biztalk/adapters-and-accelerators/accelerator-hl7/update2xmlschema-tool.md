---
title: Update2XMLSchema 工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2.XML schemas, Update2XMLSchema tool
- schemas, Update2XMLSchema tool
- Update2XMLSchema tool
- Update2XMLSchema tool, syntax
ms.assetid: fd861e2f-ebda-427f-bd52-a2f05b7e22da
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0f5a33b8951d1f02cf0504ba833b35adf275834
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961108"
---
# <a name="update2xmlschema-tool"></a><span data-ttu-id="bfae9-102">Update2XMLSchema 工具</span><span class="sxs-lookup"><span data-stu-id="bfae9-102">Update2XMLSchema Tool</span></span>
<span data-ttu-id="bfae9-103">Update2XMLSchema 工具可讓您修改 HL7 2.XML 結構描述，才能使用 「 BizTalk 編輯器。</span><span class="sxs-lookup"><span data-stu-id="bfae9-103">The Update2XMLSchema tool enables you to modify HL7 2.XML schemas to work with BizTalk Editor.</span></span> <span data-ttu-id="bfae9-104">這是必要的因為某些 HL7 2.XML 結構描述無法正確內運作[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]而不需修改。</span><span class="sxs-lookup"><span data-stu-id="bfae9-104">This is necessary because certain HL7 2.XML schemas do not work correctly within [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] without modification.</span></span> <span data-ttu-id="bfae9-105">在修改後結構描述，此工具放入結構描述資料夾其中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝時，比方說， *\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\Templates\Schemas。</span><span class="sxs-lookup"><span data-stu-id="bfae9-105">After modifying the schemas, the tool places them in the Schemas folder where [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] is installed, for instance, *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\Templates\Schemas.</span></span>  
  
 <span data-ttu-id="bfae9-106">您需要更新以手動方式從執行 Update2XMLSchema 工具產生的結構描述中的某些欄位。</span><span class="sxs-lookup"><span data-stu-id="bfae9-106">You need to update manually some fields of the schemas that result from running the Update2XMLSchema tool.</span></span> <span data-ttu-id="bfae9-107">請參閱[所需的手動更新](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)如需這些結構描述的清單。</span><span class="sxs-lookup"><span data-stu-id="bfae9-107">See [Required Manual Updates](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) for a list of those schemas.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfae9-108">語法</span><span class="sxs-lookup"><span data-stu-id="bfae9-108">Syntax</span></span>  
 <span data-ttu-id="bfae9-109">此工具位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\2XML 公用程式。</span><span class="sxs-lookup"><span data-stu-id="bfae9-109">This tool is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\2XML Utilities.</span></span> <span data-ttu-id="bfae9-110">您可以執行此工具在命令提示字元使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="bfae9-110">You run this tool at the command prompt with the following command:</span></span>  
  
```  
Update2XMLSchema /s /v  
```  
  
 <span data-ttu-id="bfae9-111">下表列出使用此命令的參數。</span><span class="sxs-lookup"><span data-stu-id="bfae9-111">The following table lists the parameters to use with this command.</span></span>  
  
|<span data-ttu-id="bfae9-112">參數</span><span class="sxs-lookup"><span data-stu-id="bfae9-112">Parameter</span></span>|<span data-ttu-id="bfae9-113">名稱</span><span class="sxs-lookup"><span data-stu-id="bfae9-113">Name</span></span>|<span data-ttu-id="bfae9-114">值</span><span class="sxs-lookup"><span data-stu-id="bfae9-114">Value</span></span>|  
|---------------|----------|-----------|  
|<span data-ttu-id="bfae9-115">*S*</span><span class="sxs-lookup"><span data-stu-id="bfae9-115">*S*</span></span>|<span data-ttu-id="bfae9-116">Source</span><span class="sxs-lookup"><span data-stu-id="bfae9-116">Source</span></span>|<span data-ttu-id="bfae9-117">原始 HL7 結構描述的完整路徑</span><span class="sxs-lookup"><span data-stu-id="bfae9-117">Full path of the original HL7 schemas</span></span>|  
|<span data-ttu-id="bfae9-118">*V*</span><span class="sxs-lookup"><span data-stu-id="bfae9-118">*V*</span></span>|<span data-ttu-id="bfae9-119">Version</span><span class="sxs-lookup"><span data-stu-id="bfae9-119">Version</span></span>|<span data-ttu-id="bfae9-120">2.XML 結構描述的版本： 2.3.1、 2.4 或 2.5</span><span class="sxs-lookup"><span data-stu-id="bfae9-120">The version of the 2.XML schemas:  either 2.3.1, 2.4, or 2.5</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bfae9-121">範例</span><span class="sxs-lookup"><span data-stu-id="bfae9-121">Example</span></span>  
  
-   <span data-ttu-id="bfae9-122">如果您想要修改版本 2.3.1 2.XML 結構描述位於 c:\231XML\v231\xsd 目錄中，您會在命令提示字元輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="bfae9-122">If you want to modify version 2.3.1 2.XML schemas located in the c:\231XML\v231\xsd directory, you would type the following command at the command prompt:</span></span>  
  
```  
Update2XMLSchema /s c:\231XML\v231\xsd /v 2.3.1  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="bfae9-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="bfae9-123">In This Section</span></span>  
  
-   [<span data-ttu-id="bfae9-124">需要手動更新</span><span class="sxs-lookup"><span data-stu-id="bfae9-124">Required Manual Updates</span></span>](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)