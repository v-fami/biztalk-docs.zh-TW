---
title: 步驟 3： 編輯交易夥伴介面程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying, PIPs
- PIPs, modifying
- loopback tutorial, modifying PIPs
ms.assetid: 4d03c598-8ed4-4135-9748-ede101997fd0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b6300c12e7bc28de0dc81af9eae23699338ed3d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965068"
---
# <a name="step-3-edit-the-partner-interface-process"></a><span data-ttu-id="2e89a-102">步驟 3： 編輯交易夥伴介面程序</span><span class="sxs-lookup"><span data-stu-id="2e89a-102">Step 3: Edit the Partner Interface Process</span></span>
<span data-ttu-id="2e89a-103">在此步驟中，如果您未在 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Internet Information Services (IIS) 中設定安全通訊端層 (SSL) 憑證，您必須編輯夥伴介面程序 (PIP) 組態設定以停用安全傳輸。</span><span class="sxs-lookup"><span data-stu-id="2e89a-103">In this step, you edit the Partner Interface Process (PIP) configuration settings to disable secure transport if you do not have a Secure Sockets Layer (SSL) certificate configured in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Internet Information Services (IIS).</span></span> <span data-ttu-id="2e89a-104">由於回送實例不支援簽章內送訊息和外寄訊息，您必須變更預設設定才能繼續進行教學課程。</span><span class="sxs-lookup"><span data-stu-id="2e89a-104">Because the loopback scenario does not support signing for both incoming and outgoing messages, you must change the default settings to continue with the tutorial.</span></span> <span data-ttu-id="2e89a-105">您將修改 STD_0C1_R01.02 PIP。</span><span class="sxs-lookup"><span data-stu-id="2e89a-105">You modify the STD_0C1_R01.02 PIP.</span></span>  
  
### <a name="to-edit-the-std0c1r0102-pip"></a><span data-ttu-id="2e89a-106">若要編輯 STD_0C1_R01.02 PIP</span><span class="sxs-lookup"><span data-stu-id="2e89a-106">To edit the STD_0C1_R01.02 PIP</span></span>  
  
1.  <span data-ttu-id="2e89a-107">在 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開 **BizTalk\<版本\>Accelerator for RosettaNet**，按一下 **程序組態設定**，以滑鼠右鍵按一下**STD_0C1_R01.02**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="2e89a-107">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand **BizTalk \<version\> Accelerator for RosettaNet**, click **Process Configuration Settings**, right-click **STD_0C1_R01.02**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2e89a-108">在 [STD_0C1_R01.02Properties] 對話方塊上**活動**索引標籤上，設定**需要安全性傳輸**選項設定為`False`。</span><span class="sxs-lookup"><span data-stu-id="2e89a-108">In the STD_0C1_R01.02Properties dialog box, on the **Activity** tab, set the **Is Secure Transport Required** option to `False`.</span></span> <span data-ttu-id="2e89a-109">請只在 IIS Web 伺服器沒有 SSL 憑證的情況下，才執行這個步驟。</span><span class="sxs-lookup"><span data-stu-id="2e89a-109">Perform this step only if you do not have a SSL certificate on your IIS Web server.</span></span>  
  
3.  <span data-ttu-id="2e89a-110">設定**不可否認性所需**至`False`，將**需要授權**至`False`，將**來源與內容的不可否認**至`False`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="2e89a-110">Set the **Non-Repudiation Required** to `False`, set **Is Authorization Required** to `False`, set **Non-Repudiation of Origin and Content** to `False`, and then click **OK**.</span></span>  
  
     <span data-ttu-id="2e89a-111">這會停用不可否認性並禁止在簽章訊息中使用憑證。</span><span class="sxs-lookup"><span data-stu-id="2e89a-111">This disables non-repudiation and the use of certificates for signing messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e89a-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="2e89a-112">See Also</span></span>  
 <span data-ttu-id="2e89a-113">[步驟 4： 建立交易協議](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md) </span><span class="sxs-lookup"><span data-stu-id="2e89a-113">[Step 4: Create a Trade Agreement](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md) </span></span>  
 [<span data-ttu-id="2e89a-114">授權與不可否認性屬性</span><span class="sxs-lookup"><span data-stu-id="2e89a-114">Authorization and Non-Repudiation Properties</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)