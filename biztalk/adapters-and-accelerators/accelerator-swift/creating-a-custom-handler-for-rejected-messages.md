---
title: "建立的自訂處理常式已拒絕訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom handlers
- Message Repair and New Submission, rejected messages
- Message Repair and New Submission, custom handlers
ms.assetid: 28d74504-6c62-427a-b75d-456fbe43ec3a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baa02ad0fcb0236ec879e43b44a891fcdf591beb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-custom-handler-for-rejected-messages"></a><span data-ttu-id="3e07a-102">拒絕的訊息建立自訂的處理常式</span><span class="sxs-lookup"><span data-stu-id="3e07a-102">Creating a Custom Handler for Rejected Messages</span></span>
<span data-ttu-id="3e07a-103">如果您拒絕訊息中的驗證或認可階段，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]將訊息傳回至第一個階段中定義的工作流程 （在此情況下是一律修復，即使建立工作流程中的第一個階段）。</span><span class="sxs-lookup"><span data-stu-id="3e07a-103">If you reject a message in the verification or approval stage, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] returns the message to the first stage defined for the workflow (which in this case is always repair, even if Create is the first stage in the workflow).</span></span> <span data-ttu-id="3e07a-104">不過，如果工作流程的第一個階段拒絕訊息時，修復協調流程將訊息發佈到 MessageBox 與升級屬性指出 MrsrRepair 協調流程會拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="3e07a-104">However, if the first stage of the workflow rejects the message, the repair orchestration publishes the message to the MessageBox with promoted properties indicating that the MrsrRepair orchestration rejected the message.</span></span> <span data-ttu-id="3e07a-105">若要處理這些訊息，您可以建立自訂處理常式 （協調流程），訂閱這些升級的屬性，並處理所需的訊息。</span><span class="sxs-lookup"><span data-stu-id="3e07a-105">To handle these messages, you can create a custom handler (orchestration) that subscribes to these promoted properties and processes the messages as required.</span></span>  
  
 <span data-ttu-id="3e07a-106">訊息無法 MrsrRepair 協調流程中可能有多種原因。</span><span class="sxs-lookup"><span data-stu-id="3e07a-106">A message can fail in the MrsrRepair orchestration for multiple reasons.</span></span> <span data-ttu-id="3e07a-107">載入時，協調流程將在下表中的屬性升級，並指派這些屬性的值，或其中一個值，資料表的權限的資料行所示。</span><span class="sxs-lookup"><span data-stu-id="3e07a-107">When it does, the orchestration promotes the properties in the following table, and assigns these properties the value, or one of the values, shown in the right column of the table.</span></span>  
  
|<span data-ttu-id="3e07a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3e07a-108">Property</span></span>|<span data-ttu-id="3e07a-109">值</span><span class="sxs-lookup"><span data-stu-id="3e07a-109">Values</span></span>|  
|--------------|------------|  
|<span data-ttu-id="3e07a-110">BTS。作業</span><span class="sxs-lookup"><span data-stu-id="3e07a-110">BTS.Operation</span></span>|<span data-ttu-id="3e07a-111">A4SWIFT_MRSRFailed</span><span class="sxs-lookup"><span data-stu-id="3e07a-111">A4SWIFT_MRSRFailed</span></span>|  
|<span data-ttu-id="3e07a-112">A4SWIFT_MRSRFailedReason</span><span class="sxs-lookup"><span data-stu-id="3e07a-112">A4SWIFT_MRSRFailedReason</span></span>|<span data-ttu-id="3e07a-113">逾時</span><span class="sxs-lookup"><span data-stu-id="3e07a-113">Timeout</span></span><br /><br /> <span data-ttu-id="3e07a-114">已拒絕 （表示訊息已遭拒絕的第一階段）</span><span class="sxs-lookup"><span data-stu-id="3e07a-114">Rejected (means the message has been rejected from the first stage)</span></span><br /><br /> <span data-ttu-id="3e07a-115">CantRepairInInfoPath</span><span class="sxs-lookup"><span data-stu-id="3e07a-115">CantRepairInInfoPath</span></span>|  
|<span data-ttu-id="3e07a-116">A4SWIFT_MRSRLastStage</span><span class="sxs-lookup"><span data-stu-id="3e07a-116">A4SWIFT_MRSRLastStage</span></span>|<span data-ttu-id="3e07a-117">\<訊息是在失敗之前的最後一個階段 （角色） 的名稱\></span><span class="sxs-lookup"><span data-stu-id="3e07a-117">\<name of last stage (role) that the message was in before failing\></span></span>|  
|<span data-ttu-id="3e07a-118">A4SWIFT_MRSRDepartment</span><span class="sxs-lookup"><span data-stu-id="3e07a-118">A4SWIFT_MRSRDepartment</span></span>|<span data-ttu-id="3e07a-119">\<部門的名稱\></span><span class="sxs-lookup"><span data-stu-id="3e07a-119">\<name of department\></span></span>|