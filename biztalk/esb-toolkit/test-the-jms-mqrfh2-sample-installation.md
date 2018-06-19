---
title: 測試 JMS MQRFH2 範例安裝 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 965e985d-f0fe-4b0f-b01b-cf98d1e2f6a4
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5970f12479cddfb6a635cbd00dd139495a2f6242
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294614"
---
# <a name="test-the-jms-mqrfh2-sample-installation"></a><span data-ttu-id="81238-102">測試 JMS MQRFH2 範例的安裝</span><span class="sxs-lookup"><span data-stu-id="81238-102">Test the JMS MQRFH2 Sample Installation</span></span>
<span data-ttu-id="81238-103">您可以檢查成功安裝及操作[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]JMS MQRFH2 範例，然後再執行任何範例案例。</span><span class="sxs-lookup"><span data-stu-id="81238-103">You can check for successful installation and operation of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] JMS MQRFH2 sample before you execute any of the sample scenarios.</span></span>  
  
 <span data-ttu-id="81238-104">**若要測試 JMS MQRFH2 範例安裝**</span><span class="sxs-lookup"><span data-stu-id="81238-104">**To test the JMS MQRFH2 sample installation**</span></span>  
  
1.  <span data-ttu-id="81238-105">使用 「 RFHUtil"JMS 測試公用程式 \Source\Samples\JMS\Test\Data\Load 資料夾中的測試訊息寫入名為 ESB 佇列。JMS。範例。SENDTOBIZTALK。</span><span class="sxs-lookup"><span data-stu-id="81238-105">Use the "RFHUtil" JMS test utility to write the test messages in the \Source\Samples\JMS\Test\Data\Load folder to the queue named ESB.JMS.SAMPLE.SENDTOBIZTALK.</span></span>  
  
2.  <span data-ttu-id="81238-106">範例會將訊息傳送至目的地佇列，以及要回覆佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="81238-106">The sample sends the message to the destination queue and a copy of the message to the reply queue.</span></span>