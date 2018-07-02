---
title: 例外狀況和錯誤處理與 SAP 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions and error handling
- error handling, troubleshooting
- troubleshooting, exceptions and error handling
ms.assetid: 598a25c5-6905-4c0c-835b-159d827b2269
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5439ae9cc58dfbb649fefd7ae3f18348502bcd48
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991623"
---
# <a name="exceptions-and-error-handling-with-the-sap-adapter"></a>例外狀況和錯誤處理與 SAP 配接器
會列出例外狀況，[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]會擲回。 其中可包含：  

- 內部例外狀況，也就是.NET Framework 會擲回系統例外狀況  

- LOB 用戶端程式庫會擲回 LOB 例外狀況。  

  如需有關內部例外狀況的詳細資訊，請參閱.NET Framework 或 SAP 文件。 例外狀況也會包含詳細的錯誤訊息，可能有助於解決此問題。  

## <a name="exception-descriptions"></a>例外狀況描述  

|例外狀況|可能的原因描述|  
|---------------|---------------------------------|  
|ObjectDisposedException|當配接器用戶端嘗試存取 XMLReader 的回應，已在處置之後，配接器會擲回這個例外狀況。|  
|XmlReaderGenerationException|無法從輸出訊息產生 XmlReader 時，配接器會擲回這個例外狀況。 這也可能是因為 SAP 系統從收到的資料有一些問題。 查看內部例外狀況和錯誤訊息，如需詳細資訊。|  
|InvalidUriException|當連線 URI 沒有連接字串所需的元件時，會擲回這個例外狀況。|  
|ConnectionException|無法連接至 SAP 系統時，或基礎的連接就會變成無效，原因是因為 SAP 系統上發生錯誤，或是因為發生網路問題，則會擲回這個例外狀況。|  
|TimeoutException|指定作業的逾時值失效時，會擲回這個例外狀況。 內部例外狀況包含的細節為何指定的逾時已不足夠。|  
|XmlReaderParsingException|如果它不支援指定的型別，或不正確的值指定的類型，則配接器會擲回這個例外狀況。 此外，可能不正確的輸入 XML。 不正確的值包括超出文字或最大的數字的最大數量的案例。 輸入 XML 可能不正確的作業名稱或命名空間是否正確。|  
|RFCException （衍生自 AdapterException）|如果沒有從 SAP 系統接收到錯誤，則配接器會擲回這個例外狀況。 內部例外狀況是從 SAP 系統接收到實際的例外狀況。|  
|UnsupportedOperationException|當配接器用戶端指定了無效的動作時，配接器會擲回這個例外狀況。|  
|MetadataException|如果中繼資料擷取、 瀏覽或搜尋期間發生錯誤，則配接器會擲回這個例外狀況。|  

## <a name="see-also"></a>另請參閱  
[SAP 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)