---
title: "從 PIP 建立格式正確的訊息執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message templates
- PIPs, message templates
ms.assetid: fed3698c-25d9-40ca-878a-60171f425bec
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e16020afb17d17c8add8e973ade0cd0c5cfcbbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-well-formed-message-instance-from-a-pip"></a><span data-ttu-id="783b8-102">從 PIP 建立格式正確的訊息執行個體</span><span class="sxs-lookup"><span data-stu-id="783b8-102">Creating a Well-Formed Message Instance from a PIP</span></span>
<span data-ttu-id="783b8-103">本主題描述如何產生格式正確的訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="783b8-103">This topic describes how to produce a well-formed message instance.</span></span> <span data-ttu-id="783b8-104">您可從交易夥伴介面程序 (PIP) 產生訊息執行個體的範本。</span><span class="sxs-lookup"><span data-stu-id="783b8-104">You can generate a template for a message instance from the Partner Interface Process (PIP).</span></span> <span data-ttu-id="783b8-105">執行這個動作後，您必須修改該範本，使其格式正確，才可新增您的資料。</span><span class="sxs-lookup"><span data-stu-id="783b8-105">After doing this, you have to modify that template, so that it is well formed, before adding your data.</span></span>  
  
### <a name="to-generate-a-message-instance-template-from-the-pip"></a><span data-ttu-id="783b8-106">從 PIP 產生格式正確的訊息執行個體</span><span class="sxs-lookup"><span data-stu-id="783b8-106">To generate a message instance template from the PIP</span></span>  
  
1.  <span data-ttu-id="783b8-107">啟動**Microsoft Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="783b8-107">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="783b8-108">在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="783b8-108">On the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="783b8-109">找出\<*磁碟機*> \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNetSDK\Schemas，按一下**RNPIPs.btproj**，然後按一下  **開啟**。</span><span class="sxs-lookup"><span data-stu-id="783b8-109">Locate \<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNetSDK\Schemas, click **RNPIPs.btproj**, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="783b8-110">在 [方案總管] 中，展開**Rnpip**，然後以滑鼠右鍵按一下您要建立執行個體的 PIP。</span><span class="sxs-lookup"><span data-stu-id="783b8-110">In Solution Explorer, expand **RNPIPs**, and then right-click the PIP for which you want to create an instance.</span></span>  
  
5.  <span data-ttu-id="783b8-111">按一下**產生執行個體**。</span><span class="sxs-lookup"><span data-stu-id="783b8-111">Click **Generate Instance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="783b8-112">這會產生一個以該 PIP 命名的檔案，該檔案名稱後附加上「_output」，且其副檔名為 .xml。</span><span class="sxs-lookup"><span data-stu-id="783b8-112">This generates a file named after the PIP, with "_output" appended to the file name, and with an .xml extension.</span></span> <span data-ttu-id="783b8-113">[輸出] 窗格中的一行陳述式會指出 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 產生執行個體的地方。</span><span class="sxs-lookup"><span data-stu-id="783b8-113">A statement in the Output pane indicates where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] generated the instance.</span></span>  
  
### <a name="to-modify-the-message-instance-template"></a><span data-ttu-id="783b8-114">修改訊息執行個體範本</span><span class="sxs-lookup"><span data-stu-id="783b8-114">To modify the message instance template</span></span>  
  
1.  <span data-ttu-id="783b8-115">在 [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer 中，找出包含 XML 檔案的資料夾，並按兩下檔案名稱開啟資料夾。</span><span class="sxs-lookup"><span data-stu-id="783b8-115">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, locate the folder holding the XML file, and double-click the file name to open the folder.</span></span>  
  
2.  <span data-ttu-id="783b8-116">在指出 XML 版本和編碼的所有其他文字之前加入 XML 標頭標記。</span><span class="sxs-lookup"><span data-stu-id="783b8-116">Add an XML header tag before all other text indicating the version of XML and the encoding.</span></span> <span data-ttu-id="783b8-117">例如：</span><span class="sxs-lookup"><span data-stu-id="783b8-117">For example:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" ?>  
    ```  
  
3.  <span data-ttu-id="783b8-118">在您剛才加入的程式碼行之後，加入指出 DTD 的 DOCTYPE 行。</span><span class="sxs-lookup"><span data-stu-id="783b8-118">After the line that you just added, add a DOCTYPE line indicating the DTD.</span></span> <span data-ttu-id="783b8-119">例如，對於 3A4 Purchase Order Request 執行個體，該行應如下所示：</span><span class="sxs-lookup"><span data-stu-id="783b8-119">For example, for a 3A4 Purchase Order Request instance, the line would be as follows:</span></span>  
  
    ```  
    <!DOCTYPE Pip3A4PurchaseOrderRequest SYSTEM "3A4_MS_V02_02_PurchaseOrderRequest.dtd">  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="783b8-120">每個訊息執行個體都應包含要處理的 DOCTYPE 行。</span><span class="sxs-lookup"><span data-stu-id="783b8-120">Each message instance must include the DOCTYPE line to be processed.</span></span>  
  
4.  <span data-ttu-id="783b8-121">您現在可以自訂此訊息，以符合您的商務需求。</span><span class="sxs-lookup"><span data-stu-id="783b8-121">You may now customize this message instance to suit your business needs.</span></span> <span data-ttu-id="783b8-122">請修改 XML 執行個體，使它不使用 XML 命名空間或命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="783b8-122">Modify the XML instance so that it does not use XML namespaces or namespace prefixes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="783b8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="783b8-123">See Also</span></span>  
 [<span data-ttu-id="783b8-124">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="783b8-124">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)