---
title: 設定使用 WCF LOB 配接器 SDK 的不可部分完成、 一致、 隔離及持久交易 |Microsoft Docs
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
ms.openlocfilehash: 37b39ec0e240a2d4ee9ba1239cf27d7b118ca0ad
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007703"
---
# <a name="configure-atomic-consistent-isolated-and-durable-transactions-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="4a2a1-102">設定使用 WCF LOB 配接器 SDK 的不可部分完成、 一致、 隔離及持久交易</span><span class="sxs-lookup"><span data-stu-id="4a2a1-102">Configure atomic, consistent, isolated, and durable transactions using the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="4a2a1-103">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]信賴憑證者所公開的功能，支援交易[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4a2a1-103">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] supports transactions by relying on functionality exposed by the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span></span> <span data-ttu-id="4a2a1-104">使用所公開的 API [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，您的配接器可以支援交易和作業：</span><span class="sxs-lookup"><span data-stu-id="4a2a1-104">By using the API exposed by [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], your adapter can support transactions and operations that are:</span></span>  
  
- <span data-ttu-id="4a2a1-105">**不可部分完成**，確保，所有暫止的更新會認可或沒有任何已認可和回復為先前的狀態。</span><span class="sxs-lookup"><span data-stu-id="4a2a1-105">**Atomic**, ensuring that either all pending updates are committed or none are committed and are rolled back to their previous state.</span></span>  
  
- <span data-ttu-id="4a2a1-106">**一致**，確保所做的變更從某個一致狀態到另一個。</span><span class="sxs-lookup"><span data-stu-id="4a2a1-106">**Consistent**, ensuring that changes made are from one consistent state to another.</span></span>  
  
- <span data-ttu-id="4a2a1-107">**隔離**，導致無法存取在其他未認可的變更暫止交易的交易。</span><span class="sxs-lookup"><span data-stu-id="4a2a1-107">**Isolated**, preventing a transaction to access uncommitted changes in other pending transactions.</span></span>  
  
- <span data-ttu-id="4a2a1-108">**永久性**，這表示經過認可之後，更新將會持續面對失敗。</span><span class="sxs-lookup"><span data-stu-id="4a2a1-108">**Durable**, meaning that once committed, updates will be persistent in the face of failures.</span></span>  
  
  <span data-ttu-id="4a2a1-109">配接器開發人員為目標的關聯式資料庫系統或其他特定業務系統的支援 （或預期） 的交易必須找出目標系統支援的方式，並公開 （expose） 的交易支援，並再找出適當[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]若要使用的交易模型。</span><span class="sxs-lookup"><span data-stu-id="4a2a1-109">Adapter developers targeting relational database systems or other line-of-business systems that support (or expect) transactions will need to identify how the target system supports and exposes transaction support and then identify an appropriate [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] transaction model to use.</span></span>  
  
  <span data-ttu-id="4a2a1-110">如需詳細資訊[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]交易，請參閱[Windows Communication Foundation 異動概觀](https://msdn.microsoft.com/library/ms733904.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4a2a1-110">For more information about [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] transactions, see [Windows Communication Foundation Transactions Overview](https://msdn.microsoft.com/library/ms733904.aspx).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="4a2a1-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a2a1-111">See Also</span></span>  
 [<span data-ttu-id="4a2a1-112">規劃和設計您的配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="4a2a1-112">Plan and Design your Adapter using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk.md)