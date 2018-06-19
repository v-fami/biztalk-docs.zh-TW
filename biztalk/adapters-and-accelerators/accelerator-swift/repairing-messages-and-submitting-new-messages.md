---
title: 修復訊息並提交新訊息 |Microsoft 文件
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
ms.openlocfilehash: 59ece524ce06430492a3927c0cd1437eef4b216d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214022"
---
# <a name="repairing-messages-and-submitting-new-messages"></a>修復訊息並提交新的訊息
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Message Repair 和 New Submission 可讓您修復 XML 或商務規則引擎的驗證失敗的訊息。 修復程序包括驗證和核准步驟可確保精確度和訊息修復恰當。 使用執行此程序[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] MRSR 站台內的表單。  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]也可讓您提交新訊息，使用此程序。 建立者提交訊息，並在工作流程包括 repairer、 驗證器，以及執行相同的工作，如訊息修復所示的核准者。  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]藉由指定不同的使用者執行每項工作，可確保此程序的安全性。 指派適當的修復、 驗證，或核准給這些使用者，每個角色，每位使用者必須使用特定的認證來執行工作。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]也支援在處理中的部門使用修復和提交訊息。 每個部門牽涉到特定的一組特定的訊息上執行的工作流程。 在建立任一，修復、 驗證，或核准步驟中，當您送出訊息，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]呼叫 BRE 驗證，並確認使用者是否適當部門的成員。 如需訊息 repair 和 new submission 的詳細資訊，請參閱[訊息修復和 New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md)。  
  
 如果您接收未剖析的訊息，訊息修復和 New Submission 顯示訊息和失敗的描述[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單，並可讓您列印訊息，或將它儲存至檔案。 您可以修復，然後再重新送出訊息。 不過，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]不呼叫 BRE 驗證或檢查在部門的成員資格，當您送出您修復未剖析的訊息。 此外，重新提交未剖析的訊息未驗證或認可。 如需剖析訊息的詳細資訊，請參閱[修復未剖析訊息](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)。  
  
 此部分包含：  
  
-   [修復訊息](../../adapters-and-accelerators/accelerator-swift/repairing-a-message.md)  
  
-   [確認訊息](../../adapters-and-accelerators/accelerator-swift/verifying-a-message.md)  
  
-   [核准訊息](../../adapters-and-accelerators/accelerator-swift/approving-a-message.md)  
  
-   [處理未剖析的訊息](../../adapters-and-accelerators/accelerator-swift/handling-an-unparsed-message.md)  
  
-   [建立及提交新的訊息](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md)  
  
-   [建立新的郵件範本](../../adapters-and-accelerators/accelerator-swift/creating-a-new-message-template.md)