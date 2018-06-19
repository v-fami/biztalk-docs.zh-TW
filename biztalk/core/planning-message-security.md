---
title: 規劃訊息安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- planning, security
- security, messages
- security, planning
- messages, security
ms.assetid: c0f93515-a822-425c-9155-270a179d6b61
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5826db8480d378342ee30993f67bbd60e27751d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264286"
---
# <a name="planning-message-security"></a>規劃訊息安全性
基於貴公司的安全性原則，您可能需要考慮下表的問題來決定您必須在 BizTalk Server 環境中實作的安全性層級。 這些問題的答案將會決定傳訊所需的安全性功能。  
  
|問題|BizTalk Server 安全性功能|  
|--------------|-------------------------------------|  
|**當接收訊息：**||  
|您如何判定訊息傳送者的識別？|您可以使用 BizTalk 管線中的合作對象解析元件以及簽章憑證或 Windows 安全性識別碼 (SID)，來確認訊息的傳送者。 如需詳細資訊，請參閱[輸入訊息驗證](../core/inbound-message-authentication.md)。|  
|是否知道傳送訊息給您的合作對象？|您可以使用 BizTalk 管線中的合作對象解析元件，來判斷傳送訊息給您的合作對象是否為系統中既有的交易夥伴。 如需詳細資訊，請參閱[輸入訊息驗證](../core/inbound-message-authentication.md)。|  
|是否要避免從不認識的合作對象接收訊息？|您可以在連接埠中使用 [需要驗證] 功能，以要求 BizTalk Server 僅處理來自認識的合作對象的訊息。 如需詳細資訊，請參閱[輸入訊息驗證](../core/inbound-message-authentication.md)。|  
|**當傳送訊息：**||  
|您如何確保外寄訊息的私密性？|您可以加密訊息來確保只有預定的合作對象才能讀取訊息。 如需詳細資訊，請參閱[輸出訊息保護](../core/outbound-message-protection.md)。|  
|如何防止惡意的使用者在傳輸期間竄改訊息？|您可以使用數位簽章來確保訊息的完整性。 如需詳細資訊，請參閱[輸出訊息保護](../core/outbound-message-protection.md)。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [傳送和接收訊息的安全性](../core/security-for-sending-and-receiving-messages.md)  
  
-   [加密和簽章憑證](../core/encryption-and-signing-certificates.md)  
  
-   [驗證訊息的寄件者](../core/authenticating-the-sender-of-a-message.md)  
  
-   [授權訊息接收器](../core/authorizing-the-receiver-of-a-message.md)