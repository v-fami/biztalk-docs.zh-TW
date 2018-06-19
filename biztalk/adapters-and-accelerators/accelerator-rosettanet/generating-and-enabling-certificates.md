---
title: 產生並啟用憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, enabling
- private process tutorial, creating certificates
- private process tutorial, enabling certificates
ms.assetid: a36d9725-d57c-499d-948d-558096709d67
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93293939ae509dcb2af04e17fcdd35e9cf6d03cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209782"
---
# <a name="generating-and-enabling-certificates"></a><span data-ttu-id="4f150-102">產生並啟用憑證</span><span class="sxs-lookup"><span data-stu-id="4f150-102">Generating and Enabling Certificates</span></span>
<span data-ttu-id="4f150-103">這個教學課程使用憑證來簽署及加密 Contoso 和 Fabrikam 組織傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="4f150-103">This tutorial uses certificates to sign and encrypt messages sent by the Contoso and Fabrikam organizations.</span></span> <span data-ttu-id="4f150-104">如果您已經完成 「 雙向動作教學課程，您可能會略過此步驟，並移至[建立 Contoso 解決方案](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="4f150-104">If you have already completed the Double Action Tutorial, you may skip this step and move on to [Creating the Contoso Solution](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-solution.md).</span></span> <span data-ttu-id="4f150-105">若要產生並使用本教學課程所述的憑證，請依照下列主題中的程序進行：</span><span class="sxs-lookup"><span data-stu-id="4f150-105">To generate and use certificates for this tutorial, follow the procedures in the following topics:</span></span>  
  
-   [<span data-ttu-id="4f150-106">步驟 1： 建立憑證授權單位</span><span class="sxs-lookup"><span data-stu-id="4f150-106">Step 1: Creating a Certification Authority</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)  
  
-   [<span data-ttu-id="4f150-107">步驟 2： 建立公開憑證與私用憑證</span><span class="sxs-lookup"><span data-stu-id="4f150-107">Step 2: Creating Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)  
  
-   [<span data-ttu-id="4f150-108">步驟 3： 匯入公開憑證與私用憑證</span><span class="sxs-lookup"><span data-stu-id="4f150-108">Step 3: Importing Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)  
  
-   [<span data-ttu-id="4f150-109">步驟 4： 啟用安全通訊端在 IIS 中的圖層</span><span class="sxs-lookup"><span data-stu-id="4f150-109">Step 4: Enabling Secure Sockets Layer in IIS</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)  
  
> [!IMPORTANT]
>  <span data-ttu-id="4f150-110">這些都是「雙向動作」教學課程中的步驟。</span><span class="sxs-lookup"><span data-stu-id="4f150-110">These steps are in the Double Action Tutorial.</span></span> <span data-ttu-id="4f150-111">當您完成上述每個步驟之後，請返回本主題繼續進行「私用程序」教學課程。</span><span class="sxs-lookup"><span data-stu-id="4f150-111">After completing each step, return to this topic to continue the Private Process Tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f150-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f150-112">See Also</span></span>  
 [<span data-ttu-id="4f150-113">建立 Contoso 解決方案</span><span class="sxs-lookup"><span data-stu-id="4f150-113">Creating the Contoso Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-solution.md)