---
title: 重複使用另一個協議屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d8e1cc60-d581-43ca-aa70-1e0d6238497a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7db2118f372014a3e8f108c1ff2273bc5aad976
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007423"
---
# <a name="reusing-properties-from-another-agreement"></a>重複使用另一個協議屬性
您可以將屬性重複運用在不同的協議上。 當新協議大部分或所有的屬性皆與現有協議的屬性相同時，這種做法可節省大量時間。 [!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)] BizTalk Server 中的使用者介面可讓您匯出成 XML 範本檔案的協議。 以後您只要匯入該 XML 範本，就能重複使用相同的協議屬性。  
  
 將協議匯出成 XML 範本會擷取到協議中大部分 (但非全部) 的屬性。 下列屬性將*不*匯出至 XML 範本檔案：  
  
-   中的所有屬性**一般屬性**頁面**一般** 索引標籤。  
  
-   中的所有屬性**連絡人**頁面**一般** 索引標籤。  
  
-   中的所有屬性**其他屬性**頁面**一般** 索引標籤。  
  
-   識別項相關的設定，從**識別碼**頁面的單向協議索引標籤。它們是：  
  
    -   **對於 X12**: ISA5、 ISA6、 ISA7、 ISA8 及其他的協議解析程式設定  
  
    -   **對於 EDIFACT**: UNB 2.1、 UNB 2.2、 UNB 3.1、 UNB 3.2 及其他的協議解析程式設定  
  
    -   **As2**: AS2-要 AS2-，以及其他的協議解析程式設定  
  
-   傳送埠關聯**傳送埠**頁面在單向協議索引標籤中的 X12、 EDIFACT 和 AS2 協議。  
  
 除去上方所列的屬性外，下列屬性都會匯出到 XML 範本檔案：  
  
-   所有 編碼通訊協定 (X12、EDIFACT 或 AS2) 相關設定。  
  
-   所有批次相關設定 (除批次識別碼外)。  
  
> [!NOTE]
>  複製 屬性到目的地協議時，將會覆寫所有適用的屬性。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [將協議屬性匯出至 XML 檔案](../core/exporting-agreement-properties-to-an-xml-file.md)  
  
-   [從 XML 檔案匯入協議屬性](../core/importing-agreement-properties-from-an-xml-file.md)  
  
## <a name="see-also"></a>請參閱  
 [設定 EDI 屬性](../core/configuring-edi-properties.md)