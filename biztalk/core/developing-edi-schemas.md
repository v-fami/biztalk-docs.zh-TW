---
title: 開發 EDI 結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a8fbf3d-ebc7-47f6-87fa-e45722651262
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b241b5d0477d7aa477511c43b642e4e312f2651a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239278"
---
# <a name="developing-edi-schemas"></a><span data-ttu-id="e1f06-102">開發 EDI 結構描述</span><span class="sxs-lookup"><span data-stu-id="e1f06-102">Developing EDI Schemas</span></span>
<span data-ttu-id="e1f06-103">本節中的主題描述如何修改 EDI 結構描述搭配[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e1f06-103">The topics in this section describe how to modify EDI Schemas for use with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e1f06-104">若要在方案中使用文件結構描述，您需要將它加入至 BizTalk 專案中部署結構描述[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，然後建置並部署專案。</span><span class="sxs-lookup"><span data-stu-id="e1f06-104">To use a document schema in your solution, you need to deploy the schema by adding it to a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], and then building and deploying the project.</span></span> [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="e1f06-105">將部署的預設 BizTalk Application 1 中的專案。</span><span class="sxs-lookup"><span data-stu-id="e1f06-105"> will deploy the project in the default BizTalk Application 1.</span></span> <span data-ttu-id="e1f06-106">您可以看到所開啟部署的結構描述**結構描述**節點下的**BizTalk Application 1**節點**應用程式**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="e1f06-106">You can see the schemas that are deployed by opening the **Schemas** node under **BizTalk Application 1** node the **Applications** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="e1f06-107">您可以使用命令列部署工具部署到不同的應用程式的組件`BTSTask`。</span><span class="sxs-lookup"><span data-stu-id="e1f06-107">You can deploy an assembly into a different application by using the command-line deployment tool `BTSTask`.</span></span>  
  
 <span data-ttu-id="e1f06-108">服務和控制結構描述會自動部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態精靈。</span><span class="sxs-lookup"><span data-stu-id="e1f06-108">The service and control schemas are automatically deployed by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration wizard.</span></span> <span data-ttu-id="e1f06-109">若要查看它們，請按一下**結構描述**節點**BizTalk EDI 應用程式**在管理主控台中的節點。</span><span class="sxs-lookup"><span data-stu-id="e1f06-109">To see them, click the **Schemas** node in the **BizTalk EDI Application** node in the Administration Console.</span></span> <span data-ttu-id="e1f06-110">如需有關這些結構描述的詳細資訊，請參閱[EDI 服務和控制結構描述](../core/edi-service-and-control-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="e1f06-110">For more information about these schemas, see [EDI Service and Control Schemas](../core/edi-service-and-control-schemas.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1f06-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="e1f06-111">In This Section</span></span>  
  
-   [<span data-ttu-id="e1f06-112">修改 EDI 結構描述</span><span class="sxs-lookup"><span data-stu-id="e1f06-112">Modifying EDI Schemas</span></span>](../core/modifying-edi-schemas.md)  
  
-   [<span data-ttu-id="e1f06-113">信封結構描述中自訂列舉</span><span class="sxs-lookup"><span data-stu-id="e1f06-113">Customizing Enumerations in the Envelope Schema</span></span>](../core/customizing-enumerations-in-the-envelope-schema.md)  
  
-   [<span data-ttu-id="e1f06-114">設定欄位交互驗證</span><span class="sxs-lookup"><span data-stu-id="e1f06-114">Configuring Cross-Field Validation</span></span>](../core/configuring-cross-field-validation.md)  
  
## <a name="see-also"></a><span data-ttu-id="e1f06-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1f06-115">See Also</span></span>  
 [<span data-ttu-id="e1f06-116">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="e1f06-116">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)