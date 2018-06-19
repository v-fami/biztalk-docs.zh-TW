---
title: 重設金鑰驗證階段 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- rekey verification
- stages, rekey verification
ms.assetid: 8a2880b6-bb25-4af5-9f51-d0b090ca38c8
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9fe163a8351b0edc904f81d77a7ea341de13df6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214198"
---
# <a name="rekey-verification-stage"></a><span data-ttu-id="b0910-102">重設金鑰驗證階段</span><span class="sxs-lookup"><span data-stu-id="b0910-102">Rekey Verification Stage</span></span>
<span data-ttu-id="b0910-103">當重設金鑰驗證階段進行訊息修復工作流程中的原始訊息複本由訊息修復和新送出與訊息的完全相同複本維護傳送的驗證器收件匣。 重設金鑰驗證。</span><span class="sxs-lookup"><span data-stu-id="b0910-103">When a Rekey Verification stage occurs in the message repair workflow, a copy of the original message is maintained by Message Repair and New Submission and an exact copy of the message is sent to the verifier's inbox for rekey verification.</span></span> <span data-ttu-id="b0910-104">在重設金鑰驗證[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Message Repair 和 New Submission 清除指定手動重新進入的欄位。</span><span class="sxs-lookup"><span data-stu-id="b0910-104">In rekey verification, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair and New Submission clears specified fields for manual re-entry.</span></span>  
  
 <span data-ttu-id="b0910-105">這個概念詳述[伺服器執行階段安全性](../../adapters-and-accelerators/accelerator-swift/server-runtime-security.md)主題。</span><span class="sxs-lookup"><span data-stu-id="b0910-105">This concept is explained further in the [Server Runtime Security](../../adapters-and-accelerators/accelerator-swift/server-runtime-security.md) topic.</span></span> <span data-ttu-id="b0910-106">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]參與重設金鑰驗證階段的使用者必須以手動方式重新輸入已清除欄位中，透過[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成，完全符合原始訊息 （從 [建立] 或 修復階段） 中的值。</span><span class="sxs-lookup"><span data-stu-id="b0910-106">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user participating in the Rekey Verification stage must manually re-enter into the cleared fields, through the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, values that exactly match those in the original message (from either the Create or Repair stage).</span></span> <span data-ttu-id="b0910-107">驗證器會簽署訊息的有效憑證，然後將訊息提交。</span><span class="sxs-lookup"><span data-stu-id="b0910-107">The verifier then signs the message with a valid certificate and submits the message.</span></span>  
  
 <span data-ttu-id="b0910-108">如果 rekeyed 欄位的值不完全符合原始訊息欄位，那麼 Message Repair 和 New Submission 時，會重設工作流程中的階段，並將訊息傳送回 repairer 收件匣。</span><span class="sxs-lookup"><span data-stu-id="b0910-108">If the values of the rekeyed fields do not match the original message fields exactly, Message Repair and New Submission resets the stage in the workflow and sends the message back to the repairer's inbox.</span></span> <span data-ttu-id="b0910-109">它也會驗證簽章的人員 rekeyed 欄位的驗證器。</span><span class="sxs-lookup"><span data-stu-id="b0910-109">It also validates the signature of the verifier who rekeyed the fields.</span></span> <span data-ttu-id="b0910-110">如果驗證器未經過驗證，它將訊息傳回的驗證器收件匣。</span><span class="sxs-lookup"><span data-stu-id="b0910-110">If the verifier is not validated, it sends the message back to the verifier's inbox.</span></span>