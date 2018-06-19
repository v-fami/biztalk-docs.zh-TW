---
title: 如何設定補償圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Compensate shape [Orchestration Designer], about Compensate shape
- Compensate shape [Orchestration Designer]
- compensations, Compensate shape [Orchestration Designer]
- configuring [Orchestration Designer], Compensate shape
- Compensate shape [Orchestration Designer], configuring
ms.assetid: 9f06289e-4d11-4864-9851-c210276865a7
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 059ac58d95d33234737033c00c4a6a2a36e256f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248278"
---
# <a name="how-to-configure-the-compensate-shape"></a><span data-ttu-id="a8951-102">如何設定補償圖形</span><span class="sxs-lookup"><span data-stu-id="a8951-102">How to Configure the Compensate Shape</span></span>
<span data-ttu-id="a8951-103">如果您在協調流程中使用巢狀的交易，您可以加入**補償**補償區塊或例外狀況區塊的交易範圍中的圖形。</span><span class="sxs-lookup"><span data-stu-id="a8951-103">If you are using nested transactions in your orchestration, you can add a **Compensate** shape in the compensation block or an exception block of a transaction scope.</span></span> <span data-ttu-id="a8951-104">如此可讓您的協調流程能明確地在巢狀交易執行補償。</span><span class="sxs-lookup"><span data-stu-id="a8951-104">This enables your orchestration to explicitly perform compensation on a nested transaction.</span></span> <span data-ttu-id="a8951-105">指定您想要在補償的交易**補償**形狀和巢狀交易中的任何補償程式碼將會執行，提供已成功認可交易。</span><span class="sxs-lookup"><span data-stu-id="a8951-105">You specify which transaction you would like to be compensated in the **Compensate** shape, and any compensation code in the nested transaction will be run, provided the transaction committed successfully.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8951-106">**補償**屬性指的是交易範圍的唯一識別碼，它不是指領域的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8951-106">The **Compensation** property refers to the unique identifier of the transaction scope; it does not refer to the name of the scope.</span></span>  
  
 <span data-ttu-id="a8951-107">如果您想要補償一個以上的巢狀的交易，您將另一個**補償**每一筆交易的圖形。</span><span class="sxs-lookup"><span data-stu-id="a8951-107">If you want to compensate more than one nested transaction, you add an additional **Compensate** shape for each transaction.</span></span>  
  
 <span data-ttu-id="a8951-108">否**補償**圖形時，需要有外部交易中沒有其他補償程式碼; 任何巢狀交易的補償程式碼將會自動執行。</span><span class="sxs-lookup"><span data-stu-id="a8951-108">No **Compensate** shape is necessary if there is no other compensation code in an outer transaction; the compensation code of any nested transactions will be run automatically.</span></span> <span data-ttu-id="a8951-109">**補償**圖形可讓您控制處理程序可讓您決定是否要補償巢狀的交易。</span><span class="sxs-lookup"><span data-stu-id="a8951-109">The **Compensate** shape gives you control over the process by allowing you to decide whether or not you want a nested transaction to be compensated.</span></span>  
  
### <a name="to-configure-a-compensate-shape"></a><span data-ttu-id="a8951-110">若要設定補償圖形</span><span class="sxs-lookup"><span data-stu-id="a8951-110">To configure a Compensate shape</span></span>  
  
-   <span data-ttu-id="a8951-111">在 屬性 視窗中，選取 從呼叫的補償區塊**補償**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a8951-111">In the Properties window, select the compensation block to call from the **Compensation** drop-down list.</span></span>  
  
     <span data-ttu-id="a8951-112">此下拉式清單將會顯示可以補償的所有交易，其中包括目前交易以及目前交易的任何直接子交易。</span><span class="sxs-lookup"><span data-stu-id="a8951-112">The drop-down list will display all of the transactions which can be compensated, which includes the current transaction and any immediate child transactions of the current transaction.</span></span> <span data-ttu-id="a8951-113">如果您看不到您預期的交易，可能是因為與這些交易的關係所導致。</span><span class="sxs-lookup"><span data-stu-id="a8951-113">If you cannot see a transaction that you expect, it might be due to the relationship of the transactions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8951-114">您無法從目前交易的主體內來補償目前的交易，</span><span class="sxs-lookup"><span data-stu-id="a8951-114">You cannot compensate the current transaction from within the body of the transaction.</span></span>  <span data-ttu-id="a8951-115">您可以從此交易的補償區塊或例外狀況區塊來補償它。</span><span class="sxs-lookup"><span data-stu-id="a8951-115">You can compensate it from the compensation block or an exception block of the transaction.</span></span>  
  
     <span data-ttu-id="a8951-116">如果您選擇補償目前的交易，這表示將會叫用預設處理常式，而不是明確的補償區塊 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="a8951-116">If you choose to compensate the current transaction, that means that the default handler will be invoked, and not an explicit compensation block (if there is one).</span></span> <span data-ttu-id="a8951-117">這是自動補償已成功完成之直接巢狀交易的一項機制。</span><span class="sxs-lookup"><span data-stu-id="a8951-117">This is a mechanism for automatically compensating directly nested transactions that have completed successfully.</span></span>