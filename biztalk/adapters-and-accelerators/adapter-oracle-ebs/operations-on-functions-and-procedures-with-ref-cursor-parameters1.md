---
title: 函式和程序的 REF CURSOR Parameters1 作業 |Microsoft Docs
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
ms.openlocfilehash: f7227d6fd100714c0b467f0b43537b364af98d37
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978647"
---
# <a name="operations-on-functions-and-procedures-with-ref-cursor-parameters"></a>函式和含有 REF CURSOR 參數的程序作業
REF 資料指標是表示執行查詢所產生的伺服器端結果集的指標的 PL/SQL 資料類型。 REF CURSOR 類型可讓輸入和輸出資料的資料流，而且非常適用於傳輸大量資料的 PL/SQL 程式碼。 

## <a name="strongly-typed-and-weakly-typed-ref-cursors"></a>強型別和弱型別 REF Cursor
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]提供強型別和弱型別 (SYS_REFCURSOR) REF 資料指標可傳遞至 PL/SQL 程序和函式做為輸入和輸出參數的支援。  
  
- **REF 資料指標中**。 配接器用戶端必須使用在 REF CURSOR，藉由提供的 Oracle 資料庫開啟 REF CURSOR PL/SQL 程式碼 （如字串）。 配接器會建立變數並將它設定為開啟的 REF CURSOR 和呼叫的函式或程序時使用該變數。 因此，在 REF CURSOR 參數的 PL/SQL 預存程序和函式應表示為採用，PL/SQL 程式碼區塊做為輸入的值將標示出 「 REF 資料指標變數的字串 「？ 」。  
  
- **REF CURSOR 出**。 OUT REF CURSOR 參數會傳回為強型別或弱式型別結果集。 傳回的結果集的類型取決於是否 REF CURSOR 參數會宣告為強型別或弱式類型的 REF CURSOR 的預存程序或函式定義在 Oracle 伺服器上。  
  
- **在出 REF CURSOR 參數**。  因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]模型中 REF CURSOR 參數做為字串和出 REF CURSOR 參數做為複雜型別，它不能支援單一類型中出 REF CURSOR 參數。 基於這個理由，它會將 IN 出 REF CURSOR 參數視為兩個不同的參數: 「 要求 」 訊息和回應訊息中的 OUT 參數中為 IN 參數。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)