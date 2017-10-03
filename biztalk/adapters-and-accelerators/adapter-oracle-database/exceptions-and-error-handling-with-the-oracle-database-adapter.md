---
title: "例外狀況和錯誤處理與 Oracle 資料庫配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exception, LOB
- exception, inner
- exceptions, error handling
- error handling, exceptions
ms.assetid: df9a1244-63cd-438e-8a06-99383fbeba2c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bd85c53a1e13d127883e463cafec742f2751722
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="exceptions-and-error-handling-with-the-oracle-database-adapter"></a>例外狀況和錯誤處理與 Oracle 資料庫配接器
此區段會列出例外狀況，[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]會擲回。 這些可以包含：  
  
-   內部例外狀況，也就是.NET Framework 就會擲回系統例外狀況。  
  
-   LOB 用戶端程式庫會擲回 LOB 例外狀況。  
  
 如需有關內部例外狀況的詳細資訊，請參閱個別的.NET Framework 或 Oracle 文件。 例外狀況也會包含詳細的錯誤訊息，可協助解決問題。  
  
|Exception|可能的原因描述|  
|---------------|---------------------------------|  
|XmlReaderParsingException|如果不支援指定的型別，或不正確的值指定的類型，則配接器會擲回這個例外狀況。 此外，輸入 XML 可能不正確。 不正確的值包含超出文字或最大的數字的最大數量的情況。 輸入 XML 可能不正確的作業名稱或命名空間是否正確。|  
|UnsupportedOperationException|當配接器用戶端指定無效的動作時，配接器會擲回這個例外狀況。|  
|ArgumentException|如果引數指定了不正確的值，則配接器會擲回這個例外狀況。|  
|NotImplementedException|如果沒有實作一些方法 XMLReader 讀取器中的，配接器會擲回這個例外狀況。|  
|ArgumentNullException|如果未指定必要的引數，則配接器會擲回這個例外狀況。|  
|ArgumentOutOfRangeException|如果它嘗試存取不存在實體或超出範圍的實體介面卡，就會擲回這個例外狀況。|  
|XmlReaderGenerationException|無法從輸出訊息產生 XmlReader 時，配接器會擲回這個例外狀況。|  
|MetadataException|如果擷取中繼資料中，瀏覽或搜尋期間發生錯誤，則配接器會擲回這個例外狀況。|  
|CredentialsException|如果發生問題的擷取，或使用安全性權杖，或未指定必要的認證，則配接器會擲回這個例外狀況。|  
|InvalidUriException|如果連線 URI 沒有連接字串的必要的元件，則配接器會擲回這個例外狀況。|  
|ConnectionException|如果沒有連接到 Oracle 資料庫使用 ODP.NET 時發生問題，則配接器會擲回這個例外狀況。 內部例外狀況包含 Oracle 例外狀況。|  
|「 逾時|如果指定作業的逾時值屆滿，配接器會擲回這個例外狀況。 內部例外狀況包含指定的逾時的原因不足夠的細節。|  
|ListenerException|如果在從目標系統接收訊息的問題，則配接器會擲回這個例外狀況。 此訊息表示 Oracle 接聽程式與相關的問題。 內部例外狀況有問題的細節。|  
|TargetSystemException|如果 Oracle 傳回錯誤或無效的回應，則配接器會擲回這個例外狀況。 內部例外狀況包含 Oracle 執行階段例外狀況。|  
|InvalidOperationException|如果配接器嘗試執行無效的作業在目標系統上，配接器會擲回這個例外狀況。 內部例外狀況包含無效的作業正在執行的細節。|  
|OverflowException|配接器擲回這個例外狀況時執行包含在資料集或弱式類型的 REF CURSOR 的 Oracle 數值資料類型的作業時，無法放入個別的.NET 型別之這些 Oracle 數值資料類型指定較大的值。|  
  
## <a name="see-also"></a>另請參閱  
[Oracle 資料庫配接器進行疑難排解](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)