---
title: 修復訊息並提交新訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- repairing messages
- Message Repair and New Submission
- submitting, messages
- submitting, Message Repair and New Submission
- messages, Message Repair and New Submission
- messages, submitting
- Message Repair and New Submission. about Message Repair and New Submission
ms.assetid: 6abcce90-f611-422a-b3c8-e25f1e75b039
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 569ab44588c2bd89c3533af8cc765e58f743a229
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003311"
---
# <a name="repairing-messages-and-submitting-new-messages"></a>修復訊息並提交新訊息
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair 和 New Submission 可讓您修復 XML 或商務規則引擎的驗證失敗的訊息。 修復程序包含驗證和核准步驟，以確保精確度和訊息修復恰當。 使用 Microsoft 來執行此程序[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] MRSR 站台內的表單。  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 也可讓您提交新訊息，使用此程序。 建立者提交的訊息，而且工作流程可以包含 repairer、 驗證器，並執行相同的工作，如訊息修復所示的核准者。  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 藉由指派不同的使用者執行每項工作，可確保此程序的安全性。 您指派適當的修復、 確認，或核准每個這些使用者的角色和每個使用者必須使用特定的認證來執行工作。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 也支援部門的使用中處理訊息修復和提交訊息。 每個部門牽涉到特定的工作流程的一組特定的訊息上執行的工作。 在任何建立修復、 確認，或核准步驟，當您送出訊息，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]呼叫 BRE 驗證，並確認使用者適當的部門的成員。 如需有關訊息 repair 和 new submission 的詳細資訊，請參閱 <<c0> [ 訊息修復和 New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md)。  
  
 如果您接收未剖析的訊息，Message Repair 和 New Submission 顯示訊息，並在失敗的描述，[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單，並可讓您列印訊息，或將它儲存至檔案。 您可以修復，然後重新提交訊息。 不過，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]不會呼叫 BRE 驗證或檢查在部門的成員資格，當您送出您修復未剖析的訊息。 此外，重新提交未剖析的訊息未驗證或認可。 如需有關未剖析的訊息的詳細資訊，請參閱[修復未剖析的訊息](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)。  
  
 此部分包含：  
  
-   [修復訊息](../../adapters-and-accelerators/accelerator-swift/repairing-a-message.md)  
  
-   [驗證訊息](../../adapters-and-accelerators/accelerator-swift/verifying-a-message.md)  
  
-   [核准訊息](../../adapters-and-accelerators/accelerator-swift/approving-a-message.md)  
  
-   [處理未剖析的訊息](../../adapters-and-accelerators/accelerator-swift/handling-an-unparsed-message.md)  
  
-   [建立和提交新的訊息](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md)  
  
-   [建立新的訊息範本](../../adapters-and-accelerators/accelerator-swift/creating-a-new-message-template.md)