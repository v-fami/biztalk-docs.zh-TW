---
title: "訊息修復和新送出 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages
- resubmitting messages
- errors, messages
- messages, errors
- messages, resubmitting
ms.assetid: 5bc6bfa2-8210-4dd3-89bb-5455e294ca92
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bc15351848fe68d6ef54c31fc6d58c075bb1c58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-repair-and-new-submission"></a>Message Repair 和 New Submission
訊息修復和 New Submission 功能[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]可讓您修復 MT 與 MX 驗證失敗的訊息。 使用 MRSR SharePoint 網站 （由使用者部署），您可以看到訊息驗證的失敗。 您可以從 MRSR 網站，來開啟 InfoPath 表單，可讓您識別錯誤，修復該郵件，並提交以進行重新處理訊息。  
  
 Message Repair 和 New Submission 支援以角色為基礎的訊息修復。 完整的修復工作流程包含修復、 驗證和核准。 修復工作流程是一個部門中定義的工作流程角色 （或階段） 及設定每個角色 A4SWIFT 使用者相關聯。 每個修復角色都有個別的 MRSR 站台檢視，為角色量身訂做。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行驗證，以及使用的認證，以確保安全的程序執行角色簽署訊息，每個 A4SWIFT 使用者。  
  
 除了訊息修復 A4SWIFT 可讓您提交新訊息，使用增強[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。 第四個 A4SWIFT 使用者，建立者，執行此函式。 程序也會執行驗證，並可包含修復、 驗證和核准的角色，以確保成功送出。 A4SWIFT 處理新訊息提交到[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成一樣，它會處理已修復的訊息。  
  
 此部分包含：  
  
-   [訊息修復程序](../../adapters-and-accelerators/accelerator-swift/message-repair-process.md)  
  
-   [Message Repair 和 New Submission 建立部門和角色](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)  
  
-   [若要修復的訊息或提交新訊息使用 InfoPath 表單](../../adapters-and-accelerators/accelerator-swift/using-an-infopath-form-to-repair-a-message-or-submit-a-new-message.md)  
  
-   [在 訊息修復和新送出的特殊處理](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md)  
  
-   [修復未剖析的訊息](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)  
  
-   [訊息修復和新送出服務處理](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission-service-processing.md)