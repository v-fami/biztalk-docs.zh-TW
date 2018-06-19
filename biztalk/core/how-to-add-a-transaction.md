---
title: 如何將異動加入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding, transactions
- transactions, adding
ms.assetid: 25385c20-3025-4cf1-bc1f-ef266e081bad
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24c67a9c76ae87f2355bb0ea4638d3bd156cda6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246814"
---
# <a name="how-to-add-a-transaction"></a><span data-ttu-id="c9f2f-102">如何新增交易</span><span class="sxs-lookup"><span data-stu-id="c9f2f-102">How to Add a Transaction</span></span>
<span data-ttu-id="c9f2f-103">請依照下列步驟來新增交易。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-103">Follow these steps to add a transaction.</span></span>  
  
### <a name="to-add-a-transaction"></a><span data-ttu-id="c9f2f-104">新增交易</span><span class="sxs-lookup"><span data-stu-id="c9f2f-104">To add a transaction</span></span>  
  
1.  <span data-ttu-id="c9f2f-105">按一下**交易** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-105">Click the **Transactions** tab.</span></span>  
  
2.  <span data-ttu-id="c9f2f-106">按一下**加入異動**。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-106">Click **Add Transaction**.</span></span>  
  
3.  <span data-ttu-id="c9f2f-107">按一下**新增值**。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-107">Click **Add a New Value**.</span></span> <span data-ttu-id="c9f2f-108">輸入下列資訊，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-108">Enter the following information, and then click **Add**.</span></span>  
  
    1.  <span data-ttu-id="c9f2f-109">**節點名稱：** 確認這是**MSEXTERNAL**。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-109">**Node Name:** Verify that this is **MSEXTERNAL**.</span></span>  
  
    2.  <span data-ttu-id="c9f2f-110">**交易類型：** 確認這是**Outbound Asynchronous**。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-110">**Transaction Type:** Verify that this is **Outbound Asynchronous**.</span></span>  
  
    3.  <span data-ttu-id="c9f2f-111">**要求訊息：** 輸入`LOCATION_SYNC`。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-111">**Request Message:** Enter `LOCATION_SYNC`.</span></span>  
  
    4.  <span data-ttu-id="c9f2f-112">**要求訊息版本：** 輸入`VERSION_1`。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-112">**Request Message Version:** Enter `VERSION_1`.</span></span>  
  
     ![](../core/media/psadapter-38-task-gatewayaddtransaction.gif "PSAdapter_38_Task_GatewayAddTransaction")  
  
4.  <span data-ttu-id="c9f2f-113">在**交易詳細資料**索引標籤上，確認下列設定：</span><span class="sxs-lookup"><span data-stu-id="c9f2f-113">On the **Transaction Detail** tab, verify the following settings:</span></span>  
  
    1.  <span data-ttu-id="c9f2f-114">**狀態：** 作用中。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-114">**Status:** Active.</span></span>  
  
    2.  <span data-ttu-id="c9f2f-115">**路由：** 隱含。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-115">**Routing:** Implicit.</span></span>  
  
     ![](../core/media/psadapter-39-task-gatewaytransdetail.gif "PSAdapter_39_Task_GatewayTransDetail")  
  
5.  <span data-ttu-id="c9f2f-116">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-116">Click **Save**.</span></span>  
  
6.  <span data-ttu-id="c9f2f-117">按一下**回到交易清單**連結。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-117">Click the **Return to Transaction List** link.</span></span>  
  
     <span data-ttu-id="c9f2f-118">這筆交易會顯示在交易清單中。</span><span class="sxs-lookup"><span data-stu-id="c9f2f-118">The transaction appears in the list of transactions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f2f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9f2f-119">See Also</span></span>  
 [<span data-ttu-id="c9f2f-120">建立 PeopleSoft HTTP 主控件和連接埠</span><span class="sxs-lookup"><span data-stu-id="c9f2f-120">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)