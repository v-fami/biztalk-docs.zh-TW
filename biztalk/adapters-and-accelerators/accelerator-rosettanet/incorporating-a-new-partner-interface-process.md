---
title: "加入新的交易夥伴介面程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, PIP schemas
- PIP schemas
- PIP schemas, deploying
- PIP schemas, downloading
- creating, PIP schemas
- PIP schemas, creating
ms.assetid: 6a5fcbcb-c6aa-40c0-bcca-dd0c391e7f42
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bf80c8bb577f4ddc8aec3282805714a830c7d23
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="incorporating-a-new-partner-interface-process"></a><span data-ttu-id="5c7ce-102">加入新的交易夥伴介面程序</span><span class="sxs-lookup"><span data-stu-id="5c7ce-102">Incorporating a New Partner Interface Process</span></span>
<span data-ttu-id="5c7ce-103">您可以將新的 RosettaNet 夥伴介面程序 (PIP) 結構描述併入 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 組件中。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-103">You can incorporate a new RosettaNet Partner Interface Process (PIP) schema in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] assemblies.</span></span> <span data-ttu-id="5c7ce-104">作法：</span><span class="sxs-lookup"><span data-stu-id="5c7ce-104">You do so by:</span></span>  
  
-   <span data-ttu-id="5c7ce-105">從 RosettaNet 網站下載 PIP 結構描述[http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859)。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-105">Downloading the PIP schema from the RosettaNet Web site at [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859).</span></span>  
  
-   <span data-ttu-id="5c7ce-106">將結構描述部署至 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 做為 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] RNPIP 組件的一部分，或是不同 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組件的一部分。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-106">Deploying the schema to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] as part of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] RNPIPs assembly or as part of a separate [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] assembly.</span></span> <span data-ttu-id="5c7ce-107">如需詳細資訊，請參閱[擴充 BTARN 使用新的 PIP](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md)。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-107">For more information, see [Extending BTARN with a New PIP](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md).</span></span>  
  
-   <span data-ttu-id="5c7ce-108">在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中建立新的「程序組態設定」。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-108">Creating a new Process Configuration Setting in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.</span></span> <span data-ttu-id="5c7ce-109">如需詳細資訊，請參閱[如何建立或編輯程序組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-109">For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span></span>  
  
 <span data-ttu-id="5c7ce-110">從 RosettaNet 組織下載的結構描述通常是 .dtd 格式，具有所附的 PIP 規格，可以當做 .doc 檔案使用。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-110">The downloaded schema is generally in .dtd format, with an accompanying PIP specification from the RosettaNet organization as a .doc file.</span></span> <span data-ttu-id="5c7ce-111">擴充管線以使用新結構描述的程序包括將 PIP .dtd 檔轉換為 .xsd 檔。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-111">The process of extending the pipeline to use the new schema includes converting the PIP .dtd file into an .xsd file.</span></span>  
  
 <span data-ttu-id="5c7ce-112">安裝 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含一些 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-112">When you install [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes a number of XSD schemas.</span></span> <span data-ttu-id="5c7ce-113">您可以找到那些結構描述中的\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\Schemas 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-113">You can find those schemas in the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas folder.</span></span> <span data-ttu-id="5c7ce-114">BTARN 會將這些結構描述建置在 RNPIPs.dll 檔案中。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-114">BTARN builds these schemas into an RNPIPs.dll file.</span></span> <span data-ttu-id="5c7ce-115">如果您要變更其中一個結構描述，則必須在同一個資料夾中開啟 RNPIP 專案，並在 BizTalk 編輯器中變更結構描述，然後重新編譯並重新部署組件。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-115">If you have to change one of these schemas, you must open the RNPIPs project in the same folder, change the schema in BizTalk Editor, and then recompile and redeploy the assembly.</span></span> <span data-ttu-id="5c7ce-116">重新部署 RNPIPs.dll 檔之後，您必須重新部署使用這個結構描述的管線。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-116">After you redeploy the RNPIPs.dll file, you must redeploy the pipeline that uses the schema.</span></span> <span data-ttu-id="5c7ce-117">您可以使用這個程序，在 BTARN 中整合新的結構描述，但是擴充管線以加入新結構描述的作法，會比較簡單。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-117">You could use this process to incorporate a new schema in BTARN, but it is easier to extend the pipeline to include the new schema.</span></span>  
  
### <a name="to-obtain-the-pip-schema"></a><span data-ttu-id="5c7ce-118">取得 PIP 結構描述</span><span class="sxs-lookup"><span data-stu-id="5c7ce-118">To obtain the PIP schema</span></span>  
  
-   <span data-ttu-id="5c7ce-119">在 Internet Explorer 中，前往 RosettaNet 網站，網址[http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859)。</span><span class="sxs-lookup"><span data-stu-id="5c7ce-119">In Internet Explorer, go to the RosettaNet Web site at [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c7ce-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="5c7ce-120">See Also</span></span>  
 [<span data-ttu-id="5c7ce-121">使用新的 PIP 擴充 BTARN</span><span class="sxs-lookup"><span data-stu-id="5c7ce-121">Extending BTARN with a New PIP</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md)