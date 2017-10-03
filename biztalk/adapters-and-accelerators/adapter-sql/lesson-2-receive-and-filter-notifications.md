---
title: "第 2 課： 接收和篩選器通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5ec679c-1c67-4bf4-aa88-0787373343f5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f28d0479510078b3717d68f99976808ee19aa7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-receive-and-filter-notifications"></a><span data-ttu-id="b5c17-102">第 2 課： 接收和篩選器通知</span><span class="sxs-lookup"><span data-stu-id="b5c17-102">Lesson 2: Receive and Filter Notifications</span></span>
<span data-ttu-id="b5c17-103">在這一課中，在您開始建立協調流程接收的變更通知**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="b5c17-103">In this lesson, you start creating an orchestration that receives notifications for changes to the **Employee** table.</span></span> <span data-ttu-id="b5c17-104">協調流程收到通知之後，它會擷取的通知和通知類型是否為插入作業中，在類型**員工**資料表，將"if"條件用來執行後續的工作。</span><span class="sxs-lookup"><span data-stu-id="b5c17-104">After the orchestration receives the notification, it extracts the type of notification and if the notification type is for an Insert operation on the **Employee** table, an “if” condition is used to perform subsequent tasks.</span></span> <span data-ttu-id="b5c17-105">在這一課，您將會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="b5c17-105">In this lesson, you will perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="b5c17-106">新增單向接收埠和**接收**圖形至協調流程接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="b5c17-106">Add a one-way receive port and a **Receive** shape to the orchestration to receive the notification message.</span></span>  
  
2.  <span data-ttu-id="b5c17-107">新增**運算式**圖形，其中包含 xpath 查詢來擷取通知類型。</span><span class="sxs-lookup"><span data-stu-id="b5c17-107">Add an **Expression** shape that contains an xpath query to extract the type of notification.</span></span>  
  
3.  <span data-ttu-id="b5c17-108">已知的通知類型之後，將篩選加入協調流程藉由**決定**圖形。</span><span class="sxs-lookup"><span data-stu-id="b5c17-108">After the notification type is known, add a filter to the orchestration by including a **Decide** shape.</span></span> <span data-ttu-id="b5c17-109">此圖形會決定是否通知用於插入通知，並接著執行後續的作業。</span><span class="sxs-lookup"><span data-stu-id="b5c17-109">This shape decides whether the notification is for an Insert notification and then performs subsequent operations.</span></span> <span data-ttu-id="b5c17-110">如果通知不是插入作業，協調流程不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="b5c17-110">If the notification is not for an Insert operation, the orchestration does not do anything.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5c17-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="b5c17-111">In This Section</span></span>  
  
-   [<span data-ttu-id="b5c17-112">步驟 1： 加入以接收通知的協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="b5c17-112">Step 1: Add Orchestration Shapes to Receive Notification</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)  
  
-   [<span data-ttu-id="b5c17-113">步驟 2： 擷取通知訊息的通知類型</span><span class="sxs-lookup"><span data-stu-id="b5c17-113">Step 2: Extract Notification Type from Notification Message</span></span>](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)  
  
-   [<span data-ttu-id="b5c17-114">步驟 3： 將篩選加入 Insert 通知</span><span class="sxs-lookup"><span data-stu-id="b5c17-114">Step 3: Add a Filter for Insert Notifications</span></span>](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md)