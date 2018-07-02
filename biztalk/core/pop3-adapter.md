---
title: POP3 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- POP3 adapters, about POP3 adapters
- authenticating, POP3 adapters
- POP3 adapters
- POP3 adapters, receive adapters
- POP3 adapters, authenticating
- receive adapters, POP3 adapters
ms.assetid: 008f7fa7-60c3-4ea3-b90d-821e4029a04c
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34a5f6a73f30ba831256ce1699b9a6a77b75c102
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982791"
---
# <a name="pop3-adapter"></a>POP3 配接器
您使用「郵局通訊協定第三版」(POP3) 配接器，經由 POP3 通訊協定，將資料從裝載 POP3 信箱的伺服器擷取到執行 Microsoft BizTalk Server 的伺服器上。  
  
 POP3 配接器僅由一個接收配接器組成。 接收配接器控制了使用 POP3 配接器的接收位置。  
  
 本主題討論 POP3 接收配接器的工作流程。  
  
 **POP3 接收配接器**  
  
 POP3 接收配接器從指定的 POP3 伺服器上指定的信箱中擷取電子郵件。 依照預設，POP3 接收配接器會套用 MIME 處理到電子郵件訊息，配接器將這些訊息視為 Multipart BizTalk 訊息，下載及提交到 BizTalk Server。 POP3 接收配接器可以透過下列格式擷取及處理電子郵件：  
  
- 純文字  
  
- MIME 編碼  
  
- MIME 加密  
  
- MIME 編碼和簽署  
  
- MIME 加密和簽署  
  
  **POP3 接收配接器批次支援**  
  
  POP3 接收配接器不支援批次。  
  
  **使用 POP3 伺服器驗證**  
  
  使用 POP3 配接器時支援以下驗證方法：  
  
- **基本的。** POP3 伺服器利用使用者提供認證以進行驗證。  這些認證以純文字格式傳送。  
  
- **摘要 (APOP)。** POP3 伺服器利用摘要字串進行驗證。  
  
- **安全密碼驗證 (SPA)。** POP3 伺服器利用目前的程序認證進行驗證。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [何謂 POP3 配接器？](../core/what-is-the-pop3-adapter.md)  
  
-   [設定 POP3 配接器](../core/configuring-the-pop3-adapter.md)  
  
-   [逐步解說：建立使用 POP3 配接器的 BizTalk 應用程式](../core/walkthrough-creating-a-biztalk-application-that-uses-the-pop3-adapter.md)  
  
-   [使用 POP3 配接器處理多部分訊息](../core/processing-multi-part-messages-with-the-pop3-adapter.md)