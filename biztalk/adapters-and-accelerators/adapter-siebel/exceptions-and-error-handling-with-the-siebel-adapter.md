---
title: 例外狀況和錯誤處理 Siebel 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error handling, troubleshooting
- exceptions, troubleshooting
- troubleshooting, exceptions and error handling
ms.assetid: d46e908f-0715-43e2-879b-f5d0beb9bc64
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 743e2a0f03e35282c24a506ff37e9d774f0b7505
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221862"
---
# <a name="exceptions-and-error-handling-with-the-siebel-adapter"></a>例外狀況和錯誤處理 Siebel 配接器
## <a name="exception-list"></a>例外狀況清單
所擲回的例外狀況[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。 這些可以包含：  
  
-   內部例外狀況，也就是.NET Framework 就會擲回系統例外狀況  
  
-   LOB 用戶端程式庫會擲回 LOB 例外狀況。  
  
 如需有關內部例外狀況的詳細資訊，請參閱個別的.NET Framework 或 Siebel 文件。 例外狀況還包含詳細的錯誤訊息，可協助解決問題。 請注意，此處提到的例外狀況的清單並不完整。  
  
|Exception|可能的原因/錯誤描述|  
|---------------|---------------------------------------|  
|ConnectionException|如果無法建立連線，或關閉現有的連接至 Siebel 系統的配接器會擲回這個例外狀況。|  
|CredentialsException|如果配接器用戶端未指定使用者名稱或密碼來連接至 Siebel 系統的配接器會擲回這個例外狀況。|  
|MetadataException|如果擷取 Siebel 成品的中繼資料失敗，配接器會擲回這個例外狀況。|  
|XmlReaderParsingException|如果輸入配接器用戶端在 Siebel 系統中，叫用作業所提供的資訊不完整或不正確，則配接器會擲回這個例外狀況。|  
|XmlReaderGenerationException|無法產生輸出 Siebel 系統中執行作業時，配接器會擲回這個例外狀況。|  
|TargetSystemException|配接器擲回這個例外狀況，如果配接器使用 Siebel COM API 介面為 Siebel 系統時，擲回例外狀況。 內部例外狀況包含 Siebel COM API 所擲回的例外狀況。|  
  
## <a name="see-also"></a>另請參閱  
 [瞭解 BizTalk Adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)   
[Siebel 配接器進行疑難排解](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)