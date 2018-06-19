---
title: 如何新增 Exception2 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions, adding messages
- messages, exceptions
- exception handling, adding messages
- fault messages, adding
ms.assetid: 9d8a3801-78cd-4c18-8deb-3fbe4a49a2f9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b2c314684094e73cb6d663bcf2183ffc3eccae5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246198"
---
# <a name="how-to-add-a-message-for-an-exception"></a><span data-ttu-id="06aa8-102">如何新增例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="06aa8-102">How to Add a Message for an Exception</span></span>
<span data-ttu-id="06aa8-103">當您第一次建立連接後端系統的連接埠時，會包含要求和回應。</span><span class="sxs-lookup"><span data-stu-id="06aa8-103">When you first create a port to the back-end system, it contains a request and a response.</span></span> <span data-ttu-id="06aa8-104">您必須新增訊息，以便將該訊息指派給錯誤。</span><span class="sxs-lookup"><span data-stu-id="06aa8-104">You must add a message so that you can assign it to the fault.</span></span>  
  
### <a name="to-add-a-fault-message"></a><span data-ttu-id="06aa8-105">若要新增錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="06aa8-105">To add a fault message</span></span>  
  
1.  <span data-ttu-id="06aa8-106">在**協調流程檢視**視窗中，以滑鼠右鍵按一下**訊息**，然後選取**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="06aa8-106">In the **Orchestration View** window, right-click **Messages**, and then select **New Message**.</span></span>  
  
     <span data-ttu-id="06aa8-107">Message_3 隨即建立，您可將它專門指派給該錯誤。</span><span class="sxs-lookup"><span data-stu-id="06aa8-107">This creates Message_3, which you can assign specifically to the fault.</span></span>  
  
2.  <span data-ttu-id="06aa8-108">以滑鼠右鍵按一下**Message_3**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="06aa8-108">Right-click **Message_3**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="06aa8-109">設定**訊息類型**，如下所示： 選取 **.NET 類別**，然後選取**System，String**</span><span class="sxs-lookup"><span data-stu-id="06aa8-109">Set the **Message Type** as follows: select **.NET Classes**, and then select **System,String**</span></span>  
  
 ![](../core/media/jdeoneworld-03-addscope.gif "JdeOneWorld_03_addscope")  
  
## <a name="see-also"></a><span data-ttu-id="06aa8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06aa8-110">See Also</span></span>  
 [<span data-ttu-id="06aa8-111">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="06aa8-111">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling1.md)