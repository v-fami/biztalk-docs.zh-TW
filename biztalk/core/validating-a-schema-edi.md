---
title: 驗證結構描述 (EDI) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6175460-2dcf-4fef-b770-02f0a058bf93
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44cd2672f7ba9be796c1ff802be51324fbfe3256
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287782"
---
# <a name="validating-a-schema-edi"></a><span data-ttu-id="50116-102">驗證結構描述 (EDI)</span><span class="sxs-lookup"><span data-stu-id="50116-102">Validating a Schema (EDI)</span></span>
<span data-ttu-id="50116-103">您可以在設計階段驗證 EDI 結構描述。</span><span class="sxs-lookup"><span data-stu-id="50116-103">You can validate an EDI schema at design time.</span></span> <span data-ttu-id="50116-104">若要執行此動作，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 XML 工具延伸模組。</span><span class="sxs-lookup"><span data-stu-id="50116-104">To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="50116-105">驗證結構描述作業會根據 EDI 規則來驗證結構描述。</span><span class="sxs-lookup"><span data-stu-id="50116-105">The validate-schema operation validates the schema based on EDI rules.</span></span> <span data-ttu-id="50116-106">因此，您不必指定輸入訊息執行個體來驗證結構描述。</span><span class="sxs-lookup"><span data-stu-id="50116-106">You do not have to designate an input message instance to validate a schema.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="50116-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="50116-107">Prerequisites</span></span>  
 <span data-ttu-id="50116-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="50116-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-validate-a-schema"></a><span data-ttu-id="50116-109">若要驗證結構描述</span><span class="sxs-lookup"><span data-stu-id="50116-109">To validate a schema</span></span>  
  
1.  <span data-ttu-id="50116-110">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟專案。</span><span class="sxs-lookup"><span data-stu-id="50116-110">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.</span></span> <span data-ttu-id="50116-111">在 [方案總管] 中，將您要驗證的訊息結構描述加入至該專案中。</span><span class="sxs-lookup"><span data-stu-id="50116-111">To the project in Solution Explorer, add the message schema that you want to validate.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50116-112">訊息結構描述底下的適當子資料夾位於[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾。</span><span class="sxs-lookup"><span data-stu-id="50116-112">The message schemas are located in the appropriate subfolder under the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder.</span></span> <span data-ttu-id="50116-113">如需安裝的結構描述檔案的資訊，請參閱[如何安裝 EDI 結構描述檔案](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550)。</span><span class="sxs-lookup"><span data-stu-id="50116-113">For information on installing the schema files, see [How to Install EDI Schema Files](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50116-114">您不必建置專案來驗證結構描述。</span><span class="sxs-lookup"><span data-stu-id="50116-114">You do not have to build the project to validate a schema.</span></span>  
  
2.  <span data-ttu-id="50116-115">以滑鼠右鍵按一下方案總管] 中的結構描述，然後按一下 [**驗證結構描述**。</span><span class="sxs-lookup"><span data-stu-id="50116-115">Right-click the schema in Solution Explorer, and then click **Validate Schema**.</span></span>  
  
3.  <span data-ttu-id="50116-116">確認 [輸出] 視窗中有指出作業成功的訊息。</span><span class="sxs-lookup"><span data-stu-id="50116-116">Verify that there is a message in the Output window indicating that the operation succeeded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50116-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50116-117">See Also</span></span>  
 [<span data-ttu-id="50116-118">使用設計階段 XML 工具</span><span class="sxs-lookup"><span data-stu-id="50116-118">Using Design-Time XML Tools</span></span>](../core/using-design-time-xml-tools.md)