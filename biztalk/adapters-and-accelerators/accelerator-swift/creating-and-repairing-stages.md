---
title: "建立與修復階段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stages, repair
- stages, create
ms.assetid: 07d7ce7b-ed15-40a7-9c85-280a1d38985b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb87112775b9664badf319796e1a6243cf6eb082
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-repairing-stages"></a><span data-ttu-id="b8cc6-102">建立與修復階段</span><span class="sxs-lookup"><span data-stu-id="b8cc6-102">Creating and Repairing Stages</span></span>
<span data-ttu-id="b8cc6-103">在任何工作流程中的第一個階段可以在建立或修復的階段，也就是建立已定義為一項功能的角色，或修復。</span><span class="sxs-lookup"><span data-stu-id="b8cc6-103">The first stage in any workflow can be either a Create or Repair stage, that is, roles that have a capability defined as create or repair.</span></span> <span data-ttu-id="b8cc6-104">來自 BizTalk MessageBox 的失敗訊息的訊息或[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者手動建立透過訊息[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。</span><span class="sxs-lookup"><span data-stu-id="b8cc6-104">The message originates from the BizTalk MessageBox as a failed message or an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user manually creates a message through the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms.</span></span>  
  
 <span data-ttu-id="b8cc6-105">原始訊息的建立者或 repairer 是訊息的第一個數位簽署，並將其數位簽章[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]建立或修復訊息之後的表單。</span><span class="sxs-lookup"><span data-stu-id="b8cc6-105">The original message creator or repairer is the first digital signer of the message, and adds his or her digital signature to the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form after creating or repairing the message.</span></span> <span data-ttu-id="b8cc6-106">此第一個簽章不僅證明 repairer，之訊息的建立者的身分識別，也會鎖定在目前的狀態訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="b8cc6-106">This first signature not only proves the identity of the message creator or repairer, but also locks the contents of the message in its current state.</span></span> <span data-ttu-id="b8cc6-107">如果訊息第一個登入後變更，數位簽章堆疊已中斷，並且會顯示警告，指出表單上的數位簽章無效的使用者。</span><span class="sxs-lookup"><span data-stu-id="b8cc6-107">If the message is altered after the first signing, the digital signature stack is broken and warnings are shown to the user stating that the digital signatures on the form are invalid.</span></span>