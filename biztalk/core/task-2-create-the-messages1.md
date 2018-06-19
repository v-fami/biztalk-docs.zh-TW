---
title: 工作 2： 建立 Messages1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df908ea0-b3be-47e6-99ba-4122cb1db561
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e326662737919e325f95d82b86aa8824e4e3a06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278846"
---
# <a name="task-2-create-the-messages"></a><span data-ttu-id="4bfe9-102">工作 2： 建立訊息</span><span class="sxs-lookup"><span data-stu-id="4bfe9-102">Task 2: Create the Messages</span></span>
<span data-ttu-id="4bfe9-103">建立下列訊息，這些訊息將在協調流程中使用。</span><span class="sxs-lookup"><span data-stu-id="4bfe9-103">Create the following Messages, they will be used in the orchestration.</span></span>  
  
### <a name="to-create-the-messages"></a><span data-ttu-id="4bfe9-104">建立訊息</span><span class="sxs-lookup"><span data-stu-id="4bfe9-104">To create the messages</span></span>  
  
1.  <span data-ttu-id="4bfe9-105">以滑鼠右鍵按一下**訊息**，然後選取**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="4bfe9-105">Right-click **Message**, and then select **New Message**.</span></span>  
  
2.  <span data-ttu-id="4bfe9-106">針對 [識別項] 和 [訊息類型] > [結構描述] 填入下列內容，並且從各訊息顯示的清單中選取類型。</span><span class="sxs-lookup"><span data-stu-id="4bfe9-106">Fill in the following for the Identifier and the Message Type>Schema and select the type from the displayed list for each message.</span></span>  
  
    |<span data-ttu-id="4bfe9-107">識別碼</span><span class="sxs-lookup"><span data-stu-id="4bfe9-107">Identifier</span></span>|<span data-ttu-id="4bfe9-108">訊息類型 > 結構描述</span><span class="sxs-lookup"><span data-stu-id="4bfe9-108">Message Type>Schema</span></span>|  
    |----------------|--------------------------|  
    |<span data-ttu-id="4bfe9-109">BeginDocMsg</span><span class="sxs-lookup"><span data-stu-id="4bfe9-109">BeginDocMsg</span></span>|<span data-ttu-id="4bfe9-110">BeginDocTest.B4200310Service_1.F4211FSBeginDoc</span><span class="sxs-lookup"><span data-stu-id="4bfe9-110">BeginDocTest.B4200310Service_1.F4211FSBeginDoc</span></span>|  
    |<span data-ttu-id="4bfe9-111">BeginDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="4bfe9-111">BeginDocResponseMsg</span></span>|<span data-ttu-id="4bfe9-112">BeginDocTest.B4200310Service_1.F4211FSBeginDocResponse</span><span class="sxs-lookup"><span data-stu-id="4bfe9-112">BeginDocTest.B4200310Service_1.F4211FSBeginDocResponse</span></span>|  
    |<span data-ttu-id="4bfe9-113">BeginDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="4bfe9-113">BeginDocSessionMsg</span></span>|<span data-ttu-id="4bfe9-114">BeginDocTest.B4200310Service_1.F4211FSBeginDoc</span><span class="sxs-lookup"><span data-stu-id="4bfe9-114">BeginDocTest.B4200310Service_1.F4211FSBeginDoc</span></span>|  
    |<span data-ttu-id="4bfe9-115">EditLineMsg</span><span class="sxs-lookup"><span data-stu-id="4bfe9-115">EditLineMsg</span></span>|<span data-ttu-id="4bfe9-116">BeginDocTest.B4200310Service_1.F4211FSEditLine</span><span class="sxs-lookup"><span data-stu-id="4bfe9-116">BeginDocTest.B4200310Service_1.F4211FSEditLine</span></span>|  
    |<span data-ttu-id="4bfe9-117">EditLineResponseMsg</span><span class="sxs-lookup"><span data-stu-id="4bfe9-117">EditLineResponseMsg</span></span>|<span data-ttu-id="4bfe9-118">BeginDocTest.B4200310Service_1.F4211FSEditLineResponse</span><span class="sxs-lookup"><span data-stu-id="4bfe9-118">BeginDocTest.B4200310Service_1.F4211FSEditLineResponse</span></span>|  
    |<span data-ttu-id="4bfe9-119">EditLineSessionMsg</span><span class="sxs-lookup"><span data-stu-id="4bfe9-119">EditLineSessionMsg</span></span>|<span data-ttu-id="4bfe9-120">BeginDocTest.B4200310Service_1.F4211FSEditLine</span><span class="sxs-lookup"><span data-stu-id="4bfe9-120">BeginDocTest.B4200310Service_1.F4211FSEditLine</span></span>|  
    |<span data-ttu-id="4bfe9-121">EndDocMsg</span><span class="sxs-lookup"><span data-stu-id="4bfe9-121">EndDocMsg</span></span>|<span data-ttu-id="4bfe9-122">BeginDocTest.B4200310Service_1.F4211FSEndDoc</span><span class="sxs-lookup"><span data-stu-id="4bfe9-122">BeginDocTest.B4200310Service_1.F4211FSEndDoc</span></span>|  
    |<span data-ttu-id="4bfe9-123">EndDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="4bfe9-123">EndDocResponseMsg</span></span>|<span data-ttu-id="4bfe9-124">BeginDocTest.B4200310Service_1.F4211FSEndDocResponse</span><span class="sxs-lookup"><span data-stu-id="4bfe9-124">BeginDocTest.B4200310Service_1.F4211FSEndDocResponse</span></span>|  
    |<span data-ttu-id="4bfe9-125">EndDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="4bfe9-125">EndDocSessionMsg</span></span>|<span data-ttu-id="4bfe9-126">BeginDocTest.B4200310Service_1.F4211FSEndDoc</span><span class="sxs-lookup"><span data-stu-id="4bfe9-126">BeginDocTest.B4200310Service_1.F4211FSEndDoc</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4bfe9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bfe9-127">See Also</span></span>  
 <span data-ttu-id="4bfe9-128">[工作 1： 建立連接埠](../core/task-1-create-the-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="4bfe9-128">[Task 1: Create the Ports](../core/task-1-create-the-ports2.md) </span></span>  
 <span data-ttu-id="4bfe9-129">[工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes1.md) </span><span class="sxs-lookup"><span data-stu-id="4bfe9-129">[Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes1.md) </span></span>  
 <span data-ttu-id="4bfe9-130">[工作 4： 設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape2.md) </span><span class="sxs-lookup"><span data-stu-id="4bfe9-130">[Task 4: Configure the Construct Message Shape](../core/task-4-configure-the-construct-message-shape2.md) </span></span>  
 [<span data-ttu-id="4bfe9-131">工作 5： 設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="4bfe9-131">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape1.md)