---
title: 設定不可部分完成、 一致、 隔離且持久的交易使用 WCF LOB 配接器 SDK |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c20d2613-c77d-4b0d-b2e2-3ed28a8fb36c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58cf80a70b04e20aeb25b27210d88dfd861d7539
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224238"
---
# <a name="configure-atomic-consistent-isolated-and-durable-transactions-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="b3d69-102">設定不可部分完成、 一致、 隔離且持久的交易使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="b3d69-102">Configure atomic, consistent, isolated, and durable transactions using the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="b3d69-103">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]上所公開的功能來支援交易[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3d69-103">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] supports transactions by relying on functionality exposed by the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span></span> <span data-ttu-id="b3d69-104">使用 API 所公開[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，您的配接器可以支援交易與作業：</span><span class="sxs-lookup"><span data-stu-id="b3d69-104">By using the API exposed by [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], your adapter can support transactions and operations that are:</span></span>  
  
-   <span data-ttu-id="b3d69-105">**不可部分完成**，確保，所有暫止的更新會認可或沒有任何已認可，且會回復至先前的狀態。</span><span class="sxs-lookup"><span data-stu-id="b3d69-105">**Atomic**, ensuring that either all pending updates are committed or none are committed and are rolled back to their previous state.</span></span>  
  
-   <span data-ttu-id="b3d69-106">**一致**，確保所做的變更從某個一致狀態到另一個。</span><span class="sxs-lookup"><span data-stu-id="b3d69-106">**Consistent**, ensuring that changes made are from one consistent state to another.</span></span>  
  
-   <span data-ttu-id="b3d69-107">**隔離**，導致無法存取在其他未認可的變更暫止的交易會在交易。</span><span class="sxs-lookup"><span data-stu-id="b3d69-107">**Isolated**, preventing a transaction to access uncommitted changes in other pending transactions.</span></span>  
  
-   <span data-ttu-id="b3d69-108">**永久性**，這表示經過認可之後，更新仍會持續遇到失敗時。</span><span class="sxs-lookup"><span data-stu-id="b3d69-108">**Durable**, meaning that once committed, updates will be persistent in the face of failures.</span></span>  
  
 <span data-ttu-id="b3d69-109">配接器開發人員為目標的關聯式資料庫系統或其他支援 （或預期） 交易的特定業務系統必須識別目標系統支援的方式，並會公開交易支援，然後找出適當的[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]要使用的交易模式。</span><span class="sxs-lookup"><span data-stu-id="b3d69-109">Adapter developers targeting relational database systems or other line-of-business systems that support (or expect) transactions will need to identify how the target system supports and exposes transaction support and then identify an appropriate [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] transaction model to use.</span></span>  
  
 <span data-ttu-id="b3d69-110">如需有關[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]交易，請參閱[Windows Communication Foundation 交易概觀](https://msdn.microsoft.com/library/ms733904.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b3d69-110">For more information about [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] transactions, see [Windows Communication Foundation Transactions Overview](https://msdn.microsoft.com/library/ms733904.aspx).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="b3d69-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3d69-111">See Also</span></span>  
 [<span data-ttu-id="b3d69-112">計劃和設計您的配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="b3d69-112">Plan and Design your Adapter using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk.md)