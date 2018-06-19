---
title: 例外狀況和錯誤處理與 SAP 配接器 |Microsoft 文件
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
ms.openlocfilehash: 043f76f7fc730430610b7598bbab208ca8b135a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216846"
---
# <a name="exceptions-and-error-handling-with-the-sap-adapter"></a>例外狀況和錯誤處理與 SAP 配接器
會列出例外狀況，[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]會擲回。 這些可以包含：  
  
-   內部例外狀況，也就是.NET Framework 就會擲回系統例外狀況  
  
-   LOB 用戶端程式庫會擲回 LOB 例外狀況。  
  
 如需有關內部例外狀況的詳細資訊，請參閱.NET Framework 或 SAP 文件。 例外狀況也會包含可能有助於解決此問題的詳細的錯誤訊息。  

## <a name="exception-descriptions"></a>例外狀況的描述  
|Exception|可能的原因描述|  
|---------------|---------------------------------|  
|ObjectDisposedException|配接器用戶端嘗試存取已在處置之後的 XMLReader 的回應時，配接器會擲回這個例外狀況。|  
|XmlReaderGenerationException|無法從輸出訊息產生 XmlReader 時，配接器會擲回這個例外狀況。 這也可能是因為從 SAP 系統接收的資料發生一些問題。 查看內部例外狀況和錯誤訊息，如需詳細資訊。|  
|InvalidUriException|URI 的連接沒有必要的元件，連接字串時，會擲回這個例外狀況。|  
|ConnectionException|當連接到 SAP 系統問題，或是基礎的連接就會變成無效，原因是因為 SAP 系統上發生錯誤，或是因為發生網路問題，則會擲回這個例外狀況。|  
|「 逾時|指定作業的逾時值屆滿時，會擲回這個例外狀況。 內部例外狀況包含指定的逾時的原因不足夠的細節。|  
|XmlReaderParsingException|如果不支援指定的型別，或不正確的值指定的類型，則配接器會擲回這個例外狀況。 此外，輸入 XML 可能不正確。 不正確的值包含超出文字或最大的數字的最大數量的情況。 輸入 XML 可能不正確的作業名稱或命名空間是否正確。|  
|RFCException （衍生自 AdapterException）|如果沒有從 SAP 系統接收到錯誤，則配接器會擲回這個例外狀況。 內部例外狀況是實際從 SAP 系統接收到的例外狀況。|  
|UnsupportedOperationException|當配接器用戶端指定無效的動作時，配接器會擲回這個例外狀況。|  
|MetadataException|如果擷取中繼資料中，瀏覽或搜尋期間發生錯誤，則配接器會擲回這個例外狀況。|  
  
## <a name="see-also"></a>另請參閱  
[SAP 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)