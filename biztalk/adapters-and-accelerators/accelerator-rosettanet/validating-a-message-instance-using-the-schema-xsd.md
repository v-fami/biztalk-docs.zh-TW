---
title: 驗證訊息執行個體使用的結構描述 XSD |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schema XSD
- validating, messages
- messages, validating
- schemas, XSDs
ms.assetid: c4cbf6b4-130d-4e0f-840b-c8008fafac0b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eda0b76b3daff53290264169c5b2effe80a9e5c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963964"
---
# <a name="validating-a-message-instance-using-the-schema-xsd"></a><span data-ttu-id="f22b4-102">驗證訊息執行個體使用的結構描述 XSD</span><span class="sxs-lookup"><span data-stu-id="f22b4-102">Validating a Message Instance Using the Schema XSD</span></span>
<span data-ttu-id="f22b4-103">本主題描述如何使用 Microsoft?[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 已建置到 RNPIP 組件檔案的其中一個結構描述 XSD 檔案來驗證訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="f22b4-103">This topic describes how to validate a message instance using one of the schema XSD files that Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] has built into the RNPIPs assembly file.</span></span>  
  
### <a name="to-validate-a-message-instance-using-the-schema-xsd"></a><span data-ttu-id="f22b4-104">若要使用結構描述 XSD 驗證訊息執行個體</span><span class="sxs-lookup"><span data-stu-id="f22b4-104">To validate a message instance using the schema XSD</span></span>  
  
1.  <span data-ttu-id="f22b4-105">啟動**Microsoft Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="f22b4-105">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="f22b4-106">在**檔案**，指向 **開啟**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="f22b4-106">On the **File**, point to **Open**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="f22b4-107">找出*\<磁碟機\>* \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\schemas 中，按一下**RNPIPs.btproj**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="f22b4-107">Locate *\<drive\>* \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas, click **RNPIPs.btproj**, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="f22b4-108">在 方案總管 中，展開**Rnpip**，以滑鼠右鍵按一下結構描述 XSD，您要用來驗證訊息執行個體，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="f22b4-108">In Solution Explorer, expand **RNPIPs**, right-click the schema XSD that you want to use to validate a message instance, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="f22b4-109">在 [屬性頁] 對話方塊中，按一下**輸入執行個體檔案名稱**，找出包含檔案的資料夾、 選取訊息執行個體 XML 檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="f22b4-109">In the Property Pages dialog box, click **Input Instance Filename**, locate the folder that contains the file, select the message instance XML file, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="f22b4-110">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f22b4-110">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="f22b4-111">在 方案總管 中，以滑鼠右鍵按一下結構描述 XSD，您要用來驗證訊息執行個體，然後按一下 **驗證執行個體**。</span><span class="sxs-lookup"><span data-stu-id="f22b4-111">In Solution Explorer, right-click the schema XSD that you want to use to validate a message instance, and then click **Validate Instance**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f22b4-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="f22b4-112">See Also</span></span>  
 <span data-ttu-id="f22b4-113">[修改 Rnpip 中的現有 PIP](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md) </span><span class="sxs-lookup"><span data-stu-id="f22b4-113">[Modifying an Existing PIP in RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md) </span></span>  
 [<span data-ttu-id="f22b4-114">使用 PIP</span><span class="sxs-lookup"><span data-stu-id="f22b4-114">Working with PIPs</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)