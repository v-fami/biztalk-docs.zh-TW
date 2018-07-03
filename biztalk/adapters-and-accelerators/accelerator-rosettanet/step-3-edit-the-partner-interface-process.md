---
title: 步驟 3： 編輯交易夥伴介面程序 |Microsoft Docs
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
ms.openlocfilehash: a3b5b6d2f6b0fcbf13ab521bc318eda54ece55f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003607"
---
# <a name="step-3-edit-the-partner-interface-process"></a><span data-ttu-id="dc6b4-102">步驟 3： 編輯交易夥伴介面程序</span><span class="sxs-lookup"><span data-stu-id="dc6b4-102">Step 3: Edit the Partner Interface Process</span></span>
<span data-ttu-id="dc6b4-103">在此步驟中，您可以編輯交易夥伴介面程序 (PIP) 組態設定來停用安全傳輸，如果您沒有在 Microsoft® 網際網路資訊服務 (IIS) 中設定安全通訊端層 (SSL) 憑證。</span><span class="sxs-lookup"><span data-stu-id="dc6b4-103">In this step, you edit the Partner Interface Process (PIP) configuration settings to disable secure transport if you do not have a Secure Sockets Layer (SSL) certificate configured in Microsoft® Internet Information Services (IIS).</span></span> <span data-ttu-id="dc6b4-104">由於回送實例不支援簽章內送訊息和外寄訊息，您必須變更預設設定才能繼續進行教學課程。</span><span class="sxs-lookup"><span data-stu-id="dc6b4-104">Because the loopback scenario does not support signing for both incoming and outgoing messages, you must change the default settings to continue with the tutorial.</span></span> <span data-ttu-id="dc6b4-105">您將修改 STD_0C1_R01.02 PIP。</span><span class="sxs-lookup"><span data-stu-id="dc6b4-105">You modify the STD_0C1_R01.02 PIP.</span></span>  
  
### <a name="to-edit-the-std0c1r0102-pip"></a><span data-ttu-id="dc6b4-106">若要編輯 STD_0C1_R01.02 PIP</span><span class="sxs-lookup"><span data-stu-id="dc6b4-106">To edit the STD_0C1_R01.02 PIP</span></span>  
  
1. <span data-ttu-id="dc6b4-107">在  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** 管理主控台中，展開**BizTalk\<版本\>Accelerator for RosettaNet**，按一下 **程序組態設定**，以滑鼠右鍵按一下**STD_0C1_R01.02**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="dc6b4-107">In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand **BizTalk \<version\> Accelerator for RosettaNet**, click **Process Configuration Settings**, right-click **STD_0C1_R01.02**, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="dc6b4-108">在 STD_0C1_R01.02Properties 對話方塊中，在**活動**索引標籤上，設定**需要安全傳輸**選項設定為`False`。</span><span class="sxs-lookup"><span data-stu-id="dc6b4-108">In the STD_0C1_R01.02Properties dialog box, on the **Activity** tab, set the **Is Secure Transport Required** option to `False`.</span></span> <span data-ttu-id="dc6b4-109">請只在 IIS Web 伺服器沒有 SSL 憑證的情況下，才執行這個步驟。</span><span class="sxs-lookup"><span data-stu-id="dc6b4-109">Perform this step only if you do not have a SSL certificate on your IIS Web server.</span></span>  
  
3. <span data-ttu-id="dc6b4-110">設定**不可否認性所需**要`False`，將**需要授權**來`False`，將**來源與內容的不可否認**到`False`，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="dc6b4-110">Set the **Non-Repudiation Required** to `False`, set **Is Authorization Required** to `False`, set **Non-Repudiation of Origin and Content** to `False`, and then click **OK**.</span></span>  
  
    <span data-ttu-id="dc6b4-111">這會停用不可否認性並禁止在簽章訊息中使用憑證。</span><span class="sxs-lookup"><span data-stu-id="dc6b4-111">This disables non-repudiation and the use of certificates for signing messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc6b4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc6b4-112">See Also</span></span>  
 <span data-ttu-id="dc6b4-113">[步驟 4： 建立交易協議](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md) </span><span class="sxs-lookup"><span data-stu-id="dc6b4-113">[Step 4: Create a Trade Agreement](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md) </span></span>  
 [<span data-ttu-id="dc6b4-114">授權與不可否認性屬性</span><span class="sxs-lookup"><span data-stu-id="dc6b4-114">Authorization and Non-Repudiation Properties</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)