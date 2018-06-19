---
title: 函式和有 REF 資料指標 Parameters1 程序上的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6801c1e-7992-40a0-bab7-87957840cedd
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dee169bca7546c404edaccce6b7a1835e3c209a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215486"
---
# <a name="operations-on-functions-and-procedures-with-ref-cursor-parameters"></a>函式和有 REF CURSOR 參數的程序的作業
REF CURSOR 是 PL/SQL 資料類型，代表要執行的查詢產生伺服器端結果集的指標。 REF CURSOR 類型可讓輸入和輸出資料的資料流和適合用來傳輸大量資料給予或來自 PL/SQL 程式碼。 

## <a name="strongly-typed-and-weakly-typed-ref-cursors"></a>強型別和弱式類型的 REF Cursor
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]提供強型別和弱型別 (SYS_REFCURSOR) REF 資料指標，可傳遞至 PL/SQL 程序和函式做為 IN 和 OUT 參數的支援。  
  
-   **在 REF CURSOR**。 配接器用戶端必須使用在 REF CURSOR，藉由提供的 Oracle 資料庫開啟 REF CURSOR 的 PL/SQL 程式碼 （如字串）。 配接器會建立變數並將它設定為開啟的 REF CURSOR，呼叫函式或程序時使用該變數。 因此，在 REF CURSOR 參數的 PL/SQL 預存程序和函式應該表示成採取 PL/SQL 程式碼區塊做為輸入的值標示出 REF 資料指標變數的字串 「？ 」。  
  
-   **REF CURSOR 出**。 OUT REF CURSOR 參數會傳回做為強型別或弱式類型的結果集。 傳回的結果集的類型取決於是否 REF CURSOR 參數宣告強型別或弱式類型的 REF CURSOR，在預存程序或函式定義為 Oracle 伺服器上。  
  
-   **在出 REF CURSOR 參數**。  因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]模型中 REF CURSOR 參數做為字串和複雜類型的 REF CURSOR OUT 參數，它不能支援單一類型 IN OUT REF CURSOR 參數。 基於這個理由，它會將 IN OUT REF CURSOR 參數視為兩個不同的參數： 在要求訊息和回應訊息中的 OUT 參數，為 IN 參數。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)